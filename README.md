js-interview
============
A list of questions that I have asked throughout the process of learning js.

# Constructors
## new

What does `new` do?

# Question:

What does `new` do in the following example.

```js
var Vehicle = function Vehicle() {
  // ...
}
var vehicle = new Vehicle();
```
# Answer : 

When new Vehicle() is called, JavaScript does four things:

1. It creates a new object.
2. It sets the constructor property of the object to Vehicle.
3. It sets up the object to delegate to Vehicle.prototype.
4. It calls Vehicle() in the context of the new object.

##Question:
Will  `new Date` run without throwing a runtime exception?
## Answer:
Yes

