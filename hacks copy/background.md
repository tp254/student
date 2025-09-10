---
layout: base
title: Background with Object
description: Use JavaScript to have an in motion background.
 # Below are images for the game
sprite: images/platformer/sprites/cartoon_rocketship-removebg-preview.png
background: images/platformer/backgrounds/spacebackground(3).jpeg
permalink: /background
---

 <!-- Below is the Game World -->
<canvas id="world"></canvas>

<script>
  // Defines the canvas, like a painter where we will place objects
  const canvas = document.getElementById("world");
  const ctx = canvas.getContext('2d');
  // Setting up image objects
  const backgroundImg = new Image();
  const spriteImg = new Image();
  // Jekyll assignment of Images
  backgroundImg.src = '{{page.background}}'; // Background Image
  spriteImg.src = '{{page.sprite}}'; // Player Image

// Image Loading Code Block
  let imagesLoaded = 0;
  backgroundImg.onload = function() {
    imagesLoaded++;
    startGameWorld();
  };
  spriteImg.onload = function() {
    imagesLoaded++;
    startGameWorld();
  };

/* This block starts the game
 * It checks for all images being loaded before starting
*/
  function startGameWorld() {
    if (imagesLoaded < 2) return; // Delays start untill everything is loaded

    class GameObject {
      constructor(image, width, height, x = 0, y = 0, speedRatio = 0) {
        this.image = image;
        this.width = width;
        this.height = height;
        this.x = x;
        this.y = y;
        this.speedRatio = speedRatio;
        this.speed = GameWorld.gameSpeed * this.speedRatio;
      }
      update() {}
      draw(ctx) {
        ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
      }
    }

    class Background extends GameObject {
      constructor(image, gameWorld) {
        // Fill entire canvas
        super(image, gameWorld.width, gameWorld.height, 0, 0, 0.1);
      }
      update() {
        this.x = (this.x - this.speed) % this.width;
      }
      draw(ctx) {
        ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
        ctx.drawImage(this.image, this.x + this.width, this.y, this.width, this.height);
      }
    }

    class Player extends GameObject {
  constructor(image, gameWorld) {
    // Keeps the background image at full scale
    const width = image.naturalWidth / 1;
    const height = image.naturalHeight / 1;

    // Divides total window width by 2 to start rocket in middle of screen
    const x = (gameWorld.width - width) / 2;
    const y = (gameWorld.height - height) / 2;

    // Call the parent GameObject constructor
    super(image, width, height, x, y);

    // Save reference to the game world so we know its width/height
    this.gameWorld = gameWorld;

    // Initial target position (where the rocket is "aiming" to move)
    this.targetX = x;
    this.targetY = y;

    // Speed of movement (pixels per frame)
    this.speed = 5;

    // Start choosing random target positions
    this.pickNewTarget();
  }

  // This is a function to randomly choose a new target position inside the screen
  pickNewTarget() {
    // Random X within the screen boundaries, keeping the rocket fully visible
    this.targetX = Math.random() * (this.gameWorld.width - this.width);

    // Random Y within the screen boundaries
    this.targetY = Math.random() * (this.gameWorld.height - this.height);

    // Schedule the rocket to pick a new target again in 1–3 seconds
    // (1000ms = 1s, so 1000 + random up to 2000)
    setTimeout(() => this.pickNewTarget(), 1000 + Math.random() * 2000);
  }

  // Called every animation frame to update rocket position
  update() {
    // Move rocket's X position closer to target
    if (this.x < this.targetX) this.x += this.speed; // move right
    if (this.x > this.targetX) this.x -= this.speed; // move left

    // Move rocket's Y position closer to target
    if (this.y < this.targetY) this.y += this.speed; // move down
    if (this.y > this.targetY) this.y -= this.speed; // move up
  }
}



    class GameWorld {
      static gameSpeed = 5;
      constructor(backgroundImg, spriteImg) {
        this.canvas = document.getElementById("world");
        this.ctx = this.canvas.getContext('2d');
        this.width = window.innerWidth;
        this.height = window.innerHeight;
        this.canvas.width = this.width;
        this.canvas.height = this.height;
        this.canvas.style.width = `${this.width}px`;
        this.canvas.style.height = `${this.height}px`;
        this.canvas.style.position = 'absolute';
        this.canvas.style.left = `0px`;
        this.canvas.style.top = `${(window.innerHeight - this.height) / 2}px`;

        this.objects = [
         new Background(backgroundImg, this),
         new Player(spriteImg, this)
        ];
      }
      gameLoop() {
        this.ctx.clearRect(0, 0, this.width, this.height);
        for (const obj of this.objects) {
          obj.update();
          obj.draw(this.ctx);
        }
        requestAnimationFrame(this.gameLoop.bind(this));
      }
      start() {
        this.gameLoop();
      }
    }

    const world = new GameWorld(backgroundImg, spriteImg);
    world.start();
  }
