UI Rulebook
================

General Rules
----------------

- **No inline CSS or JS:** CSS and JavaScript must be in their corresponding files.
``` html
<!-- Bad -->
<button style='color:red;' onclick='alert(1)'>
	DANGER!
</button>

<!-- Good -->
<button class='redAlertBtn'>
	DANGER!
</button>
```

- **Remove dead code:** When bringing in code to a new framework from an older piece of software, it is imperative that none of the old, unused code remain.  This is important because it makes understanding the code more difficult, might affect performance, and may even be a security concern.
``` html
<!-- Example -->
<input type='hidden' name='op' value='(<script>alert(1)</script>)'>
```

- **No IDs:** Do not use any HTML IDs.  Use classes instead.  Content may be duplicated at some times and, since IDs should be unique, may cause errors.
``` html
<!-- Bad -->
<button id='rareSection'>
	DANGER!
</button>

<!-- Good -->
<button class='rareSection'>
	DANGER!
</button>
```



- **Coding Style:**  Coding style is important for many reasons:
	1. It takes less mental effort and overall time for people who haven't worked on the code to figure out what the code is doing.
	2. It is easier on the eyes when trying to find a specific element amidst a wall of compact text.
	3. It ascertains that there is no broken code by using indentation as a validation tool.  If your opening and closing tags do not align vertically, you know there is a problem.



IDE Configuration
-----------------
- Please use *Hard Tabs*, not spaces.
- Each Tab should be configured to a *4 space width*.



Naming conventions
-----------------
- Use camelCase.  It is our naming convention of choice.
``` js
// Bad
var Alpha_dog = true;

// Good
var alphaDog = true;
```




HTML Tags
---------

- Whenever you open an HTML tag, you must place that element's contents on the following line.  Avoid inlining any content, even if it is simple.
``` html
<!-- Bad -->
<div class='hello'>World!</div>

<!-- Good -->
<div class='world'>
    Hello!
</div>
```

- The inner content should always be one level of indent deeper than its enclosing tag (+1 tab).
- All closing tags are one level of indent outside the current indent level (-1 tab).
- Any closing tags must *always* be vertically aligned with its opening tag. 
```
<!-- Good -->
<div class='world'>
    Hello!
    <span>
        World?
    </span>
</div>
```



- Do not indent by more than one level at a time
``` html
<!-- Bad -->
<div>
        <span>
            Apple
        </span>
</div>

<!-- Good -->
<div>
    <span>
        Apple
    </span>
</div>
```



JSP Scriptlets & Expressions
----------------------------

- JSP __scriptlet__ opening and closing tags must be on their own lines.
``` jsp
// Bad
<%String apple = "apple";%>

// Good
<%
String apple = "apple";
%>
```

- However, JSP __Expressions__ must be inlined.
``` jsp
<%= Something(); %>
```

- Do not indent the contents of JSP scriptlets.
``` jsp
// Bad
<%
    String apple = "hello";
%>

// Good
<%
String apple = "apple";
%>
```

- JSP scriptlets must obey the indentation principles of HTML documents as well as Java code.
``` jsp
// Bad
<div  class='hello'>
<%
String apple = "apple";
%>
</div>

// Bad
<div  class='hello'>
<%
	String apple = "apple";
%>
</div>

// Good
<div  class='hello'>
    <%
    String apple = "apple";
    %>
</div>
```


- You must include opening and closing curly braces wherever possible.
- Opening and closing braces must always be on their own lines.

``` java
// Bad
if (x == true) return true;

// Bad
if (x == true) {return true;}

// still bad
<div  class='hello'>
    <%
    if (x == true)
    {
    String apple = "apple";
    }
    %>
</div>

// Good
<div  class='hello'>
    <%
    if (x == true)
    {
        String apple = "apple";
    }
    %>
</div>
```



- As a rule, if the JSP you are working on is complex, it is your responsibility to make it less complex.
``` html
<!-- Bad -->
<div class='section'>
    <%
    while(zebraStripes--)
    {
    	if (x == true)
	    {
	        %>
	        </div>
	        <%
	    }
	   	else
	   	{
	    	<%
	    	<p class='stripe'>This is not striped.</p>
	    	%>
	    }
	}
	%>


<!-- Good -->
<div class='section'>
    <%
    while(zebraStripes--)
    {
    	<%
    	<p class='stripe'>This is not striped.</p>
    	%>
	}
	%>
</div>
```

> Since closing tags must always be on the previous indent level, this JSP's markup is overly complex.  It is very difficult to understand the flow of the page from the code and to gaze through the different sections at a glance.





