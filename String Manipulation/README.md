# Python String Manipulation Cheat Sheet

## 1. Creating Strings

Strings can be created by enclosing characters inside quotes (single, double, or triple quotes).
```python
s1 = 'hello'          # Single quotes
s2 = "hello"          # Double quotes
s3 = '''hello'''      # Triple quotes for multiline strings
s4 = """hello"""      # Triple double quotes for multiline strings
```

---

## 2. Accessing String Elements

Strings are indexed starting from 0. Negative indexing starts from the end of the string.
```python
s = "Python"
print(s[0])     # Output: 'P'
print(s[-1])    # Output: 'n'
```

---

## 3. Slicing Strings

Slicing allows you to get a substring using the start, stop, and step arguments.
```python
s = "Python"
print(s[0:4])    # Output: 'Pyth' (start: 0, end: 4 - 1)
print(s[:3])     # Output: 'Pyt' (equivalent to s[0:3])
print(s[2:])     # Output: 'thon' (from index 2 to end)
print(s[::2])    # Output: 'Pto' (every 2nd character)
```

---

## 4. Common String Methods

### `len()`
Returns the length of the string.
```python
s = "Python"
print(len(s))   # Output: 6
```

### `upper()`, `lower()`
Convert string to uppercase or lowercase.
```python
s = "Python"
print(s.upper())  # Output: 'PYTHON'
print(s.lower())  # Output: 'python'
```

### `capitalize()`, `title()`
Capitalize the first letter or title-case all words.
```python
s = "python programming"
print(s.capitalize())  # Output: 'Python programming'
print(s.title())       # Output: 'Python Programming'
```

### `strip()`, `lstrip()`, `rstrip()`
Remove leading or trailing whitespace or characters.
```python
s = "   Hello   "
print(s.strip())   # Output: 'Hello'
print(s.lstrip())  # Output: 'Hello   '
print(s.rstrip())  # Output: '   Hello'
```

### `replace()`
Replaces all occurrences of a substring with another.
```python
s = "I like Python"
print(s.replace("like", "love"))  # Output: 'I love Python'
```

### `split()`, `join()`
Splits a string into a list of substrings and joins a list into a string.
```python
s = "Python is fun"
words = s.split()            # Output: ['Python', 'is', 'fun']
new_s = " ".join(words)      # Output: 'Python is fun'
```

### `find()`, `rfind()`, `index()`, `rindex()`
Finds the first or last occurrence of a substring.
```python
s = "Python programming"
print(s.find("o"))       # Output: 4 (index of first 'o')
print(s.rfind("o"))      # Output: 9 (index of last 'o')
print(s.index("programming"))  # Output: 7
```

### `startswith()`, `endswith()`
Check if the string starts or ends with a substring.
```python
s = "Python programming"
print(s.startswith("Py"))    # Output: True
print(s.endswith("ing"))     # Output: True
```

---

## 5. String Formatting

### f-strings (formatted string literals)
Insert values into strings using `f` before the string.
```python
name = "Alice"
age = 25
print(f"My name is {name} and I am {age} years old.")  # Output: 'My name is Alice and I am 25 years old.'
```

### `format()`
Older style of formatting using placeholders.
```python
print("My name is {} and I am {} years old.".format("Alice", 25))  # Output: 'My name is Alice and I am 25 years old.'
```

### `%` formatting
C-style formatting.
```python
name = "Alice"
age = 25
print("My name is %s and I am %d years old." % (name, age))  # Output: 'My name is Alice and I am 25 years old.'
```

---

## 6. String Concatenation

Strings can be concatenated using the `+` operator or `join()`.
```python
s1 = "Hello"
s2 = "World"
s = s1 + " " + s2     # Output: 'Hello World'

# Efficient way to concatenate strings
s = " ".join([s1, s2])  # Output: 'Hello World'
```

---

## 7. Checking Substrings

You can check if a substring is present in a string using `in` and `not in`.
```python
s = "Python programming"
print("Python" in s)     # Output: True
print("Java" not in s)   # Output: True
```

---

## 8. Escaping Characters

You can escape special characters using backslashes.
```python
s = 'It\'s a great day!'  # Output: "It's a great day!"
s = "She said, \"Hello!\""  # Output: 'She said, "Hello!"'
```

---

## 9. Raw Strings

Raw strings treat backslashes as literal characters.
```python
s = r"C:\Users\Alice"  # Output: 'C:\\Users\\Alice'
```

---

## 10. String Methods for Checking

### `isalnum()`, `isalpha()`, `isdigit()`, `islower()`, `isupper()`
Checks whether the string consists of alphanumeric characters, alphabets, digits, lowercase, or uppercase.
```python
s = "Hello123"
print(s.isalnum())    # Output: True (contains only letters and numbers)
print(s.isalpha())    # Output: False (contains digits)
print(s.isdigit())    # Output: False (contains letters)
print(s.islower())    # Output: False (not all lowercase)
```

### `isspace()`
Check if the string contains only whitespace characters.
```python
s = "   "
print(s.isspace())  # Output: True
```

---

## 11. String Encoding and Decoding

Convert a string to bytes and back.
```python
s = "Hello"
encoded_s = s.encode()      # Output: b'Hello' (encoded to bytes)
decoded_s = encoded_s.decode()  # Output: 'Hello' (decoded back to string)
```

---

## 12. String Immutability

Strings are immutable, which means they cannot be modified after creation. You must create a new string.
```python
s = "Hello"
s = s + " World"  # Creates a new string 'Hello World'
```

---

## 13. String Reversing

Reversing a string can be done using slicing.
```python
s = "Python"
reversed_s = s[::-1]  # Output: 'nohtyP'
```

---

## 14. Multiline Strings

Use triple quotes for multiline strings.
```python
s = """This is a 
multiline
string."""
```

---

## 15. String Constants from the `string` Module

Python’s `string` module has useful constants.
```python
import string

print(string.ascii_letters)  # 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
print(string.ascii_lowercase)  # 'abcdefghijklmnopqrstuvwxyz'
print(string.ascii_uppercase)  # 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
print(string.digits)  # '0123456789'
print(string.punctuation)  # '!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~'
```

---

## 16. Exercises

### Easy
1. Create a string "Hello World" and print the string.
2. Write a program that converts a string to uppercase.
3. Write a program that replaces all spaces in a string with underscores.
4. Extract the first 5 characters from the string "Programming".
5. Reverse the string "Python".

### Medium
1. Count the occurrences of a specific character in a string.
2. Write a program to remove all vowels from a given string.
3. Given a string "12345", convert it into an integer and add 5.
4. Check if a string is a palindrome.
5. Write a program that checks if a string contains only alphabets.

### Hard
1. Implement a function that counts the frequency of each word in a string.
2. Write a program that extracts all the digits from a string.
3. Implement a function that checks if two strings are anagrams.
4. Write a program that capitalizes every other letter in a string.
5. Implement a Caesar cipher to encrypt and decrypt a string.

