# _eval()_ Function
The eval() function evaluates javascript code represented as a string and return its completion values.
```js
eval(string:any)
```
eval function accepts a parameter of string type. It accepts javascript expression or code. It can be single, multiple, even sequence or expression.  
**Example:**
```js
function foo(str){
    eval(str);
    console.log(a,b,c);     //10 20 30
}
foo("var a=10;var b=20;var c=a+b");
```
Here, a sequence of statements passed as parameter to `eval()` function. Those statements executed inside eval and the return the results.  

**Not to use eval() function is recommended**  
* With eval(), malicious code can run inside the application without permission.
* With eval(), third party code can see the scope of the application.

# _with()_ Function
