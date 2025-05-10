# SSE Auto Translator - Development Guide

## Overview

This guide provides information for developers who want to contribute to the SSE Auto Translator (SSE-AT) project. It covers the development environment setup, coding standards, and contribution workflow.

## Development Environment Setup

### Prerequisites

1. **Python 3.11+**
   - SSE-AT is developed using Python 3.11
   - Newer versions may work but are not officially supported

2. **Git**
   - Required for version control
   - Used to clone the repository and manage changes

3. **Visual Studio Code** (recommended)
   - The preferred IDE for development
   - Project settings are included in the repository

### Setting Up the Environment

1. **Clone the Repository**
   ```bash
   git clone https://github.com/cruldra/SSE-Auto-Translator.git
   cd SSE-Auto-Translator
   ```

2. **Create a Virtual Environment**
   ```bash
   python -m venv .venv
   ```

3. **Activate the Virtual Environment**
   - Windows: `.venv\Scripts\activate`
   - Linux/macOS: `source .venv/bin/activate`

4. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

5. **Run the Application**
   ```bash
   python src/app.py
   ```

### Building the Application

To build a standalone executable:

1. **Run the Build Script**
   ```bash
   build.bat
   ```

2. **Output**
   - The executable and all dependencies are built in the `app.dist` folder
   - The final distribution is created in the `SSE-AT` folder

## Project Structure

### Source Code Organization

- **src/** - Main source code
  - **app.py** - Entry point
  - **main.py** - Main application class
  - **data/** - Application data
  - **database/** - Translation database management
  - **mod_managers/** - Mod manager integrations
  - **settings/** - Settings dialog components
  - **startup_dialog/** - First-time setup components
  - **translation_editor/** - Translation editor components
  - **translator_api/** - Translation service integrations
  - **translation_provider/** - Translation source management
  - **utilities/** - Utility functions and classes

### Key Files

- **build.py** - Build configuration
- **requirements.txt** - Python dependencies
- **update.json** - Update information
- **.gitignore** - Git ignore rules

## Coding Standards

### Python Style Guide

1. **PEP 8**
   - Follow PEP 8 style guide for Python code
   - Use 4 spaces for indentation
   - Maximum line length of 88 characters

2. **Docstrings**
   - Use docstrings for all classes and functions
   - Follow the Google docstring format

3. **Type Hints**
   - Use type hints for function parameters and return values
   - Use the `typing` module for complex types

### Qt Conventions

1. **Widget Naming**
   - Use descriptive names for widgets
   - Follow the pattern `<type>_<purpose>` (e.g., `button_save`)

2. **Signal Connections**
   - Use lambda functions for simple connections
   - Use named functions for complex handlers

3. **Layout Management**
   - Use layout managers instead of fixed positioning
   - Prefer vertical and horizontal layouts

### File Organization

1. **Module Structure**
   - Each module should have a clear responsibility
   - Related functionality should be grouped together

2. **Import Order**
   - Standard library imports first
   - Third-party library imports second
   - Local imports last

3. **Class Structure**
   - Class attributes at the top
   - Constructor and initialization methods next
   - Public methods followed by private methods

## Contribution Workflow

### Issue Tracking

1. **Bug Reports**
   - Check if the issue already exists
   - Provide detailed steps to reproduce
   - Include error messages and logs

2. **Feature Requests**
   - Describe the feature and its benefits
   - Provide examples of how it would be used
   - Consider edge cases and potential issues

### Pull Requests

1. **Branch Naming**
   - Use descriptive branch names
   - Follow the pattern `<type>/<description>` (e.g., `feature/add-translation-memory`)

2. **Commit Messages**
   - Write clear and concise commit messages
   - Start with a verb in the present tense
   - Reference issue numbers when applicable

3. **Pull Request Description**
   - Describe the changes and their purpose
   - List any dependencies or requirements
   - Mention any related issues

### Code Review

1. **Review Process**
   - All code changes require review
   - Address review comments promptly
   - Request re-review after making changes

2. **Testing**
   - Ensure all tests pass
   - Add new tests for new functionality
   - Verify that the application works as expected

## Testing

### Manual Testing

1. **Functionality Testing**
   - Test all features and workflows
   - Verify that the UI behaves correctly
   - Check error handling and edge cases

2. **Integration Testing**
   - Test integration with mod managers
   - Verify that translations are applied correctly
   - Check compatibility with different game versions

### Automated Testing

1. **Unit Tests**
   - Write unit tests for core functionality
   - Use the `unittest` framework
   - Run tests before submitting changes

2. **UI Tests**
   - Test UI components and interactions
   - Verify that the UI responds correctly to user input
   - Check that the UI updates when data changes

## Documentation

### Code Documentation

1. **Docstrings**
   - Document all classes and functions
   - Explain parameters and return values
   - Provide examples for complex functionality

2. **Comments**
   - Use comments to explain complex logic
   - Avoid redundant comments
   - Keep comments up to date with code changes

### User Documentation

1. **Instructions**
   - Update user instructions when adding features
   - Provide clear and concise explanations
   - Include screenshots for visual guidance

2. **Localization**
   - Update localization files for new text
   - Ensure that all user-facing text is localized
   - Test with different languages

## Release Process

1. **Version Numbering**
   - Follow semantic versioning (MAJOR.MINOR.PATCH)
   - Increment MAJOR for incompatible changes
   - Increment MINOR for new features
   - Increment PATCH for bug fixes

2. **Release Preparation**
   - Update version number in `main.py`
   - Update changelog in `Changelog.md`
   - Update `update.json` for the auto-updater

3. **Distribution**
   - Build the application using `build.bat`
   - Create a ZIP archive of the `SSE-AT` folder
   - Upload to GitHub releases and Nexus Mods

## Resources

- [GitHub Repository](https://github.com/cruldra/SSE-Auto-Translator)
- [Nexus Mods Page](https://www.nexusmods.com/skyrimspecialedition/mods/...)
- [Discord Server](https://discord.gg/...)

## License

SSE Auto Translator is licensed under the Attribution-NonCommercial-NoDerivatives 4.0 International license. See the LICENSE file for details.
