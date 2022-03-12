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
### Deleting a todo 
We have placed a trashcan icon infront of our todo items, we want the users to click on the trashbin to delete that todo. We will reference the ul through the todos class to access all the li's in it, add a click event listener to it and a remove method to the clicked li. 

````
const list = document.querySelector('.todos');
list.addEventListener('click', e => {
  if(e.target.classList.contains('delete')){
      e.target.parentElement.remove();
  }
});
````
### Searching todos 
In our htmk, we have another form, on the top, to search individual todo items, our goal is to show the users todos that matches their search terms. 
This seems a bit tricky. Here is how I have tackled it: 
We first need to get the terms a users is typing in the search bar, we can access that data in realtime by referncing the class designated to search bar, it is called search, we then access the input via the input tag. 
````
const search = document.querySelector('.search input');
````
Then we will add a keyup event listerner, and a call back function like so: 
````
search.addEventListener('keyup', () => {
    const term = search.value.trim().toLowerCase();
    filterTodos(term);

});
````
The filterTodos function that we are calling above, serves the purpose of filtering users inout and then two things: hiding the todos that do not match with user's input and the second is only showing the one that is a match. 

````
const filterTodos = (term) => {
   
   
    Array.from(list.children)
   .filter((todo)=> !todo.textContent.toLowerCase().includes(term))
   .forEach((todo) => todo.classList.add('filtered'));  

   Array.from(list.children)
   .filter((todo)=> todo.textContent.toLowerCase().includes(term))
   .forEach((todo) => todo.classList.remove('filtered')); 
};


````