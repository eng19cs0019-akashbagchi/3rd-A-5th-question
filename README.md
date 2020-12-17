## ANS 5(a):

Consider the input:
2

1 2

2 3

2

1 4

3 5


For the same, we get the output:

{2: 3}

[[1, 4], [3, 5]]

{1: [2, 4]}

As we can see, the program is not adding the values (k, v2) to data1, when there doesn't exist any key-value pair with key k in data1.
Thus this is one input on which the function does NOT produce correct output.

## Ans 5(b):

The given code contains the following:
```
    # Examine every (k, v2) pair in data2
    for [k, v2] in data2:
        # Check if there is a key-value
        # pair with key = k in data1
        if k in data1:
            v1 = data1[k]
            # (k, v1) in dict1
            # Check if v1 != v2
            if v1 != v2:
                # Add (k, [v1, v2])
                # to dictionary                
                dupKeys[k] = [v1, v2]
                # Remove (k, v1) from data1
                del data1[k]
            else:
                # Add (k, v2) to data1
                data1[k] = v2
```

We modify the same to:
```
    # Examine every (k, v2) pair in data2
    for [k, v2] in data2:
        # Check if there is a key-value
        # pair with key = k in data1
        if k in data1:
            v1 = data1[k]
            # (k, v1) in dict1
            # Check if v1 != v2
            if v1 != v2:
                # Add (k, [v1, v2])
                # to dictionary                
                dupKeys[k] = [v1, v2]
                # Remove (k, v1) from data1
                del data1[k]
            else:
                # Add (k, v2) to data1
                data1[k] = v2
        else:
            data1[k] = data1.get(k, v2)
```

,leaving the rest of the code as it is.

Thus now we can use the same inputs as in (A) and observe correct output:

2

1 2

2 3

2

1 4

3 5

{2: 3, 3: 5}

[[1, 4], [3, 5]]

{1: [2, 4]}


## Ans 5(c):

### Test case 1:

2

1 2

2 3

2

1 4

3 5

### Test case 2:

3

1 4

2 3

3 1

3

1 1

2 4

3 5

### Test case 3:

2

3 6

4 2

2

3 1

4 2
