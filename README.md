JSP Rulebook
============

Basic principles
----------------

- Make sure there are no inline styles or events on any element.
- Make sure to remove all E2 specific logic or code.
- Remove any <input type='hidden'> that are no longer relevant.
- Clean up the markup as follows prior to commiting.  No code should be commit without being cleaned first.


JSP STYLE GUIDE

IDE:
- Please use Tabs, not spaces.
- Each Tab width should represent a 4 space width, but not transform into actual spaces.


HTML Tags
- When you open an HTML tag, anything after that line must have an additional Tab of indentation up until the corresponding closing tag.  
- All closing tags move back one level of indentation.
- The closing tag must -always- be vertically aligned with its opening tag. (No exceptions)

example:
```
<div class='world'>
    Hello!
    <span>
        World?
    </span>
</div>
```

- Whenever you open an HTML tag, you must place that element's contents on the following line.  Avoid inlining any content, even if it is simple.

BAD:
```
<div class='hello'>World!</div>
```

Good:
```
<div class='world'>
    Hello!
</div>
```

- Do not indent by more than one level at a time
Bad:
```
<div>
        <span>
            Apple
        </span>
</div>
```

Good:
```
<div>
    <span>
        Apple
    </span>
</div>
```



JSP
- JSP scriptlet opening and closing tags must be on their own lines.
Bad:
```
<%String apple = "apple";%>
```

Good:
```
<%
String apple = "apple";
%>
```

- Do not indent the contents of JSP scriptlets.
Bad:
```
<%
    String apple = "hello";
%>
```

Good:
```
<%
String apple = "apple";
%>
```

- JSP scriptlets must obey the indentation principles of HTML documents as well as Java code.
Bad:
```
<div  class='hello'>
<%
String apple = "apple";
%>
</div>
```

Good:
```
<div  class='hello'>
    <%
    String apple = "apple";
    %>
</div>
```

Bad:
```
<div  class='hello'>
    <%
    if (x == true)
    {
    String apple = "apple";
    }
    %>
</div>
```

Good:
```
<div  class='hello'>
    <%
    if (x == true)
    {
        String apple = "apple";
    }
    %>
</div>
```

- You must always include opening and closing braces
Bad:
```
if (x == true) return true;
```

Good:
```
if (x == true) 
{
    return true;
}
```

- Opening and closing braces must always be on their own lines


Bad:
```
if (x == true) {return true;}
```

Good:
```
if (x == true) 
{
    return true;
}
```


- As a rule, if a JSP you are working on is complex, it is your responsibility to make it less complex.
Example:
```
<div class='section'>
    <%
    if (x == true)
    {
        %>
        </div>
        <%
    }
    etc...
</div>
```

> Since closing tags must always be on the previous indent level, this JSP's markup is overly complex.  It is very difficult to understand the flow of the page from the code and to gaze through the different sections at a glance.



