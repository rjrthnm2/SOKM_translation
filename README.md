# SOKM Translation Pipeline

A comprehensive machine translation pipeline for English-to-Spanish translation using OpenAI GPT and Google Gemini models, with dictionary-enhanced accuracy and automated evaluation.

## Features

- **Multi-provider support**: OpenAI GPT-4 and Google Gemini
- **Dictionary-enhanced translation**: Uses spaCy for intelligent term matching
- **Batch processing**: Efficient handling of large CSV datasets
- **Automated evaluation**: BLEU, METEOR, WER, and COMET metrics
- **Context preservation**: Maintains translation consistency across segments

## Privacy Notice

This public repository contains the core translation pipeline code but excludes:
- **System prompt files** (`system_prompt_*.txt`) - Contains domain-specific translation rules
- **Dictionary files** (`en_es_dictionary.txt`) - Contains specialized terminology mappings
- **API keys** (`.env` files) - Protected environment variables
- **Data files** - Input/output CSV files with potentially sensitive content

See `system_prompt_example.md` for the general structure of system prompts.

## Setup

1. **Install dependencies**:
   ```bash
   pip install openai google-generativeai python-dotenv pandas spacy
   pip install nltk jiwer comet-ml torch seaborn matplotlib
   python -m spacy download en_core_web_trf
   ```

2. **Configure environment**:
   Create a `.env` file in the `Final pipeline/` directory:
   ```
   OPENAI_API_KEY=your_openai_key_here
   GOOGLE_API_KEY=your_google_key_here
   ```

3. **Prepare your content**:
   - Create your system prompt files following the structure in `system_prompt_example.md`
   - Prepare your dictionary file (tab-separated: English\tSpanish\tDetails)
   - Update file paths in the main script

## Usage

### Translation Pipeline

```python
# Configure your settings
MODEL_PROVIDER = "openai"  # or "gemini"
ENABLE_DICTIONARY = True
DICTIONARY_PATH = "your_dictionary.txt"

# Update paths in the main section
input_csv_path = "path/to/your/input.csv"
system_prompt_file = "your_system_prompt.txt"
```

The input CSV should have a `Segment Text` column with the text to translate.

### Evaluation

```python
# Update evaluation paths
REFERENCE_CSV = "path/to/your/reference.csv"
MT_PATTERN = "path/to/your/translated_*.csv"
```

The reference CSV should have:
- `Segment Text`: Original English text
- `Translation_nativespeaker`: Human reference translation

## File Structure

```
Final pipeline/
├── .env                              # API keys (private)
├── en_es_dictionary.txt              # Dictionary (private)
├── system_prompt_*.txt               # System prompts (private)
├── system_prompt_example.md          # Public example structure
├── SOKM_machine_translation.ipynb    # Main translation pipeline
└── other_notebooks.ipynb            # Additional processing tools
```

## Models

- **OpenAI**: GPT-4 Turbo with JSON response formatting
- **Google**: Gemini 2.5 Pro with structured output
- **spaCy**: en_core_web_trf for linguistic analysis
- **COMET**: Unbabel/wmt22-comet-da for translation evaluation

## Output

Translated files are automatically named with model and configuration info:
```
input_translated_d_openai_gpt_4_1_pv2.0.csv
```

Where:
- `d_` indicates dictionary was used
- `openai_gpt_4_1` is the model identifier
- `pv2.0` is the system prompt version

## Contributing

When contributing, ensure:
- No API keys or sensitive data in commits
- System prompts and dictionaries remain private
- Generic examples for configuration
- Proper `.gitignore` coverage

## License

MIT License - See LICENSE file for details.
