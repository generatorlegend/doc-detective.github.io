# Best Practices for Using Doc Detective

This guide provides a comprehensive list of best practices for effectively using Doc Detective in your documentation workflows. By following these recommendations, you can optimize your testing processes, maintain clean configuration files, and seamlessly integrate Doc Detective into various documentation projects.

## Organizing Tests

1. **Group related tests**: Create logical groupings of tests based on functionality, features, or documentation sections.

   ```json
   {
     "tests": [
       {
         "group": "Authentication",
         "tests": [
           // Authentication-related tests
         ]
       },
       {
         "group": "User Management",
         "tests": [
           // User management-related tests
         ]
       }
     ]
   }
   ```

2. **Use descriptive test names**: Choose clear and specific names for your tests to make them easily identifiable.

   ```json
   {
     "name": "Verify login with valid credentials",
     "action": "screenshot",
     "selector": "#login-form"
   }
   ```

3. **Implement test dependencies**: Use the `depends_on` property to create test hierarchies and ensure proper test execution order.

   ```json
   {
     "name": "Create new user",
     "action": "click",
     "selector": "#create-user-button"
   },
   {
     "name": "Verify user creation success message",
     "action": "assert",
     "selector": "#success-message",
     "attribute": "innerText",
     "value": "User created successfully",
     "depends_on": "Create new user"
   }
   ```

## Maintaining Configuration Files

1. **Use a consistent structure**: Organize your `.doc-detective.json` files with a clear and consistent structure across projects.

   ```json
   {
     "baseUrl": "https://example.com",
     "tests": [
       // Test definitions
     ],
     "variables": {
       // Variable definitions
     },
     "settings": {
       // Global settings
     }
   }
   ```

2. **Version control your configuration**: Include your `.doc-detective.json` files in your version control system to track changes and collaborate with team members.

3. **Utilize environment variables**: Use environment variables for sensitive information or values that change between environments.

   ```json
   {
     "baseUrl": "${DOC_DETECTIVE_BASE_URL}",
     "variables": {
       "adminUsername": "${ADMIN_USERNAME}",
       "adminPassword": "${ADMIN_PASSWORD}"
     }
   }
   ```

## Integrating Doc Detective into Documentation Workflows

1. **Implement continuous integration**: Set up automated Doc Detective runs as part of your CI/CD pipeline to catch documentation issues early.

2. **Use pre-commit hooks**: Implement pre-commit hooks to run Doc Detective tests before allowing commits, ensuring documentation quality.

3. **Integrate with documentation build process**: Run Doc Detective tests as part of your documentation build process to ensure up-to-date and accurate documentation.

## Project Structure

Organize your project files for optimal use of Doc Detective:

```
my-project/
├── docs/
│   ├── getting-started.md
│   ├── api-reference.md
│   └── troubleshooting.md
├── tests/
│   ├── .doc-detective.json
│   ├── getting-started.test.json
│   ├── api-reference.test.json
│   └── troubleshooting.test.json
├── .github/
│   └── workflows/
│       └── doc-detective.yml
└── package.json
```

This structure separates documentation files, test configurations, and CI/CD workflows for better organization and maintainability.

## Examples

### Basic Test Structure

```json
{
  "baseUrl": "https://docs.example.com",
  "tests": [
    {
      "name": "Verify homepage title",
      "action": "assert",
      "selector": "h1",
      "attribute": "innerText",
      "value": "Welcome to Example Docs"
    },
    {
      "name": "Navigate to API Reference",
      "action": "click",
      "selector": "a[href='/api-reference']"
    },
    {
      "name": "Check API Reference content",
      "action": "assert",
      "selector": "#api-content",
      "attribute": "exists",
      "value": true,
      "depends_on": "Navigate to API Reference"
    }
  ]
}
```

### Using Variables

```json
{
  "baseUrl": "https://docs.example.com",
  "variables": {
    "apiVersion": "v2",
    "endpointBase": "/api/${apiVersion}"
  },
  "tests": [
    {
      "name": "Check API endpoint",
      "action": "assert",
      "selector": "code",
      "attribute": "innerText",
      "value": "${endpointBase}/users"
    }
  ]
}
```

By following these best practices and examples, you can effectively use Doc Detective to ensure high-quality, accurate documentation across your projects.