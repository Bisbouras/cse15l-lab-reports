Lab Report 5.

Edstem Post:

Hi, I am having trouble with my ListExamples.java file. I believe it to be correct but one of my tests is failing and I cannot figure out why. Here is an attached screenshot of the failing test:

![Image](lab33.PNG)

TA Response:

Hi, there seems to be an issue with how you are handling the merging of the sorted lists. You could maybe try adding some print statements to print the elements being compared and added to the result list.

Student Response: It seems to have been a small typo, I was updating index1 instead of index2 by mistake, I have fixed it, thank you very much!

File and directory structure: 

cenotiadis@ieng6.ucsd.edu
-
lab7 directory
-
ListExamples.java: Java file containing the merge method.
ListExamplesTest.java file that contains the tests.
test.sh Bash script to test the file using JUnit

The code pre bug fix:

```import java.util.ArrayList;
import java.util.List;

class ListExamples {
    static List<String> merge(List<String> list1, List<String> list2) {
        List<String> result = new ArrayList<>();
        int index1 = 0, index2 = 0;
        while (index1 < list1.size() && index2 < list2.size()) {
            if (list1.get(index1).compareTo(list2.get(index2)) < 0) {
                result.add(list1.get(index1));
                index1 += 1;
            } else {
                result.add(list2.get(index2));
                index2 += 1;
            }
        }
        while (index1 < list1.size()) {
            result.add(list1.get(index1));
            index1 += 1;
        }
        while (index2 < list2.size()) {
            result.add(list2.get(index2));
            index1 += 1;
        }
        return result;
    }
}```
