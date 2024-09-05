# What is JSON? #
JSON stands for JavaScript Object Notation. It is used as a variable, since it's used to save data (information).
## Syntax ##
JSON uses a `key-value pair` syntax. That is, the "`key`" is the variable's name and the "`value`" is well... the variable's value. A key is always needed to form a pair, but the value can be defined as empty.

The way this syntax needs to be written is like `"key": "value"`, which successfully builds a key-value pair.
## Examples ##
```
{
  "fruit": "pineapple"
}
```
Here, `fruit` is the key (variable name) and `pineapple` is the value (variable value).

We have successfully built our first variable on our JSON object, but the point of JSON is to serve as a multiple-variable storage. Let's go ahead and add more variables to it.
### Multiple variables (key-value pairs) ###

```
{ 
  "fruit": "pineapple",
  "quality": "good",
  "color": "orange"
}
```
If you have multiple key-value pairs, you gotta separate each with a `,` until the last one. That is required, and will cause errors if not applied correctly.
### Nested variables ###
#### Example (1) ####
```
{
"pineapple": {
 "color": "orange",
 "quality": "good"
 },
"banana": {
 "color": "yellow",
 "quality": "bad"
 }
}
```
On this example, we have nested variables — that is, we have variables within/inside another variable. In this case, if we want to access X, then we'll have to identify the thing that owns X first.
> [!TIP]
> Think about nested variables as divisions and subdivisions — in order to access the subdivision, we'll have to get through the division first to then gain access subdivision.

If we want to access the `color` variable from the `banana` variable, we'll have to access the banana variable first.

Accessing the banana variable returns the following:
```
{
 "color": "yellow",
 "quality": "bad"
 }
 ```
Now that we have accessed the banana variable, we can obtain it's values: `color` and `quality` key-pairs.

So in conclusion, to access the color key-pair, we went through the following steps:

`Access "banana" > Get "color"|"quality" > Access "color" > Obtain "yellow"`
#### Example (2) ####
```
{
 "fruits": {
  "pineapple": {
   "color": "orange",
   "quality": "good"
 },
  "banana": {
   "color": "yellow",
   "quality": "bad"
  }
 }
}
```
This example is pretty similar to the previous one. We have a `fruits` variable with two values: `pineapple` and `banana`. We want to access the `quality` variable from the `pineapple` variable from the `fruits` variable. Sounds confusing? It's really not.

Accessing the fruits variable returns the following:
```
{
  "pineapple": {
   "color": "orange",
   "quality": "good"
 },
  "banana": {
   "color": "yellow",
   "quality": "bad"
  }
}
```
Now, we have accessed the it's values: two others variables (pineapple & banana). Let's access the pineapple variable now.
```
{
   "color": "orange",
   "quality": "good"
 }
```
Now, we have accessed the `pineapple`  variable and it's values: `color` & `quality` key-pairs.

So in conclusion, to access the quality key-pair, we went through the following steps:

`Access "fruits" > Get "pineapple"|"banana" > Access "pineapple" > Get "color"|"quality" > Access "quality" > Obtain "good"`
