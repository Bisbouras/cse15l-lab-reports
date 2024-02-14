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

Test 1 (pass):

![Image](image2.PNG)

Test 2 (fail):

![Image](image.png)

Here is the changes made to the original method to fix the bug. The original method is written above:

```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - 1 - i] = temp;
    }
}
```

The original method simply doesn't work, and instead replaces every element of the array with the value of it's last element, because the as the loop progresses, it overwrites the same values. The new one essentially uses a similar technique, but only iterates up to half the array, and swaps the elements from the beginning to the end.

Part 2 - Researching Commands.

I will be chosing the find command. The source I used is this:
[https://man7.org/linux/man-pages/man1/find.1.html](url)

COMMAND-LINE OPTION 1:

The first command-line option I chose is -mtime. This only shows files based on the time of the last modification made to them. 

Example 1:

Command:
```
find ./technical -mtime -7
```
Output:
```
./technical
./technical/911report
./technical/911report/chapter-1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
...
```
Using the command with the -mtime -7 finds the files edited within the last 7 days, which is all of them, and therefore shows all the files in /technical.

Example 2:

Command:
```
find ./technical -mtime -1
```
Output:
```
```
Using this command with the -mtime -1 returns no files, as none of the files in /technical have been modified in the past day.

COMMAND-LINE OPTION 2:

The second command line option I chose is the -name one. This allows you to simply search in the directory for files/other directories with specific names.

Example 1:

```
find ./technical -name "pmed.0020281.txt"
```

Output:

```
./technical/plos/pmed.0020281.txt
```

Example 2:

```
find ./technical/ -name "plos"
```

Output:

```
./technical/plos
```
