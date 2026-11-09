# Lab 6: Set Up Nexus Repository and Configure User Access

**Student (GitHub username):** amnajaved-dev1
**Environment:** Ubuntu server (`amnajaved-dev1@ubuntu`), Docker, IntelliJ IDEA (Lab 5 environment)
**Nexus URL:** `http://192.168.154.128:8006`

## Overview
This lab runs Sonatype Nexus Repository in Docker with persistent storage, secures it with a restricted user and role, publishes Gradle and Maven snapshot artifacts to it, queries it through the REST API, and manages blob storage and cleanup.

## Directory Structure
```
DevOps/
└── Labs/
    └── Lab06/
        ├── README.md
        ├── Lab6_Solution.pdf
        ├── images/              # Instructor reference images
        └── screenshots/         # My evidence screenshots
```

## Tasks Completed
| Task | Description |
|------|-------------|
| 1 | Ran Nexus in Docker (`nexus-data` volume, ports 8006 and 8007), completed the setup wizard, disabled anonymous access |
| 2 | Created the `nx-java` role (`nx-repository-view-maven2-maven-snapshots-*`) and the active `nexus` user, verified via the Status API |
| 3 | Configured `java-app` (Gradle, `maven-publish`), built `my-app-1.0-SNAPSHOT.jar` and published it to `maven-snapshots` |
| 4 | Configured `java-maven-app` (`distributionManagement`, `settings.xml`), ran `mvn package` and `mvn deploy` |
| 5 | Queried repositories (as `nexus` and `admin`) and components through the REST API |
| 6 | Inspected the default blob store, created the `mystore` blob store and the `docker-hosted` repository (port 8007) |
| 7 | Created and attached the `maven` cleanup policy, ran the cleanup service, then compacted the default blob store |

## Screenshots (`screenshots/`)
**Task 1:** `nexus_container_running.png`
**Task 2:** `nexus_user_access.png`
**Task 3:** `gradle_nexus_configuration.png`, `gradle_nexus_build.png`, `gradle_nexus_publish.png`, `nexus_gradle_artifact.png`
**Task 4:** `maven_nexus_project.png`, `maven_distribution_management.png`, `maven_package_nexus.png`, `maven_deploy_nexus.png`, `nexus_maven_artifact.png`
**Task 5:** `nexus_repositories_user.png`, `nexus_repositories_admin.png`, `nexus_components_list.png`, `nexus_component_details.png`
**Task 6:** `nexus_default_blob_content.png`, `nexus_mystore_created.png`, `nexus_blob_directories.png`, `nexus_docker_hosted_repository.png`
**Task 7:** `nexus_cleanup_policy_created.png`, `nexus_cleanup_policy_attached.png`, `nexus_cleanup_task_waiting.png`, `nexus_cleanup_task_completed.png`, `nexus_maven_snapshots_empty.png`, `nexus_blob_store_before_compaction.png`, `nexus_compact_task_configured.png`, `nexus_compact_task_completed.png`, `nexus_blob_store_after_compaction.png`

The full write-up with captions, in task order, is in [`Lab6_Solution.pdf`](Lab6_Solution.pdf).

## Security Notes
- No Nexus password, `admin.password` value or token appears in any screenshot or file.
- `gradle.properties` and `~/.m2/settings.xml` hold the deployment credentials and are **not** committed.
- curl commands use `-u <user>` so the password is prompted for, not typed in the command.

## Notes
- The `nexus` container and the `nexus-data` volume are kept for the next lab.
- `allowInsecureProtocol = true` is used only because this classroom Nexus runs over HTTP.
