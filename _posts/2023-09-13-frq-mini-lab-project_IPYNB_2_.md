---
title: FRQ Mini-lab project
description: Preparing for types of FRQ questions tested by College Board
layout: default
courses: {'labnotebook': {'week': 4}}
type: hacks
---

[AP Computer Science A 2023 FRQ](https://apcentral.collegeboard.org/media/pdf/ap23-frq-comp-sci-a.pdf)

## FRQ 2

This FRQ asks you to write an entire class, given specifications of what the class should do, and including any variables and methods the class should include.

- **class:** a list of attributes and instructions (a blueprint) for how to create an instance of itself
    - **attribute:** characteristics of an object
    - **behaviors:** actions hat an object can perform
- **object:** an instance of the class
- **instantiate:** to all the constructor to create an object
- **constructor:** a block of code that has the same name as the class and tells the computer how to create a new object
- creating objects example
- **parameters:** values that you can pass into methods or constructors to provide input or configuration for their operations
- **methods:** a function

![Question 2](https://cdn.discordapp.com/attachments/1010780182476496908/1153053113511596052/Untitled_drawing_4.png)

![Question 2.1](https://cdn.discordapp.com/attachments/1010780182476496908/1153052783604416542/Untitled_drawing_3.png)

After reading FRQ, we are tasked with creating a sign with a specific number of characters per line.

- **Class Description**: Create a `Sign` class.
  
- **Constructor**: The class has a constructor with two parameters:
  - A `String` message to be displayed on the sign.
  - An `int` representing the width of each line on the sign.

- **numberOfLines Method**: Implement a method called `numberOfLines` that returns the number of lines needed to display the text on the sign.

- **getLines Method**: Implement a method called `getLines` that returns the message broken into lines separated by semicolons (`;`) or `null` if the message is empty. No semicolon should appear at the end of the returned string.

- **Testing**: Create instances of the `Sign` class with different parameters and test the `numberOfLines` and `getLines` methods to ensure correct behavior.

![Diagram](https://cdn.discordapp.com/attachments/1010780182476496908/1154263074849685534/frq_2_diagram_2.png)


```java
// STEP 1: Create class
public class Sign
{
    // STEP 2: Create variables
    private String m;
    private int w;

    // STEP 3: Create constructor with two parameters referencing information given in the table
    public Sign(String message, int width)
    {
        this.m = message;
        this.w = width;
    }

    // STEP 4: Create numberOfLines() method with no parameters
        // Method should divide message by width of sign
        // If result has a remainder, another line must be added
    public int numberOfLines()
    {
       int result = m.length() / w;
       if(m.length() % w > 0)
       {
            result += 1;
       }
       return result; 
    }

    // STEP 5: Create getLines() method with no parameters
        // If length = 0, return null
        // Write message based on message length, adding a semicolon at the end
    public String getLines()
    {
        if(m.length() == 0)
        {
            return null;
        }
        String result = "";
        int count = 0;

        for(int i = 0; i < m.length(); i++)
        {
            if(count == w)
            {
                result += ";";
                count = 0;
            }
            result += m.substring(i, i+1);
            count++;
        }

        return result;
    }
    

}
```

## Testing the Code

Using the table provided by College Board, we test the code by instantiating class Sign and providing different parameters to see if the method call return value is expected.


```java
String str;
int x;

Sign sign1 = new Sign ("ABC222DE", 3);
x = sign1.numberOfLines();
str = sign1.getLines();

System.out.println(str);
System.out.println(x);
```

    ABC;222;DE
    3



```java
Sign sign2 = new Sign ("ABCD", 10);

x = sign2.numberOfLines();
str = sign2.getLines();

System.out.println(str);
System.out.println(x);
```

    ABCD
    1



```java
Sign sign3 = new Sign("ABCDEF",2);

x = sign3.numberOfLines();
str = sign3.getLines();

System.out.println(str);
System.out.println(x);

```

    AB;CD;EF
    3



```java
Sign sign4 = new Sign("",4);

x = sign4.numberOfLines();
str = sign4.getLines();

System.out.println(str);
System.out.println(x);
```

    null
    0



```java
Sign sign5 = new Sign("AB_CD_EF", 2);

x = sign5.numberOfLines();
str = sign5.getLines();

System.out.println(str);
System.out.println(x);
```

    AB;_C;D_;EF
    4


## Peer Grading: Sreeja

| Point | Requirement | Responses to Earn Point | Responses Not to Earn Point | Points |
|-------|-------------|-------------------------|----------------------------|--------|
| 1     | Declares class header: class Sign | Declare the class as public | Declare the class as something other than public | 1 point |
| 2     | Declares appropriate private instance variable(s) and constructor | Initialize instance variables using appropriate parameters | Declare the variable outside the class, or in the class within a method or constructor | 1 point |
| 3     | Declares constructor header: Sign(String ___, int ___) | Calculate values in the constructor that are returned by other methods (correctly or incorrectly), as long as the parameter types are correct | Declare the constructor as something other than public | 1/1 |
| 4     | Declares method headers: - public int numberOfLines() - public String getLines() | Omit either method | Omit public or declare the method as something other than public | 1/1 |
| 5     | numberOfLines divides the message length by the line width | Perform the division in a method other than numberOfLines | Perform the division without using the division operator by counting line-widthsized portions of the message or by counting lines produced by the line-delimiting algorithm; Incorrectly account for the final line; Use a method name inconsistent with the examples, as long as it is recognizably equivalent | 1/1 |
| 6     | numberOfLines returns appropriate value (algorithm) | Perform the return value calculation in the constructor; Return a different number of lines than getLines produces, as long as the number returned is the correct number for the message; return an incorrect number of lines for the message, as long as the number returned is exactly the number of lines produced by getLines; use a method name inconsistent with the examples, as long as it is recognizably equivalent  | incorrectly account for the final line | 1/1 |
| 7     | getLines returns null appropriately | Identify null case in a method other than getLines; Use an invalid call to length or == in guard for null return; Use a method name inconsistent with the examples, as long as it is recognizably equivalent | Guard the return with incorrect logic | 1/1 |
| 8     | Calls substring and length (or equivalent) on String objects | Calculate substring parameter values incorrectly; Call substring and/or length from a method other than getLines; Use a method name inconsistent with the examples, as long as it is recognizably equivalent | Fail to call substring or length on String objects; Call substring or length with an incorrect number of parameters, with a parameter of an incorrect type, or with incorrectly ordered parameters, anywhere in the class | 1/1 |
| 9     | getLines constructs the delimited sign output appropriately (algorithm) | Call substring and/or length incorrectly; Fail to return the constructed String (return not assessed); Handle the empty string /null case incorrectly; Construct the output in the constructor; Use a method name inconsistent with the examples, as long as it is recognizably equivalent | End the constructed output with a ; or extraneous spaces; Modify the contents of message or width after they have been initialized (no additional –1 penalty) | 1/1 |


**Score: 9/9**

**1/1**


## Major Takeaways

- Make a diagram of the class, variables, and methods
- Read descriptions of methods carefully as they tell you exactly what to do
- be careful of null outputs (make sure to include them!)
- Use sample code execution sequence to test code by mentally inputting them into your code
