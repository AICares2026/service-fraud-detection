## Stack
- Kotlin (primary language)
- Docker (containerisation tooling)
- Versions not detectable from repository metadata

## Constraints
Never modify:
- `*.lock` files (Gradle lockfiles, any lock format present)
- `gradlew`, `gradlew.bat`, `gradle/wrapper/gradle-wrapper.jar`, `gradle/wrapper/gradle-wrapper.properties`
- Any file under `src/main/resources/db/migration/` or `src/*/db/migration/` (Flyway/Liquibase migrations)
- Credential or secret files: `*.env`, `.env*`, `*secret*`, `*credentials*`
- Generated code directories: `build/`, `.gradle/`

## Conventions
- Kotlin source lives under `src/main/kotlin/`
- Tests live under `src/test/kotlin/`; test classes are named `*Test.kt`
- Dockerfiles are expected to follow hardened best practices: non-root USER, pinned base image digests, no secrets in ENV/ARG
- `docker-compose` files must pass lint checks before committing

## Dependency manifests
- `build.gradle.kts` or `build.gradle` — primary dependency declarations
- `settings.gradle.kts` or `settings.gradle` — project structure
- `gradle/libs.versions.toml` — version catalogue if present
- `Dockerfile` — base image versions must be pinned by digest
