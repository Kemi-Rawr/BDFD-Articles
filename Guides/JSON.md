# What is JSON? #
JSON stands for JavaScript Object Notation. It is used as a variable, since it's used to save data (information).
## Syntax ##
JSON uses a `key-value pair` syntax. That is, the "`key`" is the variable's name and the "`value`" is well... the variable's value. A key is always needed to form a pair, but the value can be defined as empty.

The way this syntax needs to be written is like `"key": "value"`, which successfully builds a key-value pair.
## Examples ##
```
{
  "fruit": "apple"
}
```
Here, `fruit` is the key (variable name) and `apple` is the value (variable value).

We have successfully built our first variable on our JSON object, but the point of JSON is to serve as a multiple-variable storage. Let's go ahead and add more variables to it.
### Multiple variables (key-value pairs) ###

```
{ 
  "fruit": "apple",
  "quality": "good",
  "color": "green"
}
```
Have you noticed anything different on the key-value pairs? Yup, every key-value pair, except the last, has a `,` right after the value.

If you have multiple key-value pairs, you gotta separate each of them with a `,` until the last one. That is required, and will cause errors if not applied correctly.
### Nested variables ###
On the previous example, we have built a JSON structure
