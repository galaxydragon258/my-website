<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Greeting Page</title>

  <style>
    body {
      background: linear-gradient(135deg, #74ebd5, #acb6e5);
      font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
      text-align: center;
      margin: 50px;
    }

    input, button {
      padding: 10px;
      margin: 5px;
      border-radius: 5px;
    }

   
    button{
      background-color: rgb(24, 207, 24);
      color : white;
      cursor: pointer;
      transition: background-color 0.3s, transform 0.5s;
    }

    button:hover{
      background-color: rgb(24, 207, 24);
      transform: scale(1.1);
    }

    @keyframes buttonClick{
      0%{transform: scale(1);}
      50%{transform: scale(1.1);}
      100%{transform: scale(1);}
    }
    button:active{
      animation: buttonClick 0.3 ease-in;
    }

    .fade-in {
      animation: fadeIn 1s ease-in;
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: translateY(-10px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
      
    }

    body.dark-mode{
      background: linear-gradient(135deg, #333, #555);
      color:white;
    }

    button.dark-mode{
      background-color: black;
      color: white;
    }
  </style>
</head>



<body>
  <p>Hello, bro 👋</p>

  <input type="text" id="input" placeholder="Enter Your Name:">
  <button onclick="btn()" id="btn">Click Me</button>
  <button onclick = "forgot()" id = for> Forget</button>
  <button onclick= "dark()"> Toggle Dark Mode</button>
  
  
  <p id="output"></p>

  <script>
    window.onload = function() {
      const saved = localStorage.getItem("titi");
      if (saved != null) {
        const output = document.getElementById("output");
        output.textContent = "Hello " + saved;
        output.classList.add("fade-in");
      }
      else{
        output.textContent = "Please Enter Your Name";
      }
    };

    function btn() {
      let name = document.getElementById("input").value;
      const output = document.getElementById("output");

      if (name == "") {
        output.textContent = "Please enter your name!";
      } else {
        localStorage.setItem("titi", name);

        output.classList.remove("fade-in");
        void output.offsetWidth; // force reflow

        output.textContent = "Hello " + name;
        output.classList.add("fade-in");
      }
    }

    function forgot(){
      localStorage.removeItem("titi");
      const output = document.getElementById("output");
      alert("successfully removed your name");
      output.textContent ="Please Enter Your Name";
      
      document.getElementById("input").value = ""; 
      document.getElementById("input").focus();
      
    }

    function dark(){
      document.body.classList.toggle("dark-mode");
    }

   



    
  </script>
</body>
</html>
