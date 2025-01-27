# Snowflower
Snowflower is a p5.js script, that generates a procedural flower every time it's run. The final image will result in something similar to the one below:

![Screenshot 2025-01-27 164211](https://github.com/user-attachments/assets/b7fabf2e-c4a7-403f-9b39-b3b2aed77415)

## P5.js script:
``` 
let angle //declare variable to allow us to store angles

function setup() {
  createCanvas(800, 800);

  // Set the gradient for the background
  for (let y = 0; y < height; y++) {
    let gradientColor = lerpColor(color(15, 15, 35), color(25, 25, 75), y / height)
    stroke(gradientColor)
    line(0, y, width, y)
  }

  stroke(255, 255, 255, 50); // Set the stroke values for the branches
  angle = PI / 6

  translate(width / 2, height); // Choose initial branch origin point  and set its length
  branch(180)

  // Left trunk branch off length, translation and angles (offset)
  push()
  translate(-200, height) 
  branch(150)
  pop()

  // Right trunk branch off length, translation and angles (offset) 
  push()
  translate(200, height)
  branch(150)
  pop()
}

//Smaller branch functions, starting with drawing branches and moving them to a branch tip
function branch(len) {
  if (len > 1) {
    line(0, 0, 0, -len)
    translate(0, -len)

//Set branch thickness, color, reduce density and set randomized rotation - play around with these values for interesting effects
    if (random() > 0.25) { // Reduce branch density
      push()
      strokeWeight(2); // Smaller branches
      stroke(255, 255, 255, 50)
      rotate(angle * random(0.3, 0.5))
      branch(len * random(0.6, 0.8));
      pop();
    }

    if (random() > 0.25) {
      push();
      strokeWeight(2)
      stroke(255, 255, 255, 50)
      rotate(-angle * random(0.3, 0.5))
      branch(len * random(0.6, 0.8))
      pop()
    }

    if (random() > 0.3) {
      push()
      strokeWeight(2)
      stroke(255, 255, 255, 50)
      rotate(angle * random(-0.2, 0.2))
      branch(len * random(0.5, 0.7))
      pop()
    }
  }
}

```

## Link to Sketch:
https://editor.p5js.org/rsutter/full/VZLVNSO6D
