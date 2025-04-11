---
sidebar_position: 1
---

# Quick Start Guide

Welcome to Doc Detective! This guide will help you get started quickly with installing, setting up, and running your first test using Doc Detective.

## Installation

To get started with Doc Detective, you have two options for installation:

### Option 1: VSCode Dev Container

If you're using Visual Studio Code, you can use the Dev Container feature for a quick setup:

1. Install [Docker](https://docs.docker.com/get-docker/) on your system.
2. Open VSCode and install the "Remote - Containers" extension if you haven't already.
3. Open the Command Palette (Ctrl+Shift+P or Cmd+Shift+P on Mac) and run "Dev Containers: Rebuild and Reopen in Container".

This will set up the development environment with all necessary dependencies.

### Option 2: Manual Installation

If you prefer a manual installation or are not using VSCode, follow these steps:

1. Install [Node.js](https://nodejs.org/en/download) on your system.
2. Clone the Doc Detective repository or download the project files.
3. Open a terminal and navigate to the project directory.
4. Run the following command to install dependencies:

```bash
npm install
```

## Basic Usage

Once you have Doc Detective installed, you can start using it to test your documentation. Here's how to get started:

1. Navigate to your project directory in the terminal.
2. Start the local server by running:

```bash
npm run start
```

This command will start a local development server and open the documentation in your default web browser.

## Running Your First Test

To run your first test with Doc Detective:

1. Create a new test file (e.g., `my_first_test.yml`) in your project's test directory.
2. Add your test configuration to the file. For example:

```yaml
name: My First Test
steps:
  - action: assert
    selector: h1
    value: "Welcome to Doc Detective"
```

3. Run the test using the following command:

```bash
npm run doc-detective
```

This will execute the Doc Detective test runner and display the results in your terminal.

## Next Steps

Congratulations! You've now installed Doc Detective, set up your environment, and run your first test. To learn more about creating complex tests, configuring test environments, and integrating Doc Detective into your workflow, check out our other documentation pages.

Happy testing!