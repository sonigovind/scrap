# scrap
# Marathi Sentence Splitter and Categorizer

## Overview

This project contains scripts to process a Marathi text file by splitting it into sentences, removing duplicates, and categorizing sentences based on their word count. The sentences are then saved into separate files based on their word count categories.

## Requirements

- Python 3.x

## How to Use

### Step 1: Split and Save Unique Sentences

1. **Update the Input and Output File Paths**:
    - Update `input_file_path` and `output_file_path` variables in the first script to match your file locations.
    
    ```python
    input_file_path = 'C:\\Users\\HP\\OneDrive\\Desktop\\scrapping\\sci&t2.txt'
    output_file_path = 'C:\\Users\\HP\\OneDrive\\Desktop\\scrapping\\sentence wise\\sc&t2.txt'
    ```

2. **Run the First Script**:
    - Execute the following script to split the input text into unique sentences and save them to the specified output file.
    
    ```python
    import re

    # Function to read the content of a text file
    def read_text_file(file_path):
        with open(file_path, 'r', encoding='utf-8') as file:
            return file.read()

    # Function to write sentences to a new text file
    def write_sentences_to_file(sentences, output_file_path):
        with open(output_file_path, 'w', encoding='utf-8') as file:
            for sentence in sentences:
                if sentence:  # Ensure the sentence is not empty
                    if not sentence.endswith('.'):
                        sentence += '|'
                    file.write(sentence.strip() + '\n')  # Write the sentence ending with a dot

    # Function to split text into sentences using a dot as the delimiter
    def split_into_sentences(text):
        # Split by dot (.) and filter out any empty sentences
        sentences = re.split(r'[.]', text)
        return [sentence.strip() for sentence in sentences if sentence.strip()]

    # Function to remove duplicate sentences
    def remove_duplicates(sentences):
        seen = set()
        unique_sentences = []
        for sentence in sentences:
            if sentence not in seen:
                unique_sentences.append(sentence)
                seen.add(sentence)
        return unique_sentences

    # File paths
    input_file_path = 'C:\\Users\\HP\\OneDrive\\Desktop\\scrapping\\sci&t2.txt'  # Replace with your input file path
    output_file_path = 'C:\\Users\\HP\\OneDrive\\Desktop\\scrapping\\sentence wise\\sc&t2.txt'

    # Read the text from the file
    text = read_text_file(input_file_path)

    # Split the text into sentences
    sentences = split_into_sentences(text)

    # Remove duplicate sentences
    unique_sentences = remove_duplicates(sentences)

    # Write the unique sentences to the output file
    write_sentences_to_file(unique_sentences, output_file_path)

    print(f"Split {len(unique_sentences)} unique sentences from the text and saved to {output_file_path}")
    ```

### Step 2: Categorize Sentences by Word Count

1. **Update the Input and Output Directory Paths**:
    - Update `input_file_path` and `output_dir` variables in the second script to match your file locations.

    ```python
    import os

    input_file_path = 'C:\\Users\\HP\\OneDrive\\Desktop\\scrapping\\sentence wise\\sc&t2.txt'

    # Create the output directory
    output_dir = "C:\\Users\\HP\\OneDrive\\Desktop\\scrapping\\sentence wise\\sc&t2"
    os.makedirs(output_dir, exist_ok=True)
    ```

2. **Run the Second Script**:
    - Execute the following script to categorize sentences based on their word count and save them into separate files.

    ```python
    import os

    input_file_path = 'C:\\Users\\HP\\OneDrive\\Desktop\\scrapping\\sentence wise\\sc&t2.txt'

   
