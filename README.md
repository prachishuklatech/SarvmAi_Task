📌 Overview

This project implements a spell correction system for non-English words (e.g., Hindi, Marathi) written in the English alphabet.

It handles:

Typographical errors → "ROM" → "Ram"

Phonetic deviations → "RAAM" → "Ram"

Vowel stretching/reduction → "Aum" → "Aam"

Case insensitivity → "RAM" → "Ram"

The system corrects large text files by referencing a dictionary of correct spellings and applying fuzzy matching + phonetic matching + custom rules for maximum accuracy.

📂 Files in This Project
File/Folder	Description
errors.txt	Input file containing ~10,000 misspelled words (one per line).
reference.txt	Dictionary file with ~5,000 correct words (spelled in English script).
corrected.txt	First-pass correction output (basic fuzzy matching).
output.txt	Final corrected file (with phonetic + custom rules + hybrid scoring).
Untitled12.ipynb	Jupyter Notebook (Colab compatible) with the complete implementation.

README.md	Project documentation (this file).
⚙️ Approach
🔹 Step 1: Basic Fuzzy Matching

Uses RapidFuzz library (fuzz.ratio) to match misspelled words to the closest dictionary entry.

Normalizes words by:

Lowercasing (RAM → ram)

Removing repeated letters (raam → ram)

🔹 Step 2: Custom Rules

Applies simple replacement rules for common Indian-language spellings:

"ph" → "f"

"bh" → "b"

"au" → "aa"

Example: "phestival" → "festival"

🔹 Step 3: Phonetic Matching

Uses Soundex / DMetaphone to compare words by how they sound rather than how they are spelled.

"Ram" and "Raam" → same phonetic code

🔹 Step 4: Hybrid Scoring

Final similarity = 70% fuzzy score + 30% phonetic score.
This balances spelling similarity with sound similarity.

🚀 How to Run (Google Colab)
Step 1: Open Colab

👉 Google Colab

Click New Notebook.

Step 2: Upload Files
from google.colab import files
uploaded = files.upload()  # choose errors.txt and reference.txt

Step 3: Install Dependencies
!pip install rapidfuzz fuzzy

Step 4: Run the Spell Corrector Code

For basic correction (fuzzy only) → generates corrected.txt.

For advanced correction (custom rules + phonetics + hybrid score) → generates output.txt.

Step 5: Download Corrected File
from google.colab import files
files.download("output.txt")

✅ Example
Dictionary (reference.txt)
coffee
bhajan
aarti
festival
faizabad

Errors (errors.txt)
cofffe
phestival
bhaajan
aartti

Output (output.txt)
File_Error   Corrected
cofffe       coffee
phestival    festival
bhaajan      bhajan
aartti       aarti

🌟 Key Features

✔ Handles typo + phonetic + vowel errors
✔ Works with large text files (10k+ words)
✔ Hybrid approach (Fuzzy + Phonetic) for better accuracy
✔ Easy to run in Google Colab or locally

Accuracy Calculation-
checked the accuracy of the model by comaparing it woth a ground truth file with all the correct words, I got the Accuracy of 97 percent. I am having future plans to increase the accuracy of the model.

📜 Future Improvements

Support for multi-word phrases

Trainable model for context-based corrections

Extend custom rules for more Indian languages

👨‍💻 Author

Prachi Shukla

Interview assignment submission
