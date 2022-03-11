# labfinal
## Explain 1:<br>
I used the diff command `diff student-mdparse/results.txt markdown-parse/results.txt > r.txt`.<BR>
The first two results showed 
```
48c48
< [\!\"\#\$\%\&\'\(\]
---
> []
98,99c98
< [```ruby
< def foo(x]
```
## Explain 2:<br>
For the first difference, I think that my implementation is incorrect. It prints out the stuff before the close parenthesis, and the expected output shoud be `[]` instead of `[\!\"\#\$\%\&\'\(\]`. <br>
For the second difference, my implementation is incorrect. The correct input should be `[]` instead of 
```
[```ruby
< def foo(x]
```
These errors is due to the fact that in my implementation, I used
```
if(!markdown.substring(currentIndex).contains("[") && markdown.substring(currentIndex).contains("(")){
    int nextOpenBracket = markdown.indexOf("(", currentIndex);
    int nextCloseBracket = markdown.indexOf(")", nextOpenBracket);
    int openParen = markdown.indexOf("(", nextCloseBracket);
    int closeParen = markdown.indexOf(")", openParen);
    toReturn.add(markdown.substring(openParen + 1, closeParen));
    currentIndex = closeParen + 1;
```
in order to look for the link inside a .md file with all parentheses but no brackets. I should fix it by considering adding a counter to identify stuff inside the next pair of parentheses. Both bugs happened when there's 

 
