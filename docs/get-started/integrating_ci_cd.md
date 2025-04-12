---
title: Integrating Doc Detective into CI/CD Pipelines
description: Learn how to set up automated documentation testing with Doc Detective in your continuous integration and continuous deployment (CI/CD) workflows.
---

# Integrating Doc Detective into CI/CD Pipelines

Integrating Doc Detective into your continuous integration and continuous deployment (CI/CD) pipelines allows you to automate documentation testing as part of your development workflow. This guide will walk you through the process of setting up Doc Detective in popular CI/CD platforms and provide best practices for running automated documentation tests.

## Why Integrate Doc Detective in CI/CD?

By integrating Doc Detective into your CI/CD pipeline, you can:

1. Catch documentation errors early in the development process
2. Ensure consistency across your documentation
3. Automatically validate changes to your documentation
4. Improve the overall quality of your documentation

## Setting Up Doc Detective in CI/CD

To integrate Doc Detective into your CI/CD pipeline, you'll need to add it to your project dependencies and create a configuration file. Here's how to get started:

1. Add Doc Detective to your project:

```json
{
  "dependencies": {
    "doc-detective-common": "^1.22.0"
  },
  "scripts": {
    "doc-detective": "npx doc-detective@latest runTests"
  }
}
```

2. Create a `.doc-detective.json` configuration file in your project root or in a `samples` directory, depending on your project structure.

3. Configure your CI/CD pipeline to run Doc Detective tests.

## Examples for Popular CI/CD Platforms

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
    - uses: actions/checkout@v2
    - name: Use Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '18'
    - run: npm ci
    - run: npm run doc-detective
```

### GitLab CI

For GitLab CI, add the following to your `.gitlab-ci.yml` file:

```yaml
doc-detective:
  image: node:18
  script:
    - npm ci
    - npm run doc-detective
```

### Jenkins

For Jenkins, you can add a stage to your Jenkinsfile:

```groovy
pipeline {
    agent any
    stages {
        stage('Doc Detective') {
            steps {
                sh 'npm ci'
                sh 'npm run doc-detective'
            }
        }
    }
}
```

## Best Practices for Running Doc Detective in CI/CD

1. **Use a consistent Node.js version**: Ensure you're using Node.js 18 or later, as specified in the `package.json` engine requirements.

2. **Cache dependencies**: To speed up your CI/CD pipeline, consider caching your `node_modules` directory.

3. **Run tests on both push and pull requests**: This ensures your documentation is checked at multiple stages of your development process.

4. **Fail the build on test failures**: Configure your CI/CD pipeline to fail if Doc Detective tests don't pass.

5. **Include Doc Detective results in your PR checks**: If possible, integrate the test results into your pull request checks for easy visibility.

6. **Regularly update Doc Detective**: Keep your Doc Detective version up to date to benefit from the latest features and improvements.

## Conclusion

By integrating Doc Detective into your CI/CD pipeline, you can ensure that your documentation remains accurate and up-to-date throughout your development process. This automated approach to documentation testing will help maintain high-quality documentation with minimal manual effort.