# Lab 5: Build, Test, and Package Applications with IntelliJ IDEA and Docker

This repository contains the complete documentation, solution report, and evidence screenshots for **Lab 05**, covering containerized development, build tools (Maven, Gradle, npm, Webpack), testing, packaging, and pipeline configuration.

## Repository Structure

```text
DevOps/
└── Labs/
    └── Lab05/
        ├── README.md
        ├── Lab5_Solution.pdf
        └── screenshots/
            ├── intellij_repo_clone.png
            ├── intellij_running.png
            ├── intellij_desktop.png
            ├── maven_project_clone.png
            ├── maven_installed.png
            ├── maven_package.png
            ├── maven_elasticsearch_dependency.png
            ├── maven_repackage.png
            ├── maven_test.png
            ├── maven_jar.png
            ├── maven_running.png
            ├── maven_stopped.png
            ├── maven_project_closed.png
            ├── gradle_project_clone.png
            ├── gradle_build.png
            ├── gradle_elasticsearch_dependency.png
            ├── gradle_rebuild.png
            ├── gradle_jar.png
            ├── gradle_running.png
            ├── gradle_stopped.png
            ├── gradle_project_closed.png
            ├── node_project_clone.png
            ├── nodejs_installed.png
            ├── npm_install.png
            ├── node_running.png
            ├── node_browser.png
            ├── npm_test.png
            ├── npm_pack.png
            ├── react_node_project_clone.png
            ├── react_api_dependencies.png
            ├── react_api_build.png
            ├── react_api_bundle.png
            ├── jenkins_pipeline_file.png
            └── jenkins_pipeline_success.png
Task Summary & Implementation Details
Task 1: Clone and Launch IntelliJ IDEA
Cloned the course IntelliJ Docker repository and launched the container environment via Docker Compose.

Verified access to the Webtop desktop interface and IDE terminal.

Task 2: Build and Run the Maven Project
Cloned java-maven-app (/config/IdeaProjects/java-maven-app).

Installed Maven inside the container and packaged the application (mvn package).

Added the Elasticsearch 7.0.0 dependency to pom.xml, synchronized changes, ran tests, and successfully generated the executable JAR (target/java-maven-app-1.1.0-SNAPSHOT.jar).

Task 3: Build and Run the Gradle Project
Cloned java-app (/config/IdeaProjects/java-app).

Configured the project and Gradle JVM to use JDK 16.

Added Elasticsearch 7.0.0 to build.gradle, synchronized via the Gradle Wrapper, and built the project (./gradlew build).

Verified and executed the generated JAR (build/libs/java-app-1.0-SNAPSHOT.jar).

Task 4: Install and Run the Node.js Project
Cloned node-project (/config/IdeaProjects/node-project).

Installed Node.js and npm, and installed project dependencies (npm install) inside the app directory.

Resolved port conflicts by updating server.js to run on port 4000 (app.listen(4000)).

Ran Jest unit tests (npm test) and created the distribution tarball (bootcamp-node-project-1.0.0.tgz) via npm pack.

Task 5: Build the React and Node.js API Artifact
Cloned react-nodejs-example (/config/IdeaProjects/react-nodejs-example).

Installed dependencies inside the api directory (npm install).

Built the Webpack bundle using the legacy OpenSSL provider (NODE_OPTIONS=--openssl-legacy-provider npm run build) to generate api/server.bundle.js.

Inspected the bundled output using cat server.bundle.js | more.
Task 6: Create a Jenkins Pipeline for Node.js Project
Verified the project Jenkinsfile containing automated pipeline stages (test, build jar, build image).

Validated pipeline execution and successfully ran the test suite (PASS ./server.test.js).
---
