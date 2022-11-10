## Fire your arrow

<div style="display: flex; flex-wrap: wrap">
<div style="flex-basis: 200px; flex-grow: 1; margin-right: 15px;">
When you click or tap, an arrow will fire at the position of a moving target circle. 
</div>
<div>

![The target, with a brown circle arrow appearing in a variety of positions.](images/fire_arrow.gif){:width="300px"}

</div>
</div>

### Draw a target circle every frame

<p style="border-left: solid; border-width:10px; border-color: #0faeb0; background-color: aliceblue; padding: 10px;"> Computers create the effect of movement by showing lots of images one after another. Each image is called a <span style="color: #0faeb0; font-weight: bold;"> frame </span>.   
</p>

--- task ---

Define your `shoot_arrow()` function under the comment **# The shoot_arrow function goes here**. 

Add code to randomly draw a brown circle within a target area:

![A rectangle showing the target area coordinates in a semi transparent rectangle. The target area is between x=100 and y=100 to x=300 and y=300 so covers the whole target and wider.](images/target_area.png)

--- code ---
---
language: python
filename: main.py — shoot_arrow()
line_numbers: true
line_number_start: 7
line_highlights: 8, 9, 10, 11, 12, 13, 14
---
# The shoot_arrow function goes here  
def shoot_arrow(): 
    arrow_x = randint(100, 300) # Store a random number between 100 and 300
    arrow_y = randint(100, 300) # Store a random number between 100 and 300
    fill('sienna') # Set the arrow to fill colour to brown   
    circle(arrow_x, arrow_y, 15) # Draw a small circle at random coordinates 

--- /code ---

--- /task ---

--- task ---

Go to the `draw` function and call your new `shoot_arrow` function. 

--- code ---
---
language: python
filename: main.py — draw()
line_numbers: true
line_number_start: 33
line_highlights: 35
---
    fill('yellow')   
    circle(200, 200, 30) # Middle  
    shoot_arrow()

--- /code ---

--- /task ---

--- task ---

**Test:** 🔄 Run you code and see the arrow appear in a random position each frame.

![The target, with a brown circle arrow appearing in a variety of positions.](images/fire_arrow.gif)

The background and target will be drawn over the old arrow. This means you only see one arrow at a time.

--- /task ---

### Get the colour hit by the arrow 

The `get()` function returns the colour of a pixel.

<p style="border-left: solid; border-width:10px; border-color: #0faeb0; background-color: aliceblue; padding: 10px;">
A <span style="color: #0faeb0; font-weight: bold;">pixel</span>, short for picture element, is a single coloured dot within an image. Images are made up of lots of coloured pixels.
</p>

--- task ---

Add a `hit_color` a **global variable** that can be used throughout your code.

Add code to `get` the colour of the pixel at the centre of the arrow and store it in the `hit_color` variable. 

--- code ---
---
language: python
filename: main.py — shoot_arrow() 
line_numbers: true
line_number_start: 7
line_highlights: 9, 12
---
# The shoot_arrow function goes here     
def shoot_arrow():
    global hit_color # Can be used in other functions
    arrow_x = randint(100, 300)    
    arrow_y = randint(100, 300)    
    hit_color = get(arrow_x, arrow_y) # Get the hit colour 
    fill('sienna') # Set the arrow to fill colour to brown   
    circle(arrow_x, arrow_y, 15) # Draw a small circle at random coordinates 
--- /code ---

**Tip:** 💡 The code to `get` the colour needs to be **before** the code to draw the `circle` otherwise you will always save the wood colour of the arrow! 

--- /task ---

### Print the colour when the mouse is pressed

The `p5` library 'listens' for certain events, one of these is the press of the mouse button. When it detects that the button has been pressed, it will run whatever code it has been given in the `mouse_pressed` function.

--- task ---

Define your `mouse_pressed()` function under the comment **# The mouse_pressed function goes here**. 

Add code to print the amounts of red, green, and blue in the pixel the arrow lands on. 

--- code ---
---
language: python
filename: main.py - mouse_pressed()
line_numbers: true
line_number_start: 5
line_highlights: 6, 7
---

# The mouse_pressed function goes here    
def mouse_pressed():    
    print(hit_color)

--- /code ---

--- /task ---

--- task ---

**Test:** 🔄 Run your project. 

The project prints the `hit_color` each time the arrow is redrawn.

![The target, with a brown circle arrow appearing in a variety of positions.](images/fire_arrow.gif)

**Debug:** 🐞 If you are seeing a message about `hit_color` being 'not defined', then go back to `shoot_arrow()` and check that you have the `global hit_color` line.

**Debug:** 🐞 Check the `print` line really carefully for commas and brackets. 

--- /task ---


