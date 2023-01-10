10/01/2023

In this lesson we learned about automated test and as an example we did the automated test for the quiz 3

### CODE
 ```.py
 # Tests cases: A->T/G->C/T->A/C->G
# dem_automated_testing

def translate_dna(in_protein:str)->str:
    out_protein = "not valid"
    if in_protein == "A":
        out_protein = "T"
    if in_protein == "G":
        out_protein = "C"
    if in_protein == "T":
        out_protein = "A"
    if in_protein == "C":
        out_protein = "G"
    return out_protein
```
### EVIDENCE
```.py
# test_dem_automated_testing

from dem_automated_testing import translate_dna
import pytest

def test_a_to_t():
    assert translate_dna("A") == "T"

def test_g_to_c():
    assert translate_dna("G") == "C"

def test_t_to_a():
    assert translate_dna("T") == "A"

def test_c_to_g():
    assert translate_dna("C") == "G"

def test_non_protein():
    assert translate_dna("Z") == "not valid"![Screen Shot 2023-01-10 at 11 13 10](https://user-images.githubusercontent.com/111819437/211446416-974714ce-9276-4626-9dcb-d7ed2c2e13bf.png)

```
   
![Screen Shot 2023-01-10 at 11 13 10](https://user-images.githubusercontent.com/111819437/211446475-7b3c27e4-a30b-47b8-9757-51936e093f81.png)



   
   
