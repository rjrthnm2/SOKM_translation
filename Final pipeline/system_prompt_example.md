# System Prompt Example

This directory contains system prompt files for various translation and text processing tasks. The actual prompt files are not included in this public repository to preserve privacy and proprietary content.

## System Prompt Structure

The system prompts in this project follow a structured format:

### Translation Prompts (`system_prompt_translate_*.txt`)

- **Role**: Defines the AI as an expert translator
- **Goal**: Specifies the translation task (English to Spanish)
- **Instructions**: Contains detailed rules for:
  - Subtitle formatting and line breaks
  - Fixed phrase mappings (domain-specific terminology)
  - Words/phrases that should not be translated
  - Grammar conventions (gender, number, formality)
  - Output formatting requirements

### Cleaning Prompts (`system_prompt_cleaning_*.txt`)

- **Role**: Defines the AI as a text cleaning specialist
- **Goal**: Specifies transcription cleaning and formatting tasks
- **Instructions**: Contains rules for:
  - Removing transcription artifacts
  - Standardizing punctuation and capitalization
  - Handling speaker changes and timestamps
  - Preserving semantic meaning while improving readability by removing disfluencies

### Editor Prompts (`system_prompt_editor_*.txt`)

- **Role**: Defines the AI as a text editor
- **Goal**: Specifies post-processing and refinement tasks
- **Instructions**: Contains guidelines for:
  - Final quality assurance checks
  - Consistency improvements
  - Cultural adaptation considerations
  - Format standardization

## Usage

To use this pipeline with your own content:

1. Create your own system prompt files following the structure above
2. Update the file paths in the notebooks to point to your prompt files
3. Modify the `DICTIONARY_PATH` and `system_prompt_file` variables as needed

## Versioning

System prompts are versioned (e.g., v1.0, v1.1, v2.0) to track improvements and maintain compatibility with different processing stages.
