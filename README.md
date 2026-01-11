const API = "https://python-automation-eugz.onrender.com";

async function addUser() {
  const name = document.getElementById("name").value;
  const email = document.getElementById("email").value;

  await fetch(API + "/register", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
    },
    body: JSON.stringify({ name, email }),
  });

  alert("User Registered!");
  document.getElementById("name").value = "";
  document.getElementById("email").value = "";
}
