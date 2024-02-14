Week 5 - Lab Report 3.

Part 1 - Bugs.

The bug I chose from week 4's lab is the one that existed in the reverseInPlace method, in the ArrayExamples file.

First of all, here is the code for this method, as given, including the bug:

```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
```

Here is a failure inducing test:

```
int[] input2 = {4, 2};
ArrayExamples.reverseInPlace(input2);
assertArrayEquals(new int[]{ 2, 4 }, input2);
```

Here is a non-failure inducing test:

```
int[] input1 = { 3 };
ArrayExamples.reverseInPlace(input1);
assertArrayEquals(new int[]{ 3 }, input1);
```

Here are the outputs of running these two test:

Test 1:
