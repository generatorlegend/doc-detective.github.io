---
title: Getting Started with Doc Detective
description: Learn how to install, configure, and run your first test with Doc Detective
---

# Getting Started with Doc Detective

Doc Detective is a powerful tool for testing and validating documentation content. This guide will walk you through the process of setting up Doc Detective and running your first test.

## What is Doc Detective?

Doc Detective is a content testing framework that helps ensure the accuracy and consistency of your documentation. It allows you to automate the process of verifying that your documentation matches your codebase, API responses, and other sources of truth.

## Installation

To get started with Doc Detective, you'll need to have Node.js installed on your system. If you haven't already installed Node.js, you can download it from the [official Node.js website](https://nodejs.org/en/download).

Once Node.js is installed, you can set up Doc Detective using one of the following methods:

### Option 1: VSCode Dev Container

If you're using Visual Studio Code and have Docker installed, you can use the Dev Container feature for a quick setup:

1. Install [Docker](https://docs.docker.com/get-docker/) if you haven't already.
2. Open your project in VSCode.
3. Open the Command Palette (Ctrl+Shift+P or Cmd+Shift+P on macOS).
4. Run the command "Dev Containers: Rebuild and Reopen in Container".

This will set up a development environment with all the necessary dependencies.

### Option 2: Manual Installation

If you prefer a manual installation or aren't using VSCode, follow these steps:

1. Open your terminal or command prompt.
2. Navigate to your project directory.
3. Run the following command to install Doc Detective:

```bash
npm install doc-detective
```

## Basic Configuration

After installation, you'll need to create a configuration file for Doc Detective. Create a new file named `.doc-detective.json` in your project's root directory with the following basic structure:

```json
{
  "tests": [
    {
      "name": "My First Test",
      "type": "content",
      "source": "path/to/your/documentation/file.md",
      "expectations": [
        {
          "type": "contains",
          "value": "Expected content"
        }
      ]
    }
  ]
}
```

This configuration sets up a simple content test that checks if a specific documentation file contains the expected content.

## Running Your First Test

Now that you have Doc Detective installed and configured, you can run your first test:

1. Open your terminal or command prompt.
2. Navigate to your project directory.
3. Run the following command:

```bash
npx doc-detective runTests
```

Doc Detective will execute the tests defined in your `.doc-detective.json` file and provide output on whether the tests passed or failed.

## Next Steps

Congratulations! You've successfully set up Doc Detective and run your first test. Here are some next steps to explore:

1. Learn about different test types and expectations in the Doc Detective documentation.
2. Integrate Doc Detective into your CI/CD pipeline for automated documentation testing.
3. Explore advanced configuration options to customize Doc Detective for your specific needs.

By incorporating Doc Detective into your documentation workflow, you can improve the quality and reliability of your documentation, ensuring that it stays up-to-date with your codebase and other sources of truth.

For more detailed information on Doc Detective's features and capabilities, refer to the full documentation.