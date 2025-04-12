---
sidebar_position: 1
---

# CLI Reference

Doc Detective provides a powerful command-line interface (CLI) to help you run tests, generate coverage reports, and manage your documentation testing workflow. This guide covers all available commands, their options, and usage examples to help you make the most of the Doc Detective CLI.

## Installation

Before using the CLI, make sure you have Doc Detective installed. You can install it using npm:

```bash
npm install -g doc-detective
```

## Basic Usage

The general syntax for using the Doc Detective CLI is:

```bash
doc-detective <command> [options]
```

## Available Commands

### runTests

The `runTests` command is used to execute your documentation tests.

```bash
doc-detective runTests
```

#### Options

- `--config <path>`: Specify a custom configuration file path.
- `--output <format>`: Set the output format (e.g., json, html).
- `--verbose`: Enable verbose logging for detailed test information.

#### Example

```bash
doc-detective runTests --config ./custom-config.json --output html --verbose
```

### generateCoverage

Generate a coverage report for your documentation tests.

```bash
doc-detective generateCoverage
```

#### Options

- `--format <type>`: Specify the coverage report format (e.g., html, json).
- `--output <path>`: Set the output directory for the coverage report.

#### Example

```bash
doc-detective generateCoverage --format html --output ./coverage-report
```

### init

Initialize a new Doc Detective project in the current directory.

```bash
doc-detective init
```

This command will create a basic configuration file and directory structure for your Doc Detective project.

### validate

Validate your Doc Detective configuration file.

```bash
doc-detective validate
```

#### Options

- `--config <path>`: Specify a custom configuration file path to validate.

#### Example

```bash
doc-detective validate --config ./custom-config.json
```

## Common Command Combinations

Here are some common command combinations and their effects:

1. Run tests and generate a coverage report:

```bash
doc-detective runTests && doc-detective generateCoverage
```

This will first run your tests and then generate a coverage report based on the test results.

2. Initialize a project and validate the configuration:

```bash
doc-detective init && doc-detective validate
```

This combination is useful when setting up a new Doc Detective project. It creates the initial project structure and then validates the generated configuration file.

3. Run tests with verbose logging and output in HTML format:

```bash
doc-detective runTests --verbose --output html
```

This command runs your tests with detailed logging and produces an HTML output, which can be useful for debugging and creating human-readable reports.

## Environment Variables

Doc Detective CLI also supports the use of environment variables for configuration. Some common variables include:

- `DOC_DETECTIVE_CONFIG`: Path to the configuration file.
- `DOC_DETECTIVE_OUTPUT_DIR`: Directory for output files.
- `DOC_DETECTIVE_VERBOSE`: Enable verbose logging when set to "true".

You can set these variables in your shell or include them in a `.env` file in your project root.

## Conclusion

The Doc Detective CLI provides a robust set of tools for managing your documentation testing process. By combining these commands and options, you can create efficient workflows for ensuring the accuracy and completeness of your documentation.

For more detailed information on specific features or advanced usage, refer to the other sections of our documentation.