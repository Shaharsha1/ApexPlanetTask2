# ApexPlanetTask2
 Enhance HTML and CSS skills, and learn JavaScript for DOM manipulation. 
 
index.html  file

 <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Web Practice Project</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <!-- Navigation -->
  <header>
    <h1>My Web Practice Project</h1>
    <nav>
      <a href="#contact">Contact Form</a>
      <a href="#todo">To-Do List</a>
    </nav>
  </header>

  <!-- Main Content Layout -->
  <main class="grid-container">
    
    <!-- Contact Form -->
    <section id="contact">
      <h2>Contact Form</h2>
      <form class="contact-form">
        <label>Name:</label>
        <input type="text" id="name" required>

        <label>Email:</label>
        <input type="email" id="email" required>

        <label>Subject:</label>
        <input type="text" id="subject">

        <label>Message:</label>
        <textarea id="message" rows="4"></textarea>

        <button type="submit">Submit</button>
      </form>
    </section>

    <!-- To-Do List -->
    <aside id="todo">
      <h2>To-Do List</h2>
      <input type="text" id="taskInput" placeholder="Enter task">
      <button id="addTask">Add</button>
      <ul id="taskList"></ul>
    </aside>
  </main>

  <!-- Footer -->
  <footer>
    <p>&copy; 2025 Web Practice Project</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>


style.css file

/* Reset default margins */
body, h1, h2, p {
  margin: 0;
  padding: 0;
  font-family: Arial, sans-serif;
}

/* Header with Flexbox */
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  background: #333;
  color: #fff;
}

header nav a {
  color: white;
  margin: 0 10px;
  text-decoration: none;
}

/* Grid Layout for main content */
.grid-container {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 20px;
  padding: 20px;
}

/* Contact Form */
.contact-form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.contact-form input, 
.contact-form textarea, 
.contact-form button {
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
}

.contact-form button {
  background: #4CAF50;
  color: white;
  cursor: pointer;
}

/* To-Do List */
#todo {
  background: #f4f4f4;
  padding: 15px;
  border-radius: 5px;
}

#taskList li {
  display: flex;
  justify-content: space-between;
  padding: 5px;
  background: #ddd;
  margin-bottom: 5px;
  border-radius: 3px;
}

#taskList li button {
  background: red;
  color: white;
  border: none;
  cursor: pointer;
}

/* Footer */
footer {
  text-align: center;
  padding: 10px;
  background: #eee;
  margin-top: 20px;
}

/* Responsive Layout */
@media (max-width: 600px) {
  .grid-container {
    grid-template-columns: 1fr;
  }
}


script.js file


// Contact Form Validation
document.querySelector(".contact-form").addEventListener("submit", function(e) {
  let name = document.getElementById("name").value.trim();
  let email = document.getElementById("email").value.trim();
  let error = "";

  if (name === "") {
    error += "Name is required.\n";
  }
  if (email === "" || !email.includes("@")) {
    error += "Valid email is required.\n";
  }

  if (error) {
    alert(error);
    e.preventDefault();
  }
});

// To-Do List Functionality
document.getElementById("addTask").addEventListener("click", function() {
  let taskInput = document.getElementById("taskInput");
  if (taskInput.value.trim() !== "") {
    let li = document.createElement("li");
    li.textContent = taskInput.value;

    let btn = document.createElement("button");
    btn.textContent = "Delete";
    btn.addEventListener("click", () => li.remove());

    li.appendChild(btn);
    document.getElementById("taskList").appendChild(li);
    taskInput.value = "";
  }
});




