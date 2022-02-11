```.py
class Employee:
    def __init__(self,name:str,email:str,age:int,salary:int,position:str):
        self.name=name
        self.age=age
        self.salary= salary
        self.position= position
        self.email=email

    def __repr__(self):
        return f"Hello {self.name.title()},you are {self.age} years old and work as a {self.position} in our company. "\
            f"Your email address is {self.email}"

    def get_greeting(self)->str:
        msg=f"Hello {self.name.title()},you are {self.age} years old and work as a {self.position} in our company. "\
            f"Your email address is {self.email}"
        return msg
    def get_salary(self)->str:
        return f"Salary for {self.name.title()} is currently {self.salary} USD"
    def set_salary(self,new_value:int):
        self.salary=new_value

class Manager(Employee):
    def get_bonus(self):
        return 1.1*self.salary
    def get_salary(self):
        #this salary method is overwriting the parent method from Employee
        return f"New set salary for {self.name.title()} is {self.get_bonus()} USD"

Emp_9=Employee(name="jow biden",email="jow.biden@company.xy",position="President", age=79, salary=4000000)

print(Emp_9.get_greeting())
print(Emp_9)
print(Emp_9.get_salary())
Emp_9.set_salary(50000)
print(Emp_9.get_salary())
print(Emp_9.get_greeting())
```
