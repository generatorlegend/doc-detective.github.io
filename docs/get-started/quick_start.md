---
title: Quick Start Guide
sidebar_label: Quick Start
description: Get started with Doc Detective quickly and run your first documentation test.
---

# Quick Start Guide

This guide will help you get started with Doc Detective, install it, perform basic configuration, and run your first documentation test.

## Prerequisites

Before you begin, ensure you have the following installed:

- [Node.js](https://nodejs.org/en/download) (version 18.0 or higher)
- [npm](https://www.npmjs.com/get-npm) (usually comes with Node.js)

## Installation

1. Open your terminal or command prompt.

2. Install Doc Detective globally using npm:

   ```bash
   npm install -g doc-detective
   ```

## Basic Configuration

1. Create a new directory for your Doc Detective project:

   ```bash
   mkdir my-doc-detective-project
   cd my-doc-detective-project
   ```

2. Create a basic configuration file named `.doc-detective.json` in your project root:

   ```json
   {
     "testsDir": "./tests",
     "docsDir": "./docs"
   }
   ```

   This configuration tells Doc Detective where to find your test files and documentation files.

3. Create the directories specified in the configuration:

   ```bash
   mkdir tests docs
   ```

## Writing Your First Test

1. Create a new file named `first-test.spec.json` in the `tests` directory:

   ```json
   {
     "name": "Check README existence",
     "steps": [
       {
         "action": "fileExists",
         "params": {
           "path": "README.md"
         }
       }
     ]
   }
   ```

   This test checks if a `README.md` file exists in your project root.

2. Create a simple `README.md` file in your project root:

   ```markdown
   # My Project

   Welcome to my project!
   ```

## Running Your First Test

1. In your terminal, navigate to your project root if you're not already there.

2. Run Doc Detective:

   ```bash
   doc-detective runTests
   ```

   You should see output indicating that your test passed.

## Next Steps

Congratulations! You've successfully set up Doc Detective and run your first documentation test. To learn more about Doc Detective's capabilities and how to write more complex tests, check out our full documentation.

Remember to commit your `.doc-detective.json` configuration file and your test files to version control so that your team can collaborate on documentation testing.