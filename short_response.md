# Short Responses

For this short response assignment, aim to write a response with the following qualities (your instructor will give you feedback on these areas):

- [ ] Addresses all parts of the prompt
- [ ] Accurately uses relevant technical terminology
- [ ] Is free of grammar and spelling mistakes (double check with Grammarly!)
- [ ] Uses markdown to enhance readability (preview in VS Code with Command/Control + Shift + V)
- [ ] Is easy to comprehend

Write your response in the space provided. Make sure to preview your markdown to check how it is rendered before submitting.

## Question 1

Fulton Street Post is a neighborhood shipping counter. It ships three kinds of package: letters, parcels, and freight. Each kind has its own price and its own delivery time.

Here are two versions of the code that prints the day's packages. In Version 1, two functions decide each package's price and delivery time by checking which class the package belongs to:

```py
# Version 1
class Package:
    def __init__(self, tracking, weight):
        self.tracking = tracking
        self.weight = weight


class Letter(Package):
    pass


class Parcel(Package):
    pass


class Freight(Package):
    pass


def shipping_cost(package):
    if isinstance(package, Letter):
        return 1
    elif isinstance(package, Parcel):
        return 4 + package.weight
    elif isinstance(package, Freight):
        return 30 + package.weight // 10


def delivery_days(package):
    if isinstance(package, Letter):
        return 5
    elif isinstance(package, Parcel):
        return 3
    elif isinstance(package, Freight):
        return 7


packages = [Letter('L1', weight=0), Parcel('P1', weight=6), Freight('F1', weight=120)]
for package in packages:
    print(f'{package.tracking}: ${shipping_cost(package)}, {delivery_days(package)} days')
# L1: $1, 5 days
# P1: $10, 3 days
# F1: $42, 7 days
```

In Version 2, each class defines its own `cost()` and `days()` methods, and the loop calls them:

```py
# Version 2
class Package:
    def __init__(self, tracking, weight):
        self.tracking = tracking
        self.weight = weight


class Letter(Package):
    def cost(self):
        return 1

    def days(self):
        return 5


class Parcel(Package):
    def cost(self):
        return 4 + self.weight

    def days(self):
        return 3


class Freight(Package):
    def cost(self):
        return 30 + self.weight // 10

    def days(self):
        return 7


packages = [Letter('L1', weight=0), Parcel('P1', weight=6), Freight('F1', weight=120)]
for package in packages:
    print(f'{package.tracking}: ${package.cost()}, {package.days()} days')
# L1: $1, 5 days
# P1: $10, 3 days
# F1: $42, 7 days
```

Fulton Street Post starts shipping a fourth kind of package, poster tubes, which cost $6 and take 4 days to deliver. In Version 1, a programmer adds this class but forgets to change either function:

```py
class Tube(Package):
    pass


packages.append(Tube('T1', weight=1))
```

Predict the line that Version 1's loop prints for the tube when it is added to the `packages` list, and explain why Python raises no error. Then say what the programmer would write to add tubes to Version 2, and which existing lines of Version 2 would have to change. Finally, define **polymorphism** in one sentence that names what the loop in Version 2 does not need to know about each package.

### Your Response

[Write your response here]

## Question 2

A partner company, Hudson Couriers, has its own software for the crates they carry and its developers created the class `HudsonCrate` which does not inherit from `Package` (see Question 1):

```py
class HudsonCrate:
    def __init__(self, crate_number, weight):
        self.tracking = f'HC-{crate_number}'
        self.weight = weight

    def cost(self):
        return 18
```

Hudson Couriers and Fulton Street Post are now working together to manage deliveries. Assuming at Fulton Street Post uses the Version 2 classes from question 1, the function below, `print_manifest`, is used to print out information about all of the packages shared by both companies

```py
def print_manifest(packages):
    for package in packages:
        print(f'{package.tracking}: ${package.cost()}, {package.days()} days')


shared_packages = [Letter('L1', weight=0), HudsonCrate(552, weight=40), Parcel('P1', weight=6)]
print_manifest(shared_packages)
```

List the **contract** that `print_manifest()` depends on: every attribute and method it uses on each package. Then predict what the call prints, line by line, and explain where it stops and why. Use the term **duck typing** in your response. Then, explain how this could be avoided with an **abstract base class**.

### Your Response

[Write your response here]

## Question 3

The code below defines four functions. One of them, `greet`, is defined inside `make_greeter`.

```py
def shout(text):
    return text.upper() + '!'


def apply_to_each(func, items):
    results = []
    for item in items:
        results.append(func(item))
    return results


def make_greeter(greeting):
    def greet(name):
        return f'{greeting}, {name}'
    return greet


print(apply_to_each(shout, ['hello', 'bye']))   # ['HELLO!', 'BYE!']

say_hi = make_greeter('Hi')
say_bye = make_greeter('Goodbye')
print(say_hi('Ana'))    # Hi, Ana
print(say_hi('Bob'))    # Hi, Bob
print(say_bye('Ana'))   # Goodbye, Ana
```

For each of `shout`, `apply_to_each`, `make_greeter`, and `greet`, say whether it is a **higher-order function**, and if it is, what makes it a higher-order function.

By the time `say_hi('Ana')` runs, `make_greeter('Hi')` has already returned. Explain how `greet` can still use `greeting`, and why `say_hi` and `say_bye` print different greetings. Use the term **closure** in your response.

### Your Response

[Write your response here]
