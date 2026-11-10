# Short Responses

For this short response assignment, aim to write a response with the following
qualities (your instructor will give you feedback on these areas):

- [ ] Addresses all parts of the prompt
- [ ] Accurately uses relevant technical terminology
- [ ] Is free of grammar and spelling mistakes (double check with Grammarly!)
- [ ] Uses markdown to enhance readability (preview in VS Code with
      Command/Control + Shift + V)
- [ ] Is easy to comprehend

Write your response in the space provided. Make sure to preview your markdown
to check how it is rendered before submitting.

## Question 1

`len()` works on a string, a list, and a dictionary. A `for` loop runs over all
three. None of them share an ancestor you wrote, and `len()` has no branch per
type.

Here is the same idea in Boro Bikes code:

```py
def fleet_revenue(bikes, hours):
    return sum(bike.hourly_rate() * hours for bike in bikes)

fleet = [ClassicBike("A1", "Grand Army", False),
         ElectricBike("E9", "Borough Hall", False, 24),
         Scooter("S1", 80, False)]
```

`Scooter` does not inherit from `Bike`. The loop works anyway.

**First**, define polymorphism in one sentence. The sentence has to name what
the **caller** gains, not what the classes do — the benefit belongs to
`fleet_revenue`, which is the code that got simpler.

**Second**, write down the contract this list depends on: every method name
each element must answer for `fleet_revenue` and the rental screen
(`is_rentable()`) to work. A list of names is enough.

**Third**, answer this. Nothing in the code above says that `Scooter` has to
keep answering `hourly_rate()`. Somebody could rename it tomorrow and no test
in `Scooter`'s own file would fail. Say where that rename would surface, and how
long it might take to notice.

### Your Response

[Write your response here]

## Question 2

Boro Bikes rents bikes, scooters and helmets. All three answer `is_rentable()`
and `hourly_rate()`. Two engineers disagree about how to hold that agreement in
place.

**Ama** wants an abstract base class:

```py
class Rentable(ABC):
    @abstractmethod
    def is_rentable(self): pass

    @abstractmethod
    def hourly_rate(self): pass
```

Every rentable thing inherits it, and Python refuses to build a class that
leaves a method out.

**Ben** wants the contract written in the docstring of the revenue report, and
no base class. Any object answering those two names works, whoever wrote it.

Pick one for this system and defend it. Your answer has to do three things:

1. Name the case where **Ama's** choice fails or costs more than it is worth.
   There is a real one: think about an object Boro Bikes does not own, such as a
   class from a library or a partner's API.
2. Name the case where **Ben's** choice fails. Think about who finds out, and
   when.
3. Say which you would ship, for **this** system, and what fact about Boro
   Bikes decided it.

There is no answer we are looking for. Both are used in real systems, and the
reasoning is the whole question. An answer that says one is simply better
without naming what it costs is not finished.

### Your Response

[Write your response here]

## Question 3

This question asks you to **write test code**, not prose.

An abstract base class is only worth having if it actually refuses. Here is one:

```py
from abc import ABC, abstractmethod

class Rentable(ABC):
    @abstractmethod
    def is_rentable(self): pass

    @abstractmethod
    def hourly_rate(self): pass
```

Write **one** test that proves a subclass leaving out `hourly_rate()` cannot be
instantiated. Use `pytest.raises(TypeError)`. Define the incomplete subclass
inside the test — a class defined in a function is still a class.

Use `src/playground.py` in the code repo to run it, then paste it here.

Then answer two things about it:

1. **What does this test catch?** Name the change someone could make to
   `Rentable` that would still pass every other test in the suite and fail this
   one.
2. **Where would the failure appear without the abstract base class?** The
   incomplete class would be built happily. Say which line raises instead, and
   why that is a worse place to find out.

The second part is the point. A test on a refusal is worth writing when it moves
a failure from somewhere confusing to somewhere obvious, and you should be able
to say which two places those are.

### Your Response

[Write your response here]

## Question 4

A **higher-order function** meets at least one of two conditions: it **takes** a
function as an argument, or it **returns** a function.

**First**, define a higher-order function in one sentence of your own.

**Second**, here are four pieces of code. For each one, say whether it is
higher-order, and if it is, **which of the two conditions** it meets. If it is
not, say why not.

```py
# A
sorted(bikes, key=lambda bike: bike.hourly_rate())

# B
station.bikes_where(is_cheap)

# C
sum(bike.hourly_rate() for bike in bikes)

# D
message_if(station, station.is_low, "send bikes")
```

One of these is not higher-order, and the reason is worth getting precise. It
runs an expression once per item, which looks like the others but is not the
same thing as being handed a function.

**Third**, in **D**, `station.is_low` is written with no parentheses. Say what
would be passed instead if it had them, and what error would follow — name the
type in the error message.

### Your Response

[Write your response here]

