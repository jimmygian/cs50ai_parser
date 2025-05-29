# CS50AI | Lecture 6 - Language | Project 6 - [Parser](https://cs50.harvard.edu/ai/2024/projects/6/parser/)

This project is a mandatory assignment from **CS50AI – Lecture 6: "Language"**. It involves developing an AI to parse sentences and extract noun phrases using **context-free grammar (CFG)** and **natural language processing (NLP)** techniques. The parser is designed to understand the syntactic structure of English sentences and identify key components, such as noun phrases, which are crucial for understanding the meaning of the sentence.

---

## 📌 Usage

To run the project locally, follow these steps:

1. **Clone the Repository**

   Begin by cloning the repository to your local machine:

   ```bash
   git clone https://github.com/your-username/cs50ai-parser.git
   cd cs50ai-parser
   ```

2. **Install Requirements**

   Install the necessary Python packages using pip. This project requires the Natural Language Toolkit (NLTK) for parsing and tokenization:

   ```bash
   pip install -r requirements.txt
   ```

   Note: If you encounter any issues with NLTK, you may need to install the necessary corpora and models. You can do this by running the following command: `python -m nltk.downloader all`

3. **Run the Project**

   Execute the program using Python. You can input a sentence directly or specify a file containing a sentence:

   ```bash
   python parser.py
   ```

   - **Interactive Mode:** Enter a sentence when prompted.
   - **File Mode:** Provide a filename as a command-line argument to read the sentence from a file.

4. **View the Results**

   - The program will display the parse tree of the sentence, illustrating its syntactic structure.
   - It will also list all noun phrase chunks extracted from the sentence, highlighting the key noun phrases.

---

## Project Overview

In this project, the goal is to parse English sentences to determine their structure and extract noun phrases. Parsing is a fundamental task in NLP that helps in understanding the grammatical structure of sentences, which is essential for various applications like information extraction, machine translation, and sentiment analysis.

### Key Features:

- **Context-Free Grammar (CFG):** The project uses CFG to define the grammatical rules for parsing sentences. CFG is a type of formal grammar that is well-suited for modeling the syntax of natural languages.
- **Sentence Parsing:** The parser uses NLTK's `ChartParser` to generate parse trees, which visually represent the syntactic structure of sentences.
- **Noun Phrase Extraction:** The parser identifies noun phrase chunks, which are contiguous sequences of words that function as a noun phrase, without containing nested noun phrases.

---

## My Task

- **Implemented Core Functions:**
  - `preprocess()`: This function tokenizes and preprocesses sentences to prepare them for parsing. It converts the sentence to lowercase and removes any non-alphabetic tokens.
  - `np_chunk()`: This function extracts noun phrase chunks from the parse tree. It identifies subtrees labeled as `NP` that do not contain other `NP` subtrees.
  - Defined CFG rules in `NONTERMINALS` to parse a variety of sentence structures, allowing the parser to handle complex sentences.

- **Ensured Code Efficiency:**
  - Optimized CFG rules to balance between over-generation (accepting invalid sentences) and under-generation (rejecting valid sentences).
  - Utilized NLTK's efficient parsing capabilities to handle multiple parse trees for ambiguous sentences.

---

## Implementation Explanation

### 1. Context-Free Grammar (CFG)

The CFG is defined to parse sentences and identify noun phrases:

- **Nonterminal Symbols:** These include `S` (Sentence), `NP` (Noun Phrase), `VP` (Verb Phrase), `PP` (Prepositional Phrase), etc. They represent different components of a sentence.
- **Terminal Symbols:** These include parts of speech like `N` (Noun), `V` (Verb), `Adj` (Adjective), `Adv` (Adverb), etc. They represent the actual words in the sentence.
- **Rules:** The CFG rules define how sentences and phrases are structured. For example, a sentence (`S`) can be composed of a noun phrase (`NP`) followed by a verb phrase (`VP`).

### 2. Sentence Parsing

The program uses NLTK's `ChartParser` to generate parse trees based on the defined CFG rules. The parse tree visually represents the hierarchical structure of the sentence, showing how different components relate to each other.

### 3. Noun Phrase Chunking

The `np_chunk()` function identifies noun phrase chunks by traversing the parse tree. It extracts subtrees labeled as `NP` that do not contain nested `NP` subtrees, ensuring that only the most granular noun phrases are identified.

---

## Example Output

### Terminal Output

When you run the program and input a sentence like "Holmes sat.", the output will be:

```
        S
   ***|***
  NP        VP
  |         |
  N         V
  |         |
holmes     sat

Noun Phrase Chunks
holmes
```

This output shows the parse tree and the extracted noun phrase chunk "holmes".

---

## Challenges & Learnings

- Designing CFG rules to accurately parse complex sentence structures while avoiding over-generation and under-generation.
- Implementing efficient noun phrase extraction without nested phrases, which required careful tree traversal and understanding of parse tree structures.
- Gaining a deeper understanding of natural language processing and parsing techniques, which are crucial for building intelligent language-based applications.

This project enhanced my understanding of **context-free grammar (CFG)** and **natural language processing (NLP)** techniques in AI, providing valuable insights into the complexities of language parsing and information extraction.
