
import time
import os

class TrieNode:
    def __init__(self):
        self.is_end = False
        self.children = {}

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for char in word:
            if char not in node.children:
                node.children[char] = TrieNode()
            node = node.children[char]
        node.is_end = True

    def is_compounded_word(self, word, start, count):
        node = self.root

        for i in range(start, len(word)):
            char = word[i]

            if char not in node.children:
                return False

            node = node.children[char]

            if node.is_end:
                if i == len(word) - 1:
                    return count >= 1  # Check if we have at least one valid compound word

                if self.is_compounded_word(word, i + 1, count + 1):
                    return True

        return False

def find_compounded_words(file_name, trie):
    # Read input file
    words = []

    try:
        with open(file_name, 'r') as file:
            words = file.read().splitlines()
    except FileNotFoundError:
        print(f"Unable to open file {file_name}")
        return

    # Insert words into trie
    for word in words:
        trie.insert(word)

    # Sort words in descending order by length
    words.sort(key=len, reverse=True)

    # Start measuring time
    start_time = time.time()

    longest_compounded_word = ""
    second_longest_compounded_word = ""

    # Iterate through words to find compounded words
    for word in words:
        if trie.is_compounded_word(word, 0, 0):
            if not longest_compounded_word:
                longest_compounded_word = word
            else:
                second_longest_compounded_word = word
                break  # Break once second longest is found

    # Stop measuring time
    stop_time = time.time()
    duration = int((stop_time - start_time) * 1e6)

    # Display results
    print(f"Results for file {file_name}:")
    print(f"Longest Compound Word: {longest_compounded_word}")
    print(f"Second Longest Compound Word: {second_longest_compounded_word}")
    print(f"Time taken to process file {file_name}: {duration} microseconds")
    print()

def main():
    # Create Trie instance
    trie = Trie()

    # Process each input file
    find_compounded_words("Input_01.txt", trie)
    find_compounded_words("Input_02.txt", trie)

if __name__ == "__main__":
    main()
