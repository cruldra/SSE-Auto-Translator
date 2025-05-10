# SSE Auto Translator - User Interface

## Overview

SSE Auto Translator (SSE-AT) provides a comprehensive user interface for managing translations of Skyrim Special Edition mods. This document describes the main components of the user interface and their functions.

## Main Window

The main window is divided into several key areas:

### Main Page

The main page is the primary interface for managing mods and translations. It consists of:

1. **Mod List Panel**
   - Displays all mods and their plugins
   - Shows the translation status of each plugin
   - Allows selection of mods for scanning and translation
   - Provides context menu for additional actions

2. **Database Panel**
   - Shows installed translations
   - Displays coverage information for each translation
   - Provides options for importing, updating, and managing translations

3. **Main Toolbar**
   - Scan Mod List: Scans the mod list for translation needs
   - Scan Nexus Mods: Searches for available translations online
   - Download Translations: Downloads and installs selected translations
   - Build Output: Creates output files for Dynamic String Distributor

### Translation Editor

The Translation Editor is used for creating and editing translations. It includes:

1. **Side Menu**
   - Lists open translations and plugins
   - Allows navigation between different translation files

2. **String List**
   - Displays strings that need translation
   - Shows metadata like editor ID, form ID, and string type
   - Indicates translation status with color coding

3. **Editor Panel**
   - Shows the original string
   - Provides a text area for entering the translation
   - Includes buttons for automatic translation and navigation

## Dialog Windows

The application includes several important dialog windows:

### Startup Dialog

Guides first-time users through the setup process:

1. **Introduction Page**
   - Welcomes the user and explains the application
   - Allows language selection

2. **Setup Page**
   - Handles Nexus Mods authentication
   - Configures basic settings

3. **Instance Page**
   - Selects the mod manager and instance to use
   - Configures mod manager integration

### Settings Dialog

Provides access to application settings:

1. **App Settings**
   - General application settings
   - UI preferences and logging options

2. **User Settings**
   - Mod manager selection
   - Instance and profile configuration
   - Translation preferences

3. **Translator API Settings**
   - Selection of translation API
   - API key configuration
   - Translation options

### Other Dialogs

1. **String List Dialog**
   - Displays strings from a plugin or translation
   - Used for reference and debugging

2. **Ignore List Dialog**
   - Shows plugins that are excluded from translation
   - Allows management of the ignore list

3. **Loading Dialog**
   - Displays progress during long operations
   - Shows detailed status information

## UI Components

### Tree Widgets

Tree widgets are used extensively in the application:

1. **Mod List Tree**
   - Hierarchical view of mods and plugins
   - Supports checkboxes for selection
   - Uses color coding for status indication

2. **Translation Tree**
   - Shows installed translations
   - Organizes translations by source and status

### Custom Widgets

The application includes several custom widgets:

1. **Search Bar**
   - Provides filtering for lists and trees
   - Supports advanced search options

2. **Stacked Bar**
   - Shows progress and statistics
   - Used in the mod list and database panels

3. **Shortcut Button**
   - Combines button and shortcut functionality
   - Used in the main toolbar

## Color Coding

The application uses color coding to indicate status:

1. **Plugin Status**
   - Green: Fully translated
   - Yellow: Partially translated
   - Red: Not translated
   - Gray: Ignored

2. **String Status**
   - Green: Translation complete
   - Yellow: Translation incomplete
   - Red: Translation required
   - Gray: No translation required

## Keyboard Shortcuts

The application supports several keyboard shortcuts:

1. **F5**: Refresh the current view
2. **Ctrl+S**: Save the current translation
3. **Ctrl+Z**: Undo the last edit
4. **Ctrl+Y**: Redo the last edit
5. **Ctrl+F**: Focus the search bar

## Themes and Styling

The application uses a customizable theme system:

1. **Accent Color**
   - User-configurable accent color
   - Applied to buttons, highlights, and selected items

2. **Dark Mode**
   - Dark theme for reduced eye strain
   - Consistent styling across all components

3. **QSS Styling**
   - Uses Qt Style Sheets for UI customization
   - Styles are defined in `data/app/style.qss`

## Localization

The user interface is fully localized:

1. **Language Selection**
   - Supports multiple languages
   - Can use system language or user selection

2. **Localization Files**
   - Stored in `data/locales/<language>`
   - JSON format for easy editing

3. **Dynamic Text**
   - All UI text is loaded from localization files
   - Updates immediately when language is changed

## Responsive Design

The interface adapts to different window sizes:

1. **Splitters**
   - Allow resizing of panels
   - Remember user preferences

2. **Minimum Sizes**
   - Ensure components remain usable at smaller sizes

3. **Scrolling**
   - Provides scrollbars for content that doesn't fit

## Accessibility Features

The application includes several accessibility features:

1. **Keyboard Navigation**
   - All functions accessible via keyboard
   - Tab order follows logical flow

2. **Screen Reader Support**
   - UI elements have descriptive names
   - Status information is provided in text form

3. **High Contrast**
   - Color choices ensure readability
   - Status indicators use both color and icons

## UI Workflow

The typical UI workflow follows these steps:

1. User selects mods in the Mod List Panel
2. User scans for translation needs
3. User searches for available translations
4. User downloads and installs translations
5. User builds output for Dynamic String Distributor
6. User can edit translations in the Translation Editor

This workflow is designed to be intuitive and efficient, allowing users to quickly find and apply translations for their mods.
