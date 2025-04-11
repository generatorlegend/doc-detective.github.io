# Configuration Options

The `.doc-detective.json` file is the central configuration file for Doc Detective, allowing you to customize its behavior to suit your project's needs. This guide will walk you through all available configuration options, provide examples of common configurations, and offer best practices for different project types.

## Table of Contents

1. [Basic Structure](#basic-structure)
2. [General Options](#general-options)
3. [Test Configuration](#test-configuration)
4. [Output Configuration](#output-configuration)
5. [Advanced Options](#advanced-options)
6. [Common Configurations](#common-configurations)
7. [Best Practices](#best-practices)

## Basic Structure

The `.doc-detective.json` file is a JSON object with several top-level keys. Here's a basic example:

```json
{
  "rootDir": "./docs",
  "testDir": "./tests",
  "outputDir": "./results",
  "verbose": true,
  "tests": [
    {
      "type": "link",
      "files": ["**/*.md"]
    }
  ]
}
```

## General Options

- `rootDir` (string): The root directory of your documentation files. Default: `"./"`
- `testDir` (string): The directory where test files are located. Default: `"./tests"`
- `outputDir` (string): The directory where test results will be saved. Default: `"./results"`
- `verbose` (boolean): Enable verbose logging. Default: `false`

## Test Configuration

The `tests` array allows you to specify which tests to run and on which files. Each test object has the following properties:

- `type` (string): The type of test to run (e.g., "link", "spelling", "custom")
- `files` (array of strings): Glob patterns to match files to test
- `ignore` (array of strings, optional): Glob patterns to exclude files from testing

Example:

```json
"tests": [
  {
    "type": "link",
    "files": ["**/*.md"],
    "ignore": ["**/node_modules/**"]
  },
  {
    "type": "spelling",
    "files": ["**/*.md", "**/*.txt"]
  }
]
```

## Output Configuration

- `outputFormat` (string): The format of the test results output. Options: "json", "html", "markdown". Default: "json"
- `failOnError` (boolean): Whether to exit with a non-zero status code if any tests fail. Default: `true`

## Advanced Options

- `customTests` (object): Define custom test functions. Keys are test names, values are file paths to test functions.
- `variables` (object): Define variables that can be used in your documentation and tests.
- `plugins` (array of strings): List of plugin names or file paths to load additional functionality.

Example:

```json
{
  "customTests": {
    "myCustomTest": "./tests/customTest.js"
  },
  "variables": {
    "VERSION": "1.2.3",
    "API_URL": "https://api.example.com"
  },
  "plugins": [
    "doc-detective-plugin-accessibility",
    "./plugins/myCustomPlugin.js"
  ]
}
```

## Common Configurations

### Basic Documentation Project

```json
{
  "rootDir": "./docs",
  "outputDir": "./doc-detective-results",
  "verbose": true,
  "tests": [
    {
      "type": "link",
      "files": ["**/*.md"]
    },
    {
      "type": "spelling",
      "files": ["**/*.md"]
    }
  ],
  "outputFormat": "markdown",
  "failOnError": true
}
```

### API Documentation Project

```json
{
  "rootDir": "./api-docs",
  "testDir": "./api-tests",
  "outputDir": "./api-test-results",
  "verbose": true,
  "tests": [
    {
      "type": "link",
      "files": ["**/*.md", "**/*.html"]
    },
    {
      "type": "custom",
      "files": ["**/*.md"],
      "customTests": {
        "validateOpenAPI": "./tests/validateOpenAPI.js"
      }
    }
  ],
  "variables": {
    "API_VERSION": "v2",
    "BASE_URL": "https://api.example.com"
  },
  "outputFormat": "html",
  "failOnError": true
}
```

## Best Practices

1. **Organize your configuration**: Group related options together for better readability.
2. **Use specific file patterns**: Be as specific as possible in your `files` patterns to avoid unnecessary processing.
3. **Leverage ignore patterns**: Use the `ignore` option to exclude files or directories that don't need testing.
4. **Enable verbose logging**: During initial setup or troubleshooting, set `verbose` to `true` for detailed output.
5. **Customize output**: Choose an `outputFormat` that integrates well with your existing tools and workflows.
6. **Fail on error**: Keep `failOnError` set to `true` to catch issues in CI/CD pipelines.
7. **Use variables**: Leverage the `variables` option for values that may change between environments or versions.
8. **Implement custom tests**: For project-specific requirements, create and use custom test functions.
9. **Explore plugins**: Look for existing plugins that may provide additional functionality you need.
10. **Version control**: Include your `.doc-detective.json` file in version control to ensure consistency across your team.

By following these guidelines and leveraging the full range of configuration options, you can tailor Doc Detective to meet the specific needs of your documentation project, ensuring high-quality, accurate, and up-to-date documentation for your users.