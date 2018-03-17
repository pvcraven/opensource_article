Easy 2D Game Creation With Python And Arcade
===

Python is a great language for people learning to program. It is also a great 
language for anyone just wanting to "get stuff done" without spending a lot of 
time on language or framework overhead.

Arcade is a Python library that makes it easy to create 2D video games.  

Other populare Python libraries used for games:[Pyglet](https://bitbucket.org/pyglet/pyglet/wiki/Home), 
[Pygame](https://www.pygame.org), [Kivy](https://kivy.org)

Installation
---

Arcade, like many other packages, is available via 
[PyPi](https://pypi.python.org/pypi). That means you can install it using the 
`pip` command. If you already have Python installed, you can likely just open
up a command prompt on Windows and type:

`pip install aracde`

Or on MacOS and Linux type:

`pip3 install arcade`

For more detailed installation instructions you can refer to the 
[Arcade installation documentation](http://arcade.academy/installation.html).

Simple Drawing
---

You can open a window and create simple drawings with just a few lines of code.
Let's create an example that draws a smiley face:

![Smiley Face](smiley_face.png)

The script below shows how you can use 
[Arcade's drawing commands](http://arcade.academy/quick_index.html#drawing-module)
to draw the smiley face. Note that you don't need to know how to use "classes"
or even define "functions." This great for anyone who wants to get started
doing something visual.

```python
import arcade

SCREEN_WIDTH = 600
SCREEN_HEIGHT = 600

# Open the window. Set the window title and dimensions (width and height)
arcade.open_window(SCREEN_WIDTH, SCREEN_HEIGHT, "Drawing Example")

# Set the background color to white
# For a list of named colors see
# https://pythonhosted.org/arcade/arcade.color.html
# Colors can also be specified in (red, green, blue) format and
# (red, green, blue, alpha) format.
arcade.set_background_color(arcade.color.WHITE)

# Start the render process. This must be done before any drawing commands.
arcade.start_render()

# Draw the face
x = 300
y = 300
radius = 200
arcade.draw_circle_filled(x, y, radius, arcade.color.YELLOW)

# Draw the right eye
x = 370
y = 350
radius = 20
arcade.draw_circle_filled(x, y, radius, arcade.color.BLACK)

# Draw the left eye
x = 230
y = 350
radius = 20
arcade.draw_circle_filled(x, y, radius, arcade.color.BLACK)

# Draw the smile
x = 300
y = 280
width = 120
height = 100
start_angle = 190
end_angle = 350
arcade.draw_arc_outline(x, y, width, height, arcade.color.BLACK, start_angle, end_angle, 10)

# Finish drawing and display the result
arcade.finish_render()

# Keep the window open until the user hits the 'close' button
arcade.run()
```

Using Classes and Functions
---

Of course, writing code in the global context isn't good form. It is easy to
use learn about using classes and functions in the context of creating graphics.

![Classes and Functions](classes_and_functions.png)

```python
import arcade

SCREEN_WIDTH = 600
SCREEN_HEIGHT = 600


def draw_background():
    """
    This function draws the background. Specifically, the sky and ground.
    """
    # Draw the sky in the top two-thirds
    arcade.draw_lrtb_rectangle_filled(0,
                                      SCREEN_WIDTH,
                                      SCREEN_HEIGHT,
                                      SCREEN_HEIGHT * (1 / 3),
                                      arcade.color.SKY_BLUE)

    # Draw the ground in the bottom third
    arcade.draw_lrtb_rectangle_filled(0,
                                      SCREEN_WIDTH,
                                      SCREEN_HEIGHT / 3,
                                      0,
                                      arcade.color.DARK_SPRING_GREEN)


def draw_bird(x, y):
    """
    Draw a bird using a couple arcs.
    """
    arcade.draw_arc_outline(x, y, 20, 20, arcade.color.BLACK, 0, 90)
    arcade.draw_arc_outline(x + 40, y, 20, 20, arcade.color.BLACK, 90, 180)


def draw_pine_tree(x, y):
    """
    This function draws a pine tree at the specified location.
    """
    # Draw the triangle on top of the trunk
    arcade.draw_triangle_filled(x + 40, y,
                                x, y - 100,
                                x + 80, y - 100,
                                arcade.color.DARK_GREEN)

    # Draw the trunk
    arcade.draw_lrtb_rectangle_filled(x + 30, x + 50, y - 100, y - 140,
                                      arcade.color.DARK_BROWN)


def main():
    """
    This is the main program.
    """

    # Open the window
    arcade.open_window(SCREEN_WIDTH, SCREEN_HEIGHT, "Drawing With Functions")

    # Start the render process. This must be done before any drawing commands.
    arcade.start_render()

    # Call our drawing functions.
    draw_background()
    draw_pine_tree(50, 250)
    draw_pine_tree(350, 320)
    draw_bird(70, 500)
    draw_bird(470, 550)

    # Finish the render.
    # Nothing will be drawn without this.
    # Must happen after all draw commands
    arcade.finish_render()

    # Keep the window up until someone closes it.
    arcade.run()


if __name__ == "__main__":
    main()
```

Using Sprites
---

Platformers
---


Other Example Code
---

[Example Arcade Code](http://arcade.academy/examples/index.html)