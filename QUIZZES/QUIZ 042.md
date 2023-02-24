# QUIZ 042
![Screen Shot 2023-02-24 at 10 00 22](https://user-images.githubusercontent.com/111819437/221066112-c0038ec5-196d-448a-b164-8ee5d590408a.png)


## CODE
```.py
# QUIZ 042

from kivymd.app import MDApp
from kivymd.uix.screen import MDScreen

class MysteryMain(MDScreen):
    pass

class MysteryPageA(MDScreen):
    pass

class MysteryPageB(MDScreen):
    pass

class Quiz_042(MDApp):
    def build(self):
        return

QUIZ042 = Quiz_042()
QUIZ042.run()
```


## LAYOUT
```.kv

# QUIZ 042 Layout

ScreenManager:

    MysteryMain:
        name:"MysteryMain"

    MysteryPageA:
        name:"MysteryPageA"

    MysteryPageB:
        name:"MysteryPageB"



<MysteryMain>:
    FitImage:
        source:"fundo.jpg"

    MDCard:
        size_hint: .6,.8
        pos_hint: {"center_x":.5, "center_y":.5}
        orientation: "vertical"

        MDLabel:
            size_hint: 1,.1
            font_style: "H2"
            text: "MYSTERY"
            halign: "center"

            MDBoxLayout:
                size_hint: 1,.2

            MDRaisedButton:
                id:login
                text:"Next page"
                md_bg_color: "a8dadc"
                on_press: root.parent.current="MysteryPageA"
                size_hint:.5,.3
<MysteryPageA>:
    FitImage:
        source:"fundo.jpg"

    MDCard:
        size_hint: .6,.8
        pos_hint: {"center_x":.5, "center_y":.5}
        orientation: "vertical"

        MDLabel:
            size_hint: 1,.1
            font_style: "H4"
            text: "THIS IS PAGE A YOU PRESSED THE BUTTON"
            halign: "center"

            MDBoxLayout:
                size_hint: 1,.2

            MDRaisedButton:
                id:login
                text:"Next page"
                md_bg_color: "a8dadc"
                on_press: root.parent.current="MysteryPageB"
                size_hint:.5,.3
<MysteryPageB>:
    FitImage:
        source:"fundo.jpg"

    MDCard:
        size_hint: .6,.8
        pos_hint: {"center_x":.5, "center_y":.5}
        orientation: "vertical"

        MDLabel:
            size_hint: 1,.1
            font_style: "H4"
            text: "THIS IS PAGE B YOU PRESSED THE BUTTON"
            halign: "center"

            MDBoxLayout:
                size_hint: 1,.2

            MDRaisedButton:
                id:login
                text:"Previous page"
                md_bg_color: "a8dadc"
                on_press: root.parent.current="MysteryPageA"
                size_hint:.5,.3


```


## EVIDENCE


https://user-images.githubusercontent.com/111819437/216991119-1051be9a-2402-4592-bcc7-05de9df66d46.mov


