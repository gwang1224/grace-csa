---
layout: default
title: JS Input
description: A Tech Talk on user inputs using Javascript. The grade calculator takes multiple values and does a calculation on them. User input can be useful for other projects, such as being used as a query.
courses: {'labnotebook': {'week': 2}}
type: notes
---

## HTML
> Identify the HTML for a grade calculator;  it enables input and totals.

- [DIV element](https://www.w3schools.com/tags/tag_div.asp) defines a division or a section in an HTML document. Used to divide headings, totals, and input in this example.
- [SPAN element](https://www.w3schools.com/tags/tag_span.asp) defines a inline container within text. Used to capture different totals in this example.
- [INPUT tag](https://www.w3schools.com/tags/tag_input.asp) specifies an input field where the user can enter data. Used to capture series of numbers in this example.
- [ID attributes](https://www.w3schools.com/html/html_id.asp) are used by CSS for style and JavaScript for reference.  Used to update totals in this example.


### Resources HTML
- [HTML Tutorial](https://www.w3schools.com/html/)
- [learn about id](https://www.washington.edu/accesscomputing/webd2/student/unit3/module5/lesson1.html)

## JavaScript newInputLine
> Identify the function that generates a new input line after each score is entered.

### Resources createElement
- [Create Element](https://www.w3schools.com/jsref/met_document_createelement.asp)
- [Set Attribute](https://www.w3schools.com/jsref/met_element_setattribute.asp)

## JavaScript calculator
> Indentify the code below calculates the the total, count, and average of the user inputs.

### Resources getElements
- [Get Elements by ID](https://www.w3schools.com/jsref/met_document_getelementbyid.asp)
- [Get Elements by Name](https://www.w3schools.com/jsref/met_doc_getelementsbyname.asp)


## HTML Magic runs Calculator
> The code below runs in VSCode and on Jupyter Notebook. 
- [SCRIPT tag](https://www.w3schools.com/tags/tag_script.asp) is used to embed JavaScript inside of HTML


```python
%%html

<!-- Heading -->
<h1>Grade Calculator</h1>
<h2>Input scores, press tab to add each new number.</h2>
<!-- Totals -->
<h3>
    Total : <span id="total">0.0</span>
    Count : <span id="count">0.0</span>
    Average : <span id="average">0.0</span>
</h3>
<!-- Rows -->
<div id="scores">
    <!-- javascript generated inputs -->
</div>

<script>
// Creates a new input box
function newInputLine(index) {

    // Add a label for each score element
    var title = document.createElement('label');
    title.htmlFor = index;
    title.innerHTML = index + ". ";    
    document.getElementById("scores").appendChild(title); // add to HTML

    // Setup score element and attributes
    var score = document.createElement("input"); // input element
    score.id =  index;  // id of input element
    score.onkeydown = calculator // Each key triggers event (using function as a value)
    score.type = "number"; // Use text type to allow typing multiple characters
    score.name = "score";  // name is used to group "score" elements
    score.style.textAlign = "right";
    score.style.width = "5em";
    document.getElementById("scores").appendChild(score);  // add to HTML

    // Create and add blank line after input box
    var br = document.createElement("br");  // line break element
    document.getElementById("scores").appendChild(br); // add to HTML

    // Set focus on the new input line
    document.getElementById(index).focus();
}

// Handles event and calculates totals
function calculator(event) {
    var key = event.key;
    // Check if the pressed key is the "Tab" key (key code 9) or "Enter" key (key code 13)
    if (key === "Tab" || key === "Enter") { 
        event.preventDefault(); // Prevent default behavior (tabbing to the next element)
   
        var array = document.getElementsByName('score'); // setup array of scores
        var total = 0;  // running total
        var count = 0;  // count of input elements with valid values

        for (var i = 0; i < array.length; i++) {  // iterate through array
            var value = array[i].value;
            if (parseFloat(value)) {
                var parsedValue = parseFloat(value);
                total += parsedValue;  // add to running total
                count++;
            }
        }

        // update totals
        document.getElementById('total').innerHTML = total.toFixed(2); // show two decimals
        document.getElementById('count').innerHTML = count;

        if (count > 0) {
            document.getElementById('average').innerHTML = (total / count).toFixed(2);
        } else {
            document.getElementById('average').innerHTML = "0.0";
        }

        // adds newInputLine, only if all array values satisfy parseFloat 
        if (count === document.getElementsByName('score').length) {
            newInputLine(count); // make a new input line
        }
    }
}

// Creates 1st input box on Window load
newInputLine(0);

</script>

```



<!-- Heading -->
<h1>Grade Calculator</h1>
<h2>Input scores, press tab to add each new number.</h2>
<!-- Totals -->
<h3>
    Total : <span id="total">0.0</span>
    Count : <span id="count">0.0</span>
    Average : <span id="average">0.0</span>
</h3>
<!-- Rows -->
<div id="scores">
    <!-- javascript generated inputs -->
</div>

<script>
// Creates a new input box
function newInputLine(index) {

    // Add a label for each score element
    var title = document.createElement('label');
    title.htmlFor = index;
    title.innerHTML = index + ". ";    
    document.getElementById("scores").appendChild(title); // add to HTML

    // Setup score element and attributes
    var score = document.createElement("input"); // input element
    score.id =  index;  // id of input element
    score.onkeydown = calculator // Each key triggers event (using function as a value)
    score.type = "number"; // Use text type to allow typing multiple characters
    score.name = "score";  // name is used to group "score" elements
    score.style.textAlign = "right";
    score.style.width = "5em";
    document.getElementById("scores").appendChild(score);  // add to HTML

    // Create and add blank line after input box
    var br = document.createElement("br");  // line break element
    document.getElementById("scores").appendChild(br); // add to HTML

    // Set focus on the new input line
    document.getElementById(index).focus();
}

// Handles event and calculates totals
function calculator(event) {
    var key = event.key;
    // Check if the pressed key is the "Tab" key (key code 9) or "Enter" key (key code 13)
    if (key === "Tab" || key === "Enter") { 
        event.preventDefault(); // Prevent default behavior (tabbing to the next element)

        var array = document.getElementsByName('score'); // setup array of scores
        var total = 0;  // running total
        var count = 0;  // count of input elements with valid values

        for (var i = 0; i < array.length; i++) {  // iterate through array
            var value = array[i].value;
            if (parseFloat(value)) {
                var parsedValue = parseFloat(value);
                total += parsedValue;  // add to running total
                count++;
            }
        }

        // update totals
        document.getElementById('total').innerHTML = total.toFixed(2); // show two decimals
        document.getElementById('count').innerHTML = count;

        if (count > 0) {
            document.getElementById('average').innerHTML = (total / count).toFixed(2);
        } else {
            document.getElementById('average').innerHTML = "0.0";
        }

        // adds newInputLine, only if all array values satisfy parseFloat 
        if (count === document.getElementsByName('score').length) {
            newInputLine(count); // make a new input line
        }
    }
}

// Creates 1st input box on Window load
newInputLine(0);

</script>


