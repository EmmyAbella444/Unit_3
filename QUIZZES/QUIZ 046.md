# QUIZ 046

![Screen Shot 2023-02-21 at 8 11 43](https://user-images.githubusercontent.com/111819437/220211277-e24610d1-50a9-4c19-bee1-651d6eaee691.png)

## CODE

```.py
import sqlite3

haiku="""Code flows like a stream algorithms guide its way in silence, it solves
"""

class database_handler:
    def __init__(self,namedb:str):
        self.connection = sqlite3.connect(namedb)
        self.cursor = self.connection.cursor()

    def create_table(self):
        query = f"""CREATE TABLE if not exists WORDS(
            id INTEGER PRIMARY KEY not NULL,
            word_text not NULL,
            lengtth int not NULL
            )"""
        self.run_query(query)

    def run_query(self, query: str):
        self.cursor.execute(query)
        self.connection.commit()

    def close(self):
        self.connection.close()

    def insert(self, word, length):
        query = f"INSERT into WORDS(id, word_text, lengtth) VALUES (null, '{word}', '{length}')"
        self.run_query(query)

db = database_handler(namedb="test")
db.create_table()

for word in haiku.split():
    db.insert(word, len(word))

query = f"SELECT avg(lengtth) from WORDS"
db.run_query(query)
print(db.cursor.fetchone())

db.close()

```
## EVIDENCE
![Screen Shot 2023-03-17 at 13 10 43](https://user-images.githubusercontent.com/111819437/225810706-e6a568fd-4602-4131-bc8e-5028b31cd28d.png)
