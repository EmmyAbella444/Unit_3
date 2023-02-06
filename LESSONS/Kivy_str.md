## Kivy Start

```.py
# kivy_start.py
from kivymd.app import MDApp
class main(MDApp):
    def build(self):
        return

    def hello_world(self):
        print("Hello, successful click!")
        self.root.ids.label.text = "Well done"

demonstration = main()
demonstration.run()
```

```.kv
# main.kv

Screen:
    id: scr_manager

    MDBoxLayout:
        orientation: "vertical"
        size_hint: 0.7, 0.3
        pos_hint: {"center_x": 0.5, "center_y": 0.5}
        MDLabel:
            id: label
            text: "Hi, Emmy"
            halign: "center"
            font_size: "34pt"

        MDRaisedButton:
            id: click_me_button
            size_hint: 1, .3
            on_press: root.parent.current="MisteryPageB"
                size_hint:.5,.3
                
```
