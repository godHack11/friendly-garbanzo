# To-Do-List using html, CSS & JS

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <script src="script1.js" defer></script>
    <link rel="stylesheet" href="style.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">

    <title>Document</title>
</head>

<body>
    <div class="container-title">
        <h1>To Do List 🕐</h1>
    </div>
    <div class="container">
        <div class="inputcol">
            <textarea name="text" class="textarea"></textarea>
            <button type="button" class="buttoninput"><i class="fa-solid fa-check"></i></button>
        </div>
    </div>
    <div class="todolist">
        
    </div>
</body>

</html>

Using CSS

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Times New Roman', Times, serif;
}

body {
    background-image: linear-gradient(to right, #605e7e, #6b73c1, #37b3cc);
    margin: 50px 2%;
}

/* container title */
.container-title {
    font-size: 25px;
    text-align: center;
    margin: 0 0 30px 0;
    color: white;
    text-shadow: 3px 1px black;
}

/* container */
.inputcol {
    display: grid;
    column-gap: 5px;
    grid-template-columns: 60% 10%;
    justify-content: center;
    margin-top: 10px;
}

.textarea {
    min-height: 50px;
    height: 50px;
    max-width: 100%;
    min-width: 100%;
    border-radius: 10px;
    border-color: #333;
    font-size: 20px;
    padding: 10px 10px;
    overflow: auto;
    overflow-x: hidden;
}

.textarea::-webkit-scrollbar-track {
    border-radius: 10px;
    background-color: #333;
}

.textarea::-webkit-scrollbar {
    width: 10px;
    cursor: pointer;
}

.textarea::-webkit-scrollbar-thumb {
    border-radius: 10px;
    background-color: #8f8acc;
    cursor: pointer;
}

.textarea:focus {
    outline: none;
}

.buttoninput {
    border-radius: 10px;
    border-color: #333;
    background-color: white;
    font-size: 20px;
}

.buttoninput:hover {
    background-color: #8f8acc;
    color: white;
}

/* js */
.todolist {
    margin-top: 20px;
}

.itemall {
    display: grid;
    grid-template-columns: 60% 5% 5%;
    justify-content: center;
    margin-bottom: 2px;
}

.item, .check-button, .trash-button {
    border: none;
    background-color: white;
    min-height: 50px;
    padding: 10px 10px;
}

.item {
    word-wrap: break-word;
    word-break: break-all;
    border-radius: 10px 0 0 10px;
    display: grid;
    align-content: center;
    font-size: 20px;
}

.check-button, .trash-button {
    font-size: 15px;
}

.trash-button {
    border-radius: 0 10px 10px 0;
}

.check-button:hover {
    background-color: #37b3cc;
    color: white;
}

.trash-button:hover {
    background-color: #6b73c1;
    color: white;
}

.checklist {
    text-decoration: line-through;
}

.fa-check, .fa-trash {
    pointer-events: none;
}

button, .check-button, .trash-button {
    cursor: pointer;
}

And now using JS

const inputtdl = document.querySelector('.textarea')
const buttontdl = document.querySelector('.buttoninput')
const listtdl = document.querySelector('.todolist')

function clickButton(e) {
    e.preventDefault()
    addTodo()
}

// adding todoList
function addTodo() {
    const itemall = document.createElement('div')
    itemall.classList.add('itemall')

    const item = document.createElement('p')
    item.classList.add('item')
    item.innerText = inputtdl.value
    itemall.appendChild(item)

    if (inputtdl.value === '') return

    const checkbutton = document.createElement("button")
    checkbutton.innerHTML = '<i class="fa-solid fa-check"></i>'
    checkbutton.classList.add("check-button")
    itemall.appendChild(checkbutton)

    const trashbutton = document.createElement("button")
    trashbutton.innerHTML = '<i class="fa-solid fa-trash"></i>'
    trashbutton.classList.add("trash-button")
    itemall.appendChild(trashbutton)

    listtdl.appendChild(itemall)
    inputtdl.value = ''
}

// checking and delete todoList 
function okdel(e) {
    const item = e.target

    // check
    if (item.classList[0] === 'check-button') {
        const todolist = item.parentElement
        todolist.classList.toggle('checklist')
    }

    // delete
    if (item.classList[0] === 'trash-button') {
        const todolist = item.parentElement
        todolist.remove()
    }
}

buttontdl.addEventListener('click', clickButton)
listtdl.addEventListener('click', okdel)
