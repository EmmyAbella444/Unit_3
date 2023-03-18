
# QUIZ 041

## CODE
```.py
from kivymd.app import MDApp               # import the MDApp class from the kivymd package
from kivy.uix.boxlayout import BoxLayout   # import the BoxLayout class from the kivy package
from kivy.properties import StringProperty # import the StringProperty class from the kivy package
from kivy.clock import Clock               # import the Clock class from the kivy package
from kivymd.uix.dialog import MDDialog      # import the MDDialog class from the kivymd package
from kivymd.uix.button import MDFlatButton # import the MDFlatButton class from the kivymd package

# Create a new class called TicTacToe that extends the BoxLayout class
class TicTacToe(BoxLayout):
    
    # Define a StringProperty called title with a default value of "Tic Tac Toe"
    title = StringProperty("Tic Tac Toe")
    
    # Define a StringProperty called current_player with a default value of "X"
    current_player = StringProperty("X")

    # Define an __init__ method that calls the reset_game() method
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.reset_game()

    # Define a method called reset_game that resets the game board and sets the current player to "X"
    def reset_game(self, *args, **kwargs):
        self.board = [[None, None, None], [None, None, None], [None, None, None]]
        self.current_player = "X"
        for i in range(3):
            for j in range(3):
                button = self.ids["b{}{}".format(i, j)]
                button.text = ""

    # Define a method called button_pressed that handles when a button is pressed
    def button_pressed(self, row, col):
        if self.board[row][col] is not None:
            return
        button = self.ids["b{}{}".format(row, col)]
        button.text = self.current_player
        self.board[row][col] = self.current_player
        if self.check_win():
            self.show_win_dialog()
            return
        if self.check_draw():
            self.show_draw_dialog()
            return
        self.current_player = "O" if self.current_player == "X" else "X"

    # Define a method called check_win that checks if there is a winner on the board
    def check_win(self):
        for i in range(3):
            if self.board[i][0] == self.board[i][1] == self.board[i][2] != None:
                return True
            if self.board[0][i] == self.board[1][i] == self.board[2][i] != None:
                return True
        if self.board[0][0] == self.board[1][1] == self.board[2][2] != None:
            return True
        if self.board[0][2] == self.board[1][1] == self.board[2][0] != None:
            return True
        return False

    # Define a method called check_draw that checks if there is a draw on the board
    def check_draw(self):
        for i in range(3):
            for j in range(3):
                if self.board[i][j] is None:
                    return False
        return True

    # Define a method called show_win_dialog that shows a dialog box when a player wins
   dialog = MDDialog(
            title="{} wins!".format(self.current_player),
            buttons=[MDFlatButton(text="Restart", on_release=self.reset_game)]
        )
        dialog.open()
    # Define a method called show_draw_dialogthat shows a dialog box when it is a draw
    def show_draw_dialog(self):
        dialog = MDDialog(
            title="Draw!",
            buttons=[MDFlatButton(text="Restart", on_release=self.reset_game)]
        )
        dialog.open()


class TicTacToeApp(MDApp):
    def build(self):
        return TicTacToe()


if __name__ == '__main__':
    TicTacToeApp().run()

            
           
```

```.kv
<TicTacToe>:
    title: "Tic Tac Toe by Emmy"
    BoxLayout:
        orientation: "vertical"
        Label:
            text: root.title
            color:"#0d050c"
            font_size: 32

        Label:
            id: current_player_label
            text: "It is {} turn !".format(root.current_player if hasattr(root, 'current_player') else 'unknown')
            color:"#0d050c"
            font_size: 24


        MDBoxLayout:
            orientation: "horizontal"
            spacing: 10
            Button:
                id: b00
                text: ""
                font_size: 50
                background_color:"#d11fc3"
                on_press: root.button_pressed(0, 0)
            Button:
                id: b01
                text: ""
                font_size: 50
                on_press: root.button_pressed(0, 1)
                background_color:"#d11fc3"
            Button:
                id: b02
                text: ""
                font_size: 50
                on_press: root.button_pressed(0, 2)
                background_color:"#d11fc3"
        MDBoxLayout:
            orientation: "horizontal"
            spacing: 10
            Button:
                id: b10
                text: ""
                font_size: 50
                on_press: root.button_pressed(1, 0)
                background_color:"#d11fc3"
            Button:
                id: b11
                text: ""
                font_size: 50
                on_press: root.button_pressed(1, 1)
                background_color:"#d11fc3"
            Button:
                id: b12
                text: ""
                font_size: 50
                on_press: root.button_pressed(1, 2)
                background_color:"#d11fc3"
        MDBoxLayout:
            orientation: "horizontal"
            spacing: 10
            Button:
                id: b20
                text: ""
                font_size: 50
                on_press: root.button_pressed(2, 0)
                background_color:"#d11fc3"
            Button:
                id: b21
                text: ""
                font_size: 50
                on_press: root.button_pressed(2, 1)
                background_color:"#d11fc3"
            Button:
                id: b22
                text: ""
                font_size: 50
                on_press: root.button_pressed(2, 2)
                background_color:"#d11fc3"

```

## EVIDENCE

https://user-images.githubusercontent.com/111819437/226081097-787886ad-38db-408b-ba33-77aecf8a8ed5.mov

