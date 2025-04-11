---
title: Integrating Doc Detective
description: Learn how to integrate Doc Detective with other tools and workflows for seamless documentation testing.
---

# Integrating Doc Detective

Doc Detective is a powerful tool for testing and validating documentation. This guide will help you integrate Doc Detective with other tools and workflows to enhance your documentation process.

## CI/CD Integration

Integrating Doc Detective into your Continuous Integration/Continuous Deployment (CI/CD) pipeline ensures that your documentation is automatically tested with each code change.

### GitHub Actions

To use Doc Detective with GitHub Actions, create a workflow file (e.g., `.github/workflows/doc-detective.yml`) with the following content:

```yaml
name: Doc Detective Tests

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Use Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18.x'
    - run: npm ci
    - name: Run Doc Detective tests
      run: npx doc-detective@latest runTests
```

This workflow will run Doc Detective tests on every push to the main branch and on pull requests targeting the main branch.

### GitLab CI

For GitLab CI, create a `.gitlab-ci.yml` file in your repository root with the following content:

```yaml
image: node:18

stages:
  - test

doc-detective:
  stage: test
  script:
    - npm ci
    - npx doc-detective@latest runTests
```

This configuration will run Doc Detective tests as part of your GitLab CI pipeline.

## Version Control Integration

Doc Detective works seamlessly with version control systems like Git. Here are some best practices for integrating Doc Detective with your version control workflow:

1. Include your Doc Detective configuration file (`doc-detective.json`) in your repository.
2. Add test files (e.g., `.md` or `.mdx` files) to your repository alongside your documentation.
3. Use branching strategies to test documentation changes before merging into the main branch.
4. Consider using pre-commit hooks to run Doc Detective tests locally before committing changes.

## Documentation Platform Integrations

Doc Detective can be integrated with various documentation platforms to enhance your documentation workflow.

### Docusaurus Integration

As seen in the project's `package.json`, Doc Detective is already integrated with Docusaurus. You can run Doc Detective tests as part of your Docusaurus build process by adding the following script to your `package.json`:

```json
{
  "scripts": {
    "test-docs": "npx doc-detective@latest runTests && npm run build"
  }
}
```

This script will run Doc Detective tests before building your Docusaurus site, ensuring that your documentation passes all tests before deployment.

### Other Documentation Platforms

For other documentation platforms, you can integrate Doc Detective by:

1. Adding a test step in your build process that runs Doc Detective tests.
2. Using Doc Detective's output to generate reports or notifications about documentation issues.
3. Implementing custom scripts that use Doc Detective's API to perform specific checks relevant to your documentation platform.

## Advanced Integrations

For more advanced integrations, consider:

- Creating custom plugins that extend Doc Detective's functionality for your specific needs.
- Developing scripts that parse Doc Detective's output and integrate it with your project management tools or issue trackers.
- Setting up automated notifications (e.g., Slack, email) based on Doc Detective test results.

By integrating Doc Detective with your existing tools and workflows, you can ensure consistent, high-quality documentation throughout your development process.