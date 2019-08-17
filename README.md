# python_random


## python sort and comparison
0. https://docs.python.org/2/howto/sorting.html#sortinghowto
1. sort as builtin or sort as list function
2. itemgetter, attrgetter
3. cpm function takes 2 objects as input, return positive if o1>o2, 0 if ==, negative if <. using cpm, you get increasing order. in python 3 cpm was removed, from functools import cmp_to_key is used to transform cmp to key function


```
sorted(iterables, key=some function takes in one element and return one number, reverse=False by default)
lst.sort(key=some function takes in one element and return one number, reverse=False by default)

example:
from operator import itemgetter, attrgetter
from functools import cmp_to_key
class person():
 def __init__(self, name, age):
  self.name = name
  self.age = age
lst = [person('wang', 12), person('li', 34)]
lst = sorted(lst, key=lambda x: x.age)
lst.sorted(key=lambda x: x.age) #inplace
lst.sorted(key=attrgetter('age', 'name'))

lst = [(1,2), (4,5), (7,8)]
lst.sort(key=lambda x: x[1])
lst = sorted(lst, key=lambda x: x[1])
lst = sorted(lst, key=itemgetter(1))

lst = sorted(lst, key=cpm_to_key(some comparison function))

```

## Class builtin function

1. __repr__ vs __str__
- https://blog.csdn.net/luckytanggu/article/details/53649156

- __repr__ define results for both str output and print
- __str__ only for print

## list swap

a[i], a[i+1] = a[i+1], a[i]
https://codeandchaos.wordpress.com/2014/11/15/swap-two-objects-in-python/

## arithmetic
```
5 / 3
1.6666666666666667

5 // 3
1

5 % 3
2
```


## list

1. list pointwise out of index is not okay, but rangewise is okay

```
lst = [1, 2, 3]
lst[0: 2] # okay
lst[0: 100] # okay
lst[100: 2200] # okay
lst[4] # error
```

2. list sort

 - list.sort(key=..., reverse=...) # in place
 - sorted(list, key, reverse) # return a new list
 - Another difference is that the list.sort() method is only defined for lists. In contrast, the sorted() function accepts any iterable.
```
lst = [1, 2, 3]
lst.sort(key=len)

def add1(item):
  return item + 1

lst.sort(add1)

sorted("This is a test string from Andrew".split(), key=str.lower)


# sort multidim lst
x=sorted(lst, key=lambda x: x[1], reverse=True)
```
3. list slicing 

list indices must be integers or slices, not tuple

```
lst = [[1, 2, 3], [1, 2, 3], [1, 2, 3]]
lst[1] -- okay
lst[2:1000] --okay
lst[1, 2] --error
lst[1][2] --okay

```


4. move dups from list
```
 l = [1,2,3]
 v = [2,3,4]
 dict.fromkeys(l,v)
{1: [2, 3, 4], 2: [2, 3, 4], 3: [2, 3, 4]}
 l = [1,2,2,2,3]

 dict.fromkeys(l)
{1: None, 2: None, 3: None}
 list(dict.fromkeys(l))
[1, 2, 3]
```


5. list remove/delete/pop


```
lst = [1, 2, 3, 4, 1]
lst.remove(1) # remove the first occurence

del lst[0] # remove an item at a centain index

x = lst.pop() # remove the last item and return it
x = lst.pop(2) # remove the second item and return it

```


## try exception

1. try/except/else/finally

```

try:
  # code has to be executed and tested out if there's an error
except [Exception]:
  # if there is [certain type of] exceptions raised in the try block.=, code here gets executed like normal code
else:
  # if there's no exception raised in try block, code here gets executed
finally:
  # no matter what, this code gets executed at the end (even if there was an uncaught exception (that didn’t cause a crash, obviously) or a return statement in one of the other blocks.)

```

## Set

 - sets operations: equal, union, intersect, difference, symmetric difference
 
 ```
 set_a = {1, 2, 3}
 set_b = {2, 4}
 
 set_a == set_b #False
 set_a & set_b # {2}
 set_a | set_b # {1, 2, 3, 4}
 set_a - set_b # {1, 3}
 set_a ^ set_b # {1, 3, 4} symmetric difference
 
 ```
