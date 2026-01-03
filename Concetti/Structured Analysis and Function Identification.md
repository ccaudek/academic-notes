---
type: Zettel
title: Structured Analysis and Function Identification
description: null
modificationDate: 2024-11-14 22:40
tags: [coding]
coverImage: null
---

At a very high level, Functional Decomposition consists of a series of steps such as those outlined below:

1. Find/Identify the inputs and outputs of the system.

2. Define how the inputs are converted to the outputs. This will help identify the top most, high level function(s).

3. Look at the current function(s) and try to break them down into a list of sub functions. Identify what each sub function should do and what its inputs and outputs are.

4. Repeat step 2 for each function identified until the functions identified can’t or should not be decomposed further.

5. Draw a diagram of the function hierarchy you have created. Viewing the functions and their relationships is a very useful thing to do as it allows developers to visualise the system functionally. There are many CASE (Computer Aided Software Engineering) tools that help with this but any drawing tool (such as Visio) can be used.

6. Examine the diagram for any repeating functions. That is, functions that do the same thing but appear in different places in the design. These are probably more generic functions that can be reused. Also examine the diagram to see if you can identify any missing functions.

7. Refine/Design the interfaces between one function and another. That is, what data/information is passed to and from a function to a sub function as well as between functions.

## Pseudo Code

An example of pseudo code.

```bash
This program calculates the Lowest Common multiple for excessively long input values
function lcmNaive(Argument one, Argument two) {
    Calculate the lowest common variable of 
      Argument 1 and Argument 2 by dividing their 
      product by their Greatest common divisor product
    return lowest common multiple
end
}
function greatestCommonDivisor(Argument one, Argument two) { 
   if Argument two is equal to zero 
     then return Argument one
    return the greatest common divisor
end
}
{
In the main function
   
   print prompt "Input two numbers"
   Take the first number from the user
   Take the second number from the user
   Send the first number and second number to the 
   lcmNaive function and print the result to the user   
}
```

