## _Shallow Copy_ & _Deep Copy_  ==>  in **Python** 🐍
Understanding the difference between Shallow copy and Deep Copy is crucial for _managing memory_, _optimizing performance_, _and ensuring data integrity_ in Python languange.

Let's dive deeper into the technical aspects of shallow copy and deep copy in Python, focusing on **memory management**, **object mutability**, and _how Python handles these operations at a lower level_.

<br> 

### **Shallow Copy -->** 
A shallow copy creates a new object, but it does not create copies of objects that the original object references. Instead, it copies references to those objects. This means that a shallow copy will create a new compound object and then (to the extent possible) insert references into it to the objects found in the original. Thus, the new object contains the same references to the child objects as the original object.

- Faster because it _only copies references._ Suitable when you want a new top-level container but are okay with sharing nested objects between the copy and the original.
- More memory-efficient for copying large objects where duplicating the full content is unnecessary. However, this efficiency comes with the risk of unintended side effects.
- copy.copy(): The copy() function from the copy module performs a shallow copy. It creates a new object and then populates it with references to the objects found in the original.
- _Reference Copying:_ Copies the references (memory addresses) to the objects. No new objects are created for nested elements, only new references.
- Memory Management: A shallow copy allocates memory for the new object only for the top-level container. All the nested objects are not copied; instead, references (memory addresses) to these objects are copied. This is a lightweight operation because it avoids duplicating large data structures in memory, only copying pointers to the objects themselves.
- Object Mutability: If the object you are copying contains mutable objects (like lists or dictionaries), modifications to these mutable objects in the original or copied object will affect both objects. This happens because the shallow copy shares references to the same mutable objects. Immutable objects (like integers, strings, and tuples) are safe from unintended side effects because they cannot be changed after they are created.

<br>

### **Deep Copy -->**
A deep copy creates a new object and recursively copies all objects found within the original object. This means it duplicates everything: the outer object and all objects it references, directly or indirectly. Therefore, deep copying ensures that the new object is entirely independent of the original, including all nested objects.

- Slower, especially for complex or deeply nested objects, due to the need to traverse and copy every object in the hierarchy. 
- Deep copies are necessary when you need a complete duplicate of an object and its entire structure, ensuring no changes affect the original copy.
- Uses more memory, as it creates a full, independent copy of the original object and all nested objects. It eliminates any risk of unintended side effects due to shared references.
- copy.deepcopy(): The deepcopy() function recursively constructs new compound objects, copying each element of the original object. It ensures that even if nested objects are mutable, changes do not affect the original objects.
- _Object Duplication:_ Duplicates everything recursively. New objects are created for the original object and all nested elements.
- Memory Management: A deep copy requires more memory because it recursively copies every object and its sub-objects. This can significantly increase memory usage, especially for large or complex objects with many nested layers. The memory allocation for each nested object ensures that each object is a standalone entity with no shared references to the original objects.
- Object Mutability: In a deep copy, all objects are recursively copied, including mutable objects. This means modifications to any object (top-level or nested) in the original or copied object do not affect the other. This independence is particularly important when working with complex data structures where changes should not propagate back to the original.

<br>

### Key Differences::

##### _Copy Depth:_

Shallow Copy: Copies only the outermost object and references to nested objects.

Deep Copy: Copies the outer object and all nested objects recursively, creating fully independent copies.

##### _Shared References:_

Shallow Copy: The original and copied objects share references to nested objects, so changes to nested objects in one will reflect in the other.

Deep Copy: The original and copied objects have completely independent copies of all nested objects, so changes to one do not affect the other.

##### _Use Cases:_

Shallow Copy: Useful when you need a copy of an object but do not want to duplicate the entire structure, especially if the nested objects do not change or are large and duplicating them would be resource-intensive.

Deep Copy: Useful when you need a complete, independent copy of an object, including all its nested objects, to ensure modifications to one do not affect the other.

##### _Summary_:

- Use shallow copy when you need a quick copy of an object, but you are okay with shared references to nested objects.

- Use deep copy when you need a complete, independent duplicate of an object, including all nested objects.

<br>

*Let me elaborate the above two concepts using various code snippets* --> 💻
<!--- we can use "single *    &     _ underscore" to write something in MarkDown syntax --->
<!--- we can use html like syntax to write something as a COMMENT in markdown language, the read.md file will not parse that specific portion written inside these notation --->
<!--- we can use ":emoji_name:" syntax to include emojis in MarkDown language/files  / READ.me files"  --->


```python
lst1 = [1,2,3,4]
lst2 = lst1
print(lst1)
print(lst2)

lst1[1]

lst1[1]=1000
print(lst1)
print(lst2)

print("")

# Copy Operation ".copy()"
# Kind of SHALLOW COPY
lst1 = [1,2,3,4]
lst2 = lst1.copy()
print(lst1)
print(lst2)


lst1[1]=1000
print(lst1)
print(lst2)
# Now both having diff MEMORY LOCATION

print("")

# Shallow Copy ==> in Nested Lists
lst1= [[1,2,3,4],[5,6,7,8]]
lst2= lst1.copy()
print(lst1)
print(lst2)


lst1[1][0]=1000
print(lst1)
print(lst2)


print("")

# When you try to make a change in the ITEM of a list, it will not reflect in both lists, 
# if you try to make change in the OBJECT of a list, it will get updated
lst1.append([10,11,12,13])
print(lst1)
print(lst2)
```

### The Output would be:

```bash
[1, 2, 3, 4]
[1, 2, 3, 4]
[1, 1000, 3, 4]
[1, 1000, 3, 4]

[1, 2, 3, 4]
[1, 2, 3, 4]
[1, 1000, 3, 4]
[1, 2, 3, 4]

[[1, 2, 3, 4], [5, 6, 7, 8]]
[[1, 2, 3, 4], [5, 6, 7, 8]]
[[1, 2, 3, 4], [1000, 6, 7, 8]]
[[1, 2, 3, 4], [1000, 6, 7, 8]]

[[1, 2, 3, 4], [1000, 6, 7, 8], [10, 11, 12, 13]]
[[1, 2, 3, 4], [1000, 6, 7, 8]]
```

In the example above, both original_list and shallow_copied_list reflect the change because the inner lists are not copied but referenced, meaning they point to the same memory location.
In this example, deep_copied_list remains unchanged after modifying original_list because a deep copy duplicates all objects, including nested ones, _ensuring no shared references between the original and the copy._

<br>

### Lists are Mutable
```python
lst = [1,2,3,4]
newlist= lst


# List are Mutable
print(id(lst))
print(id(newlist))
```

```bash
2300424847488
2300424847488
```
<br>

### Find the memory location of each list using _id()_ method

```python
lst = [1,2,3,4]
newlst = lst
lst.append("Alpha")

print(id(lst))
print(id(newlst))

id(lst) == id(newlst)
```

```bash
2300424941824
2300424941824
True
```
<br>

### Syntax to implement _Deep Copy_ in **Python** using "Import"

```python
import copy
lst = [[1,2,3], [4,5,6]]
newlst = copy.deepcopy(lst)

print (lst)
print(newlst)


print (id(lst))
print (id(newlst))

print("")

print (id(lst[0]))
print (id(newlst[0]))


newlst.append("Deep")
lst[0].append("Copy")

print("")                 #This print("") is used to bring space between output of diff snippets of code

print (lst)
print (newlst)


for i in range(2):
    print(id(lst[i]), id(newlist[i]))



lst.reverse()          # .reverse() method to reverse the items in the list
print(lst)

```

```bash
[[1, 2, 3], [4, 5, 6]]
[[1, 2, 3], [4, 5, 6]]
2300430649728
2300430759040

2300430735168
2300430652928

[[1, 2, 3, 'Copy'], [4, 5, 6]]
[[1, 2, 3], [4, 5, 6], 'Deep']
2300430735168 140732975342376
2300430573824 140732975342408
[[4, 5, 6], [1, 2, 3, 'Copy']]
```
