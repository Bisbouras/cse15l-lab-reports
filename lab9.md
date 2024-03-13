Lab Report 5.

Edstem Post:

Hi, I am having trouble with my ListExamples.java file. I believe it to be correct but one of my tests is failing and I cannot figure out why. Here is an attached screenshot of the failing test:

![Image](lab33.PNG)

TA Response:

Hi, there seems to be an issue with how you are handling the merging of the sorted lists. You could maybe try adding some print statements to print the elements being compared and added to the result list.

Student Response: It seems to have been a small typo, I was updating index1 instead of index2 by mistake, I have fixed it, thank you very much!




File and directory structure: 

cenotiadis@ieng6.ucsd.edu/lab7

ListExamples.java: Java file containing the merge method.

ListExamplesTest.java file that contains the tests.

test.sh Bash script to test the file using JUnit




The code pre bug fix:

```import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      // change index1 below to index2 to fix test
      index1 += 1;
    }
    return result;
  }


}```




command line:

bash test.sh ListExamplesTest.java

shows the failing test cases.




In order to fix the bug, you must change where it says index1 in the 4th to last line to index2. It is a simple typo. Additionally, you must change the line that says ```result.add(0, s);``` to be ```result.add(s);```



Part 2: Reflection.

In my lab experiences of the second hlf of the quarter, I think that the coolest thing I learnt is how to genuinely use the terminal to access and edit files freely. I had always watched my father use the terminal with expertise and I had thought it was extremely hard, but now having learnt all the basic commands and formats I am happy to be able to use it, albeit not to the same extent.
