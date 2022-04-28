CRITERIA A : Planning

Problem Definition :

My client, Watchapol Aup, is a second-year high school student here at UWC ISAK Japan. Throughout his time at the school, living away from home and his parents, he quickly realized that he would need to make controlled decisions regarding his spending habits, as he would need to buy all his basic necessities with the allowance given from his parents on an irregular basis. This issue has proven itself to be very difficult to Aup as he would easily lose track of his spendings and quickly run out of money very quickly. In addition to this, as well as purchases in cash, the client makes many online purchases from international sites, especially from Thailand, his home country, meaning he gets easily confused in how much he is spending in JPY, the currency here in Japan. He is in need of a laptop application where he is able to easily view his current total balance combining both his cash and his card balance, be able to report his spending and earning statements, as well as to convert all spendings, earnings and balance into yen. A laptop application is most preferable for this, as it would keep his statements more secure and private through a sign-up and login system, rather than keeping a physical copy of them.

Success Criteria :

The application should have a registration system that registers users through inputted usernames and passwords.
The system should encrypt the password inputted and linked to the user to secure it.
The application should have a login system that identifies pre-existing users through data validation of inputted username and password.
The user can create new statement entries for their spendings on the ‘New Spending’ page in which they can log the following : The date, amount, currency, location, activity, and type of transaction.
If the date, amount and/or currency is missing when logging in a a new statement entry for spendings, it will not log it into the database and will show an invalid statement message to the user.
The user can create new statement entries for their earnings ‘New Earning’ page in which they can log the following : The date, amount, currency, reason, and type of transaction.
If the date, amount and/or currency is missing when logging in a a new statement entry for earnings, it will not log it into the database and will show an invalid statement message to the user.
The user can set their current balance manually when first using the application.
The user can see their current balance in either JPY or THB, as well as all their previous statements on a ‘statements and balance’ page.

Rationale for Proposed Solution :

For this project i will be using the Python language, as aswell as being one of the most known coding languages worldwide, it is the coding language i am most comfortable using overall in comparison to others. For the application interface I will be using KIvyMD, SQLite for the database system, and python 3.9 for function. KivyMD is a very accessible and simple way to create a simple GUI for the application, as it provides detailed online documentation on how to implement every element available. It also allows the application to run on a GUI screen rather than the python console, which gives much creative freedom and customizability. 
In addition to this, KivyMD has cross platform accessibility and support, opening the possibility of expanding to a mobile interface such as Android and IOS at later stages in development.
As for the database system, I will be using SQLite. The reason for this is because unlike many other database systems, it allows for easy compatibility with python and kivyMD. In addition to this, SQLite offers much online documentation and support similarly to kivyMD, which will support development especially when encountering bugs in the code. Likewise to kivyMD, it also has cross platform support, which means that expansion to mobile would be possible without sacrificing any components already being used.

CRITERIA B : Solution

System diagram :
UML diagram :
Wireframe :
ER Diagram :
Flow Diagrams:

Record of tasks:
| TASK No. | Planned Action                                                                    | Planned Outcome                                    | Time Estimate | Target Completion | Criteria |
|----------|-----------------------------------------------------------------------------------|----------------------------------------------------|---------------|-------------------|----------|
| 1        | First client meeting for project outline                                          | Outline of client demand/requirements for project  |               |                   | A        |
| 2        | Write out success criteria                                                        | List success criteria                              |               |                   | A        |
| 3        | Write out problem definition                                                      | Identify client and problem, needs and demands     |               |                   | A        |
| 4        | Meet with client to confirm success criteria                                      | Confirmation of demands from application           |               |                   | A        |
| 5        | Create wireframe diagram                                                          |                                                    |               |                   | B        |
| 6        | Create system diagram                                                             |                                                    |               |                   | B        |
| 7        | Create ER diagram                                                                 |                                                    |               |                   | B        |
| 8        | Create data table                                                                 |                                                    |               |                   | B        |
| 9        | Create UML diagram                                                                |                                                    |               |                   | B        |
| 10       | Start coding out login and registration system                                    |                                                    |               |                   | C        |
| 11       | User password encryption workings                                                 |                                                    |               |                   | C        |
| 12       | Start integrating database system for User registration and statement input       |                                                    |               |                   | C        |
| 13       | Main GUI menu coding                                                              |                                                    |               |                   | C        |
| 14       | Test ‘Spending’ and ‘Earnings’ page navigation                                    |                                                    |               |                   |          |
| 15       | Testing out database cooperation with GUI with Spending and Earnings pages so far |                                                    |               |                   | C        |
| 16       | Start ‘Statements’ screen and visuals                                             |                                                    |               |                   | C        |
| 17       | Testing statements recording and visualization on GUI                             |                                                    |               |                   | C        |
| 18       | Test overall navigation throughout application                                    |                                                    |               |                   | C        |
| 19       | Full test run of application as test user                                         |                                                    |               |                   | C        |
| 20       | Update client on progress and discuss GUI visuals                                 |                                                    |               |                   | A        |
| 21       | Work on GUI visuals                                                               |                                                    |               |                   |  C       |
| 22       | Test currency conversion and editing of past statements                           |                                                    |               |                   | C        |
| 23       | Final test run of application as test user                                        |                                                    |               |                   | C        |
| 24       | Final meeting with client for approval of product                                 |                                                    |               |                   | A        |
| 25       | Record test video                                                                 |                                                    |               |                   | D        |
| 26       | Complete documentation and submission                                             |                                                    |               |                   | B        |

CRITERIA C : Development

Techniques used :
If function
While function
For loops
KivyMD Library - UI/GUI building
SQLite - database building
Datetime

Python code :
```.p

Window.size = (500, 500)

pwd_context = CryptContext(
    schemes=["pbkdf2_sha256"],
    default = 'pbkdf2_sha256',
    pbkdf2_sha256__default_rounds=3000)

class login(MDApp):
    def build(self):
        return

def encrypt_password(password):
    return pwd_context.hash(password)
# function to check if a password is correct

def check_password(password, hashed):
    return pwd_context.verify(password, hashed)

class database:

    def __init__(self, name):
        self.name = name
        self.connection = sqlite3.connect(self.name)
        self.cursor = self.connection.cursor()

    def close(self):
        self.connection.close()

    def create(self):
        self.cursor.execute("""CREATE TABLE if not exists Users(
            id INTEGER primary key,
            username VARCHAR(200) not null,
            password VARCHAR(256) not null
        );
        """)
        print("dekita")
        self.cursor.execute("""
        CREATE TABLE if not exists Spending(
            date INTEGER not null,
            amount INTEGER not null,
            currency VARCHAR(250) not null,
            location VARCHAR(250),
            activity VARCHAR(250),
            type VARCHAR (250)
        );
        """)
        self.cursor.execute("""
        CREATE TABLE if not exists Income(
            date INTEGER not null,
            amount INTEGER not null,
            currency VARCHAR(250) not null,
            location VARCHAR(250),
            reason VARCHAR(250),
            type VARCHAR (250)
        );
        """)

        self.cursor.execute("""
        CREATE TABLE if not exists Total(
            current_balace INTEGER,
            total_spending INTEGER,
            total_income INTEGER
        );
        """)
        self.connection.commit()

    def create_new_spending_input(self, date, amount, currency, location, activity, type):
        print(date,amount)
        self.cursor.execute("INSERT into Spending values (?,?,?,?,?,?)",(date,amount,currency,location,activity,type))
        self.connection.commit()

    def create_new_income_input(self, date, amount, currency, location, reason, type):
        self.cursor.execute(
            f"INSERT into Spending values('{date}','{location}','{amount}','{currency}','{reason}','{type}');")
        self.connection.commit()

    def create_new_user(self, username, password):
        print(username, password)
        self.cursor.execute("INSERT into Users values(?,?,?)",(random.randint(1, 1000000), username, encrypt_password(password)))
        self.connection.commit()

#class HomePage(MDScreen):

    #def go_to_LoginApp(self):
    #    self.parent.current = "LoginApp"
    #def go_to_RegisterScreen(self):
    #    self.parent.current="RegisterScreen"

class MenuPage(MDScreen):

    def go_to_SpendingEntry(self):
        self.parent.current="SpendingEntry"

    def go_to_IncomeEntry(self):
        self.parent.current="IncomeEntry"

    pass

class LoginApp(MDScreen):
    dialog = None

    #def build(self):
    #    self.theme_cls.theme_style = "Light"
    #    self.theme_cls.primary_palette = "BlueGray"
    #    return Builder.load_file('login.kv')


    def login(self):
        # user and pass check
        print("logging in")
        input_user = self.ids.user.text
        input_password = self.ids.password.text
        print(input_user,input_password)
        db = database("register.db")
        user=db.query_Users(username=input_user)
        if user:
            id,username,hashed_pwd = input_user
            if check_password(password=input_password, hashed= hashed_pwd):
                    self.dialog = MDDialog(
                        title="Log in",
                        text=f"Welcome {self.root.ids.user.text}!",
                        buttons=[
                            MDFlatButton(
                                text="OK", on_release=self.closed
                            )
                        ]
                    )

            else :
                # failed login
                self.dialog = MDDialog(
                    title="Log in failed",
                    text=f"die {self.root.ids.user.text}!",
                    buttons=[
                        MDFlatButton(
                            text="OK", on_release=self.closed
                        )
                    ]
                )
                self.dialog.open()



    def closed(self, instance):
        self.dialog.dismiss()

    def go_to_RegisterScreen(self):
       self.parent.current="RegisterScreen"

    def go_to_LoginApp(self):
        self.parent.current="LoginApp"

    def go_to_MenuPage(self):
        self.parent.current="MenuPage"


class RegisterScreen(MDScreen):
    dialog = None

    #def build(self):
     #3  self.theme_cls.primary_palette = "BlueGray"
       # return Builder.load_file('login.kv')

    def register(self):
        print("I gave up -Anju")
        username_i = self.ids.signup_username.text
        password_i = self.ids.signup_password.text
        #print(username_i, password_i)
        db = database("register.db")
        db.create_new_user(username=username_i, password=password_i)
        db.close()

    def go_to_RegisterScreen(self):
        self.parent.current = "RegisterScreen"

    def go_to_LoginApp(self):
        self.parent.current = "LoginApp"

    def go_to_MenuPage(self):
        self.parent.current="MenuPage"


class SpendingEntry(MDScreen):

    def go_to_MenuPage(self):
        self.parent.current = "MenuPage"

class IncomeEntry(MDScreen):

    def go_to_MenuPage(self):
        self.parent.current = "MenuPage"


db=database("register.db")
db.create()
db.close()

m=login()
m.run()
```
Kivy code:
```.p
ScreenManager:
    id: screen_manager

    LoginApp:
        id: loginscreen
        name :"LoginApp"

    RegisterScreen:
        id: RegisterScreen
        name:"RegisterScreen"

    MenuPage:
        id:MenuPage
        name:"MenuPage"

    SpendingEntry:
        id:SpendingEntry
        name:"SpendingEntry"

    IncomeEntry:
        id:IncomeEntry
        name:"IncomeEntry"

<LoginApp>
    MDCard:
        size_hint: None, None
        size: 300, 400
        pos_hint: {"center_x": 0.5, "center_y": 0.5}
        elevation: 10
        padding: 25
        spacing: 25
        orientation: 'vertical'

        MDLabel:
            id: welcome_label
            text: "WELCOME"
            font_size: 40
            halign: 'center'
            size_hint_y: None
            height: self.texture_size[1]
            padding_y: 15

        MDTextFieldRound:
            id: user
            hint_text: "username"
            icon_right: "account"
            size_hint_x: None
            width: 200
            font_size: 18
            pos_hint: {"center_x": 0.5}

        MDTextFieldRound:
            id: password
            hint_text: "password"
            icon_right: "eye-off"
            size_hint_x: None
            width: 200
            font_size: 18
            pos_hint: {"center_x": 0.5}
            password: True

        MDRoundFlatButton:
            text: "LOG IN"
            font_size: 12
            pos_hint: {"center_x": 0.5}
            on_press: root.login()

        MDRoundFlatButton:
            text: "SIGN UP"
            font_size: 12
            pos_hint: {"center_x": 0.5}
            on_press: root.go_to_RegisterScreen()

        MDRoundFlatButton:
            text: "USE AS GUEST"
            font_size: 12
            pos_hint: {"center_x": 0.5}
            on_press: root.go_to_MenuPage()

        #MDRoundFlatButton:
            #text: "CLEAR"
            #font_size: 12
            #pos_hint: {"center_x": 0.5}
            #on_press: app.clear()

        Widget:
            size_hint_y: None
            height: 10

<RegisterScreen>
    MDCard:
        size_hint: None, None
        size: 300, 400
        pos_hint: {"center_x": 0.5, "center_y": 0.5}
        elevation: 10
        padding: 25
        spacing: 25
        orientation: 'vertical'

        MDLabel:
            id: welcome_label
            text: "WELCOME"
            font_size: 40
            halign: 'center'
            size_hint_y: None
            height: self.texture_size[1]
            padding_y: 15

        MDTextFieldRound:
            id: signup_username
            hint_text: "username"
            icon_right: "account"
            size_hint_x: None
            width: 200
            font_size: 18
            pos_hint: {"center_x": 0.5}

        MDTextFieldRound:
            id: signup_password
            hint_text: "Password"
            icon_right: "eye-off"
            size_hint_x: None
            width: 200
            font_size: 18
            pos_hint: {"center_x": 0.5}
            password: True

        MDRoundFlatButton:
            text: "SIGN UP"
            font_size: 12
            pos_hint: {"center_x": 0.5}
            on_press: root.register()

        MDRoundFlatButton:
            text: "BACK TO LOG IN"
            font_size: 12
            pos_hint: {"center_x": 0.5}
            on_press: root.go_to_LoginApp()

        #MDRoundFlatButton:
            #text: "CLEAR"
            #font_size: 12
            #pos_hint: {"center_x": 0.5}
            #on_press: app.clear()

        Widget:
            size_hint_y: None
            height: 10

<MenuPage>:
    MDCard:
        size_hint: None, None
        size: 900, 600
        pos_hint: {"center_x": 0.5, "center_y": 0.5}
        elevation: 10
        padding: 25
        spacing: 25
        orientation: 'vertical'

        MDRoundFlatButton:
            text: "ENTER NEW SPENDINGS"
            font_size: 26
            pos_hint: {-3.5:"center_y"}
            on_press: root.go_to_SpendingEntry()

        MDRoundFlatButton:
            text: "ENTER NEW INCOME"
            font_size: 26
            pos_hint: {-3.5:"center_y"}
            on_press: root.go_to_IncomeEntry()

<SpendingEntry>:
    MDCard:
        size_hint: None, None
        size: 900, 600
        pos_hint: {"center_x": 0.5, "center_y": 0.5}
        elevation: 10
        padding: 25
        spacing: 25
        orientation: 'vertical'

        MDRoundFlatButton:
            text: "BACK TO MENU"
            font_size: 12
            pos_hint: {-3.5: "center_y"}
            on_press: root.go_to_MenuPage()

<IncomeEntry>:
    MDCard:
        size_hint: None, None
        size: 900, 600
        pos_hint: {"center_x": 0.5, "center_y": 0.5}
        elevation: 10
        padding: 25
        spacing: 25
        orientation: 'vertical'

        MDRoundFlatButton:
            text: "BACK TO MENU"
            font_size: 12
            pos_hint: {-3.5: "center_y"}
            on_press: root.go_to_MenuPage()
```
