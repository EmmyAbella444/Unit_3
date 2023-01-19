# QUIZ 037

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
