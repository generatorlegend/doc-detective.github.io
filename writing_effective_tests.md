# Writing Effective Tests with Doc Detective

Doc Detective is a powerful tool for testing and validating documentation. This guide will help you write effective tests using Doc Detective, covering the different types of actions available, how to structure test specifications, and best practices for writing tests that provide meaningful coverage of your documentation.

## Understanding Doc Detective Actions

Doc Detective provides several actions that you can use to test various aspects of your documentation. Some of the key actions include:

1. `checkLink`: Verifies that a link is valid and accessible.
2. `find`: Searches for specific text or elements on a page.
3. `goTo`: Navigates to a specified URL.

These actions form the building blocks of your tests, allowing you to simulate user interactions and verify the content and functionality of your documentation.

## Structuring Test Specifications

Test specifications in Doc Detective are typically written in JSON format. Here's a basic structure for a test specification:

```json
{
  "name": "My Test Suite",
  "tests": [
    {
      "name": "Check Homepage",
      "steps": [
        {
          "action": "goTo",
          "url": "https://example.com"
        },
        {
          "action": "find",
          "text": "Welcome to Example"
        }
      ]
    }
  ]
}
```

This example shows a simple test that navigates to a website and checks for specific text on the page.

## Best Practices for Writing Effective Tests

1. **Start with critical paths**: Focus on testing the most important user journeys and documentation sections first.

2. **Use descriptive test names**: Make your test names clear and descriptive to easily understand what each test is checking.

3. **Break tests into small, focused units**: Each test should verify a specific aspect of your documentation. This makes tests easier to maintain and debug.

4. **Use variables for reusable values**: If you have URLs or text that appear in multiple tests, consider using variables to make your tests more maintainable.

5. **Test both positive and negative scenarios**: Don't just test that things work correctly, also test for proper error handling and edge cases.

6. **Keep tests independent**: Each test should be able to run independently of others. Avoid creating dependencies between tests.

7. **Use assertions effectively**: Make sure your tests are actually verifying the expected outcomes, not just checking that actions complete without errors.

8. **Regularly update and maintain tests**: As your documentation evolves, make sure to update your tests to reflect changes and new content.

## Example: Comprehensive Documentation Test

Here's an example of a more comprehensive test specification that covers multiple aspects of a documentation site:

```json
{
  "name": "Documentation Site Test Suite",
  "tests": [
    {
      "name": "Verify Homepage",
      "steps": [
        {
          "action": "goTo",
          "url": "https://docs.example.com"
        },
        {
          "action": "find",
          "text": "Welcome to Our Documentation"
        },
        {
          "action": "checkLink",
          "selector": "a[href='/getting-started']",
          "text": "Getting Started"
        }
      ]
    },
    {
      "name": "Check API Reference",
      "steps": [
        {
          "action": "goTo",
          "url": "https://docs.example.com/api"
        },
        {
          "action": "find",
          "text": "API Reference"
        },
        {
          "action": "find",
          "selector": "h2",
          "text": "Endpoints"
        }
      ]
    }
  ]
}
```

This test suite checks both the homepage and the API reference page, verifying key content and navigation elements.

By following these guidelines and best practices, you can create effective tests using Doc Detective that provide comprehensive coverage of your documentation, ensuring its accuracy and reliability for your users.