# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed

- Migrate to App Build Suite (ABS)
- Update CircleCI config to use app-build-suite executor
- Add serviceType to values.yaml
- Update Chart.yaml with proper versioning and metadata

## [0.1.3] - 2023-12-11

### Changed

- Configure `gsoci.azurecr.io` as the default container image registry.

## [0.1.2] - 2023-10-31

### Changed

- Make app PSS compliant.

## [0.1.1] - 2023-04-24

### Added

- Add icon to chart metadata

## [0.1.0] - 2023-02-06

### Changed

- Push `Jiralert` app to GiantSwarm catalog.

## [0.0.3] - 2022-07-08

### Changed

- Updated `Jiralert` to version 1.2. This version adds the auto-resolve feature.

## [0.0.2] - 2022-05-16

### Changed

- Removed sample credentials to allow external secrets.

## [0.0.1] - 2022-04-29

- Add Jiralert app chart

[Unreleased]: https://github.com/giantswarm/jiralert-app/compare/v0.1.3...HEAD
[0.1.3]: https://github.com/giantswarm/jiralert-app/compare/v0.1.2...v0.1.3
[0.1.2]: https://github.com/giantswarm/jiralert-app/compare/v0.1.1...v0.1.2
[0.1.1]: https://github.com/giantswarm/jiralert-app/compare/v0.1.0...v0.1.1
[0.1.0]: https://github.com/giantswarm/jiralert-app/compare/v0.0.3...v0.1.0
[0.0.3]: https://github.com/giantswarm/jiralert-app/compare/v0.0.2...v0.0.3
[0.0.2]: https://github.com/giantswarm/jiralert-app/compare/v0.0.1...v0.0.2
[0.0.1]: https://github.com/giantswarm/jiralert-app/releases/tag/v0.0.1
