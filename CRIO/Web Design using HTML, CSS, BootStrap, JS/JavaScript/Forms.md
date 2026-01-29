What is Form and how do we control the form using JS.
	- How data is taken from the form.
	- How to stop the default behavior of form using `event.preventDefault()`
- Three ways to fetch the user entered values from the form:
```JavaScript
let formEle.document.getElementId("FormData");

formELe.eventListner("submit",(e) => {
//way
let name=document.getElementID("Specific field in the form").value;
//another way
let name= e.target.elements["name attribute from the field inside the form"].value;
//another way
let name= formEle.elemnts["name attribute from the field inside the form"].value;
// We are replacing the e.target with formEle
}
```
- When 2 or more submit buttons are used in the form, then both the submit buttons will work. We only need to use one submit button and if we need another buttons we can use type as button instead of submit.

- 