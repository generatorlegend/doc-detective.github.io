# Advanced Features

This guide explores the advanced features of Doc Detective, including custom actions, complex test scenarios, and advanced configuration options. By leveraging these features, you can create more comprehensive and flexible documentation testing setups.

## Custom Actions

Doc Detective allows you to define custom actions to extend its functionality and tailor it to your specific documentation needs. Custom actions are particularly useful when you need to perform tasks that are not covered by the built-in actions.

To create a custom action:

1. Create a new JavaScript file in the `custom-actions` directory.
2. Define your custom action as a function that takes appropriate parameters.
3. Export the function so that Doc Detective can use it.

Example:

```javascript
// custom-actions/validateCustomFormat.js

function validateCustomFormat(content, format) {
  // Your custom validation logic here
  return {
    passed: true,
    message: "Custom format validation passed"
  };
}

module.exports = validateCustomFormat;
```

To use your custom action in a test scenario:

```json
{
  "type": "custom",
  "action": "validateCustomFormat",
  "params": {
    "content": "{{content}}",
    "format": "myCustomFormat"
  }
}
```

## Complex Test Scenarios

Doc Detective supports complex test scenarios that allow you to chain multiple actions and use conditional logic. This enables you to create more sophisticated tests for your documentation.

### Action Chaining

You can chain multiple actions together to create a sequence of tests:

```json
{
  "name": "Complex documentation test",
  "actions": [
    {
      "type": "exists",
      "selector": "h1"
    },
    {
      "type": "contains",
      "selector": "p",
      "value": "Important information"
    },
    {
      "type": "custom",
      "action": "validateCustomFormat",
      "params": {
        "content": "{{content}}",
        "format": "myCustomFormat"
      }
    }
  ]
}
```

### Conditional Logic

Use conditional statements to create branching test flows:

```json
{
  "name": "Conditional test scenario",
  "actions": [
    {
      "type": "exists",
      "selector": "#advanced-section"
    },
    {
      "if": "{{previous.passed}}",
      "then": [
        {
          "type": "contains",
          "selector": "#advanced-section",
          "value": "Advanced configuration"
        }
      ],
      "else": [
        {
          "type": "log",
          "message": "Advanced section not found, skipping detailed checks"
        }
      ]
    }
  ]
}
```

## Advanced Configuration Options

Doc Detective offers several advanced configuration options to fine-tune your testing setup. These options can be set in your `.doc-detective.json` file.

### Parallel Execution

Enable parallel execution of tests to improve performance:

```json
{
  "parallelExecution": true,
  "maxConcurrency": 5
}
```

### Custom Reporters

Implement custom reporters to tailor the output of your test results:

```json
{
  "reporters": [
    "./custom-reporters/my-custom-reporter.js"
  ]
}
```

### Environment Variables

Use environment variables to manage sensitive information or configuration that varies between environments:

```json
{
  "environmentVariables": {
    "API_KEY": "{{ENV.DOC_DETECTIVE_API_KEY}}",
    "BASE_URL": "{{ENV.DOC_DETECTIVE_BASE_URL}}"
  }
}
```

### Hooks

Implement pre and post-test hooks to set up or tear down test environments:

```json
{
  "hooks": {
    "beforeAll": "./scripts/setup-test-environment.js",
    "afterAll": "./scripts/cleanup-test-environment.js",
    "beforeEach": "./scripts/reset-test-state.js",
    "afterEach": "./scripts/log-test-result.js"
  }
}
```

By leveraging these advanced features, you can create a robust and flexible documentation testing setup with Doc Detective. Experiment with these options to find the best configuration for your project's needs.