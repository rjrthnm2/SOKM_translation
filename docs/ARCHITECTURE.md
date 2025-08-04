# Technical Architecture

## System Overview

The SOKM Translation system employs a modular, provider-agnostic architecture designed for scalability, maintainability, and rapid deployment. The system processes English-to-Spanish translations with domain-specific enhancements and comprehensive quality evaluation.

## Core Components

### 1. LLM-based Translation Engine (`SOKM_machine_translation.ipynb`)

- **Purpose**: Core translation processing with multi-provider support
- **Design Pattern**: Strategy pattern for different AI providers (OpenAI GPT-4o, Google Gemini)
- **Key Features**:
  - Unified interface for multiple AI providers
  - Dictionary-enhanced translations using spaCy
  - Batch processing with error recovery
  - JSON-structured output parsing
  - Rate limiting and retry logic

### 2. Dictionary Enhancement Layer

- **Purpose**: Domain-specific terminology consistency and improving context accuracy
- **Implementation**: spaCy PhraseMatcher with custom preprocessing
- **Algorithm**:
  ```python
  # Intelligent phrase matching with context preservation
  matcher = PhraseMatcher(nlp.vocab, attr="LOWER")
  # Processes terms while maintaining grammatical context
  ```

### 3. Evaluation Framework (`SOKM_validation_GT.ipynb`)

- **Purpose**: Comprehensive translation quality assessment
- **Metrics Implemented**:
  - **BLEU**: N-gram precision for fluency assessment
  - **METEOR**: Semantic similarity with synonym matching
  - **WER**: Word Error Rate for transcription accuracy
  - **COMET**: Neural-based quality estimation (state-of-the-art)

### 4. Data Processing Pipeline

- **Input Handling**: CSV files with `Segment Text` column
- **Output Format**: Structured CSV with metadata (model, version, configuration)
- **Memory Management**: Chunked processing for large datasets

## Processing Pipeline Details

1. **Input Validation**: Schema validation, encoding detection, data quality checks
2. **Preprocessing**: Text normalization, segment preparation, context extraction
3. **Dictionary Enhancement**: Intelligent term identification and replacement preparation
4. **AI Translation**: Provider-specific API calls with retry logic and rate limiting
5. **Post-processing**: Output parsing, format standardization, quality checks
6. **Evaluation**: Multi-metric assessment against reference translations
7. **Output Generation**: Structured CSV with comprehensive metadata

### Scalability Features

- **Batch Processing**: Configurable batch sizes for memory management
- **Concurrent Processing**: Parallel API calls within rate limits

## Technology Justification

### Python Ecosystem Choice

- **Rapid Development**: Rich ML/NLP library ecosystem
- **Integration**: Seamless API integration with major AI providers
- **Data Processing**: Pandas for efficient CSV manipulation

### Jupyter Notebook Architecture

- **Rapid Prototyping**: Interactive development and testing
- **Documentation**: Self-documenting code with markdown cells
- **Reproducibility**: Version-controlled notebooks with output stripping
- **Collaboration**: Easy sharing and modification of processing steps
