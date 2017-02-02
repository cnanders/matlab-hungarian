# Motivation

[Hungarian notation](https://en.wikipedia.org/wiki/Hungarian_notation) is not a standard in MATLAB, however, it is often useful to have a prefix that specifies variable type to make MATLAB code more readable and maintanable.  

* MATLAB IDE is not good about type hinting.  
* It is often difficult to tell if something is a `char`, a `cell`, a `double`, an `int8`, etc.  
* Hungarian makes it possible to see the class of a variable at a glance.

# Hungarian Prefixes

<table>
  <tr>
    <th>MATLAB Class</th>
    <th>Prefix</th>
  </tr>
  
  <tr>
    <td>uint8</td>
    <td>u8</td>
  </tr>
  <tr>
    <td>uint16</td>
    <td>u16</td>
  </tr>
   <tr>
    <td>uint32</td>
    <td>u32</td>
  </tr>
   <tr>
    <td>uint64</td>
    <td>u64</td>
  </tr>

  <tr>
    <td>int8</td>
    <td>i8</td>
  </tr>
  <tr>
    <td>int16</td>
    <td>i16</td>
  </tr>
   <tr>
    <td>int32</td>
    <td>i32</td>
  </tr>
   <tr>
    <td>int64</td>
    <td>i64</td>
  </tr>
  <tr>
    <td>double</td>
    <td>d</td>
  </tr>
  <tr>
    <td>single</td>
    <td>s</td>
  </tr>
  <tr>
    <td>char</td>
    <td>c</td>
  </tr>
  <tr>
    <td>handle</td>
    <td>h</td>
  </tr>
   <tr>
    <td>logical</td>
    <td>l</td>
  </tr>

  <tr>
    <td>cell</td>
    <td>ce</td>
  </tr>

  <tr>
    <td>struct</td>
    <td>st</td>
  </tr>
  <tr>
    <td>timer</td>
    <td>t</td>
  </tr>

  <tr>
    <td>function_handle</td>
    <td>fh</td>
  </tr>

  <tr>
    <td>table</td>
    <td>ta</td>
  </tr>

  <tr>
    <td>videoinput</td>
    <td>vi</td>
  </tr>
  <tr>
    <td>java.*</td>
    <td>j</td>
  </tr>

  <tr>
	<td>mixed (any type)</td>
    <td>x</td>
  </tr>
</table>


# Examples

## int16
`i16Val = int16(1234);`

## double
`dVal = 20.4;`

## logical
`lIsPressed = true;`
## char
`cHello = 'Hello World!';`

## cell
`ceMulti = {'foo' 20.2 int8(4)};`

In this scenario, the MATLAB class of each element of the `cell` is different: 

* `b{1} % char (1x3)` 
* `b{2} % double (1x1)`
* `b{3} % uint8 (1x1)`

In scenarios where the class of each element of the cell is the same, a compound Hungarian prefix can be used.  E.g., for a “cell of char”, combine the Hungarian prefix for `cell` and `char` to form the compound prefix “cec”, as shown below.

## cell of char
`cecNames = {'jane', 'chris', 'rachel'}`

## struct

	stCar = struct( ...
		'year', 2016, ...
		'make', 'tesla', ...
		'model', 'model s', ...
		'color', 'red', ...
		'license', '2x33fy7' ...
	);

# Loop Counters

Loop counters are excempt from Hungarian notation

# When to Use Hungarian Notation?

For small scripts or projects, Hungarian notaion is likely overkill.  For large projects with multiple contributors, that rely on many classes (e.g., everything is not a `double`), Hungarian notaion can be useful.

# Custom Classes

If you use OOP for a MATLAB project, feel free to come up with your own Hungarian prefixes for each class you define.

# Discussion

Hungarian notation lets you define two things with the variable name:

1. the MATLAB class 
2. the thing the variable represents

For example, “u8BeveragesConsumed" declaratively says two things:

1. this variable represents beverages that have been consumed
2. it is a `uint8` MATLAB class. The class immediatly informs the reader that half-finished beverages cannot be accounted for since the class `uint8` does not support non-integers. 








