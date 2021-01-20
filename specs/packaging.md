# Packaging

Every langauge has its own way to publish and import library. We should deliver SDK library by a widely accepted tool for the language.

For example:
* Java is published by Maven central repository: https://search.maven.org/artifact/com.diem/client-sdk-java
* Python is published by pypi: https://pypi.org/project/diem
* Golang is published by codebase url.

The packaging, publishing and releasing process should be mostly automatic, and can be triggered by minimum manual steps. Use github action for automation and github repository secrets for private keys.
API reference should also be published, and added to https://developers.diem.com/docs/sdks/overview.
