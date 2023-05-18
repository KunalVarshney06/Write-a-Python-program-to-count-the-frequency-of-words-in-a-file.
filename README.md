# Write-a-Python-program-to-count-the-frequency-of-words-in-a-file.
import re
from collections import Counter

def count_word_frequency(file_path):
    word_frequency = Counter()
    try:
        with open(file_path, 'r') as file:
            for line in file:
                words = re.findall(r'\b\w+\b', line.lower())
                word_frequency.update(words)
    except FileNotFoundError:
        print("File not found.")
    except IOError:
        print("An error occurred while reading the file.")
    return word_frequency

# Example usage
file_path = 'path/to/your/text/file.txt'  # Replace with the actual file path
frequency_dict = count_word_frequency(file_path)
print("Word frequencies in the file:")
for word, count in frequency_dict.items():
    print(word, ":", count)

