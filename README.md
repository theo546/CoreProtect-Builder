<div align="center">
  <img src="logo.svg" width="120" height="120" alt="CoreProtect Builder Logo">
  <h1>CoreProtect Builder</h1>

  <p>
    <a href="https://github.com/theo546/CoreProtect-builder/releases/download/nightly/coreprotect.jar">
      <img src="https://img.shields.io/badge/Download-Latest%20Build-blue?style=for-the-badge&logo=github" alt="Download Latest Build">
    </a>
  </p>
  <p>
    <a href="https://github.com/theo546/CoreProtect-builder/releases/download/nightly/coreprotect.jar"><strong>Direct Download (coreprotect.jar)</strong></a>
  </p>
</div>

This repository automatically builds the latest version of [CoreProtect](https://github.com/PlayPro/CoreProtect) and releases it as a pre-release.

## How it works

1.  A GitHub Action runs every day.
2.  It checks the latest commit on the official CoreProtect repository.
3.  It checks if a build is necessary:
    *   It checks for the latest existing release in this repository.
    *   If no release exists (first run), it builds.
    *   If a release exists, it compares the git diff between the last built SHA and the current upstream SHA.
    *   **It only triggers a new build if `.java` files have changed.** This avoids useless builds for README updates or other non-code changes.
4.  If a build is required:
    *   Clones the repository.
    *   Patches `pom.xml` to set the branch to `development`.
    *   Builds the JAR using Maven (JDK 21).
    *   Creates a new GitHub Release with the tag `build-<commit-hash>`.
    *   Uploads the `coreprotect.jar`.
    *   **Cleanup**: Automatically deletes old releases to keep only the 5 most recent ones.

## Usage

Check the [Releases](../../releases) page for the latest builds.
