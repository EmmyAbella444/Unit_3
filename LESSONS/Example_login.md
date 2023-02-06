# Example of a login with kv

## CODE
```.py
# Login APP.py
from kivymd.app import MDApp
from kivymd.uix.screen import MDScreen

class LoginScreen(MDScreen):
    def try_login(self):
        print("User tried to login")
        # Get the input username and password and print it
        uname = self.ids.uname.text
        password = self.ids.password.text

        print(f"Credential are {uname} and {password}")

class RegistrationScreen(MDScreen):
    def try_register(self):
        print("User tried to register")
        uname = self.ids.uname.text
        password = self.ids.password.text
        email = self.ids.email.text
        password_check = self.ids.password_check.text
        if password != password_check:
            self.ids.password_check.error = True
            self.ids.password.error = True
            self.ids.password_check.md_bg_color = "red"

class example_login(MDApp):
    def build(self):
        return

my_app = example_login()
my_app.run()
```
## LAYOUT

```.kv
ScreenManager:
    LoginScreen:
        name:"LoginScreen"

    RegistrationScreen:
        name:"RegistrationScreen"

<LoginScreen>:
    FitImage:
        source:"download.jpeg"

    MDCard:
        size_hint: .6,.8
        pos_hint: {"center_x":.5, "center_y":.5}
        orientation: "vertical"

        MDLabel:
            size_hint: 1,.1
            font_style: "H2"
            text: "Login"
            halign: "center"

        MDTextField:
            id:uname
            hint_text: "enter username or email"
            size_hint:.8,.1
            pos_hint: {"center_x":.5}


        MDTextField:
            id:password
            hint_text: "enter password"
            password: True
            size_hint:.8,.1
            pos_hint:{"center_x":.5}

        MDBoxLayout:
            size_hint: 1,.2

            MDRaisedButton:
                id:login
                text:"login"
                md_bg_color: "a8dadc"
                on_press: root.try_login()
                size_hint:.5,.3

            MDRaisedButton:
                id:register
                text:"register"
                md_bg_color: "#e63946"
                on_press: root.parent.current="RegistrationScreen"
                size_hint:.5,.3

<RegistrationScreen>:
    FitImage:
        source:"download.jpeg"

    MDCard:
        size_hint: .6,.8
        pos_hint: {"center_x":.5, "center_y":.5}
        orientation: "vertical"

        MDLabel:
            size_hint: 1,.1
            font_style: "H4"
            text: "Register"
            halign: "center"

        MDTextField:
            id:uname
            hint_text: "enter username "
            size_hint:.8,.1
            pos_hint: {"center_x":.5}

        MDTextField:
            id:email
            hint_text: "enter email"
            size_hint:.8,.1
            pos_hint:{"center_x":.5}


        MDTextField:
            id:password_check
            hint_text: "enter password"
            password: True
            size_hint:.8,.1
            pos_hint:{"center_x":.5}

        MDTextField:
            id:password
            hint_text: "re- enter password"
            password: True
            size_hint:.8,.1
            pos_hint:{"center_x":.5}



        MDBoxLayout:
            size_hint: 1,.1

            MDRaisedButton:
                id:login
                text:"Back"
                md_bg_color: "a8dadc"
                on_press: root.parent.current="LoginScreen"
                size_hint:.5,.5

            MDRaisedButton:
                text:"register"
                md_bg_color: "#e63946"
                on_press: root.try_register()
                size_hint:.5,.5



```
## PROGRAM


https://user-images.githubusercontent.com/111819437/216994930-d0ac2152-83ea-445c-954f-6fac91024022.mov


