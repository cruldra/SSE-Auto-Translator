# SSE Auto Translator - Translation Workflow

## Overview

This document describes the translation workflow in SSE Auto Translator (SSE-AT), explaining how the application handles the process of finding, creating, and applying translations for Skyrim Special Edition mods.

## Translation Sources

SSE-AT can obtain translations from multiple sources:

1. **Nexus Mods**
   - The primary source for translations
   - Uses the Nexus Mods API to find translations for installed mods
   - Downloads translation files directly from Nexus Mods

2. **Confrerie des Traducteurs**
   - Alternative source for translations
   - Specialized in French translations
   - Integrated as an additional translation provider

3. **Local Files**
   - Users can import translations from local files
   - Supports various formats including archives (.zip, .7z, .rar), plugins (.esp, .esm, .esl), DSD translations (.json), and xTranslator exports (.xml)

4. **Machine Translation**
   - Built-in integration with translation APIs
   - Supports Google Translate and DeepL
   - Used for automatic translation of strings

## Translation Database

The application maintains a database of translations:

1. **Vanilla Translation**
   - Contains translations for base game strings
   - Used as a reference for creating new translations

2. **User Translations**
   - Translations installed by the user
   - Stored in the user database directory
   - Indexed for quick access and management

## Translation Workflow

### 1. Scanning Mod List

When the user initiates a mod list scan:

1. The application retrieves the list of installed mods from the selected mod manager
2. For each mod, it identifies the plugins that need translation
3. It checks the translation database to see which plugins already have translations
4. It marks plugins as:
   - Translated: A translation exists in the database
   - Untranslated: No translation exists
   - Partially Translated: Some strings are translated, but not all

### 2. Scanning for Available Translations

When the user initiates an online scan:

1. The application uses the Translation Provider to search for translations
2. For each untranslated mod, it queries Nexus Mods and/or Confrerie
3. It filters results based on the user's language preference
4. It presents a list of available translations to the user

### 3. Downloading Translations

When the user selects translations to download:

1. The application downloads the translation files
2. It extracts and processes the files based on their format
3. It converts the translations to the internal format
4. It adds the translations to the database
5. It updates the status of the affected plugins

### 4. Creating Translations

Users can create new translations using the Translation Editor:

1. The user selects a plugin to translate
2. The application extracts strings from the plugin
3. The user can translate strings manually or use translation APIs
4. The application saves the translation to the database

### 5. Building Output

To apply translations in-game:

1. The user builds the output for Dynamic String Distributor (DSD)
2. The application exports translations to the DSD format
3. It creates a mod that can be installed in the mod manager
4. DSD applies the translations in-game

## String Processing

### String Extraction

Strings are extracted from plugins using the following process:

1. The application parses the plugin file structure
2. It identifies records that contain translatable strings
3. It extracts the strings along with metadata (editor ID, form ID, type)
4. It creates String objects for each extracted string

### String Translation

Strings can be translated in several ways:

1. **Manual Translation**
   - User enters translations directly in the Translation Editor
   - Most accurate but time-consuming

2. **Automatic Translation**
   - Uses translation APIs to translate strings automatically
   - Quick but may require manual review

3. **Database Translation**
   - Applies existing translations from the database
   - Useful for strings that appear in multiple plugins

### String Status

Each string has a status that indicates its translation state:

1. **Translation Required**
   - String needs to be translated
   - No translation exists

2. **Translation Incomplete**
   - String has been automatically translated
   - Needs manual review

3. **Translation Complete**
   - String has been translated and verified
   - Ready for use

4. **No Translation Required**
   - String should not be translated
   - Marked by the user to be skipped

## Output Format

SSE-AT generates output for the Dynamic String Distributor (DSD) SKSE plugin:

1. **File Structure**
   - Creates a directory structure compatible with DSD
   - Organizes translations by plugin

2. **JSON Format**
   - Exports translations as JSON files
   - Each file contains the translated strings for a plugin

3. **Metadata**
   - Includes information about the original string
   - Preserves editor IDs, form IDs, and string types

## Integration with Dynamic String Distributor

The Dynamic String Distributor (DSD) is an SKSE plugin that applies translations in-game:

1. DSD loads the translation files generated by SSE-AT
2. It intercepts string requests from the game
3. It replaces original strings with translated versions
4. It handles different string types and contexts

This approach allows translations to be applied without modifying the original plugin files, making it compatible with updates and other mods.

## Workflow Diagram

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   Mod Manager   │────▶│   Mod Scanner   │────▶│ Online Scanner  │
└─────────────────┘     └─────────────────┘     └─────────────────┘
                                                         │
                                                         ▼
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  DSD Output     │◀────│  Translation    │◀────│   Translation   │
│  Generator      │     │   Database      │     │   Downloader    │
└─────────────────┘     └─────────────────┘     └─────────────────┘
        │                        ▲
        │                        │
        ▼                        │
┌─────────────────┐     ┌─────────────────┐
│  Dynamic String │     │   Translation   │
│   Distributor   │     │     Editor      │
└─────────────────┘     └─────────────────┘
```
