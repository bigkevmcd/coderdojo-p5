---
layout: default
---

<h2 id="intro">Introduction</h2>

In this short guide, I"ll introduce some simple P5.js code.

p5.js programs are called _"sketches"_ and they must have at least two
functions.

Functions are small blocks of code with names, that can be called to perform a
"function".

All p5.js sketches must have the following two named functions `function setup()` and `function draw()`.

The setup is executed at the start, when the sketch is loaded, the draw function is executed 60 times per second.

You can execute a small p5 sketch below.

<h2 id="first-program">Our first program</h2>

{% include start.html %}
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background('red');
  fill('blue');
  rect(30, 30, 120, 40);
}
{% include end.html %}


In the `setup()` function, the code creates a canvas 400 pixels square to draw
on.

Just like a painter's canvas, we use a canvas to draw images, shapes and text in the browser.

You'll see in the code below, that we always create a canvas.

In the `draw()` function, the code carries out the following steps:

1. calls `background('red')` to set the background colour to red.
   The browser can render a wide range of colours including 'blue', 'tomato'
   and 'skyblue'.
2. calls `fill('blue')` to set the fill colour for upcoming drawing operations
   to blue.
3. the `rect(30, 30, 120, 40)` call draws a rectangle 120 pixels wide by 40
   pixels deep, at position `30, 30`.


### Exercises:

1. Try changing the colour of the rectangle.
2. Try making the rectangle smaller.
3. Try drawing a square beside the rectangle.
4. Try making the square draw at a random place each time.


<h2 id="coordinates">Co-ordinates</h2>

{% include start.html %}
function setup() {
    createCanvas(400, 400);
}

function draw() {
  rect(0, 0, 2, 2);

  point(width * 0.5, height * 0.5);
  point((width * 0.5) + 10, (height * 0.5) + 10);
  point((width * 0.5) - 10, (height * 0.5) + 10);
  point((width * 0.5), (height * 0.5) + 20);

  rect(width, height, 2, 2);
}
{% include end.html %}

This plots 4 tiny dots on the screen, can you see them?

It also plots two squares, but you can only see one of them.

Why is the second square (at the bottom-right) not visible?

### Exercises

1. Fix the second square to draw correctly on the page.


<h2 id="text">Drawing text</h2>

One of the simplest things we can do is draw text.

{% include start.html %}
function setup() {
    createCanvas(400, 400);
}

function draw() {
  background(255, 255, 255);
  fill(0, 0, 0, 255);
  textSize(14);
  textAlign(CENTER);
  text("say something", width/2, height/2);
}
{% include end.html %}

### Exercises

1. Change the text to output your name.
2. Draw two of your friends' names on the screen beside your name.

<h2 id="simple-shapes">Simple Shapes</h2>

P5.js includes many simple functions for drawing, we've already seen how to draw
rectangles above but it's easy to draw the following shapes.

* `rect(x, y, w, h)`
* `triangle(x1, y1, x2, y2, x3, y3)`
* `ellipse(x, y, w)`
* `point(x, y)`
* `line(x1, y1, x2, y2)`

Some of the drawing commands have optional parameters which allow you to draw
more advanced graphs, but you don't need these just now.

You can change the fill colour for the drawing, or the line colour using the
following instructions:

* `fill()` // TODO make explain the colours and transparency.
* `stroke()`

{% include start.html %}
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background('red');
  fill('yellow');
  ellipse(56, 46, 55, 35);
  line(56,46, 90, 90);
}
{% include end.html %}

### Exercises

1. Try making the ellipse bigger, what happens if it draws off the canvas?
2. Try making one ellipse draw on top of another ellipse.
3. Try drawing a triangle.
4. the `stroke()` function take a colour to change the line colour for the next
   line you draw, change the line colour above to white.

You can read more about the drawing capabilities of P5 here

https://p5js.org/reference/#group-Shape

<h2 id="interactions">Interactions</h2>

{% include start.html %}
var yPos, xPos;
const W_KEY= 87, S_KEY=83, A_KEY=65, D_KEY=68;

function setup() {
  createCanvas(400, 400);
  xPos = width/2;
  yPos = height/2;
}

function draw() {
  background('white');
  rect(xPos, yPos, 10, 10);
}

function keyPressed() {
  if (keyCode == W_KEY) {
    yPos = yPos - 10;
  } else if (keyCode == S_KEY) {
    yPos = yPos + 10;
  }
}
{% include end.html %}

In this example, we are drawing a square a `xPos, yPos`, so if `xPos` has the
value 50, and `yPos` has the value 50, we draw a `10x10` square at `50, 50`.

We've made changes to the code so that if you press the up and down arrow keys,
the position that the square is drawn on the canvas is moved up and down.

The `keyPressed()` function is called by P5.js whenever a key is pressed, and
the `keyCode` variable is set to the key that is pressed, the codes are a
special computer representation of the keys that you press.

### Exercises

1. When you press `a` or `d` make the square go left or
   right.
2. What happens if you move off the canvas?  How could we fix that?
3. What happens if you remove the `background('white')` call?

<h2 id="interactions-2">More interactions</h2>

Because our code is running in a browser, we can also respond to mouse clicks.

{% include start.html %}
function setup() {
  createCanvas(400, 400);
}

function draw() {
}

function mouseClicked() {
  ellipse(mouseX, mouseY, 80, 80);
}
{% include end.html %}

Whenever you click the mouse, the function `mouseClicked` is called
automatically by p5.js.

The current position when you click is stored in two variables the `mouseX`
and `mouseY` variables, these are positions within the area of the canvas.

### Exercises

1. Make the colour of the circle random.
2. Make the size of the circle random.
3. Change the code so that if you click the right button, you get a different
   shape, _hint: `mouseButton` contains the button you pressed_
