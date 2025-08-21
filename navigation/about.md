---
layout: post
title: About
permalink: /about/
comments: true
---

## As a conversation Starter

Here are some places I have lived.

<comment>
Flags are made using Wikipedia images
</comment>

<style>
    /* Style looks pretty compact, 
       - grid-container and grid-item are referenced the code 
    */
    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Dynamic columns */
        gap: 10px;
    }
    .grid-item {
        text-align: center;
    }
    .grid-item img {
        width: 100%;
        height: 100px; /* Fixed height for uniformity */
        object-fit: contain; /* Ensure the image fits within the fixed height */
    }
    .grid-item p {
        margin: 5px 0; /* Add some margin for spacing */
    }

    .image-gallery {
        display: flex;
        flex-wrap: nowrap;
        overflow-x: auto;
        gap: 10px;
        }

    .image-gallery img {
        max-height: 150px;
        object-fit: cover;
        border-radius: 5px;
    }
</style>

<!-- This grid_container class is used by CSS styling and the id is used by JavaScript connection -->
<div class="grid-container" id="grid_container">
    <!-- content will be added here by JavaScript -->
</div>

<script>
    // 1. Make a connection to the HTML container defined in the HTML div
    var container = document.getElementById("grid_container"); // This container connects to the HTML div

    // 2. Define a JavaScript object for our http source and our data rows for the Living in the World grid
    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
        {"flag": "0/01/Flag_of_California.svg", "greeting": "Hey", "description": "California - forever"},
        {"flag": "b/b9/Flag_of_Oregon.svg", "greeting": "Hi", "description": "Oregon - 9 years"},
        {"flag": "b/be/Flag_of_England.svg", "greeting": "Alright mate", "description": "England - 2 years"},
        {"flag": "e/ef/Flag_of_Hawaii.svg", "greeting": "Aloha", "description": "Hawaii - 2 years"},
    ];

    // 3a. Consider how to update style count for size of container
    // The grid-template-columns has been defined as dynamic with auto-fill and minmax

    // 3b. Build grid items inside of our container for each row of data
    for (const location of living_in_the_world) {
        // Create a "div" with "class grid-item" for each row
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";  // This class name connects the gridItem to the CSS style elements
        // Add "img" HTML tag for the flag
        var img = document.createElement("img");
        img.src = http_source + location.flag; // concatenate the source and flag
        img.alt = location.flag + " Flag"; // add alt text for accessibility

        // Add "p" HTML tag for the description
        var description = document.createElement("p");
        description.textContent = location.description; // extract the description

        // Add "p" HTML tag for the greeting
        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;  // extract the greeting

        // Append img and p HTML tags to the grid item DIV
        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);

        // Append the grid item DIV to the container DIV
        container.appendChild(gridItem);
    }
</script>

## 👋 About Me

### 📘 My Journey
<div class="about-section">
  <ul>
    <li>Born & raised in San Diego 🌴</li>
    <li>Monterey Ridge Elementary → Oak Valley Middle → Del Norte High School 🎓</li>
    <li>Proud to have lived in San Diego my whole life</li>
  </ul>
</div>

### 🔧 Technical Passions
<div class="about-section">
  <ul>
    <li>Robotics 🤖 – Director of Assembly & Mechanics, working with industrial tools and companies</li>
    <li>Design & Manufacturing 🛠️ – Love using CAD to engineer and manufacture complex parts</li>
    <li>Rocketry 🚀 – Create simulations in OpenRocket and build real rockets with laser-cut fabrication</li>
    <li>Innovation 💡 – Passionate about problem-solving and turning ideas into solutions</li>
  </ul>
</div>

### 🎶 Personal Interests
<div class="about-section">
  <ul>
    <li>Tennis 🎾 – Enjoy playing both casually and competitively</li>
    <li>Piano 🎹 – Over 12 years experience, completed ABRSM exams</li>
    <li>Family & Friends 🤝 – Value spending quality time and building strong connections</li>
  </ul>
</div>


<style>


body {
    background: linear-gradient(135deg, #2c5aa0, #000000);
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
}


.scroll-bar {
    position: fixed;
    top: 0;
    right: 10px;
    width: 15px;
    height: 100vh;
    background: rgba(255,255,255,0.3);
}

.scroll-fill {
    width: 100%;
    background: #74b9ff;
    height: 0%;
}

.about-section {
    margin-bottom: 2rem;
    border: 3px solid rgba(255, 255, 255, 0.68);
    padding: 25px;
    border-radius: 15px;
}

.about-section:hover {
    transform: translateY(-8px);
    box-shadow: 0 15px 25px rgba(255,255,255,0.1);
    transition: all 0.4s ease;
}

.about-section ul {
    list-style: none;
    padding-left: 0;
}

.about-section li {
    margin-bottom: 0.5rem;
    font-size: 1rem;
}


.slideshow {
    width: 300px;
    height: 200px;
    margin: 20px auto;
    border-radius: 10px;
    overflow: hidden;
}

.slideshow img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}


</style>

<script>
window.onscroll = () => {
    document.getElementById('fill').style.height = (window.pageYOffset / (document.body.scrollHeight - window.innerHeight)) * 100 + '%';
};
</script>


<script>
let photos = [
    "https://raw.githubusercontent.com/tp254/student/main/assets/assets/IMG_2933.JPG",
    "https://raw.githubusercontent.com/tp254/student/main/assets/assets/IMG_9919.JPG",
    
    
];

let currentPhoto = 0;

setInterval(() => {
    currentPhoto++;
    if (currentPhoto >= photos.length) currentPhoto = 0;
    document.getElementById('slideImg').src = photos[currentPhoto];
}, 2000);
</script>


<div class="scroll-bar">
    <div class="scroll-fill" id="fill">
</div>


<div class="slideshow">
    <img id="slideImg" src="https://raw.githubusercontent.com/tp254/student/main/assets/assets/IMG_2933.JPG" alt="My Photos">
    <img id="slideImg" src="https://raw.githubusercontent.com/tp254/student/main/assets/assets/IMG_9919.JPG" alt="My Photos">
</div>
