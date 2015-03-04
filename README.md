js-interview
============
A list of questions that I have asked throughout the process of learning js.

# Constructors

## new

What does `new` do?

### Question:

What does `new` do in the following example.

```js
var Vehicle = function Vehicle() {
  // ...
}
var vehicle = new Vehicle();
```
### Answer : 

When `new Vehicle()` is called, JavaScript does four things:

1. It creates a new object.
2. It sets the `constructor` property of the object to `Vehicle`.
3. It sets up the object to delegate to `Vehicle.prototype`.
4. It calls `Vehicle()` in the context of the new object.

---

### Question:

Will  `new Date` run without throwing a runtime exception?

### Answer:

Yes

#### Follow up Question:
Is there a functional difference the following two statements?
```javascript
var date1 = new Date;
var date2 = new Date();
```

#### Follow up Answer:
No

---

### Question:

What is the value of `this` when invoking `privateBirthday` while initializing `daniel`?

```javascript
function Person(age, name)
{

	this.age  = age;
	this.name = name;

	privateBirthday();
	this.birthday();
}

Person.prototype.birthday = birthday;

function birthday()
{
	this.age++;
}

function privateBirthday()
{
	this.age++;
}

var daniel = new Person(24, 'Daniel');
```

### Answer:

`window`

#### Follow up Question:

#### Follow up Answer:

#Operators
## Precedence

### Question:
Given the following snippet of code, what is the value of `url` once the code has finished running?
```
var flag = true;

url = '/root/server/system';
url += '/endpoint/' + flag ? 'true' : 'false';
```
### Answer:

`/root/server/systemtrue`

#### Follow up Question:

How would you fix this code to work as you would initially expect it to? Why does this fix the problem? Alternatively you could answer why the problem was happening.

#### Follow up Answer:

```
var flag = true;

url = '/root/server/system';
url += '/endpoint/' + (flag ? 'true' : 'false';)
```

# Mind Benders

## Syntax 

### Question :

Write out the expected console.log.

```js
(function(arg1)
 {
  console.log("func1");
     
     return function(arg)
     {
         console.log('func3');
         console.log(arg);
     }
 })()

(function nextFunc()
{
   console.log('func2'); 
})();
```

### Answer :

```
2015-03-04 11:03:34.469 (index):24 func1
2015-03-04 11:03:34.469 (index):28 func3
2015-03-04 11:03:34.469 (index):29 function nextFunc(){ console.log('func2'); }
2015-03-04 11:03:34.469 (index):34 Uncaught TypeError: (intermediate value)(intermediate value)(...)(...) is not a function
```

### Why :

Whitespace

```js
(function(arg1)
 {
  console.log("func1");
     
     return function(arg)
     {
         console.log('func3');
         console.log(arg);
     }
 })()

(function nextFunc()
{
   console.log('func2'); 
})();
```
After func1 is invoked.
```js
function(arg)
{
 console.log('func3');
 console.log(arg);
}(function nextFunc(){console.log('func2'); })();
```

After func3 is invoked 
```js
// implicitly return so undefined is left
undefined();
```

