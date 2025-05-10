# SSE Auto Translator - Project Architecture

## Overview

SSE Auto Translator (SSE-AT) is a tool designed to help users translate mods for Skyrim Special Edition. It provides a user-friendly interface for managing, creating, and applying translations to game mods. The application is built using Python with Qt for the GUI and integrates with popular mod managers like Mod Organizer 2 and Vortex.

## Core Components

### Main Application (`MainApp` class)

The central class that initializes and manages the application. Located in `src/main.py`, it:
- Handles application startup and configuration
- Manages paths for data, configuration, and resources
- Initializes the GUI and other components
- Provides access to shared resources like the translation database and cacher

### Mod Management

The application interacts with mod managers through the following components:

1. **ModManager Interface** (`src/mod_managers/mod_manager.py`)
   - Base class for all mod manager implementations
   - Defines methods for retrieving mod instances and mod lists

2. **Mod Organizer 2 Support** (`src/mod_managers/modorganizer.py`)
   - Implements the ModManager interface for MO2
   - Handles parsing MO2 configuration files and mod metadata

3. **Vortex Support** (`src/mod_managers/vortex.py`)
   - Implements the ModManager interface for Vortex
   - Uses LevelDB to access Vortex's state database

### Translation System

The translation system consists of several key components:

1. **Translation Database** (`src/database/database.py`)
   - Manages the collection of translations
   - Handles loading, saving, and querying translations
   - Maintains both vanilla (base game) and user translations

2. **Translation Class** (`src/database/translation.py`)
   - Represents a single translation for a mod
   - Contains methods for loading, saving, and exporting translations
   - Manages the collection of strings for each plugin

3. **String Class** (`src/utilities/string.py`)
   - Represents a single translatable string
   - Contains metadata like editor ID, form ID, and string type
   - Tracks translation status (complete, incomplete, required, etc.)

4. **Translator APIs** (`src/translator_api/`)
   - Base class: `src/translator_api/translator.py`
   - Implementations for different translation services (Google, DeepL)
   - Provides methods for translating individual strings and batches

5. **Translation Provider** (`src/translation_provider/provider.py`)
   - Manages sources for translations (Nexus Mods, Confrerie)
   - Handles API interactions with translation sources
   - Provides methods for finding and retrieving translations

### User Interface

The UI is built with Qt and organized into several main components:

1. **Main Page** (`src/main_page.py`)
   - Primary interface showing mod list and translation database
   - Provides buttons for scanning, downloading, and building translations

2. **Translation Editor** (`src/translation_editor/`)
   - Interface for creating and editing translations
   - Allows users to translate strings manually or with translation APIs

3. **Settings Dialog** (`src/settings/`)
   - Configures application, user, and translator settings
   - Manages mod manager integration and API keys

4. **Startup Dialog** (`src/startup_dialog/`)
   - Guides first-time users through setup
   - Handles Nexus Mods authentication and mod manager selection

### Utility Components

1. **Cacher** (`src/cacher.py`)
   - Caches plugin strings to improve performance
   - Avoids repeated parsing of the same plugins

2. **Processor** (`src/processor.py`)
   - Handles batch operations like scanning mod lists and building outputs
   - Manages the workflow for creating and applying translations

3. **Localization** (`src/utilities/localisation.py`)
   - Manages application translations
   - Loads language files based on user preferences

4. **Archive Parser** (`src/archive_parser.py`)
   - Extracts files from mod archives (.zip, .7z, .rar)
   - Used when importing translations from archives

## Data Flow

1. **Mod Discovery**
   - Application connects to the selected mod manager
   - Retrieves the list of installed mods and their plugins
   - Displays them in the mod list panel

2. **Translation Scanning**
   - User initiates a scan of the mod list
   - Application checks which mods need translations
   - Scans Nexus Mods for available translations

3. **Translation Download**
   - User selects translations to download
   - Application downloads and processes the translations
   - Adds them to the translation database

4. **Translation Application**
   - User builds the output for Dynamic String Distributor
   - Application exports translations to the DSD format
   - Creates a mod that can be installed in the mod manager

5. **Translation Editing**
   - User can create or edit translations in the editor
   - Strings can be translated manually or with translation APIs
   - Changes are saved to the translation database

## File Structure

- **src/** - Main source code
  - **data/** - Application data (icons, styles, localization)
  - **database/** - Translation database management
  - **mod_managers/** - Mod manager integrations
  - **settings/** - Settings dialog components
  - **startup_dialog/** - First-time setup components
  - **translation_editor/** - Translation editor components
  - **translator_api/** - Translation service integrations
  - **translation_provider/** - Translation source management
  - **utilities/** - Utility functions and classes

- **doc/** - Documentation
  - **imgs/** - Images for documentation
  - **Instructions_*.md** - User instructions in different languages

- **masterlists/** - Lists of plugins to ignore or handle specially

## Configuration

The application uses several configuration files:

1. **App Config** (`data/app/config.json`)
   - General application settings
   - UI preferences and logging settings

2. **User Config** (`data/user/config.json`)
   - User-specific settings
   - Mod manager selection and API keys

3. **Translator Config** (`data/translator/config.json`)
   - Translation API settings
   - API keys and preferences

## Integration Points

1. **Nexus Mods API**
   - Used to find and download translations
   - Handles authentication and API requests

2. **Mod Managers**
   - Integrates with MO2 and Vortex
   - Reads mod lists and configuration

3. **Dynamic String Distributor**
   - SKSE plugin that applies translations in-game
   - SSE-AT generates compatible output files

4. **Translation APIs**
   - Integrates with Google Translate and DeepL
   - Used for automatic translation of strings
