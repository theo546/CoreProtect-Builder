# CoreProtect Builder

This repository automatically builds the latest version of [CoreProtect](https://github.com/PlayPro/CoreProtect) and releases it as a pre-release.

## How it works

1.  A GitHub Action runs every hour.
2.  It checks the latest commit on the official CoreProtect repository.
3.  If a release for that commit doesn't exist here, it:
    *   Clones the repository.
    *   Builds the JAR using Maven (JDK 21).
    *   Creates a new GitHub Release with the tag `build-<commit-hash>`.
    *   Uploads the `coreprotect.jar`.

## Usage

Check the [Releases](../../releases) page for the latest builds.
