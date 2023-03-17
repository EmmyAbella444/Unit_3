
# QUIZ 047
![Screen Shot 2023-02-24 at 9 57 12](https://user-images.githubusercontent.com/111819437/221065740-e473fc20-0bac-4fd9-ae3b-77b26c1dd267.png)

## CODE
```.py
import sqlite3

from kivymd.app import MDApp
from Secure_passwords import encrypt_password,check_password

class database_handler:
    def __init__(self, name):
        self.connection = sqlite3.connect(name)
        self.cursor = self.connection.cursor()

    def search(self, query):
        result = self.cursor.execute(query).fetchall()
        return result

    def run_save(self, query):
        self.cursor.execute(query)
        self.connection.commit()

    def close(self):
        self.connection.close()


class quiz047(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.components = {"basic":0}


    def build(self):
        return

    def update(self):
        #This function updates all the labels in the form using the base salary and the percentage
        # Pseudocode
        # 1- get the base salary from the GUI
        base = self.root.ids.base.text
        hash = ""
        ids = [ "inhabitant","income_tax","pension","health"]
        # 2- if base salary define total=int(base) and an empty string to store build a hash (for_hash="") if no base then end the function
        if base !="":
            total = int(base)
            hash+=f"base{total}"
            # 3- for Each TextField with ids: "inhabitant","income_tax","pension","health" get the text property
            for each in ids:
                value = self.root.ids[each].text
                # 4- if the TextField.text has a number (value), calculate the equation new_value="(base*int(value)//100) JPY" and subbctract the equation to the total
                if value!= "":
                    new_value = f"{int(value)*int(base)//100}JYP"
                    total -= int(value)*int(base)//100
                    hash +=f"id_of_textField{value}"
                # 5- if no: then new_value = " JPY"
                else:
                    new_value="JPY"
                    hash+=f"id_of_textField{0}"
            # 6- set the label next to the TextField (inhabitant_label, income_tax_label, etc) to the variable new_value
                self.root.ids[f"{each}_label"].text = new_value

            # 7- concatenate to the hash variable the f"{id}{value}"
            hash += f"total{total}"
            # 8- set the text of the element id=total to the total with the JPY symbol
            self.root.ids.salary_label.text = f"{total}JYP"
            # 9- encrypt the hash and change the text of the label with id=hash to the last 50 characters of the hash
            encrypted = encrypt_password(hash)
            self.root.ids.hash.text = encrypted[:50]



    def save(self):
        #repeat the algorithm in update but create variables to save the amount of each item:
        base = self.root.ids.base.text
        hash = ""
        ids = ["inhabitant", "income_tax", "pension", "health"]
        if base != "":
            total = int(base)
            hash += f"base{total}"
            # 3- for Each TextField with ids: "inhabitant","income_tax","pension","health" get the text property
            for each in ids:
                value = self.root.ids[each].text
                # 4- if the TextField.text has a number (value), calculate the equation new_value="(base*int(value)//100) JPY" and subbctract the equation to the total
                if value != "":
                    new_value = f"{int(value)*int(base)//100} JPY"
                    total -= int(value)*int(base)/100
                    hash += f"id_of_textField{value}"
                # 5- if no: then new_value = " JPY"
                else:
                    new_value = " JPY"
                    hash += f"id_of_textField{0}"
                # 6- set the label next to the TextField (inhabitant_label, income_tax_label, etc) to the variable new_value
                self.root.ids[f"{each}_label"].text = new_value.split(".")[0]
            # 7- concatenate to the hash variable the f"{id}{value}"
            hash += f"total{total}"
            # 8- set the text of the element id=total to the total with the JPY symbol
            self.root.ids.salary_label.text = f"{str(total).split('.')[0]} JPY"
            # 9- encrypt the hash and change the text of the label with id=hash to the last 50 characters of the hash
            encrypted_hash = encrypt_password(hash)
            self.root.ids.hash.text = encrypted_hash[:50]
            #inhabitant = amount in JPY to remove from base for inhabitant tax
            inhabitant = int(self.root.ids.inhabitant_label.text.split(" JPY")[0])
            #income_tax = amount in JPY to remove from base for income tax
            income_tax = int(self.root.ids.income_tax_label.text.split(" JPY")[0])
            #pension = amount in JPY to remove from base for pension tax
            pension = int(self.root.ids.pension_label.text.split(" JPY")[0])
            #health = amount in JPY to remove from base for health tax
            health = int(self.root.ids.health_label.text.split(" JPY")[0])
            #total = total net salary
            total = int(self.root.ids.salary_label.text.split(" JPY")[0].split('.')[0])
            #hash = hash of the calculations in the format
            hash = self.root.ids.hash.text

            #inhabitant4,income_tax3,pension2,health1,total1103  (here the numbers next to the category are percentages)

            query = f"INSERT into payments(base, inhabitant, income_tax, pension, health, total, hash) values('{int(base)}', '{inhabitant}', '{income_tax}', '{pension}', '{health}', '{total}', '{hash}')"
            db = database_handler("payments (1).db")
            db.run_save(query)
            db.close()
            self.root.ids.hash.text = f"Payment saved"

    def clear(self):
        for label in ["base", "inhabitant","income_tax","pension","health"]:
            self.root.ids[label].text = ""
            self.root.ids[label+"_label"].text = " JPY"

        self.root.ids["salary_label"].text = " JPY"
        self.root.ids.hash.text = "----"

def check_fraud(database):
    cur = sqlite3.connect(database)
    cursor = cur.cursor()

    cursor.execute("SELECT id, base, inhabitant, income_tax, pension, health, total, hash FROM payments")
    rows = cursor.fetchall()
    switch = 0
    for row in rows:
        (id, base, inhabitant, income_tax, pension, health, total, hash) = row
        hash_string = f"base{base},inhabitant{inhabitant},income_tax{income_tax},pension{pension},health{health},total{total}"

        if not check_password(hash_string,hash):
            print(f"Payment record {id} is fraudulant.")
            print()
            switch = 1
    if not switch:
        print("Fraud check complete. No fraud found.")

    cur.close()




test = quiz047()
create = """CREATE TABLE if not exists payments(
                  id INTEGER PRIMARY KEY,
                  base int,
                  inhabitant int,
                  income_tax int,
                  pension int,
                  total int,
                  hash text ,
                  health int

              )"""
db = database_handler("payments (1).db")
db.run_save(create)
db.close()
check_fraud("payments (1).db")
test.run()

```

## EVIDENCE
![Screen Shot 2023-03-17 at 14 18 48](https://user-images.githubusercontent.com/111819437/225820963-6d3f04e4-b6ce-4f5f-be72-e5533cb2b31a.png)
