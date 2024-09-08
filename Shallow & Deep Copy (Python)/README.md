## _Shallow Copy_ & _Deep Copy_  ==>  in **Python** 🐍
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
