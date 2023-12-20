Compounded Word Finder
Overview
This program is designed to find the longest and second longest compounded words from a list of alphabetically sorted words stored in files Input_01.txt and Input_02.txt. A compounded word is defined as one that can be constructed by concatenating shorter words from the same file. The solution utilizes a Trie data structure for efficient word insertion and lookup, ensuring optimal performance even for large datasets.

How to Execute
Clone Repository:

bash
Copy code
git clone https://github.com/Navya-Malik/compounded-word-finder.git
cd compounded-word-finder
Run the Program:

Ensure you have a compatible Python version installed (e.g., Python 3.x).
Execute the program by running the following command in the terminal:
Copy code
python compounded_word_finder.py
Results:

The program will display the longest and second longest compounded words, along with the time taken to process each input file.
Design Decisions
Trie Data Structure:

A Trie is used to efficiently store and retrieve words from the input files. This reduces the time complexity of word lookup operations.
Sorting Words:

Words are initially sorted in descending order by length. This ensures that when checking for compounded words, longer words are considered first, optimizing the identification of the longest and second longest compounded words.
File Handling:

The program gracefully handles file-related issues, such as file not found or errors during reading. It provides informative error messages to assist the user.
Performance Optimization:

The program is designed with a focus on performance, especially for large datasets (e.g., 100,000+ items). The Trie structure and sorting contribute to efficient word processing.
