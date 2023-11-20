---
marp: true
theme: plain-theme
---

# Coding

Learn the fun way

---

# Pahlevi Fikri Auliya

AVP of Engineering at Ruangguru

@\_fikri_auliya

---

# Day to Day Programming

- As a user, I want to login to my account
- As a user, I want to register to the system
- As a user, I want to see my profile
- As a user, I want to see my friends
- As a user, I want to see my friend's profile

---

![Bored](image.png)

---

# You will be bored

---

## Let's make it fun again

![Fun](image-1.png)

---

# Competitive Programming

---

## What is that?

---

Competitive Programming is a **mind sport**, involving participants trying to program according to provided specifications.

---

## FUN!

---

### Sudoku

![Sudoku](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e0/Sudoku_Puzzle_by_L2G-20050714_standardized_layout.svg/1200px-Sudoku_Puzzle_by_L2G-20050714_standardized_layout.svg.png)

---

### Maze

![Maze](https://upload.wikimedia.org/wikipedia/commons/2/2e/Maze_Type_Standard.png)

---

### Chess

![Chess](chess.png)

---

Why do we solve these problems?
Because **it's fun!**

---

So does **Competitive Programming!**

---

![Car](https://open.kattis.com/problems/carvet/file/statement/en/img-0001.png)

![Input](car-input.png)

---

Why do we code these problems?

- Do we get paid?
- Is it going to be used by end users?

---

No, but it's **fun!**

---

# Tips #0: Fun Mindset

---

---

Given this

```python
names = ["John", "Mary", "John", "John", "Sherlock", "Sherlock"]
```

How to remove duplicates?

---

```python
for i in range(len(names)):
    for j in range(i + 1, len(names)):
        if names[i] == names[j]:
            names.pop(j)
```

---

That's `O(n^2)`!

And the code is long!

---

```python
names = set(names)
```

> `set` is a data structure with unique elements

---

If we know `set` data structure,
we can simplify the way we solve

---

Now, how to find the most frequent name?

```python
names = ["John", "Mary", "John", "John", "Sherlock", "Sherlock"]
```

---

Build a frequency table

| Name     | Count |
| -------- | ----- |
| John     | 3     |
| Mary     | 1     |
| Sherlock | 2     |

---

```python
tables = [[]]
for name in names:
    found = False
    for table in tables:
        if table[0] == name:
            table[1] += 1
            found = True
            break
    if not found:
        tables.append([name, 1])
```

---

Such a long code!
And it's `O(n^2)`!

---

```python
freq = {}
for name in names:
    if name in freq:
        freq[name] += 1
    else:
        freq[name] = 1
```

> Hashmap is a data structure that maps a key to a value

---

If we know `hashmap` data structure,
we can simplify the way we solve

---

Let's say we have this huge data

```python
name_and_score = [
    ("John", 90),
    ("Mary", 80),
    ("Sherlock", 100),
    ("Holmes", 100),
    ("Doe", 80),
    ...
]
```

How to get the top 10 highest score?

---

Easy, just sort it

```python
sorted_data = sorted(name_and_score, key=lambda x: x[1], reverse=True)
top_10 = sorted_data[:10]
```

---

But wait, sorting is `O(n log n)`!
We only need top 10!
Why should we sort all of them?

---

```python
import heapq

heap = []
for name, score in name_and_score:
    heapq.heappush(heap, (-score, name))

top_10 = []
for _ in range(10):
    score, name = heapq.heappop(heap)
    top_10.append((name, -score))
```

---

This is `O(n log k)`! `k` here is 10
Faster than `O(n log n)` if `n` is large

---

If we know `heap` data structure...
...ok you get the point

---

# Tips #1: Learn Data Structures

---

---

Remember this earlier code

```python
freq = {}
for name in names:
    if name in freq:
        freq[name] += 1
    else:
        freq[name] = 1
```

This can even be made shorter!

---

Use `defaultdict`...

```python
from collections import defaultdict

freq = defaultdict(int)
for name in names:
    freq[name] += 1
```

---

Or use `Counter`...

```python
from collections import Counter

freq = Counter(names)
```

---

Remember this code?

```python
import heapq

heap = []
for name, score in name_and_score:
    heapq.heappush(heap, (-score, name))

top_10 = []
for _ in range(10):
    score, name = heapq.heappop(heap)
    top_10.append((name, -score))
```

This is also can be made shorter!

---

```python
k = 3
top_k = heapq.nlargest(k, name_and_score, key=lambda x: x[1])
```

---

# Tips #2: Be familiar with standard lib

---

---

But as curious programmers, we are not satisfied with just using existing data structures

We want to know how they work!

---

## Binary Search Tree

- What is that?
- What is its power? What problem it solve?
- Build intuition how it work
- How to build it?
- What is real life application?

---

![BST](https://upload.wikimedia.org/wikipedia/commons/thumb/d/da/Binary_search_tree.svg/1200px-Binary_search_tree.svg.png)

---

### What is that?

- Binary: It's a tree where each node has at most 2 children
- The left child is always smaller than the parent
- The right child is always bigger than the parent

---

### What is its power?

- It can be used to search a value in `O(log n)` time
- Why? Because we can eliminate half of the tree in each step

---

### Build intuition how it work

Can you explain to a 8 year old?
If not, you don't understand it well enough

---

### How to build it?

```python
class Node:
    def __init__(self, value):
        ...

    def insert(self, value):
        ...
```

- Implement it yourself
- Confusion/struggling is part of learning, embrace it!

---

### What are real life applications?

- It can be used to implement a `map` data structure
- We can build simple database index with it
- ...

---

Another example
![Card](https://upload.wikimedia.org/wikipedia/commons/f/f6/Poker_Solitaire.jpg)

---

How do you sort it?

---

![insertion-sort](https://upload.wikimedia.org/wikipedia/commons/9/9c/Insertion-sort-example.gif?20110309111239)

---

That's insertion sort, this should be executable by child

---

<img src="https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif" width=500px/>

---

<img width=500px src="https://upload.wikimedia.org/wikipedia/commons/8/8e/Merge_sort_animation.gif"/>

---

That's merge sort...

If you really understand it,
you have to be able to explain it to a 8 year old

---

### So...

- What is that?
- What is its power? What problem it solve?
- Build intuition how it work
- How to build it?
- What is real life application?

---

### Pen and Paper Execution

**Only if** you can execute the algorithm in paper,
using only hands and pens,
you have understood it

---

# Tips #3: Build intuition

---

---

We can also build intuition by visualizing it

---

https://visualgo.net/

<img src="visualgo.png" width="100%"/>
<img style="padding-top: 20px" src="visualgo-2.png" width="100%"/>

---

<iframe width="800" height="500" src="https://www.youtube.com/embed/kPRA0W1kECg?si=Q1XhdTcC4VRkW5Be" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

---

# Tips #4: Visualize

---

---

You can't be a doctor just by reading a book.
You have to practice!

---

## Structured practice ftw

<img src="mts.png" width="800px">

<small>https://cpbook.net/methodstosolve</small>

---

## ChatGPT as your tutor

You can now ask ChatGPT to give you hint
...or even give answer :P

---

<img src="chatgpt.png" width="100%"/>

---

## Consistency

Try to practice everyday,
...or every 2 days
...or every week

Don't break the strike

---

# Tips #5: Practice

---

---

## What motivate us?

---

## Goal

---

### CP is competitive by nature

<img width="100%" src="leaderboard.png">

https://open.kattis.com/countries/IDN

---

Invite your friend to compete/learn with you
You will grow together :)

---

# Tips #6: Compete!

---

---

# Conclusion

1. Learn Data Structures
2. Be familiar with standard lib
3. Build intuition
4. Visualize
5. Practice
6. Compete!

---

# Thank you

Have fun :)
