---
title: Anteriore Exam
draft: false
tags:
  -
---
# Rules #

1. Start with *==Anteriore start==*, end with ==*Anteriore end*==
2. To declare variables, use ==*Armory.[int, float or boolean]*== (i.e., Armory.int to declare an int)
	- Will take and keep current value of int in the current context
	- Armory can only keep 1 value. **Declaring a new value will replace the value**
3. Float is a decimal, 1.0, 4.5, 99.12
4. Int is a whole number that does not have a decimal place
5. Boolean uses true and false
6. ==*Assume*== used to assign temporary values to a certain variable without changing value outside of context
```
		Anteriore start
		Armory.int = 10
			// Armory.int is 10 in this context
		Assume {
			Armory.int = 20
			// Armory.int is 20 in this context
		}
		// Armory.int is 10 in this context
		Anteriore end
		
```
- Assume is a function, variables are locally scoped
7. To store the sum, product, or quotient of different equations, do Armory * [value] and it will store answer where applicable (i.e., if int is the answer, stored in int)
8. Operators
	- <, 'less than', compare current float or int value to current float or int respectively
		- Stored in Armory.boolean, produces true or false
	- >, 'greater than', compare current float or int value to current float or int respectively
		- Stored in Armory.boolean, produces true or false
	- '\*' is multiply, '/' is divide, '-' is subtract, '+' is addition, produces float or int and stored to Armory.int or Armory.float depending on produced
	- Operations can be stacked. Done left to right.
9. Float and int default have 0 if not yet assigned anything (null), boolean is default true
10. ==*Assemble*== writes all values of Armory on screen in this order: **int, float boolean**
	- if value has not been changed, 'null' is result.
11. To do repetition in code, its as simple as declaring ==*Again*== in an Assume context to repeat code. ==*Again*== is declared alongside a **value** that will only top until equal. 
	- This is a loop

Highlighted words are ==**keywords**==

```
Anteriore start
Assume {
	Armory.int = 20 //assumed armory.int to 20
	Armory + 2 // what the fuck is armory? the entire of the array?
	Assemble // should output the 22, null, null
	Again 22 // repeats Assume function again
	}
```


**A question I asked to Seaver**
Seeing the example usage of the Again keywords. We see that it is first established Armory.int = 20, then we add into Armory. This should go to the int then we declare the Again. 

I'd like to ask a few questions:
1. Considering the example, is it correct to interpret Armory is a global scope?
2. If once we get out of the Assume function, would the local scope nature of Armory.int cause that variable to be subtracted from Armory? 
3. In relation to question 2, supposed there is no assume function, if we declared Armory.int = x
   Armory + y
   Should the output be x+y, null, null?
4. Is the Again keyword inclusive of the function it is in? Meaning that after the Again happens, the next pass is Again 21, or will the Again value start on the next pass? Meaning we do once we get to Again, we pass it, that's the first of 22?


# Questions 

**Question 1**: What is the output of the code?
```
Anteriore start
Armory.int = 20 //declated Armory.int in this context to be 20
Armory * Armory.int // Armory specifically its int becomes 0 because two diff contexts
Assemble //0, null, null
Assume{
	Armory + 2 
	Assemble 
	Armory < 3 
	Again true
}
Anteriore end
```

**Answer**
In Assume function 
First pass
	0 + 2 = 2
	2,null,null
	False
Second Pass
	2 + 2 = 4
	4, null, null
	True
	Exit Assume

Answer: **4, null, null**

Possible questions to Seaver:


**Question 2**: What is the output of the code?

```
Anteriore start
Assume{
	Armory - 2 // -2,null,null
	Assume{
		Assemble // -2, null, null
	}
	Armory > 0.0 // false
	Armory + 2.0 // float value, 2.0
	Again true // still currently false , need to do one more pass to change conditional
	Assemble // -2, 2.0, false 
}
Anteriore end
```

Possible questions to Seaver:

**Question 3**: Write code to determine output of Summation of (n). The answer should be stored in Armory.float

i.e., Summation of 5 is 5 + 4 + 3 + 2 + 1 = 15

Pseudocode
Start
Assume{
	Declare n
	Function to Loop when adding into n. (so Assume {... Again n})
	Assemble 
}
End