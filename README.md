# QA System

## Overview
This project implements a Question-Answering (QA) system using the BERT model fine-tuned on the SQuAD dataset. The system extracts answers to user questions based on provided text passages.

## Features
- Loads the CoQA dataset and preprocesses it into a structured CSV format.
- Uses `BertForQuestionAnswering` and `BertTokenizer` from the `transformers` library.
- Encodes the question-text pair and processes it with BERT to extract answers.
- Displays confidence scores of answer predictions using visualizations.
- Allows user interaction to input custom text and questions.
- Provides an interactive loop to answer multiple questions based on the same text.

## Dependencies
- Python 3.7+
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Transformers (Hugging Face library)
- Torch

## Installation
1. Install required dependencies using pip:
   ```bash
   pip install pandas numpy matplotlib seaborn transformers torch
   ```
2. If using Google Colab, ensure to install `transformers` inside the notebook:
   ```python
   !pip install transformers
   ```

## Dataset
The system loads the CoQA dataset from Stanford:
- The dataset is retrieved using:
  ```python
  coqa = pd.read_json('http://downloads.cs.stanford.edu/nlp/data/coqa/coqa-train-v1.0.json')
  ```
- It is processed into a structured format and saved as `CoQA_data.csv`.

## Model
- Uses `bert-large-uncased-whole-word-masking-finetuned-squad`.
- Tokenizes input text and questions using `BertTokenizer`.
- Computes start and end token probabilities for answer extraction.

## Usage
1. Run the script.
2. Enter a text passage when prompted.
3. Enter a question related to the passage.
4. The system outputs an extracted answer.
5. Users can continue asking more questions based on the same text.
6. Type `N` when prompted to exit.

## Example Interaction
```
Please enter your text:
New York (CNN) -- More than 80 Michael Jackson collectibles...

Please enter your question:
Where was the auction held?

Answer:
Hard Rock Cafe in New York's Times Square.

Do you want to ask another question based on this text (Y/N)? Y

Please enter your question:
What was the highest auction price?

Answer:
$420,000.

Do you want to ask another question based on this text (Y/N)? N

Bye!
```

## Visualization
- Displays token importance using bar charts.
- Uses `seaborn` to visualize start and end word scores.

## Notes
- The system works best with well-structured text inputs.
- If no valid answer is found, it outputs: `Unable to find the answer to your question.`
- Requires an active internet connection to download the BERT model and dataset.

## License
This project is for educational and research purposes only.

## Acknowledgments
- Stanford CoQA Dataset
- Hugging Face Transformers
- BERT by Google AI

