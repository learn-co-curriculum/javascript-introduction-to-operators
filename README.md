Introduction to Operators in JavaScript
---

## Objectives

- Explain the difference between unary, binary, and ternary operators
- Use comparison operators to evaluate boolean expressions
- Use arithmetic operators to evaluate mathematical expressions

## Hello, operator

Operators are characters in JavaScript that perform special functions. You can get the lowdown from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators), but we'll go over the important bits here.

## One, Two, Three

JavaScript operators come in three flavors: unary operators, which operate on _one_ item; binary operators, which operate on _two_ items; and a special ternary operator, which operates (you guessed it) on _three_ items.

## The Assignment Operator

The basic assignment operator, `=`, is a binary operator that gives the _left side_ of `=` the value of the right side of `=`.

It works _kind of_ like good old `=` that you learned about in elementary-school math class, but it does not actually _assert_ anything about the equality of the two sides of `=` — it merely makes their values match. For example:

``` javascript
x = 2;
y = 3;

x = y;

console.log(x);
```

We just used `=` three times to assign assign values. First, we assign the variable `x` the value `2`; then we do the same with `y` and `3`. Finally, we assign to `x` the current value of `y`.

Pretty straightforward, right? Keep in mind that just because at the end of this example, we could say that "x equals y," the `=` operator doesn't know or care about any of that. It just assigns the value of `y` to `x`.

## Arithmetic Operators

JavaScript supports the standard arithmetic operators that you learned about in math class (`+` for addition, `-` for subtraction, `*` for multiplication, and `/` for division) as well as the [_modulo operator_](https://en.wikipedia.org/wiki/Modulo_operation), `%`, which gives the remainder of its left-hand side divided by its right-hand side; along with a few handy (but intuitive) unary operators.

Follow along in your console with the code below:

``` javascript
1 + 2  // 3
2 - 4  // -2
2 * 8  // 16
10 / 5 // 2
10 % 2 // 0
10 % 9 // 1

// Now we're going to get a little fancy

x = 1 // 1
x++   // `++` is the unary increment operator
x     // 2
x--   // `--` is the unary decrement operator
x     // 1

-x // -1 (`-` here is the unary negation operator)
x  // 1 (note that `-` doesn't cause a persistent change to the value of x

+"3"   // 3 (`+` here is the unary plus operator
       // it attempts to convert its operand into a number)
+true  // 1
+"foo" // NaN
```

### Compound Assignment Operators

Now that you know about the assignment operator and the arithmetic operators, we can explore _compound assignment operators_. For example, in JavaScript, the following expression is valid:

``` javascript
x = 2

x += 3

x // 5
```

You can think of `x += 3` as shorthand for `x = x + 3`. The other arithmetic operators can be combined with the assignment operator in similar fashion:

``` javascript
x = 2

x += 3 // 5
x -= 2 // 3  (just like `x = x - 2`)
x *= 4 // 12 (just like `x = x * 4`)
x /= 3 // 4  (just like `x = x / 3`)
x %= 3 // 1  (just like `x = x % 3`)
```

### Comparison Operators

Comparison operators are used, as their name suggests, to compare two items.

Remember when we said that `=` doesn't assert anything about the equality of its operands? That's because JavaScript leaves that assertion to `==`, which returns `true` if its operands are equal.

``` javascript
1 == 1 // true
1 == 2 // false
"1" == 1 // true (!?)
```

Did you catch that weirdness at the end? JavaScript thinks that the _string_ `"1"` is equal to the number `1`?

That's because we're using the loose equality operator, which attempts to _coerce_ both operands to a common type. You can read more about that process (it's a bit complicated) on [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness).

The upshot of this is that we almost always want to use the strict equality operator, `===`:

``` javascript
"1" === 1 // false
```

There we go.

JavaScript also has an inequality operator, `!=`, and a strict version of the same, `!==`. Again, you should almost always use the strict version:

``` javascript
1 !== 1 // false
1 !== 2 // true
```

Finally, JavaScript provides comparison operators for greater than (`>`), greater than or equal (`>=`), less than (`<`), and less than or equal (`<=`). Note that the order of the greater- or less-than character and the equals sign matters: `=<` is not a comparison operator, and `=>` is not only _not_ comparison operator but has another use entirely (it's used in [arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)).

### Logical Operators

Generally, we use logical operators (`||`, `&&`, and `!`) with boolean operands (`true` or `false`), and in these cases the logical operators return boolean values. However, logical operators actually return the value of one of their operands — so they might return non-boolean values.

`&&` is the logical AND operator. It returns its left-hand side if that side evaluates to `false` (that is, if that side is "falsey"); otherwise, it returns its right-hand side.

``` javascript
true && true  // true
true && false // false
true && 1     // 1
true && 0     // 0

false && true // false
false && 1    // false
false && 0    // false

1 && "foo"     // "foo"
"foo" && "bar" // "bar"
"" && "bar"    // ""
```

`||` is the logical OR operator. It returns its left-hand side if that side evaluates to `true` (that is, if that side is "truthy"); otherwise, it returns its right-hand side.

``` javascript
true || true // true

false || true // true

0 || 1 // 1

0 || "foo" // "foo
1 || "foo" // 1
```

`!` is the logical NOT operator. It's a unary operator that returns `false` if its operand is truthy, and `true` if its operand is falsey.

``` javascript
!true // false

!false // true

!1 // false
!0 // true

!"" // true

!"foo" // false
```

### String Operators

Operators in JavaScript aren't limited to numbers and booleans. We can use `+` and `+=` to concatenate (join together) strings, too.

``` javascript
"Flat" + "iron" // "Flatiron"

x = "water"

x += "melon"

x // "watermelon"
```

### JavaScript's Solitary Ternary Operator

JavaScript's ternary operator, `?:`, can be a bit hard to grasp at first. It looks at the expression to the left of `?`; if that expression is truthy, it returns the expression to the left of `:`; otherwise, it returns the expression to the left of `:`.

``` javascript
1 ? "hey!" : "yo!" // "hey!"
0 ? "hey!" : "yo!" // "yo!"

1 === 2 ? "Math is broken" : "Math works!" // "Math works!"
1 === 1 ? "1 is 1" : "1 is not 1" // "1 is 1"

"foo" === "bar" ? 1 : 0 // 0
"dog" === "dog" ? false : true // false
```

### The Commma Operator

The comma operator, according to MDN, "simply evaluates both of its operands and returns the value of the last operand." This just means that `1, 2` evaluates ("runs") both `1` and `2` and returns `2`.

### Special Unary Operators

JavaScript also has a number of keywords that are unary operators.

- `delete`:  deletes properties of objects and arrays (although it doesn't always behave like you'd expect). We'll learn more about `delete` when we learn about objects and arrays.

- `typeof`: We learned about the `typeof` unary operator when we were exploring data types in JavaScript. It returns the type of its operand as a lowercase string.

- `void`: The `void` operator evaluates an expression but always returns `undefined`. If you know a bit of HTML, you might have seen something like

``` html
<a href="javascript:void(0)">I do nothing</a>
```

`void(0)` evaluates `0` and returns `undefined`. Similarly, `void("foo")` evaluates "foo" and returns undefined; `void(1 || 1)` evaluates `1 || 1` and returns `undefined`. The parentheses are optional with `void`, but they're good style: `void 1 || 1` actually ends up evaluating `1` and returning `undefined`, so it becomes `undefined || 1`, which, of course, returns `1`.

### Relational Operators

JavaScript has two relational operators, `in` and `instanceof`. We'll learn more about these operators when we cover objects and constructors, but for now, here are some examples to show how they work:

``` javascript
/**
 * `in` returns `true` if its left-hand operand is a property
 * of its right-hand operand.
 */

x = ["cats", "dogs", "cows"]

"cats" in x // false
0 in x // true -- indices are properties of arrays


/**
 * `instanceof` returns `true` if its left-hand operand is
 * an object of the type of its right-hand operand —
 * that is, if its left-hand operand is an _instance of_
 * its right-hand operand.
 */

new String('foo') instanceof String // true
new Object() instanceof String // false
```

### Conclusion

That was a lot to take in! Be sure to check out the resources, and try out a few examples in console on your own.

### Resources

- [MDN - Expressions and Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)
- [MDN - Equality comparisions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness)
- [JavaScript Equality Table](https://dorey.github.io/JavaScript-Equality-Table/)
