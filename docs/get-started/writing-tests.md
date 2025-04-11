---
title: Writing Tests with Doc Detective
---

# Writing Tests with Doc Detective

Doc Detective is a powerful tool for creating and running automated tests for your documentation. This guide will walk you through the process of writing effective tests using Doc Detective, explaining the structure of test specifications, available actions, and best practices.

## Test Specification Structure

A Doc Detective test specification is typically defined in a JSON file. The basic structure of a test specification includes:

- Test metadata
- Steps to perform
- Expected results

Here's a simple example of a test specification:

```json
{
  "name": "Example Test",
  "description": "This is a sample test specification",
  "steps": [
    {
      "action": "navigate",
      "url": "https://example.com"
    },
    {
      "action": "click",
      "selector": "#submit-button"
    }
  ],
  "expect": [
    {
      "action": "see",
      "text": "Success!"
    }
  ]
}
```

## Available Actions

Doc Detective supports various actions that you can use in your test specifications. Some commonly used actions include:

1. `navigate`: Open a specific URL
2. `click`: Click on an element
3. `type`: Enter text into an input field
4. `see`: Check if specific text is visible
5. `not_see`: Check if specific text is not visible
6. `wait`: Wait for a specified amount of time

For a complete list of supported actions and their usage, refer to the API documentation.

## Writing Effective Tests

To write effective tests using Doc Detective, follow these best practices:

1. **Be specific**: Define clear and specific test cases that cover individual functionality or user flows.

2. **Use descriptive names**: Give your tests meaningful names that describe what they're testing.

3. **Keep tests independent**: Each test should be self-contained and not rely on the state of other tests.

4. **Use appropriate selectors**: When interacting with elements, use reliable selectors like IDs or data attributes instead of relying on text content or class names that may change.

5. **Include both positive and negative tests**: Test both expected behavior and error handling.

6. **Use variables and parameterization**: Leverage variables and parameterization to create more flexible and reusable tests.

7. **Add clear assertions**: Use explicit expectations to verify the desired outcomes of your tests.

## Example Test Specification

Here's a more comprehensive example of a test specification:

```json
{
  "name": "Login Functionality Test",
  "description": "Verifies that a user can successfully log in to the application",
  "steps": [
    {
      "action": "navigate",
      "url": "https://example.com/login"
    },
    {
      "action": "type",
      "selector": "#username",
      "text": "testuser@example.com"
    },
    {
      "action": "type",
      "selector": "#password",
      "text": "securepassword123"
    },
    {
      "action": "click",
      "selector": "#login-button"
    },
    {
      "action": "wait",
      "time": 2000
    }
  ],
  "expect": [
    {
      "action": "see",
      "text": "Welcome, Test User"
    },
    {
      "action": "not_see",
      "text": "Invalid username or password"
    }
  ]
}
```

This test specification checks the login functionality of an application by navigating to the login page, entering credentials, clicking the login button, and verifying the expected results.

## Running Tests

To run your tests using Doc Detective, use the following command in your terminal:

```bash
doc-detective run path/to/your/test-spec.json
```

For more information on running tests and configuring Doc Detective, refer to the CLI documentation.

## Conclusion

Writing effective tests with Doc Detective allows you to automate the process of verifying your documentation and ensuring its accuracy. By following the structure and best practices outlined in this guide, you can create robust and maintainable test specifications that help improve the quality of your documentation.