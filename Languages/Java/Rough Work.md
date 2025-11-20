Try with resources;
- this is used when we want to automatically close the file classes(like input reader, input reader buffer).
- we can write only auto closable classes(the classes which implement auto closable(by opening that class we can see if it was auto closable or not)) as resources in try block.
- we have to call them as resources instead of parameters because in methods we won't initialize any value but here we will initialize values. the values are separated by comma in methods but here semicolon.
- we can keep only single try block and if needed we can keep multiple catch blocks. or we can keep multiple try catch bocks.
-  system.exit()- will not run finally block
- learn how to keep resources in try block, how to throw user defined and custom exceptions


