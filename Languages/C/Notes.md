- There are macros in c, these are processed by preprocessor before executing  the program. you can define macros by adding # before them. they are not variables and their value cannot be changed once they were defined. we can define constants, functions-like macros, conditional compilation, complex expressions, etc... in macros.
		Example: # define max 100(here max value is defined as 100, in similar way we can define different macros.)
- "%4.1f " - f(float), 4(minimum field width specifies that the printed number should occupy at least 4 characters of space.), .1(specifies the number of digits to be displayed after the decimal point.)

- pass by value, pass by reference.(same as call by value, call by reference in c language)
- User defined functions - Function Prototype, Function definition, Function call.
- Function Prototype- is a declaration of a function that provides information about its name, return type, and parameters to the compiler before the function is actually defined or called. This allows the compiler to check for correct usage of the function when it is called.
- In 3 ways we can declare constants in c: 
		Const, # define, Enum
-  Syntax of main function:
		return_type ****main()**** {  
		    // Statement 1;
			// and so on..
			return value;
			}
- Call back Functions- 
- Malloc, Calloc & realloc
- Using Dynamic Memory