# To-Do List App

This is a simple to-do list application built with HTML, CSS, and JavaScript. It allows users to add tasks, mark them as completed, and remove them from the list. The application utilizes local storage to save tasks, enabling users to access their to-do list even after closing the browser.

## Features

- Add tasks to the list
- Mark tasks as completed by clicking on them
- Remove tasks from the list
- Tasks are saved locally, allowing persistence across sessions

## Installation

There is no installation required for this application. Simply clone the repository or download the source code files to your local machine and open the `index.html` file in your web browser.

## Usage

1. Open the `index.html` file in your web browser.
2. Enter a task in the input box provided.
3. Press the "Enter" key or click the "Add" button to add the task to the list.
4. Click on a task to mark it as completed. Click again to undo.
5. To remove a task, click on the 'x' icon next to it.

## Code Logic

```javascript
const inputBox = document.getElementById("input-box");
const listContainer = document.getElementById("list-container");

// Function to add a new task to the list
function addTask() {
  if (inputBox.value === "") {
    alert("You must select a task");
  } else {
    let li = document.createElement("li");
    li.innerHTML = inputBox.value;
    listContainer.appendChild(li);
    let span = document.createElement("span");
    span.innerHTML = "\u00d7";
    li.appendChild(span);
  }
  inputBox.value = "";
  saveData();
}

// Event listener to toggle task completion and remove tasks
listContainer.addEventListener(
  "click",
  function (e) {
    if (e.target.tagName === "LI") {
      e.target.classList.toggle("checked");
      saveData();
    } else if (e.target.tagName === "SPAN") {
      e.target.parentElement.remove();
      saveData();
    }
  },
  false
);

// Function to save tasks to local storage
function saveData() {
  localStorage.setItem("data", listContainer.innerHTML);
}

// Function to retrieve and display tasks from local storage
function showTask() {
  listContainer.innerHTML = localStorage.getItem("data");
}
showTask();
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

Special thanks to [OpenAI](https://openai.com) for providing assistance in generating this README file.

## Contributing

Contributions are welcome! Fork the repository and submit a pull request with your changes.
