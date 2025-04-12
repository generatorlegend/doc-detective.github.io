# Configuration Guide

This guide provides comprehensive information on configuring Doc Detective. You'll learn about the `.doc-detective.json` configuration file, its purpose, structure, and all available options. We'll also cover how to set up different testing environments and contexts.

## The .doc-detective.json File

The `.doc-detective.json` file is the central configuration file for Doc Detective. It allows you to customize the behavior of Doc Detective for your specific documentation needs.

### Purpose

The main purposes of the `.doc-detective.json` file are:

1. Define the structure and location of your documentation
2. Specify testing parameters and environments
3. Configure output and reporting options

### Structure

The `.doc-detective.json` file uses a JSON format. Here's a basic structure:

```json
{
  "rootDir": "./docs",
  "outDir": "./test-results",
  "tests": [
    {
      "type": "codeblock",
      "files": ["**/*.md"],
      "langs": ["javascript", "python"]
    }
  ],
  "environments": [
    {
      "name": "node",
      "command": "node"
    }
  ]
}
```

## Configuration Options

Let's explore the available configuration options in detail:

### rootDir

- Type: `string`
- Default: `"./"`

Specifies the root directory of your documentation files.

Example:
```json
"rootDir": "./docs"
```

### outDir

- Type: `string`
- Default: `"./doc-detective-results"`

Defines the directory where test results and reports will be saved.

Example:
```json
"outDir": "./test-results"
```

### tests

- Type: `array`
- Default: `[]`

An array of test configurations. Each test configuration is an object that specifies the type of test and its parameters.

Example:
```json
"tests": [
  {
    "type": "codeblock",
    "files": ["**/*.md"],
    "langs": ["javascript", "python"]
  },
  {
    "type": "link",
    "files": ["**/*.md"]
  }
]
```

### environments

- Type: `array`
- Default: `[]`

Defines the execution environments for running code samples.

Example:
```json
"environments": [
  {
    "name": "node",
    "command": "node"
  },
  {
    "name": "python",
    "command": "python3"
  }
]
```

## Common Configurations

Here are some common configuration scenarios:

### Testing JavaScript and Python Code Blocks

```json
{
  "rootDir": "./docs",
  "outDir": "./test-results",
  "tests": [
    {
      "type": "codeblock",
      "files": ["**/*.md"],
      "langs": ["javascript", "python"]
    }
  ],
  "environments": [
    {
      "name": "node",
      "command": "node"
    },
    {
      "name": "python",
      "command": "python3"
    }
  ]
}
```

### Checking Links and Images

```json
{
  "rootDir": "./docs",
  "outDir": "./test-results",
  "tests": [
    {
      "type": "link",
      "files": ["**/*.md"]
    },
    {
      "type": "image",
      "files": ["**/*.md"]
    }
  ]
}
```

### Testing Specific Directories

```json
{
  "rootDir": "./docs",
  "outDir": "./test-results",
  "tests": [
    {
      "type": "codeblock",
      "files": ["api/**/*.md", "tutorials/**/*.md"],
      "langs": ["javascript"]
    }
  ],
  "environments": [
    {
      "name": "node",
      "command": "node"
    }
  ]
}
```

## Setting Up Different Testing Environments

To set up different testing environments, use the `environments` array in your configuration. Each environment should have a `name` and a `command` to execute code in that environment.

Example with multiple environments:

```json
{
  "environments": [
    {
      "name": "node",
      "command": "node"
    },
    {
      "name": "python",
      "command": "python3"
    },
    {
      "name": "ruby",
      "command": "ruby"
    }
  ]
}
```

You can then reference these environments in your test configurations:

```json
{
  "tests": [
    {
      "type": "codeblock",
      "files": ["**/*.md"],
      "langs": ["javascript", "python", "ruby"]
    }
  ]
}
```

Doc Detective will use the appropriate environment to execute code blocks based on the language specified.

## Conclusion

This guide covered the essential aspects of configuring Doc Detective using the `.doc-detective.json` file. By understanding and utilizing these configuration options, you can tailor Doc Detective to meet your specific documentation testing needs. Remember to adjust the settings based on your project structure, supported languages, and desired test coverage.