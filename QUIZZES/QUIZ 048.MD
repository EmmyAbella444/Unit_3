# QUIZ


## CODE
```PY
import sqlite3
from Secure_passwords import encrypt_password, check_password


class database_handler:
    def __init__(self,namedb:str):
        self.connection = sqlite3.connect(namedb)
        self.cursor = self.connection.cursor()


    def search(self, query):
        result = self.cursor.execute(query).fetchall()
        return result

    def run_save(self, query):
        self.cursor.execute(query)
        self.connection.commit()

    def close(self):
        self.connection.close()



x = database_handler("bitcoin_exchange.db")
query = "SELECT * from ledger"
result = x.search(query)
x.close()

end_code = "\033[00m"
green = "\033[0;32m"
red = "\33[0;31m"

for i in result:
    id = i[0]
    sender_id = i[1]
    receiver_id = i[2]
    amount = i[3]
    signature = i[4]
    string = f"id {id},sender_id {sender_id},receiver_id {receiver_id},amount {amount}"

    if check_password(string,signature) == True:
        print(f"{green}Tx id={id} Signature matches{end_code}")
    else:
        print(f"{red}Tx id={id} Error signature{end_code}")

```
## EVIDENCE
![Screen Shot 2023-02-24 at 9 54 46](https://user-images.githubusercontent.com/111819437/221065566-6865a65f-ee18-4de5-afac-20aa203ede48.png)


