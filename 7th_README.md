## Maven Automation Script

This script automates common Maven tasks such as building artifacts, installing them into the local repository, running static code analysis, generating reports, executing plugins, and deploying the application to Tomcat. It also verifies and installs required tools such as Java, Maven, and Tomcat if they are missing.

### Usage
```bash
./buildMaven.sh [-a] [-i] [-s <tool>] [-t <plugin>] [-d] [-r <report>]
```

### Options

| Option | Description |
|--------|-------------|
| -a | Generate artifact (WAR file) |
| -i | Install artifact to local repository |
| -s <tool> | Run static code analysis (checkstyle, findbugs, pmd) |
| -t <plugin> | Run tests or Maven plugins (owasp, junit, cobertura, etc.) |
| -d | Deploy the generated WAR to Tomcat9 |
| -r <report> | Generate reports (pmd, checkstyle, findbugs) |

### Project Directory

The script clones the project if it does not already exist:
```bash
$HOME/spring3hibernate
```
### Auto-Installed Dependencies

The script checks and installs the following if not present:

- OpenJDK 11  
- Maven  
- Tomcat9  

### Features

#### Build Artifact
```bash
./buildMaven.sh -a
```

#### Install Artifact
```bash
./buildMaven.sh -i
```

#### Static Code Analysis
```bash
./buildMaven.sh -s checkstyle
./buildMaven.sh -s pmd
./buildMaven.sh -s findbugs
```

#### Run Plugins or Unit Tests
```bash
./buildMaven.sh -t junit
./buildMaven.sh -t owasp
./buildMaven.sh -t cobertura
```
#### Generate Reports
```bash
./buildMaven.sh -r javadoc
./buildMaven.sh -r pmd
./buildMaven.sh -r checkstyle
./buildMaven.sh -r findbugs
```

#### Deploy Artifact to Tomcat9
```bash
./buildMaven.sh -d
```

Application will be available at:
```bash
http://localhost:8080/Spring3HibernateApp
```

### Example Combined Commands

#### Build, test, and deploy
```bash
./buildMaven.sh -a -t junit -d
```

#### Run analysis and generate reports
```bash
./buildMaven.sh -s pmd -r pmd
./buildMaven.sh -s checkstyle -r checkstyle
```

### Notes

- Ensure required plugins/tools are configured in the project's pom.xml.  
- Tomcat deployment requires sudo access.  
