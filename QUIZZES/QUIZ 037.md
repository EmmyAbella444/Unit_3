# QUIZ 037
![Screen Shot 2023-01-24 at 17 10 51](https://user-images.githubusercontent.com/111819437/214241375-e0a73f12-4e4e-49f6-ae79-550e4f05ddc2.png)


## CODE
```.py
class CompoundInterest:
    def __init__(self, principal:int,rate:int,years:int):
        self.principal = principal
        self.rate = rate
        self.years = years

    def Calculate(self):
        return self.principal *(1 + self.rate) ** self.years


class AccountingProgram:
    def __init__(self):
        self.data = CompoundInterest(principal=0, rate=0,years=0)

    def set_rate(self,rate):
        self.data.rate = rate

    def set_years(self,years):
        self.data.years = years

    def set_principal(self,principal):
        self.data.principal = principal

    def calculate_interest(self):
        return self.data.Calculate()

Save = CompoundInterest(principal=100,rate=0.1,years=10)
print(Save.Calculate())
```


## EVIDENCE

![Screen Shot 2023-01-19 at 22 57 38](https://user-images.githubusercontent.com/111819437/213461240-4aace399-eae6-479f-b0d7-008a1bfd717d.png)


## UML DIAGRAM
![Screen Shot 2023-02-06 at 11 27 20](https://user-images.githubusercontent.com/111819437/216869420-6f90be1b-ba62-48b4-97b6-433e6ec32897.png)

