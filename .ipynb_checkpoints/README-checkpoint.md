# test_speed_python

All test executed on Windows 10, intel core i5 4590, 12gb of RAM, GTX 970

Results until now:

- To check if an element is in a data structure (array-like), it is fastest if the data structure is a set. If it is not a set:
    - if it is a Python list, convert it to set and do the operation (if the operation needs to be done more than 10 times, this is the way to go)
    - if it is a numpy array and you have to do the operation less then 100 times, do it as is, else, convert the np.array to a set.
- To add a list to another one, the fastest way is to use: ```seq_1 = seq_1 + seq_2```, do not use += or extend
- To create a dict, the fastest way is to initialize one empty dict ```dictionary = {}``` and then fill it using ```dictionary[key] = value```
- To multiply two matrices, the fastest way is to use ```m1@m2``` with the ```@numba.jit(nopython=True)``` decorator (numba required)
- To do a for cycle in which only python or numpy objects are used, the fastest way is to use ```@numba.jit(nopython=True)``` decorator (numba required)
- 