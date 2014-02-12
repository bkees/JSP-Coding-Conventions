# UI Conventions

## <a name='TOC'>Table of Contents</a>

  1. [General](#general)
  1. [Tabbing](#tabbing)
  1. [Indentation](#indentation)
  1. [Comments](#comments)
  1. [Naming Convention](#naming-convention)
  1. [JSP](#jsp)

## <a name='general'>General</a>

Coding conventions are a set of guidelines that promote software maintenance.  
  + 40%-80% of the lifetime cost of a piece of software goes into maintenance. 
  + Hardly any software is maintained for its whole life by the original author.
  + Code conventions improve the readability of the software, allowing engineers to understand new code more quickly and thoroughly.
  + It provides simple layers for code validation, reducing the likelihood of bugs and increasing development speed.

> Source: [Wikipedia](http://en.wikipedia.org/wiki/Coding_conventions)

**[[⬆]](#TOC)**


## <a name='tabbing'>Tabbing</a>

  Use 4 space width *hard* tabs. Set your IDE to tab this way for you from the start.

  **[[⬆]](#TOC)**


## <a name='indentation'>Indentation</a>
  - HTML tags, curly braces, and JSP scriptlet tags must all be on their own lines.
    ``` html
    <!-- Bad -->
    <div class='hello'>World!</div>

    <!-- Good -->
    <div class='world'>
        Hello!
    </div>


    <!-- Bad -->
    <% doFunc(); %>

    <!-- Good -->
    <%
    doFunc4();
    %>


    <!-- Bad -->
    if (x == true) { return true; }

    <!-- Good -->
    if (x == true) 
    {
        return true;
    }

    ```

  
  - HTML tags and curly braces force a level of indentation.  __JSP scriptlets do *not*__.
    
    ``` html
    <!-- Bad -->
    <div class='hello'>
    World!
    </div>

    <!-- Good -->
    <div class='world'>
        Hello!
    </div>


    <!-- Bad -->
    if (x == true) 
    {
    return true;
    }

    <!-- Good -->
    if (x == true) 
    {
        return true;
    }



    <!-- !Bad! -->
    <%
        doFunc1();
    %>

    <!-- Good -->
    <%
    doFunc2();
    %>
    ```

  - Any closing tags must *always* be vertically aligned with its corresponding opening tag.
  	
    ``` html
    <!-- Bad -->
    <div class='world'>
        Hello!
        <span>
            World?</span>
        </div>

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


  - JSP **Expressions** must be inlined.
    ``` jsp
    <%= Something(); %>
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




## <a name='comments'>Comments</a>

### HTML Comments
  - Do not use HTML comments.  It adds overhead to each request as it is sent to the users.  Instead, use JSP comments.

### JSP Comments
  - Single line comments with //, multi-line comments with /* */
  - Don't explain each word of the code unless it is very cryptic.  Instead, explain why you are doing it.
  - Complex functions should be summarized above the function declaration.

  **[[⬆]](#TOC)**



## <a name='naming-convention'>Naming Convention</a>

For all file naming, use camelCase.

### JS Filenames
  - If working on a section plugin, name it after the section and append "Section" to the name.
    ```
    documentSection.js
    contactSection.js
    ```

  - If working on a page script, name it after the JSP filename
    ```
    editPoUI.jsp -> editPoUI.js
    ```

  - If working on a particular UI element, name it after the element
    ```
    // example
    filterButton.js
    userDetails.js
    eTable.js
    ```

### Handlebar Filenames
  - If plugin specific, name it after the plugin
    ```
    documentSection.js -> documentSection.handlebars
    ```

  - If generic, name it after the ui element
    ```
    contextMenu.handlebars
    ```


### In Code
  - Use camelCase.  It is our naming convention of choice.
    ``` js
    // Bad
    var Alpha_dog = false;

    // Good
    var alphaDog = true;
    ```
  
  **[[⬆]](#TOC)**




## <a name='jsp'>JSP</a>

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


  - **Remove dead code:** When bringing in code to a new framework from an older piece of software, it is imperative that none of the old, unused code remain.  This is important because it makes understanding the code more difficult, might affect performance, and may even be a security concern.
	
  	``` html
  	<!-- Example -->
  	<input type='hidden' name='op' value='(<script>alert(1)</script>)'>
  	```


  - **Remove complex logic**: As a rule, if the JSP you are working on is complex, it is your responsibility to make it less complex.
  	
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





