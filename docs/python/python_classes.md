# Python Classes

## Basic Python Class
The below is a basic format for a Python class: 

```py linenums="1" title="python_classes_example.py"
class Inventory:    #class name starts with capital
    def __init__(self, type, color, origin, unit_cost):
        self.type = type
        self.color = color
        self.origin = origin
        self.unit_cost = unit_cost


item1 = Inventory("Apple", "green", "USA", 1.44)

print("for item1, we have the following details:")
print(f"type      => {item1.type}")
print(f"color     => {item1.color}")
print(f"origin    => {item1.origin}")
print(f"unit cost => {item1.unit_cost}")
```
