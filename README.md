# UI Conventions

## <a name='TOC'>Table of Contents</a>

  1. [General](#general)
  1. [Tabbing](#tabbing)
  1. [Indentation](#indentation)
  1. [Comments](#comments)
  1. [Naming Convention](#naming-convention)
  1. [White Space](#white-space)
  1. [File Organization](#file-organization)

## <a name='general'>General</a>

  Coding conventions are a set of guidelines that promote software maintenance.  
    + 40%-80% of the lifetime cost of a piece of software goes into maintenance. 
    + Hardly any software is maintained for its whole life by the original author.
    + Code conventions improve the readability of the software, allowing engineers to understand new code more quickly and thoroughly.
    + It can provide a simple layers for code validation, reducing the likelihood of bugs.
    + It can provide confidence for automation, reducing the risk of breaking things if you need to do a project wide fix.

  > Source: [Wikipedia](http://en.wikipedia.org/wiki/Coding_conventions)

  **[[⬆]](#TOC)**


## <a name='tabbing'>Tabbing</a>

  Use 4 space width *hard* tabs. Set your IDE to tab this way for you from the start.

  **[[⬆]](#TOC)**


## <a name='indentation'>Indentation</a>
  
  - Opening HTML tags and curly braces set the indent one level deeper.
    
    ``` html
    <!-- Bad -->
    <div class='hello'>
    World!
    </div>

    <!-- Good -->
    <div class='world'>
        Hello!
    </div>
    ```

  - Any closing tags must *always* be vertically aligned with its opening tag, moving the indent outwards by one tab. 
  	
    ``` html
  	<!-- Good -->
  	<div class='world'>
  	    Hello!
  	    <span>
  	        World?
  	    </span>
  	</div>
  	```

  - Do not indent by more than one level at a time.
  	
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
    
  **[[⬆]](#TOC)**










  - **No inline CSS or JS:** CSS and JavaScript must be in their corresponding files

	```html
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


	
  

    





IDE Configuration
-----------------



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





JSP Scriptlets & Expressions
----------------------------




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





