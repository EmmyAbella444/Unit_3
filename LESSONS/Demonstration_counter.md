# Demonstration of a counter using kv

## CODE
```.py
demo_conter.py

from kivymd.app import MDApp

class layout_demo(MDApp):
    def __init__(self,**kwargs):
        super().__init__(**kwargs)
        self.count = 0

    def build(self):
        return

    def set_counter(self):
        # validate that it is a digit
        user_start = int(self.root.ids.user_start_x.text)
        self.count = user_start
        self.root.ids.counter_label.text = f"x={self.count}"

    def change(self,name:str):
        user_start = int(self.root.ids.user_start_x.text)
        self.count = user_start
        if 'up' in name:
            self.count += 1
        else:
            self.count -=1
        self.root.ids.counter_label.text = f"x={self.count}"

demo_class = layout_demo()
demo_class.run()
```
## Layout
```.kv

# Layout_demo_kv
Screen:
    size: 500,500

    MDBoxLayout:
        id: main_box
        orientation: "vertical"
        size_hint:1,.5
        md_bg_color: "#fc03f4"
        pos_hint: {"center_x": .5, "center_y": .5}

        MDTextField:
            id: user_start_x
            hint_text: "Enter a number"
            mode: "round"
            size_hint: .25,1
            pos_hint: {"center_x":.5}
            on_text: app.set_counter





        MDBoxLayout:
            id: second_box
            orientation: "horizontal"
            md_bg_color: "#2003fc"

            MDLabel:
                id:counter_label
                font_style: "H3"
                halign: "center"

            MDBoxLayout:
                id: third_box
                orientation: "vertical"


                MDRaisedButton:
                    id: up_btn
                    text: "+1"
                    on_release: app.change("up")
                    size_hint:1,1

                MDRaisedButton:
                    id: down_btn
                    text: "-1"
                    on_release: app.change("down")
                    size_hint:1,1
                    
 ```


