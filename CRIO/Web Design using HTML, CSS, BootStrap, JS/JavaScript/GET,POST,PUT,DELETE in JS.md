### GET:
- We use fetch to get the data from the backend.

```Javascript
fetch("url to fetch the data");
```
- Fetch will return promise. So, use "await, try, catch, then, async functions" to handle the promise.
### POST:
- We use fetch to get the data from the backend.
- Backend Dev/ Document provides how the body should look like for the body.
- If the data needs to be sent to backend we need to convert the JSON to the string. We use Stringfy function to convert the data to the string.
- Instead of providing the data directly it is best to provide the data through a string. If we provide the json data we need to send directly, then the address of the data in the memory location will also be sent. 

How we do it:
```JavaScript
fetch("url to fetch the data",{
method: "POST", //Instead of post, we need to update we can use method:'PUT'

body: JSON.stringfy({
//How the data should look will be provided by developer.
//Example Data:
title:'foo',
body:'bar',
userId: 1,
}),

headers: {
	'Content-type':'application/json;charset=UFT-8',
},

}).then((response)=> response.json())
.then((json)=>console.log(json));
```
- The mandatory fields are:
	- Method: describes which method we are using
	- Body: describes the data.
	- Headers: describes what type of content we are sending. It is similar to meta data in the head tag in html.
- For the sting data to convert to the json again, we need to use "parse function".
- When the data is sent to backend, an id will be created and will be added to the data and sent to the backend. we can see the id if we fetch that data from the backend.