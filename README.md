# Motivation

[Hungarian notation](https://en.wikipedia.org/wiki/Hungarian_notation) is not a standard in MATLAB, however, it is often useful to have a prefix that specifies variable type to make MATLAB code more readable and maintanable.  

* MATLAB IDE is not good about type hinting.  
* It is usually difficult to tell if something is a `char`, a `cell`, a `double`, an `int8`, etc.  
* Hungarian makes it easy to see at a glance what type a variable is.   

# Hungarian Prefixes

<table>
  <tr>
    <th>MATLAB Class</th>
    <th>Hungarian Prefix</th>
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
`dVal = 20;`

## logical
`lIsPressed = true;`
## char
`cHello = 'Hello World!';`

## cell
`b = {'foo' 20.2 int8(4)};`
In this scenario, the MATLAB class of each element of the `cell` is different: 

* `b{1} % char (1x3)` 
* `b{2} % double (1x1)`
* `b{3} % uint8 (1x1)`

In scenarios where the class of each element of the cell is the same, the Hungarian prefix can be compounded.  E.g., a “cell of char” would combine the Hungarian prefix for `cell` and `char` to form a compound prefix “cec”

### cell of char
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

k, m, p, q (loop counters are excempt from Hungarian notation)

# When to Use Hungarian Notation?

Only for primitive Matlab classes and core framework classes, as outlined above

For me Hungarian notation lets you define two things with the variable name:

 1. the Matlab class 
 2. the physical thing the variable represents

For example, "uieResistName" says that this variable represents the name of the resist and that it is a UIEdit Matlab class. We need the Hungarian prefix because the "representation" part (ResistName) is not enough to specify what Matlab class it is (it could be a char, or anything). It is ambiguous)

But lets consider a higher-level class like ReticleCoarseStage. Here, if we use a variable name like "reticleCoarseStage" the "physical thing the variable represents" and the Matlab class name are identical, so there is no need for the hungarian prefix. I.E., the variable instance represents the reticle coarse stage and the Matlab class is called ReticleCoarseStage, so there is no need for the Hungarian prefix.

I think whenever the Matlab class name is identical to the physical thing the variable represents, there is no need for a hungarian prefix.


## Array initialization

- true(0)                 0x0 logical
- []                      0x0 double
- {}                      0x0 cell
- struct()                1x1 struct with no fields
- struct([])              0x0 struct with no fields






