	#### Read & Update element content:
element.textContent;
element.innerHTML;

### Read attributes:
element.getAttribute('Id');
element.value;

#### Set Attributes:
element.setAttribute("attributeName",value)

-------------------------------------------
#### Create:
document.createEement();

---
#### Accessing:
document.getElementById()
document.getElementByClassName()
document.getElementByTagName()
document.querySelector('(# for ID),(. for class), (element));
document.querySelectorAll('(# for ID),(. for class), (element));

---
#### Modifying:

For Elements:
use textContent, innerHTML for setting element content.

For Attributes:
element.setAttribute('class','new-class or value');
element.id = 'new Id'

Update Style:
element.style.color/fontSize = value;

Remove:
element.remove();
parent.removeChild(child)
parent.innerHTML = '';
element.removeAttribute('class');

---