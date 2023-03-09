## Exercise
The goal of this exercise is to simulate a project consisting in developing a robot assistant which has many features, 
such as detecting persons, providing the temperature, recording cardiac frequency etc... And collaborate on its 
development using git. The development will be done in python for simplicity, as it's not a python lecture, feel free to
create methods that only print something. 

<u>Form groups of 3 or 4 people</u>

## 1 - Create a new git repository (locally and remotely on Github)
You can start by adding a README.md and a .gitignore file to your empty repository


## 2 - Let's build a task tracking board
> It can be done on github directly, which provide a very nice integration between task & branch
You can choose the task management application of you choice, you just need to check that it provide an integration with
github


It can be :

* Linear
* Asana
* Notion (it's not dedicated to task tracking but provides a nice board feature)

## 3 - Create your backlog
Add the following tasks to your board : 

* 1 - Implement a basic robot that say hello 
* 2 - Create a feature to give date & time  
* 3 - Allow robots to move : right/left/forward/backward
* 4 - Allow robots to detect obstacle
* 5 - Allow robots to record cardiac frequency
* 6 - Allow robots to record ambient temperature
* 7 - Integrate some slack or discord alerts when a branch is merged on main
* Bonus 1 Implement a more real code by adding camera / sensors class
* Bonus 2 Create some unit tests and automate the execution 


## 4 - Let's implement your robot

> You must create a branch foreach task, submit a pull request, review it with you pair and merge it
> Don't forget to link your pull request to the corresponding ticket

### 1 - Implement a basic robot that say hello


In a file ``robot.py``

```python
class Robot:
    def __init__(self, name):
        self.name = name
        
    def say_hello(self):
        print(f"hello, my name is {self.name}")
        
```

In your ``main.py``

```python
from robot import Robot


def start():
    robot = Robot(robot="my_robot_name")
    robot.say_hello()
    
    
if __name__ == '__main__':
    start()
```

### 2 - Create a feature to give date & time

In your file ``robot.py``

```python
from datetime import datetime

class Robot:
    def __init__(self, name):
        self.name = name
        
    def say_hello(self):
        print(f"hello, my name is {self.name}")
    
    @staticmethod
    def give_date_and_time(self):
        current_datetime = datetime.now()
        print(current_datetime)
        
```

**Don't forget** to call the method `robot.give_date_and_time()` from your `main.py`  

### 3 - It's your turn

Now let's implement all the feature described in your backlog.
As the aim is to simulate a real project (having conflicts etc...), you must develop task 3 & 4 in parallel, do the same for 5, 6 & 7


### Bonus 1
In a more realistic project, you will have other classes which implements some logic behind the feature added in 3 / 4 / 5 / 6 / 7.  
For any sensor, you'll have to configure the pins you're using in your wiring etc.

In our case, it can be something like :

* `CardiacFrequencySensor`
* `TemperatureSensor`
* `Camera`
* etc...


``` mermaid
classDiagram
  CardiacFrequencySensor "1" <-- "0..1" Robot:has
  Camera "1" <-- "0..1" Robot:has
  
  Robot : +String name
  Robot : +String phoneNumber
  Robot : +String emailAddress
  Robot: +say_hello()
  Robot: +give_date_and_time()
  Robot: +output_cardiac_frequency()
  
  class CardiacFrequencySensor{
    +int data_pin
    +int sample_frequency
    +read_value()  
  }
  
  class Camera {
    +int fps
    +int frame_width
    +int frame_height
    +read_frame()  
  }
```



### Bonus 2
Create a continuous integration pipeline using github action to automate test execution on pull request

Here is an example of a unit test in python: 

```python
import unittest
from code.my_calculations import Calculations


class TestCalculations(unittest.TestCase):

    def test_sum(self):
        calculation = Calculations(8, 2)
        self.assertEqual(calculation.get_sum(), 10, 'The sum is wrong.')

if __name__ == '__main__':
    unittest.main()

```