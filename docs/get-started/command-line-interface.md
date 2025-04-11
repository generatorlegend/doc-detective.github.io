# Command-Line Interface

This guide provides comprehensive information on using the Doc Detective command-line interface (CLI). The CLI offers various commands and options to help you interact with Doc Detective efficiently.

## Installation

Before using the CLI, make sure you have installed Doc Detective. If you haven't done so, follow these steps:

1. Install [Node.js](https://nodejs.org/en/download) if it's not already installed on your system.
2. Install Doc Detective using npm:

```bash
npm install -g doc-detective
```

## Available Commands

Doc Detective CLI provides the following commands:

### `doc-detective <command> [options]`

Replace `<command>` with one of the available commands listed below. Each command may have its own set of options.

#### `init`

Initializes a new Doc Detective project in the current directory.

Usage:
```bash
doc-detective init
```

#### `test`

Runs tests on your documentation.

Usage:
```bash
doc-detective test [options]
```

Options:
- `-c, --config <path>`: Specify the path to the configuration file (default: "doc-detective.json")
- `-o, --output <path>`: Specify the output directory for test results

#### `generate`

Generates documentation based on your codebase and configuration.

Usage:
```bash
doc-detective generate [options]
```

Options:
- `-c, --config <path>`: Specify the path to the configuration file (default: "doc-detective.json")
- `-o, --output <path>`: Specify the output directory for generated documentation

#### `validate`

Validates your documentation against predefined rules and best practices.

Usage:
```bash
doc-detective validate [options]
```

Options:
- `-c, --config <path>`: Specify the path to the configuration file (default: "doc-detective.json")
- `-r, --rules <path>`: Specify a custom rules file

#### `help`

Displays help information for Doc Detective CLI.

Usage:
```bash
doc-detective help [command]
```

Replace `[command]` with a specific command to get detailed help for that command.

## Configuration

Doc Detective uses a configuration file (default: `doc-detective.json`) to customize its behavior. You can specify a different configuration file using the `-c` or `--config` option with most commands.

Example configuration file:

```json
{
  "sourceDir": "./src",
  "docsDir": "./docs",
  "outputDir": "./output",
  "testPatterns": ["**/*.md", "**/*.html"],
  "ignorePatterns": ["**/node_modules/**"],
  "customRules": "./custom-rules.js"
}
```

## Examples

Here are some examples of how to use the Doc Detective CLI:

1. Initialize a new project:
   ```bash
   doc-detective init
   ```

2. Run tests on your documentation:
   ```bash
   doc-detective test
   ```

3. Generate documentation with a custom configuration file:
   ```bash
   doc-detective generate -c ./custom-config.json
   ```

4. Validate documentation and output results to a specific directory:
   ```bash
   doc-detective validate -o ./validation-results
   ```

5. Get help for a specific command:
   ```bash
   doc-detective help test
   ```

## Troubleshooting

If you encounter any issues while using the Doc Detective CLI, try the following:

1. Ensure you have the latest version of Doc Detective installed.
2. Check your configuration file for any errors or misconfigurations.
3. Use the `--help` option with any command to see detailed usage information.
4. If the problem persists, please refer to our [GitHub repository](https://github.com/example/doc-detective) for known issues or to report a new one.

For more information and advanced usage, please refer to our full documentation.