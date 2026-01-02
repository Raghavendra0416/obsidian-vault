

```JavaScript
const taskInput = document.getElementById('task-inp');
const addButton = document.getElementById('add-btn');
const viewButton = document.getElementById('view-btn');

// Load existing tasks or create empty array
let tasks = JSON.parse(sessionStorage.getItem('tasks')) || [];

addButton.addEventListener('click', function() {
    const task = taskInput.value;
    
    // Add to array
    tasks.push(task);
    
    // Save to sessionStorage
    sessionStorage.setItem('tasks', JSON.stringify(tasks));
    
    // Clear input
    taskInput.value = '';
    
    alert('Task added!');
});

viewButton.addEventListener('click', function() {
    window.location.href = 'page2.html';
});
```