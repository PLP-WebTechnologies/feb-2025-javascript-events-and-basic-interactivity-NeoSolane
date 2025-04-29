<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-widith, initial-scale=1">
        <title>JS Event Playground</title>
        <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Welcome to My Interactive Playground</h1>
    <button id="magicButton">Click Me!</button>
    <div class="gallery>
        <img id="galleryImage" src="https://via.placeholder.com/300x200?text=Image+1" alt="=Gallery Image">
    <br>
    <button id="nextImage">Next Image</button>
    </div>
    <div class="tabs">
        <button class="tab" data-tab="tab1">Tab 1</button>
        <button class="tab" data-tab="tab2">Tab 2</button>
        <div id="tab1" class="tabcontent">
            <p>This is content tab 1.</p>
        </div>
    <div id="tab2" class="tabcontent">
        <p>This is content tab 2.</p>
    </div>
</div>
<form id="signUpForm">
    <h2>Sign Up</h2>
    <input type="text" id=""name" Placeholder="Name" required><br>
    <input type="email" id="email" placeholder="Email" required><br>
    <input type="password" id="password" placeholder="password" required><br>
    <button type="submit"></button>
    <p id="formMessage"></p>
</form>
<script src="script.js"></script>
</body>
</html>


body {
    font-family: Arial, sans-serif;
    text-align: center;
    padding: 20px;
}

button {
    padding: 10px 20px;
    margin: 10px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

button:hover {
    background-color: #add8e6;
}

.gallery {
    margin-top: 20px;
}

.tabcontent {
    border: 1px solid #ccc;
    padding: 10px;
    margin-top: 10px;
}

input {
    margin: 5px;
    padding: 8px;
    width: 200px;
}

#forMessage {
    color: blueviolet;
    margin-top: 10px;
}

@keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-5px); }
    50% { transform: translateX(5px); }
    75% { transorm : translateX(-5px); }
    100% { transform: translateX(0); }
}

.shake {
    animation: shake 0.5s;
}


const magicButton = document.getElementById('magicButton');
magicButton.addEventListener('click', () => {
    magicButton.textcontent = "You clicked Me!";
    magicButton.style.backgroundColor = "lightgreen";
});

magicButton.addEventListener('dbclick' , () => {
    alert("secrete double-click detected!");
});

document.addEventListener('keydown', (e) => {
    console.log('key pressed: ${e.key}');
});

const images = [
    'https://via.placeholder.com/300x200?text=Image+1',
    'https://via.placeholder.com/300x200?text=Image+2',
    'https://via.placeholder,com/300x200?text=Image+3',
];
let currentImage = 0;
const galleryImage = document.getElementById('galleryImage');
const nextImageButton = document.getElementById('nnextIage');
nextImageButton.addEventListener('click', () => {
    currentImage = (currentImage + 1) % images.length;
    galleryImage.src = images[currentImage];
});

 const tablinks = document.querySelectorAll('.tablink');
 const tabcontents = document.querySelectorAll('.tabcontent');

 tablinks.forEach(button => {
    button.addEventListener('click', () => {
        const tab = button.getAttribute('data-tab');
        tabcontents.forEach(tc => {
            tc.style.display = 'none';
        });
        document.getElementById(tab).style.display = 'block';
    });
 });

 const signupForm = documentById('signupForm');
 const formMessage = documentById('formMessage');
 
 signupForm.addEventListener('submit', (e) => {
    e.preventDefault();

    const name = document.getElementById('name'). Value.trim();
    const email = document.getElementById('email'). value.trim();
    const password = document.getElementById('password'). value.trim();
    if (!name || !email || !password) {
        formMessage.textContent = "please fill in all fields.";
        return;
    }
    if (!email.includes('@') || !email.includes('.')) {
        formMessage.textcontent = "please enter a valid email.";
        return;
    }
    if (password.length <8) {
        formMessage.textcontent = "password must be at least 8 characters.";
        return;
    }
    formMessage.style.color = "purple";
    formMessage.textContent = "form submitted successfully!";
 });

 const passwordInput = document.getElementById('password');
 passwordInput.addEventListener('input', () => {
    if (passwordInput.value.length < 8) {
        passwordInput.classList.add('shake');
        formMessage.textContent = "password too short!";
        formMessage.style.color = "red";
    } else  {
        passwordInput.classList.remove('shake');
        formMessage.textContent = "";
    }
 });
  
