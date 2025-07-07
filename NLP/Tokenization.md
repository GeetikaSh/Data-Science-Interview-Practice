# 🧠 Tokenization: Interview Questions and Answers

## 📌 What is Tokenization?

Before diving into tokenization-related interview questions, let’s first understand what tokenization is:

Computers do not understand raw text — they understand numbers. So, we need to convert human-readable language into machine-readable formats.

Tokenization is the process of breaking down a sentence or a piece of text into smaller units called **tokens**, typically words or subwords.

### ❗ Why Not Use ASCII Directly?

Let’s say we have the word `"SILENT"`:
- Each letter has its own ASCII value.
- But reordering these characters can form the word `"LISTEN"` (an anagram).
- Using only ASCII leads to **loss of semantic meaning** and **confusion** in understanding.

### ✅ With Tokenization

In tokenization, each **word** in the sentence is assigned a unique **token ID**. For example:

- `"I love my cat"` → `[0, 1, 2, 3]`
- `"I love my dog"` → `[0, 1, 2, 4]`

Now, comparing the two sentences becomes easier — **token 0, 1, and 2 are shared**, showing high similarity, and minimizing confusion.

### 🧪 Code Example: Using Keras Tokenizer

```python
import tensorflow as tf
from tensorflow.keras.preprocessing.text import Tokenizer

# Input sentences
sentences = [
    'i love my dog',
    'I, love my cat',
    'You love my dog!'
]

# Initialize tokenizer
tokenizer = Tokenizer(num_words=100)

# Fit tokenizer on sentences
tokenizer.fit_on_texts(sentences)

# Get the word index mapping
word_index = tokenizer.word_index

# Print the token dictionary
print(word_index)
```

```
output:
{'love': 1, 'my': 2, 'dog': 3, 'i': 4, 'cat': 5, 'you': 6}
```

### 🧠 Insight:
- The tokenizer automatically lowercases text and removes punctuation like commas and exclamation marks.
- "I, love my cat" and "You love my dog!" are cleaned and tokenized as if they had no punctuation.

---
## 🔁 Sequencing – Turning Sentences into Machine-Usable Data

Once tokenization is complete, the next step is to **convert these tokenized words into uniform-length sequences** — this is called **sequencing**.

### ❓ Why Use Sequencing?

Machine learning models require inputs to be of **uniform shape**. However, sentences can vary in length. Sequencing helps by:

- Converting text into integer sequences (tokenized)
- Padding shorter sequences with zeros so all sequences have the **same length**


### 🚫 What Happens If a Word Is Not in the Vocabulary?

If a word is **not present in the training corpus**, it's marked using an **OOV (Out-Of-Vocabulary) token**.

```python
tokenizer = Tokenizer(num_words=100, oov_token="<OOV>")
```

This ensures:
- No failure in processing unknown words
- Loss of information is minimized
- It helps the model generalize better on unseen data

### 🧩 What is Padding?
Not all sequences have the same length. pad_sequences() helps ensure equal-length input by adding padding tokens (usually 0) either at the start (pre-padding) or end (post-padding).

```python
pad_sequences(sequences, maxlen=5, padding='pre')
```
Default padding is `pre`. You can also use `post`.

### 🧪 Code Example: Sequencing and Padding with TensorFlow 

```python
import tensorflow as tf
from tensorflow import keras


from tensorflow.keras.preprocessing.text import Tokenizer
from tensorflow.keras.preprocessing.sequence import pad_sequences

sentences = [
    'I love my dog',
    'I love my cat',
    'You love my dog!',
    'Do you think my dog is amazing?'
]

tokenizer = Tokenizer(num_words = 100, oov_token="<OOV>")
tokenizer.fit_on_texts(sentences)
word_index = tokenizer.word_index

sequences = tokenizer.texts_to_sequences(sentences)

padded = pad_sequences(sequences, maxlen=5)
print("\nWord Index = " , word_index)
print("\nSequences = " , sequences)
print("\nPadded Sequences:")
print(padded)


# Try with words that the tokenizer wasn't fit to
test_data = [
    'i really love my dog',
    'my dog loves my manatee'
]

test_seq = tokenizer.texts_to_sequences(test_data)
print("\nTest Sequence = ", test_seq)

padded = pad_sequences(test_seq, maxlen=10)
print("\nPadded Test Sequence: ")
print(padded)
```

#### 📦 Output (Padded Sequences Example)

```text
Word Index =  {'<OOV>': 1, 'my': 2, 'love': 3, 'dog': 4, 'i': 5, 'you': 6, 'cat': 7, 'do': 8, 'think': 9, 'is': 10, 'amazing': 11}

Sequences =  [[5, 3, 2, 4], [5, 3, 2, 7], [6, 3, 2, 4], [8, 6, 9, 2, 4, 10, 11]]

Padded Sequences:
[[ 0  5  3  2  4]
 [ 0  5  3  2  7]
 [ 0  6  3  2  4]
 [ 9  2  4 10 11]]

Test Sequence =  [[5, 1, 3, 2, 4], [2, 4, 1, 2, 1]]

Padded Test Sequence: 
[[0 0 0 0 0 5 1 3 2 4]
 [0 0 0 0 0 2 4 1 2 1]]
```

---

### **Why is Tokenization important in NLP?**  
**Answer:**  
Tokenization is important because:  
- It helps convert unstructured text into structured data.  
- It enables efficient analysis of textual data by splitting it into manageable parts.  
- Many NLP models and algorithms require tokenized input.

### **What are the types of Tokenization?**  
**Answer:**  
1. **Word Tokenization**: Splits text into words. Example: "Natural Language Processing" → ["Natural", "Language", "Processing"].  
2. **Character Tokenization**: Splits text into individual characters. Example: "NLP" → ["N", "L", "P"].  
3. **Subword Tokenization**: Breaks words into subwords or smaller units. Common in models like BERT. Example: "tokenization" → ["token", "##ization"].

### **How does Subword Tokenization work?**  
**Answer:**  
Subword Tokenization splits rare or unknown words into smaller, meaningful units based on frequency in a corpus. For example:  
- Byte Pair Encoding (BPE): Merges frequent character pairs iteratively.  
- WordPiece: Used in BERT, segments words into subwords using a vocabulary optimized for maximum likelihood.  

### **What are the challenges of Tokenization?**  
**Answer:**  
1. **Ambiguity**: Words like "New York" could be a single entity or separate tokens.  
2. **Languages with No Spaces**: Tokenizing languages like Chinese or Japanese is challenging as they don't have spaces between words.  
3. **Misspellings/Errors**: Typos can complicate tokenization.  

### **What is the difference between Tokenization and Stemming/Lemmatization?**  
**Answer:**  
- **Tokenization**: Splits text into smaller units (tokens).  
- **Stemming/Lemmatization**: Reduces words to their root or base form.  

Example:  
- Tokenization: "running fast" → ["running", "fast"]  
- Stemming: "running" → "run"  
- Lemmatization: "running" → "run"  

### **What libraries or tools are commonly used for Tokenization?**  
**Answer:**  
1. **NLTK**: Provides `word_tokenize` and `sent_tokenize` methods.  
2. **SpaCy**: Efficient and fast tokenization for multiple languages.  
3. **Transformers (Hugging Face)**: For subword tokenization with pre-trained models.  
4. **OpenNLP**: Java-based library for tokenization and other NLP tasks.  

### **What is Sentence Tokenization? How does it differ from Word Tokenization?**  
**Answer:**  
- **Sentence Tokenization**: Splits text into sentences. Example: "Hello world. NLP is amazing." → ["Hello world.", "NLP is amazing."]  
- **Word Tokenization**: Splits sentences or text into words.  
Sentence tokenization is often a precursor to word tokenization.  

### 10. **What are some challenges in Tokenizing URLs or email addresses?**  
**Answer:**  
- URLs or emails contain multiple components like protocols, domains, or special characters which can be split incorrectly.  
- Example: "https://example.com" → ["https", ":", "/", "/", "example", ".", "com"].  
Custom regex or libraries like `URITokenizer` are used to handle these cases.  

### **Explain how tokenization is handled in BERT.**  
**Answer:**  
BERT uses **WordPiece Tokenizer**, which splits words into subwords based on a fixed vocabulary.  
Example:  
- Input: "unaffordable"  
- Tokenized: ["un", "##afford", "##able"].  
The "##" indicates that the subword is part of a previous token.  

### **How does tokenization affect the vocabulary size in NLP models?**  
**Answer:**  
- **Word Tokenization**: Larger vocabulary, as each unique word is a token.  
- **Subword Tokenization**: Smaller vocabulary, as words are broken into reusable subwords.  
Smaller vocabularies reduce memory usage and improve model generalization to unseen words.  

### **What is Byte Pair Encoding (BPE)?**  
**Answer:**  
BPE is a subword tokenization technique that merges the most frequent pairs of characters in a corpus iteratively. It balances vocabulary size and token granularity, enabling better handling of rare words.  

### **What is whitespace tokenization, and when is it used?**  
**Answer:**  
Whitespace tokenization splits text into tokens using spaces as delimiters.  
Example: "Tokenization is fun." → ["Tokenization", "is", "fun."].  
It’s simple but may not handle punctuation or special cases well.  

### **Can Tokenization be language-agnostic?**  
**Answer:**  
Basic tokenization methods like character tokenization are language-agnostic. However, language-specific features like morphology, grammar, and punctuation often require customized tokenization strategies.

---

### Interview Tip:

- Be ready to explain the difference between tokenization and embedding.
- Also know subword tokenization methods like Byte-Pair Encoding (BPE) and WordPiece.
- Language Agnostic
