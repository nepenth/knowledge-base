
## Planning
### Overview
Netflix Engineering uses JIRA for planning and Confluence for documentation. JIRA is a project management tool that helps teams plan, track, and deliver software projects. Confluence is a collaboration platform that enables teams to create, share, and store knowledge and documents.
### Example Use Case
For example, when a new feature is proposed, the development team creates a JIRA ticket to track the progress of the feature. The team then uses Confluence to document the design, architecture, and implementation details of the feature.

## Coding
### Overview
Java is the primary programming language for the backend service, while other languages are used for different use cases. Netflix also uses a variety of frameworks and libraries to support its services.
### Example Code (Java)
```java
// Example Java code for a simple RESTful API
import javax.ws.rs.GET;
import javax.ws.rs.Path;
import javax.ws.rs.Produces;
import javax.ws.rs.core.MediaType;

@Path("/api")
public class MyResource {
    @GET
    @Produces(MediaType.TEXT_PLAIN)
    public String getMessage() {
        return "Hello, World!";
    }
}
```
### Key Points

* Java is the primary programming language for backend services
* Other languages are used for different use cases
* Frameworks and libraries are used to support services

## Build
### Overview
Gradle is mainly used for building, and Gradle plugins are built to support various use cases. Gradle is a build tool that helps teams automate the build process and manage dependencies.
### Example Build Script (Gradle)
```groovy
// Example Gradle build script
plugins {
    id 'java'
}

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web:2.5.4'
}
```
### Key Points

* Gradle is used for building and managing dependencies
* Gradle plugins are used to support various use cases

## Packaging
### Overview
Package and dependencies are packed into an Amazon Machine Image (AMI) for release. This enables Netflix to deploy its services quickly and reliably.
### Example Code (Packer)
```json
// Example Packer configuration file
{
    "builders": [
        {
            "type": "amazon-ebs",
            "region": "us-west-2",
            "source_ami": "ami-abcd1234",
            "instance_type": "t2.micro",
            "ssh_username": "ec2-user"
        }
    ],
    "provisioners": [
        {
            "type": "shell",
            "script": "setup.sh"
        }
    ]
}
```
### Key Points

* Packages and dependencies are packed into an AMI for release
* Packer is used to create the AMI

## Testing
### Overview
Testing emphasizes the production culture's focus on building chaos tools. Netflix uses a variety of testing frameworks and tools to ensure its services are reliable and scalable.
### Example Test Code (JUnit)
```java
// Example JUnit test code
import org.junit.Test;
import static org.junit.Assert.assertEquals;

public class MyTest {
    @Test
    public void testMyMethod() {
        // Test code here
        assertEquals(2, 1 + 1);
    }
}
```
### Key Points

* Testing is emphasized in the production culture
* Chaos tools are used to ensure services are reliable and scalable

## Deployment
### Overview
Netflix uses its self-built Spinnaker for canary rollout deployment. Spinnaker is a continuous delivery platform that enables teams to deploy software quickly and reliably.
### Example Code (Spinnaker)
```yml
# Example Spinnaker configuration file
applications:
  - name: my-app
    clusters:
      - name: my-cluster
        account: my-account
        region: us-west-2
```
### Key Points

* Spinnaker is used for canary rollout deployment
* Spinnaker enables teams to deploy software quickly and reliably

## Monitoring
### Overview
The monitoring metrics are centralized in Atlas, and Kayenta is used to detect anomalies. Atlas is a monitoring platform that provides real-time insights into system performance.
### Example Code (Atlas)
```json
// Example Atlas configuration file
{
    "metric": {
        "name": "my-metric",
        "type": "counter",
        "description": "My metric"
    }
}
```
### Key Points

* Monitoring metrics are centralized in Atlas
* Kayenta is used to detect anomalies

## Incident Report
### Overview
Incidents are dispatched according to priority, and PagerDuty is used for incident handling. PagerDuty is an incident management platform that enables teams to respond quickly and effectively to incidents.
### Example Code (PagerDuty)
```json
// Example PagerDuty configuration file
{
    "service": {
        "name": "my-service",
        "description": "My service"
    },
    "escalation_policy": {
        "name": "my-escalation-policy",
        "description": "My escalation policy"
    }
}
```
### Key Points

* Incidents are dispatched according to priority
* PagerDuty is used for incident handling

## Conclusion
The Netflix tech stack is a robust and scalable CI/CD pipeline that enables the company to deliver high-quality software quickly and reliably. This knowledge base entry provides an overview of the main concepts, examples, key points, and takeaways related to the Netflix tech stack.

## References
* [Netflix Engineering Blog](https://netflixtechblog.com/)
* [Spinnaker Documentation](https://www.spinnaker.io/docs/)
* [Atlas Documentation](https://atlas-docs.readthedocs.io/en/latest/)
* [PagerDuty Documentation](https://developer.pagerduty.com/api-reference/)

---
**Source**: [Original Tweet](https://twitter.com/i/web/status/1910913333945086365)