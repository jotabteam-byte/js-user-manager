const API = "https://python-automation-eugz.onrender.com";

async function addUser() {
  const name = document.getElementById("name").value;
  const email = document.getElementById("email").value;

  await fetch(API + "/register", {
    method: "POST",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify({ name, email })
  });

  alert("User Registered!");

  document.getElementById("name").value = "";
  document.getElementById("email").value = "";
}

async function loadUsers() {
  const response = await fetch(API + "/users");
  const users = await response.json();

  const list = document.getElementById("userList");
  list.innerHTML = "";

  users.forEach(user => {
    const li = document.createElement("li");
    li.textContent = user.name + " - " + user.email;
    list.appendChild(li);
  });
}

window.onload = loadUsers;

