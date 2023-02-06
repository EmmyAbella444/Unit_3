# QUIZ 039

![Screen Shot 2023-02-02 at 10 05 47](https://user-images.githubusercontent.com/111819437/216205840-891e41f5-c8c9-4c2a-b252-474919581eed.png)

## Code
```.py
from kivymd.app import MDApp

class Quiz_039(MDApp):
    def __init__(self,**kwargs):
        super().__init__(**kwargs)
        self.count = 0

    def build(self):
        return

    def add(self):
        self.count+=1
        self.root.ids.counter_label.text = f"Count = {self.count}"

QUIZ039 = Quiz_039()
QUIZ039.run()
```
## Layout
```.kv
# Layout_demo_kv
Screen:
    size: 500,500

    MDBoxLayout:
        id: main_box
        orientation: 'horizontal'
        size_hint:.7,.3
        md_bg_color: "#fc03f4"
        pos_hint: {"center_x": .5, "center_y": .5}

        MDLabel:
            id : counter_label
            font_size: '34'
            size_hint:.5,1
            text: 'Start'
        MDRaisedButton:
            id: add
            text: 'Add+1'
            font_size: '34'
            size_hint:.5,1
            on_press: app.add()

```

## Evidence

https://user-images.githubusercontent.com/111819437/216987117-f4f07bbf-3da5-429b-b8a3-c03b799ad556.mov







