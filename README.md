# 📘 Information Retrieval with Inverted Index and B-Tree (Python)

This repository contains an educational Information Retrieval (IR) system written in Python.  
It builds an **Inverted Index** over a set of text documents and stores the dictionary (term → posting list) using a custom **B-Tree** data structure.

This project is suitable for learning IR fundamentals, B-Tree data structures, and basic search techniques.

---

## 🚀 Features

- **Text normalization and tokenization**  
- **Inverted index** (term → set of document IDs)  
- **Custom B-Tree implementation** for storing the index  
- **Efficient term lookup** via B-Tree search  
- **ASCII visualization** of the B-Tree structure  
- **Full output saving** (documents, terms, postings, tree) to a file  

---

## 📁 Project Structure

information-retrieval/
│
├── docs/ # Document text files (input)
│ ├── doc1.txt
│ ├── doc2.txt
│ └── doc3.txt
│
├── invertedIndex.py # Core inverted index + B-Tree logic
├── IRQuery.py # Query interface for searching terms
├── README.md # This file
└── full_output.txt # (Generated) full output dump

yaml
Copy code

Each `.txt` file in the `docs/` directory is treated as a document.  
The filename (without extension) is used as the document ID.

---

## 🧠 Core Components

### 1. **SimpleTokenizer**
- Converts text to lowercase  
- Removes punctuation  
- Splits text based on whitespace  

The tokenizer ensures consistent normalization across all documents.

---

### 2. **B-Tree Implementation**
A custom B-Tree is used to store the inverted dictionary efficiently.  
It supports:

- `insert(key, value)`
- `search(key)`
- `traverse()`
- `ascii_print()`  

The B-Tree stores:
- **term** as key  
- **posting list** (list of document IDs) as value

This enables faster lookup than a simple list or dictionary for large term sets.

---

### 3. **InvertedIndex**
This class builds and manages the inverted index:

- Tokenizes documents  
- Builds term → document mapping  
- Inserts all terms into the B-Tree  
- Performs search queries  
- Saves/loads index to/from JSON  

---

## 📌 How to Run

### 💾 Prepare Input Documents

Create a folder named `docs` at the root of the project.  
Add `.txt` files containing your text documents, for example:

docs/
├── doc1.txt
├── doc2.txt
└── doc3.txt

css
Copy code

Example contents of a doc:

Information retrieval systems rely on indexing and efficient search.

yaml
Copy code

---

### ▶ Run the Program

```bash
python IRQuery.py
🖨 Output
Running the program will generate:

✅ Terminal Output:
Full document content

All extracted terms (sorted)

Complete inverted index (term → postings)

B-Tree traversal output

ASCII visualization of the B-Tree

📄 File Output:
Copy code
full_output.txt
Contains:

Full documents

All terms

Posting lists

ASCII B-Tree structure

🧩 Example ASCII B-Tree Output
css
Copy code
['algorithm', 'data']
    ['buffer', 'compute']
    ['index', 'memory', 'search']
(The exact structure depends on input data and B-Tree configuration.)

⚙️ Configuration
You can adjust the B-Tree degree (branching factor):

python
Copy code
INVERTED_INDEX, DOCUMENTS = demo_build_and_show_from_files(
    input_dir="docs",
    btree_t=3
)
Larger t → wider, shallower tree

Smaller t → narrower, deeper tree

📝 Notes
This implementation focuses on clarity and learning rather than performance.
It does NOT include:

Stemming or lemmatization

Stop-word removal

Positional indexes

TF-IDF weighting or ranking

Boolean query operators

Those can be added as future enhancements.

🚀 Possible Extensions
Add TF-IDF weighting for ranked retrieval

Enable Boolean queries (AND/OR/NOT)

Add positional inverted index for phrase search

Support Persian/Unicode text

Export index to disk-based B-Tree

🎓 Author
An educational implementation for learning:

Inverted Index structures

B-Tree data structure

Fundamentals of Information Retrieval

