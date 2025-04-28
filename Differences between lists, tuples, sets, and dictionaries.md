# Differences between lists, tuples, sets, and dictionaries

## 1. Lists
- **Definition:** A list is an ordered collection of items, which can be of any data type.
- **Syntax:**
```python
my_list = [1, 2, 3, "Python", 4.5]
```
- **Key Characteristics:**
    - **Ordered:** Items in a list maintain the order in which they were inserted.
    - **Mutable:** You can modify the elements (add, remove, change) after the list is created.
    - **Allows Duplicates**: Lists can contain duplicate elements.
    - **Supports Indexing and Slicing:** You can access elements via indices and use slicing to get sublists.
```python
my_list = [1, 2, 3, 3]
my_list[0] = 10  # Modify an element
print(my_list)  # Output: [10, 2, 3, 3]
```

## 2. Tuples
- **Definition:** A tuple is an ordered collection of items, which can also be of any data type.
- **Syntax:**
```python
my_tuple = (1, 2, 3, "Python", 4.5)
```
- **Key Characteristics:**
    - **Ordered:** Like lists, tuples maintain the order of elements.
    - **Imutable:** Once a tuple is created, you cannot modify, add, or remove elements.
    - **Allows Duplicates**: Tuples can contain duplicate elements.
    - **No Indexing:** You cannot access elements by index (sets are unordered).
```python
my_tuple = (1, 2, 3)
# my_tuple[0] = 10  # This would raise an error because tuples are immutable
print(my_tuple)  # Output: (1, 2, 3)
```

## 3. Sets
- **Definition:** A set is an unordered collection of unique items.
- **Syntax:**
```python
my_set = {1, 2, 2, 3}
print(my_set)  # Output: {1, 2, 3}  (duplicates are removed)
my_set.add(4)  # Add an element
print(my_set)  # Output: {1, 2, 3, 4}
```
- **Key Characteristics:**
    - **Unordered:** Sets do not maintain any order of elements. The order of elements can change.
    - **Mutable:** You can add or remove elements, but the elements themselves must be immutable (e.g., numbers, strings, tuples).
    - **No Duplicates:** Sets automatically remove duplicate values.
    - **No Indexing:** You cannot access elements by index (sets are unordered).
```python
my_set = {1, 2, 2, 3}
print(my_set)  # Output: {1, 2, 3}  (duplicates are removed)
my_set.add(4)  # Add an element
print(my_set)  # Output: {1, 2, 3, 4}
```

## 4. Dictionaries
- **Definition:** A dictionary is an unordered collection of key-value pairs, where each key is unique.
- **Syntax:**
```python
my_dict = {"name": "Alice", "age": 25, "city": "New York"}
```
- **Key Characteristics:**
    - **Unordered** (Python 3.6+ maintains insertion order): Items are stored as key-value pairs.
    - **Mutable:** You can modify, add, and remove key-value pairs.
    - **Keys must be unique::** A dictionary cannot have duplicate keys, but values can be duplicated.
    - **Supports Key-based Access:** You access the values by referring to the keys.
```python
my_dict = {"name": "Alice", "age": 25}
my_dict["age"] = 26  # Modify a value
my_dict["city"] = "London"  # Add a new key-value pair
print(my_dict)  # Output: {'name': 'Alice', 'age': 26, 'city': 'London'}
```

# Comparision Summary
Feature    | List | Tuple | Set | Dictionary
|--------- |---|---|---|-----------|
Ordered   | Yes | Yes | No | No (Python 3.6+ maintains order)
Mutable   | Yes | No | Yes | Yes
Allows Duplicates | Yes | Yes | No | Keys: No, Values: Yes
Indexing/Slicing    | Yes | Yes | No | Yes (by key)
Use Case   | When order matters and you need to modify elements | When order matters but you don't need to modify elements | When you need unique values and don’t care about order | When you need key-value pairs with fast lookups
