# Configuration Guide

This guide provides a comprehensive overview of how to configure Doc Detective using the `.doc-detective.json` file. Understanding and properly setting up this configuration file is crucial for tailoring Doc Detective to your project's specific needs.

## Introduction to .doc-detective.json

The `.doc-detective.json` file is the central configuration file for Doc Detective. It allows you to customize various aspects of how Doc Detective operates within your project.

## File Location

Place the `.doc-detective.json` file in the root directory of your project. Doc Detective will automatically look for this file when it runs.

## Configuration Options

Below are the available configuration options, their purposes, and how to set them up in the `.doc-detective.json` file.

### Sample Configuration

Here's a basic structure of the `.doc-detective.json` file:

```json
{
  "option1": "value1",
  "option2": "value2",
  "nestedOption": {
    "subOption1": "subValue1",
    "subOption2": "subValue2"
  }
}
```

### Available Options

(Note: As the actual configuration options were not provided in the context, the following are placeholder examples. Replace these with the actual options available in Doc Detective.)

1. **testFiles**
   - Purpose: Specifies the files or directories to be tested by Doc Detective.
   - Example:
     ```json
     "testFiles": ["./docs/**/*.md", "./api/**/*.js"]
     ```

2. **ignoreFiles**
   - Purpose: Defines files or patterns to be ignored during testing.
   - Example:
     ```json
     "ignoreFiles": ["**/node_modules/**", "**/.git/**"]
     ```

3. **customRules**
   - Purpose: Allows you to define custom validation rules.
   - Example:
     ```json
     "customRules": {
       "noTodos": {
         "pattern": "TODO:",
         "message": "TODOs should not be present in documentation"
       }
     }
     ```

4. **outputFormat**
   - Purpose: Specifies the format of the test results output.
   - Example:
     ```json
     "outputFormat": "json"
     ```

## Best Practices

1. **Version Control**: Include your `.doc-detective.json` file in version control to ensure consistency across your team.
2. **Comments**: While JSON doesn't support comments, you can use a separate markdown file to document your configuration choices.
3. **Regular Updates**: Review and update your configuration regularly as your project evolves.

## Troubleshooting

If you encounter issues with your configuration:

1. Verify that your JSON is valid using a JSON validator.
2. Check for typos in option names.
3. Ensure all file paths are correct relative to your project root.

## Conclusion

Proper configuration of Doc Detective through the `.doc-detective.json` file is key to leveraging its full potential. Experiment with different options to find the setup that best suits your project's documentation needs.

For more detailed information on specific options or advanced configurations, refer to the [Doc Detective API Reference](link-to-api-reference) (Note: Replace with actual link when available).