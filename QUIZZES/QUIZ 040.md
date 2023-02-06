# QUIZ 040

![Screen Shot 2023-02-03 at 13 38 18](https://user-images.githubusercontent.com/111819437/216513789-e201bda8-1f8f-477b-a987-f4d2ba1685ea.png)


## CODE
```.py

from kivymd.app import MDApp

class Quiz_040(MDApp):
    def __init__(self,**kwargs):
        super().__init__(**kwargs)


    def build(self):
        return

    def set_color(self):
        self.root.ids.label.md_bg_color="#121111"
        self.root.ids.label.text_color=1,1,1,1
QUIZ040=Quiz_040()
QUIZ040.run()

```
## Layout
```.kv

Screen:
    size: 500,500

    MDBoxLayout:
        id: main_box
        orientation: "vertical"
        md_bg_color: "#FFFFFF"


        MDLabel:
            id: label
            text: "Emmy Abella"
            theme_text_color: "Custom"
            text_color:0,0,0,1
            halign: "center"
            font_style: "H2"
            pos_hint: {"center_x": 0.5, "center_y": 0.5}

        MDRaisedButton:
            id: btn
            text: "DARK MODE"
            on_release: app.set_color()


```

## EVIDENCE
