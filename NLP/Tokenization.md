# Tokenization: Interview Questions and Answers

### 1. **What is Tokenization in NLP?**  
**Answer:**  
Tokenization is the process of breaking down text into smaller units called tokens. These tokens can be words, characters, or subwords, depending on the application. Tokenization is a fundamental preprocessing step in Natural Language Processing (NLP).

---

### 2. **Why is Tokenization important in NLP?**  
**Answer:**  
Tokenization is important because:  
- It helps convert unstructured text into structured data.  
- It enables efficient analysis of textual data by splitting it into manageable parts.  
- Many NLP models and algorithms require tokenized input.

---

### 3. **What are the types of Tokenization?**  
**Answer:**  
1. **Word Tokenization**: Splits text into words. Example: "Natural Language Processing" → ["Natural", "Language", "Processing"].  
2. **Character Tokenization**: Splits text into individual characters. Example: "NLP" → ["N", "L", "P"].  
3. **Subword Tokenization**: Breaks words into subwords or smaller units. Common in models like BERT. Example: "tokenization" → ["token", "##ization"].  

---

### 4. **How does Subword Tokenization work?**  
**Answer:**  
Subword Tokenization splits rare or unknown words into smaller, meaningful units based on frequency in a corpus. For example:  
- Byte Pair Encoding (BPE): Merges frequent character pairs iteratively.  
- WordPiece: Used in BERT, segments words into subwords using a vocabulary optimized for maximum likelihood.  

---

### 5. **What are the challenges of Tokenization?**  
**Answer:**  
1. **Ambiguity**: Words like "New York" could be a single entity or separate tokens.  
2. **Languages with No Spaces**: Tokenizing languages like Chinese or Japanese is challenging as they don't have spaces between words.  
3. **Misspellings/Errors**: Typos can complicate tokenization.  

---

### 6. **What is the difference between Tokenization and Stemming/Lemmatization?**  
**Answer:**  
- **Tokenization**: Splits text into smaller units (tokens).  
- **Stemming/Lemmatization**: Reduces words to their root or base form.  

Example:  
- Tokenization: "running fast" → ["running", "fast"]  
- Stemming: "running" → "run"  
- Lemmatization: "running" → "run"  

---

### 7. **What libraries or tools are commonly used for Tokenization?**  
**Answer:**  
1. **NLTK**: Provides `word_tokenize` and `sent_tokenize` methods.  
2. **SpaCy**: Efficient and fast tokenization for multiple languages.  
3. **Transformers (Hugging Face)**: For subword tokenization with pre-trained models.  
4. **OpenNLP**: Java-based library for tokenization and other NLP tasks.  

---

### 8. **How does Tokenization differ for programming languages (Code Tokenization)?**  
**Answer:**  
Code tokenization involves splitting source code into tokens like keywords, variables, operators, and literals, considering syntax and semantics of the programming language. Tools like **Tree-Sitter** or **ANTLR** are used for this purpose.  

---

### 9. **What is Sentence Tokenization? How does it differ from Word Tokenization?**  
**Answer:**  
- **Sentence Tokenization**: Splits text into sentences. Example: "Hello world. NLP is amazing." → ["Hello world.", "NLP is amazing."]  
- **Word Tokenization**: Splits sentences or text into words.  
Sentence tokenization is often a precursor to word tokenization.  

---

### 10. **What are some challenges in Tokenizing URLs or email addresses?**  
**Answer:**  
- URLs or emails contain multiple components like protocols, domains, or special characters which can be split incorrectly.  
- Example: "https://example.com" → ["https", ":", "/", "/", "example", ".", "com"].  
Custom regex or libraries like `URITokenizer` are used to handle these cases.  

---

### 11. **Explain how tokenization is handled in BERT.**  
**Answer:**  
BERT uses **WordPiece Tokenizer**, which splits words into subwords based on a fixed vocabulary.  
Example:  
- Input: "unaffordable"  
- Tokenized: ["un", "##afford", "##able"].  
The "##" indicates that the subword is part of a previous token.  

---

### 12. **How does tokenization affect the vocabulary size in NLP models?**  
**Answer:**  
- **Word Tokenization**: Larger vocabulary, as each unique word is a token.  
- **Subword Tokenization**: Smaller vocabulary, as words are broken into reusable subwords.  
Smaller vocabularies reduce memory usage and improve model generalization to unseen words.  

---

### 13. **What is Byte Pair Encoding (BPE)?**  
**Answer:**  
BPE is a subword tokenization technique that merges the most frequent pairs of characters in a corpus iteratively. It balances vocabulary size and token granularity, enabling better handling of rare words.  

---

### 14. **What is whitespace tokenization, and when is it used?**  
**Answer:**  
Whitespace tokenization splits text into tokens using spaces as delimiters.  
Example: "Tokenization is fun." → ["Tokenization", "is", "fun."].  
It’s simple but may not handle punctuation or special cases well.  

---

### 15. **Can Tokenization be language-agnostic?**  
**Answer:**  
Basic tokenization methods like character tokenization are language-agnostic. However, language-specific features like morphology, grammar, and punctuation often require customized tokenization strategies.  

---
