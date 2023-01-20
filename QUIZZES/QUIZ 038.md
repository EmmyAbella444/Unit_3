# QUIZ 038

## CODE
```.py
import random
import math
import matplotlib.pyplot as plt

plt.style.use('ggplot')  # Theme background
ax = plt.axes()
ax.set_facecolor("#ffafcc")  # Color background Violet
class Coordinate:
    def __init__(self, x:int, y:int):
        self.x:int = x
        self.y:int = y

    def __repr__(self)->str:
        return f"[Coordinate class]x={self.x} y={self.y}"

class city:
    def __init__(self, name:str, location:Coordinate):
        self.name = name
        self.location = location

    def __repr__(self):
        return f"[City class] {self.name} is located at {self.location}"
    # Create a method in the class city that receives as input another city and return the distance between the two cities

    def distance(self,city2):
        xa,xb = self.location.x,self.location.x
        ya,yb = city2.self.location.y,city2.self.location.y
        d = math.sqrt((xb-xa)^2 +(yb-ya)^2)
        return round(d,2)

class country:
    def __init__(self, name:str):
        self.cities = []
        self.name = name
    def add_city(self, new_city:city):
        if isinstance(new_city, city):
            self.cities.append(city)
        else:
            raise ValueError("City must be a city object")


# Create 10 random cities 
Brazil = country(name="Brazil")
cities_brazil = ["Piracicaba", "Capivari", "Sao Paulo", "Rio de janeiro", " Ilheus", "Sabinopolis", "Natal", "joao pessoa", "Campinas", "Arraial do cabo"]
for i in cities_brazil:
    point = Coordinate(x=random.randint(0,9), y=random.randint(0,9))
    new_city = city(name=i, location=point)
    Brazil.add_city(new_city=new_city)
    plt.title("Cities in Brazil")
    plt.scatter(point.x,point.y, color='b', marker='o', s=100)
    plt.text(point.x,point.y,f"{new_city.name}")
plt.xlabel("Latitude(m)")
plt.ylabel("Longitude(m)")
plt.show()
```

## EVIDENCE

![Screen Shot 2023-01-20 at 15 05 57](https://user-images.githubusercontent.com/111819437/213628663-fbf3589e-8d20-4eb2-a766-59c4c52808c8.png)
