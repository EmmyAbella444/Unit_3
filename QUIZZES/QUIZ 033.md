
# QUIZ 33
![Screen Shot 2023-01-11 at 9 45 13](https://user-images.githubusercontent.com/111819437/211691887-d1c7b3b7-6ae6-471a-bd34-3feaccba7129.png)

## CODE
```.py
def mystery (list1,list2)->list:  # def  function with two lists as input and one list as output
    output = []  # create an empty lis called output
    for y in list1:  # iterates each element of list1
        for x in list2:  # For each element of list1 iterates over the elements of list2
            if y==x:  # Check if the element on list1 and list2 are the same
                output.append(y)  # If it is true add the value of list 1 to the list output
    return output  # return output list
```

## AUTOMATED TEST
```.PY
from QUIZ_033 import mystery
import pytest

def test_empty_lists():
  assert mystery([], []) == []

def test_one_common_element():
  assert mystery([1, 2, 3], [3, 4, 5]) == [3]

def test_multiple_common_elements():
  assert mystery([1, 2, 3, 4], [3, 4, 5, 6]) == [3, 4]
  ```
  
  ## EVIDENCE
  ![Screen Shot 2023-01-10 at 10 14 24](https://user-images.githubusercontent.com/111819437/211439755-d5630270-498a-45c8-b77c-b87a6eda28ef.png)
