# Gradle Multi-Module JaCoCo Test Coverage Demo

This project demonstrates how to set up a multi-module Gradle project with JaCoCo test coverage reporting, showcasing both unit tests and integration tests with combined code coverage analysis.

## Project Structure

```
gradle-multimodule-jacoco/
├── application/          # Spring Boot application module
├── api/                  # API controllers module
├── buildSrc/             # Custom Gradle plugins
├── common/               # Common utilities and models
├── products/             # Product domain and business logic
└── README.md
```

### Modules

- **common**: Contains base entity models and utility classes
- **products**: Implements product domain model, repository, and service layer
- **api**: Provides RESTful API endpoints via Spring controllers
- **application**: Main Spring Boot application that integrates all modules
- **buildSrc**: Custom Gradle plugins for shared build configuration

## Features

- Multi-module Gradle project structure
- Custom Gradle plugins (LibraryConventionsPlugin and ApplicationConventionsPlugin)
- Unit testing with JUnit 5, Mockito, and AssertJ
- Integration testing with Spring Boot Test and Testcontainers
- JaCoCo test coverage for each module
- Aggregated JaCoCo test coverage report across all modules

## Prerequisites

- JDK 17 or higher
- Gradle 7.4 or higher
- Docker (for running integration tests with Testcontainers)

## Getting Started

### Building the Project

To build the project and run all tests:

```bash
./gradlew clean build
```

### Running Tests

To run all tests and generate test coverage reports:

```bash
./gradlew test
```

### Generating JaCoCo Reports

To generate the JaCoCo test coverage reports:

```bash
./gradlew jacocoTestReport
```

To generate the aggregated JaCoCo report:

```bash
./gradlew jacocoMergedReport
```

### Running the Application

To run the Spring Boot application:

```bash
./gradlew :application:bootRun
```

The API will be available at: http://localhost:8080/api/products

## Test Coverage Reports

After running the tests and generating reports, JaCoCo coverage reports can be found at:

- Individual module reports:
  - `common/build/reports/jacoco/test/html/index.html`
  - `products/build/reports/jacoco/test/html/index.html`
  - `api/build/reports/jacoco/test/html/index.html`
  - `application/build/reports/jacoco/test/html/index.html`

- Aggregated report:
  - `build/reports/jacoco/jacocoMergedReport/html/index.html`

## Custom Gradle Plugins

The project uses two custom Gradle plugins defined in the buildSrc directory:

### LibraryConventionsPlugin

Applied to library modules (common, products, api) to:
- Set Java conventions (JDK 17)
- Configure JaCoCo coverage
- Add common test dependencies (JUnit 5, Mockito, AssertJ)
- Apply consistent build settings

### ApplicationConventionsPlugin

Applied to the application module to:
- Configure Spring Boot
- Set up integration testing
- Configure JaCoCo coverage
- Set consistent Spring dependencies

## Key Technical Concepts

1. **Gradle Multi-Module Project**: Demonstrates proper modularization of a Spring application
2. **JaCoCo Test Coverage**: Shows how to configure and aggregate test coverage across modules
3. **Custom Gradle Plugins**: Illustrates how to share build logic through custom plugins
4. **Spring Boot Integration Tests**: Uses Testcontainers for realistic integration testing
5. **Proper Test Practices**: Includes unit tests and integration tests with appropriate mocking

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
