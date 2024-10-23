# Python Exercises with Solutions

## Easy Exercises (1-35)

1. **Reverse a String**: Write a function to reverse a string.
   - **Reference**: String Manipulation
   ```python
   def reverse_string(s):
       return s[::-1]
   print(reverse_string("hello"))  # Output: "olleh"
   ```

2. **Sum of List**: Write a function to find the sum of all elements in a list.
   - **Reference**: Lists
   ```python
   def sum_list(lst):
       return sum(lst)
   print(sum_list([1, 2, 3, 4]))  # Output: 10
   ```

3. **Count Characters in a String**: Write a function that counts the number of each character in a string.
   - **Reference**: String Manipulation, Dictionaries
   ```python
   def count_characters(s):
       counts = {}
       for char in s:
           counts[char] = counts.get(char, 0) + 1
       return counts
   print(count_characters("hello"))  # Output: {'h': 1, 'e': 1, 'l': 2, 'o': 1}
   ```

4. **Fahrenheit to Celsius**: Convert a temperature from Fahrenheit to Celsius.
   - **Reference**: Variables and Data Types
   ```python
   def fahrenheit_to_celsius(f):
       return (f - 32) * 5/9
   print(fahrenheit_to_celsius(98))  # Output: 36.6667
   ```

5. **Check Even or Odd**: Write a function to check if a number is even or odd.
   - **Reference**: Variables and Data Types, Functions
   ```python
   def check_even_odd(num):
       return "Even" if num % 2 == 0 else "Odd"
   print(check_even_odd(5))  # Output: Odd
   ```

6. **Find Maximum in a List**: Write a function to find the maximum number in a list.
   - **Reference**: Lists
   ```python
   def find_max(lst):
       return max(lst)
   print(find_max([1, 2, 3, 9, 5]))  # Output: 9
   ```

7. **Check Palindrome**: Write a function that checks if a given string is a palindrome.
   - **Reference**: String Manipulation
   ```python
   def is_palindrome(s):
       return s == s[::-1]
   print(is_palindrome("madam"))  # Output: True
   ```

8. **Multiply All Elements**: Write a function that multiplies all the elements in a list.
   - **Reference**: Lists, Functions
   ```python
   def multiply_list(lst):
       result = 1
       for num in lst:
           result *= num
       return result
   print(multiply_list([1, 2, 3]))  # Output: 6
   ```

9. **Find Common Elements in Two Lists**: Write a function that finds common elements between two lists.
   - **Reference**: Lists, Sets
   ```python
   def find_common(lst1, lst2):
       return list(set(lst1).intersection(lst2))
   print(find_common([1, 2, 3], [3, 4, 5]))  # Output: [3]
   ```

10. **Swap Two Variables**: Write a function to swap two variables without using a third variable.
    - **Reference**: Variables and Data Types
    ```python
    def swap(a, b):
        a, b = b, a
        return a, b
    print(swap(1, 2))  # Output: (2, 1)
    ```

11. **Remove Duplicates from List**: Write a function that removes duplicates from a list.
    - **Reference**: Lists, Sets
    ```python
    def remove_duplicates(lst):
        return list(set(lst))
    print(remove_duplicates([1, 2, 2, 3, 4, 4]))  # Output: [1, 2, 3, 4]
    ```

12. **Find the Length of a String**: Write a function to find the length of a string.
    - **Reference**: String Manipulation
    ```python
    def length_of_string(s):
        return len(s)
    print(length_of_string("hello"))  # Output: 5
    ```

13. **Sum of Digits**: Write a function that takes an integer and returns the sum of its digits.
    - **Reference**: Variables and Data Types, Functions
    ```python
    def sum_of_digits(n):
        return sum(int(digit) for digit in str(n))
    print(sum_of_digits(1234))  # Output: 10
    ```

14. **Print Fibonacci Sequence**: Write a function that prints the first `n` Fibonacci numbers.
    - **Reference**: Functions, Variables and Data Types
    ```python
    def fibonacci(n):
        fib_seq = [0, 1]
        while len(fib_seq) < n:
            fib_seq.append(fib_seq[-1] + fib_seq[-2])
        return fib_seq[:n]
    print(fibonacci(5))  # Output: [0, 1, 1, 2, 3]
    ```

15. **Convert String to Uppercase**: Write a function that converts a string to uppercase.
    - **Reference**: String Manipulation
    ```python
    def to_uppercase(s):
        return s.upper()
    print(to_uppercase("hello"))  # Output: "HELLO"
    ```

16. **Check Prime**: Write a function to check if a number is prime.
    - **Reference**: Functions, Variables and Data Types
    ```python
    def is_prime(n):
        if n <= 1:
            return False
        for i in range(2, int(n**0.5) + 1):
            if n % i == 0:
                return False
        return True
    print(is_prime(7))  # Output: True
    ```

17. **List of Squares**: Write a function that returns a list of squares of numbers from 1 to `n`.
    - **Reference**: Functions, Lists
    ```python
    def list_of_squares(n):
        return [x**2 for x in range(1, n + 1)]
    print(list_of_squares(5))  # Output: [1, 4, 9, 16, 25]
    ```

18. **Merge Two Dictionaries**: Write a function to merge two dictionaries.
    - **Reference**: Dictionaries
    ```python
    def merge_dicts(dict1, dict2):
        merged = dict1.copy()
        merged.update(dict2)
        return merged
    print(merge_dicts({'a': 1}, {'b': 2}))  # Output: {'a': 1, 'b': 2}
    ```

19. **Find Intersection of Two Sets**: Write a function to find the intersection of two sets.
    - **Reference**: Sets
    ```python
    def find_intersection(set1, set2):
        return set1.intersection(set2)
    print(find_intersection({1, 2, 3}, {3, 4, 5}))  # Output: {3}
    ```

20. **Check Vowel or Consonant**: Write a function that checks if a given character is a vowel or consonant.
    - **Reference**: String Manipulation, Functions
    ```python
    def check_vowel_consonant(char):
        vowels = 'aeiouAEIOU'
        if char in vowels:
            return "Vowel"
        return "Consonant"
    print(check_vowel_consonant("a"))  # Output: Vowel
    ```

21. **Find Factorial**: Write a recursive function to find the factorial of a number.
    - **Reference**: Recursion, Functions
    ```python
    def factorial(n):
        if n == 1:
            return 1
        return n * factorial(n - 1)
    print(factorial(5))  # Output: 120
    ```

22. **Replace Spaces with Underscores**: Write a function that replaces all spaces in a string with underscores.
    - **Reference**: String Manipulation
    ```python
    def replace_spaces(s):
        return s.replace(' ', '_')
    print(replace_spaces("hello world"))  # Output: "hello_world"
    ```

23. **Sort List in Ascending Order**: Write a function to sort a list in ascending order.
    - **Reference**: Lists
    ```python
    def sort_list(lst):
        return sorted(lst)
    print(sort_list([3, 1, 4, 2]))  # Output: [1, 2, 3, 4]
    ```

24. **Sum of Odd Numbers**: Write a function to find the sum of all odd numbers in a list.
    - **Reference**: Functions, Lists
    ```python
    def sum_of_odd(lst):
        return sum(num for num in lst if num % 2 != 0)
    print(sum_of_odd([1, 2, 3, 4, 5]))  # Output: 9
    ```

25. **Reverse a List**: Write a function that reverses a list.
    - **Reference**: Lists
    ```python
    def reverse_list(lst):
        return lst[::-1]
    print(reverse_list([1, 2, 3, 4]))  # Output: [4, 3, 2, 1]
    ```

26. **Count Words in a String**: Write a function to count the number of words in a string.
    - **Reference**: String Manipulation
    ```python
    def count_words(s):
        return len(s.split())
    print(count_words("hello world"))  # Output: 2
    ```

27. **Check Substring**: Write a function to check if a string is a substring of another string.
    - **Reference**: String Manipulation
    ```python
    def is_substring(sub, string):
        return sub in string
    print(is_substring("hello", "hello world"))  # Output: True
    ```

28. **Find Minimum in a List**: Write a function to find the minimum number in a list.
    - **Reference**: Lists
    ```python
    def find_min(lst):
        return min(lst)
    print(find_min([3, 1, 4, 2]))  # Output: 1
    ```

29. **Print Multiplication Table**: Write a function to print the multiplication table of a number.
    - **Reference**: Functions
    ```python
    def multiplication_table(n):
        return [n * i for i in range(1, 11)]
    print(multiplication_table(5))  # Output: [5, 10, 15, 20, 25, 30, 35, 40, 45, 50]
    ```

30. **Remove Vowels from a String**: Write a function to remove all vowels from a string.
    - **Reference**: String Manipulation
    ```python
    def remove_vowels(s):
        vowels = 'aeiouAEIOU'
        return ''.join([char for char in s if char not in vowels])
    print(remove_vowels("hello"))  # Output: "hll"
    ```

31. **Calculate Average of List**: Write a function that calculates the average of all elements in a list.
    - **Reference**: Lists
    ```python
    def calculate_average(lst):
        return sum(lst) / len(lst)
    print(calculate_average([1, 2, 3, 4]))  # Output: 2.5
    ```

32. **List of Even Numbers**: Write a function that returns a list of even numbers from 1 to `n`.
    - **Reference**: Lists, Functions
    ```python
    def even_numbers(n):
        return [x for x in range(1, n + 1) if x % 2 == 0]
    print(even_numbers(10))  # Output: [2, 4, 6, 8, 10]
    ```

33. **Reverse a Sentence**: Write a function that reverses the words in a sentence.
    - **Reference**: String Manipulation
    ```python
    def reverse_sentence(sentence):
        return ' '.join(sentence.split()[::-1])
    print(reverse_sentence("hello world"))  # Output: "world hello"
    ```

34. **Find Length of List**: Write a function to find the length of a list.
    - **Reference**: Lists
    ```python
    def length_of_list(lst):
        return len(lst)
    print(length_of_list([1, 2, 3, 4]))  # Output: 4
    ```

35. **Convert List of Strings to Integers**: Write a function that converts a list of strings into integers.
    - **Reference**: Lists, Variables and Data Types
    ```python
    def convert_to_int(lst):
        return [int(x) for x in lst]
    print(convert_to_int(["1", "2", "3"]))  # Output: [1, 2, 3]
    ```

## Medium Exercises (36-70)

36. **Find Missing Number**: Write a function to find the missing number from a list of consecutive numbers.
    - **Reference**: Lists, Functions
    ```python
    def find_missing(lst):
        return set(range(min(lst), max(lst) + 1)) - set(lst)
    print(find_missing([1, 2, 4, 5]))  # Output: {3}
    ```

37. **Remove Duplicate Words**: Write a function to remove duplicate words from a string.
    - **Reference**: String Manipulation, Lists, Sets
    ```python
    def remove_duplicate_words(s):
        words = s.split()
        return ' '.join(sorted(set(words), key=words.index))
    print(remove_duplicate_words("hello world hello"))  # Output: "hello world"
    ```

38. **Check Anagram**: Write a function to check if two strings are anagrams.
    - **Reference**: String Manipulation, Dictionaries
    ```python
    def is_anagram(str1, str2):
        return sorted(str1) == sorted(str2)
    print(is_anagram("listen", "silent"))  # Output: True
    ```

39. **Flatten Nested List**: Write a function that flattens a nested list (a list within a list).
    - **Reference**: Lists
    ```python
    def flatten_list(lst):
        flat_list = []
        for item in lst:
            if isinstance(item, list):
                flat_list.extend(flatten_list(item))
            else:
                flat_list.append(item)
        return flat_list
    print(flatten_list([1, [2, [3, 4], 5], 6]))  # Output: [1, 2, 3, 4, 5, 6]
    ```

40. **Convert List to Dictionary**: Write a function that converts two lists into a dictionary (one for keys and one for values).
    - **Reference**: Lists, Dictionaries
    ```python
    def lists_to_dict(keys, values):
        return dict(zip(keys, values))
    print(lists_to_dict(['a', 'b', 'c'], [1, 2, 3]))  # Output: {'a': 1, 'b': 2, 'c': 3}
    ```

41. **Generate a Random Password**: Write a function to generate a random password of given length.
    - **Reference**: String Manipulation
    ```python
    import random
    import string

    def generate_password(length):
        characters = string.ascii_letters + string.digits + string.punctuation
        return ''.join(random.choice(characters) for i in range(length))

    print(generate_password(8))  # Example Output: "aB2!eF1*"
    ```

42. **Count Uppercase and Lowercase Letters**: Write a function to count the number of uppercase and lowercase letters in a string.
    - **Reference**: String Manipulation
    ```python
    def count_case(s):
        upper = sum(1 for char in s if char.isupper())
        lower = sum(1 for char in s if char.islower())
        return upper, lower
    print(count_case("Hello World"))  # Output: (2, 8)
    ```

43. **Calculate Exponent without Built-in Function**: Write a function that calculates the exponent of a number without using Python’s built-in `**` operator.
    - **Reference**: Functions, Variables and Data Types
    ```python
    def exponent(base, exp):
        result = 1
        for _ in range(exp):
            result *= base
        return result
    print(exponent(2, 3))  # Output: 8
    ```

44. **Find First Non-Repeating Character**: Write a function that finds the first non-repeating character in a string.
    - **Reference**: String Manipulation, Dictionaries
    ```python
    def first_non_repeating(s):
        char_count = {}
        for char in s:
            char_count[char] = char_count.get(char, 0) + 1
        for char in s:
            if char_count[char] == 1:
                return char
        return None
    print(first_non_repeating("swiss"))  # Output: "w"
    ```

45. **Longest Word in a Sentence**: Write a function that finds the longest word in a sentence.
    - **Reference**: String Manipulation
    ```python
    def longest_word(s):
        words = s.split()
        return max(words, key=len)
    print(longest_word("The quick brown fox"))  # Output: "quick"
    ```

46. **Group Elements in a List**: Write a function to group elements of a list into sublists based on a condition.
    - **Reference**: Lists, Functions
    ```python
    def group_elements(lst):
        return [lst[i:i+2] for i in range(0, len(lst), 2)]
    print(group_elements([1, 2, 3, 4, 5, 6]))  # Output: [[1, 2], [3, 4], [5, 6]]
    ```

47. **Count Occurrences of a Word in a String**: Write a function that counts the number of occurrences of a word in a string.
    - **Reference**: String Manipulation, Dictionaries
    ```python
    def count_word_occurrences(s, word):
        return s.lower().split().count(word.lower())
    print(count_word_occurrences("hello world hello", "hello"))  # Output: 2
    ```

48. **Find the Second Largest Number in a List**: Write a function that finds the second largest number in a list.
    - **Reference**: Lists
    ```python
    def second_largest(lst):
        unique_sorted = sorted(set(lst))
        return unique_sorted[-2] if len(unique_sorted) > 1 else None
    print(second_largest([1, 2, 3, 4, 5]))  # Output: 4
    ```

49. **Calculate GCD of Two Numbers**: Write a function to calculate the greatest common divisor (GCD) of two numbers.
    - **Reference**: Functions, Variables and Data Types
    ```python
    def gcd(a, b):
        while b:
            a, b = b, a % b
        return a
    print(gcd(48, 18))  # Output: 6
    ```

50. **Find Common Characters in Two Strings**: Write a function to find the common characters between two strings.
    - **Reference**: String Manipulation, Sets
    ```python
    def common_characters(str1, str2):
        return ''.join(sorted(set(str1).intersection(set(str2))))
    print(common_characters("hello", "world"))  # Output: "lo"
    ```

51. **Check if String is a Pangram**: Write a function that checks if a string contains every letter of the alphabet at least once.
    - **Reference**: String Manipulation, Sets
    ```python
    def is_pangram(s):
        alphabet = set("abcdefghijklmnopqrstuvwxyz")
        return alphabet.issubset(set(s.lower()))
    print(is_pangram("The quick brown fox jumps over the lazy dog"))  # Output: True
    ```

52. **Find All Permutations of a String**: Write a function to find all permutations of a given string.
    - **Reference**: String Manipulation
    ```python
    from itertools import permutations

    def find_permutations(s):
        return [''.join(p) for p in permutations(s)]
    print(find_permutations("abc"))  # Output: ['abc', 'acb', 'bac', 'bca', 'cab', 'cba']
    ```

53. **Sum of Digits in a List**: Write a function that finds the sum of digits in all numbers in a list.
    - **Reference**: Data Structures (Lists), Python Functions
    ```python
    def sum_of_digits_in_list(lst):
        return sum(sum(int(digit) for digit in str(num)) for num in lst)
    print(sum_of_digits_in_list([123, 456]))  # Output: 21
    ```

54. **Intersection of Multiple Sets**: Write a function that finds the intersection of multiple sets.
    - **Reference**: Data Structures (Sets)
    ```python
    def intersect_multiple_sets(*sets):
        return set.intersection(*sets)
    print(intersect_multiple_sets({1, 2}, {2, 3}, {2, 4}))  # Output: {2}
    ```

55. **Find Index of Element in List**: Write a function to find the index of an element in a list.
    - **Reference**: Data Structures (Lists)
    ```python
    def find_index(lst, element):
        return lst.index(element) if element in lst else None
    print(find_index([1, 2, 3], 2))  # Output: 1
    ```

56. **Flatten Dictionary**: Write a function to flatten a dictionary with nested dictionaries.
    - **Reference**: Data Structures (Dictionaries)
    ```python
    def flatten_dict(d, parent_key='', sep='_'):
        items = []
        for k, v in d.items():
            new_key = parent_key + sep + k if parent_key else k
            if isinstance(v, dict):
                items.extend(flatten_dict(v, new_key, sep=sep).items())
            else:
                items.append((new_key, v))
        return dict(items)
    nested_dict = {'a': 1, 'b': {'c': 2, 'd': {'e': 3}}}
    print(flatten_dict(nested_dict))  # Output: {'a': 1, 'b_c': 2, 'b_d_e': 3}
    ```

57. **Create Acronym**: Write a function that creates an acronym for a given string (e.g., "National Aeronautics and Space Administration" -> "NASA").
    - **Reference**: String Manipulation
    ```python
    def create_acronym(phrase):
        return ''.join([word[0].upper() for word in phrase.split()])
    print(create_acronym("National Aeronautics and Space Administration"))  # Output: "NASA"
    ```

58. **Check if Two Sets are Disjoint**: Write a function to check if two sets are disjoint.
    - **Reference**: Data Structures (Sets)
    ```python
    def are_disjoint(set1, set2):
        return set1.isdisjoint(set2)
    print(are_disjoint({1, 2}, {3, 4}))  # Output: True
    ```

59. **Remove All Occurrences of a Value from List**: Write a function to remove all occurrences of a given value from a list.
    - **Reference**: Data Structures (Lists)
    ```python
    def remove_all_occurrences(lst, value):
        return [x for x in lst if x != value]
    print(remove_all_occurrences([1, 2, 2, 3], 2))  # Output: [1, 3]
    ```

60. **Reverse a Dictionary**: Write a function that reverses the keys and values in a dictionary.
    - **Reference**: Data Structures (Dictionaries)
    ```python
    def reverse_dict(d):
        return {v: k for k, v in d.items()}
    print(reverse_dict({'a': 1, 'b': 2}))  # Output: {1: 'a', 2: 'b'}
    ```


