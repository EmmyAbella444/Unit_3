
# TASK 1 SL
![Screen Shot 2023-01-31 at 9 00 24](https://user-images.githubusercontent.com/111819437/215644792-96fe490e-561d-4529-b999-5bedec9b6572.png)

## Layout.kv

```.kv
# Layout_demo_kv
Screen:
    size: 500,500


    MDBoxLayout:
        id: main_box
        orientation: "vertical"
        size_hint:1,.5
        pos_hint: {"center_x": .5, "center_y": .5}

        MDLabel:
            text: "$Currency Converter$"
            halign: "center"
            font_size: "34pt"


        MDTextField:
            id: user_start_x
            hint_text: "Enter an amount in BRL"
            validator: "phone"
            line_color_focus: "pink"
            text_color_normal: "pink"
            size_hint: .20,0.5
            pos_hint: {"center_x":.13,}
            on_text: app.set_counter

        MDBoxLayout:
            id: second_box
            orientation: "horizontal"


            MDLabel:
                id:counter_label
                font_style: "H3"
                halign: "center"

            MDBoxLayout:
                id: third_box
                orientation: "vertical"

                MDRaisedButton:
                    id: dolar_btn
                    text: "USD $"
                    on_press: app.change("dolar")
                    size_hint:1,1.5
                    md_bg_color: "#ffabfe"

                MDRaisedButton:
                    id: yen_btn
                    text: "JYP ¥"
                    on_press: app.change("yen")
                    size_hint:1,1.5
                    md_bg_color: "#7ed6d2"


```

## Code.py

```.py
#converter_task1.py

from kivymd.app import MDApp


class layout_converter(MDApp):
    def __init__(self,**kwargs):
        super().__init__(**kwargs)
        self.amount = 0

    def build(self):
        return

    def set_counter(self):
        # validate that it is a digit
        user_start = self.root.ids.user_start_x.text



    def change(self,name:str):
        user_start = int(self.root.ids.user_start_x.text)
        self.amount = user_start
        if 'dolar' in name:
            self.amount = self.amount / 5.1
            self.root.ids.counter_label.text = f"{round(self.amount,2)} USD$"
        else:
            self.amount *= 25
            self.root.ids.counter_label.text = f"{round(self.amount,2)} JYP¥"

convert_class = layout_converter()
convert_class.run()
```
## EVIDENCE


https://user-images.githubusercontent.com/111819437/215647992-7f0ffc01-eeda-4be1-bbef-97ea9abade5c.mov



# TASK 1 HL

![Screen Shot 2023-01-31 at 9 00 58](https://user-images.githubusercontent.com/111819437/215645369-dc55a218-b1da-4b6a-a417-9b013e41a05c.png)

## Layout.kv
```.kv
# Layout_demo_kv
Screen:
    size: 500,500


    MDBoxLayout:
        id: main_box
        orientation: "vertical"
        size_hint:1,.5
        pos_hint: {"center_x": .5, "center_y": .5}

        MDLabel:
            text: "Converter Bits to Bytes"
            halign: "center"
            font_size: "30pt"


        MDTextField:
            id: user_start_x
            hint_text: "Enter the amount of bits"
            line_color_focus: "pink"
            text_color_normal: "pink"
            size_hint: .20,0.5
            pos_hint: {"center_x":.13,}
            on_text: app.set_counter



        MDBoxLayout:
            id: second_box
            orientation: "horizontal"


            MDLabel:
                id:counter_label
                font_style: "H3"
                halign: "center"

            MDBoxLayout:
                id: third_box
                orientation: "vertical"

                MDRaisedButton:
                    id: bytes_btn
                    text: "CONVERT"
                    on_press: app.change("convert")
                    size_hint:1,1.5
                    md_bg_color: "#ffabfe"


```
## Code.py

```.py
from kivymd.app import MDApp

class layout_bits(MDApp):
    def __init__(self,**kwargs):
        super().__init__(**kwargs)
        self.amount = 0

    def build(self):
        return

    def check(self):
        if self.amount is not int:
            raise ValueError
    def set_counter(self):
        # validate that it is a digit
        user_start = self.root.ids.user_start_x.text
        if user_start.isdigit():
            self.amount = user_start
            self.root.ids.counter_label.text = f"B/.{self.amount}"


    def change(self,name:str):
        user_start = int(self.root.ids.user_start_x.text)
        self.amount = user_start
        if "convert" in name:

            if self.amount<8:
                self.root.ids.counter_label.text = f"{self.amount}bits"

            elif self.amount>7 and self.amount <8192:
                self.amount = self.amount // 8
                self.root.ids.counter_label.text = f"{self.amount}byte"

            elif self.amount >8191 and self.amount<8388608:
                self.amount = self.amount // 8192
                self.root.ids.counter_label.text = f"{self.amount}kilo"

            elif self.amount >=8388608 and self.amount<8589934592:
                self.amount = self.amount // 8388608
                self.root.ids.counter_label.text = f"{self.amount}Mega"

            elif self.amount >=8589934592 and self.amount<8796093022208:
                self.amount = self.amount // 8589934592
                self.root.ids.counter_label.text = f"{self.amount}Giga"

            elif self.amount >=8796093022208 and self.amount<9007199254740992:
                self.amount = self.amount // 8796093022208
                self.root.ids.counter_label.text = f"{self.amount}Tera"

            elif self.amount >=9007199254740992 and self.amount<9223372036854775808:
                self.amount = self.amount // 9007199254740992
                self.root.ids.counter_label.text = f"{self.amount}Peta"

            elif self.amount >=9223372036854775808:
                self.amount = self.amount // 9223372036854775808
                self.root.ids.counter_label.text = f"{self.amount}Exa"



convert_class = layout_bits()
convert_class.run()








```
## Evidence



https://user-images.githubusercontent.com/111819437/215649574-2c3d05fd-97a7-4d80-9b2f-b2a7576b65cd.mov



