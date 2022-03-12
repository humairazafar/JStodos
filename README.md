## Technologies/Languages used
- JavaScript
- CSS Bootstrap
- HTML
This simple todo list is created with html, javascript and css. The functionality is that users can add, and delete the to the list item, and they can also searh for a todo in this list. 

### HTML code
The htmk is simple, one h1 and a ul with multiple li. UL has a class of todos for us to reference in our js code. Each li tag also has a span tag for the text of the list. The classes in the li tag are there for cssbootstrap, we are also importing fontawesome to display a trashcan in front of each todo list object. 

````
 <ul class="list-group todos mx-auto text-light">
            <li class="list-group-item d-flex justify-content-between align-items-center text-light">
                <span>play macman</span>
                <i class="far fa-trash-alt delete"></i>
            </li>
````
The html file also contains a form, for the users to add to the todo list. The form has input set for text, and a class of add for referencing in our js code. 

### Creating functionalities with JavaScript

### How to add a todo 
In order to add a new todo, we will reference the form text item in our code via documen.query selector. We will add an event listerner for submit, append user's input to the ul, use trim method to tackle any spaces, and a function created for generate the html template to be appended in the ul. 
````
const addForm = document.querySelector('.add');

const generateTemplate = (todo) => {
const html = 
 `<li class="list-group-item d-flex justify-content-between align-items-center text-light">
    <span>${todo}</span>
    <i class="far fa-trash-alt delete"></i>
 </li>
`;
 list.innerHTML += html;

};


addForm.addEventListener('submit', e => {

  e.preventDefault();
  const todo = addForm.add.value.trim();
  
  if(todo.length){
    generateTemplate(todo);
    addForm.reset();
  }
  
});
const generateTemplate = (todo) => {
const html = 
 `<li class="list-group-item d-flex justify-content-between align-items-center text-light">
    <span>${todo}</span>
    <i class="far fa-trash-alt delete"></i>
 </li>
`;
 list.innerHTML += html;

};
````