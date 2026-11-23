Forked from [cptactionhank's jira service desk repo](https://github.com/cptactionhank/docker-atlassian-jira-service-desk) to meet ACP’s specific requirements.

## Isolated JDBC investigation

`test/Dockerfile.jdbc8` derives from the production image digest and replaces
Connector/J 5.1.38 with the experimental 8.0.33 candidate. Jira 4.22.2 and Java
8u212 remain unchanged. This is not a supported-platform or security-remediation
claim; confirm the driver recommendation before production use.

Build and verify locally without publishing:

```sh
docker build --platform linux/amd64 -f test/Dockerfile.jdbc8 -t jira-jdbc-test:local .
docker run --rm --platform linux/amd64 --entrypoint sh jira-jdbc-test:local -c 'java -version; find /opt/atlassian/jira/lib -name "*mysql*.jar"'
```

Drone builds this Dockerfile on pushes to `mysql8-test`, using the existing scan
step. Only tags matching `v4.22.2-jdbc8-test-*` use the dedicated test publisher.
Other branches and tags retain their existing build selection. The root
Dockerfile is not used for this controlled comparison.

Before publishing, obtain repository approval, confirm Drone is active with the
existing registry secret, and review the branch build and scan. Tag the reviewed
commit using a new unused test tag. Never overwrite `v4.22.2-1`. Tag publication
rebuilds the image and does not itself run the push-event scan; verify and scan
the published digest through the approved process before deployment.

Deploy that digest only in `acp-test_ACP/jira-jdbc-test` by changing the image in
`test/jira-baseline.yaml`. No image is published or deployed by editing these
files. Leave production and the existing `service-desk` test instance unchanged.

Database credentials must remain outside Git. Configure MySQL 8 and verified TLS
for the dedicated database user. Adding the connector alone does not configure
Jira's JDBC TLS trust; the Java truststore needs the approved RDS CA chain.
