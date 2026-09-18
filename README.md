# 🐍 Snake Game

A simple **Snake Game built with Python Turtle Graphics**.

The player controls a snake using the keyboard arrow keys, collects food to increase the score, and grows longer each time food is eaten. The game also keeps track of the **highest score** achieved during the current game session.

---

## 📌 Project Overview

This project is a classic Snake Game implemented using Python's built-in **Turtle graphics library**.

The player controls the snake using the **Up, Down, Left, and Right arrow keys**. When the snake reaches the food, its body grows and the score increases by 10 points.

The game includes:

* 🐍 Snake movement
* 🍎 Random food placement
* 📈 Score tracking
* 🏆 Highest score tracking
* 🧱 Border wrapping
* 💥 Snake-body collision detection
* 🔄 Automatic game reset after collision
* ⌨️ Keyboard controls

---

# ✨ Features

### 🐍 Snake Movement

The snake can move in four directions:

* ⬆️ Up
* ⬇️ Down
* ⬅️ Left
* ➡️ Right

The snake cannot immediately reverse its direction. For example, if the snake is moving right, pressing the left arrow will not make it instantly move backward.

---

### 🍎 Food System

Food appears on the screen at a random location.

When the snake reaches the food:

* The food moves to another random location.
* A new body segment is added.
* The score increases by 10.
* The highest score is updated if necessary.

---

### 📊 Score System

The game maintains two scores:

```text
Score
Highest Score
```

Each food item increases the score by:

```text
+10
```

Example:

```text
Score: 30 Highest Score: 50
```

---

### 🏆 Highest Score

The game keeps track of the highest score achieved during the current execution of the program.

Whenever:

```python
score > highestscore
```

the highest score is updated.

---

### 🧱 Border Wrapping

Instead of ending the game when the snake reaches the border, the snake appears on the opposite side.

For example:

```text
Right edge → Left edge
Left edge  → Right edge
Top edge   → Bottom edge
Bottom edge → Top edge
```

This creates a continuous playing area.

---

### 💥 Collision Detection

The game checks whether the snake's head collides with any part of its body.

If a collision occurs:

1. The game pauses briefly.
2. The snake returns to the starting position.
3. The snake's body disappears.
4. The body list is cleared.
5. The score resets to 0.
6. The highest score remains unchanged.

---

# 🛠️ Technologies Used

| Technology | Purpose                   |
| ---------- | ------------------------- |
| Python     | Main programming language |
| Turtle     | Graphics and game objects |
| Random     | Random food positioning   |
| Time       | Game timing and delay     |

All of these modules are part of Python's standard library, so no external package is required.

---



# ⚙️ Requirements

You only need:

* Python 3.x
* A computer with keyboard support
* Python Turtle graphics support

No external libraries are required.

---

# 🚀 Installation

## 1. Clone the Repository

Open Command Prompt or Terminal:

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
```

Move into the project directory:

```bash
cd Snake-Game
```

---

## 2. Run the Game

Execute:

```bash
python snake_game.py
```

On some systems, you may need:

```bash
python3 snake_game.py
```

A Turtle graphics window will open and the game will start.

---

# 🎮 How to Play

Use the keyboard arrow keys to control the snake.

| Key            | Action     |
| -------------- | ---------- |
| ⬆️ Up Arrow    | Move Up    |
| ⬇️ Down Arrow  | Move Down  |
| ⬅️ Left Arrow  | Move Left  |
| ➡️ Right Arrow | Move Right |
| Space          | Stop Snake |

---

# 🎯 Game Rules

1. Control the snake using the arrow keys.
2. Move the snake toward the food.
3. Eating food increases your score by **10 points**.
4. Each food item makes the snake longer.
5. The snake can pass through the screen borders.
6. Avoid hitting the snake's own body.
7. If the snake hits itself, the current score becomes 0.
8. The highest score remains saved during the current program session.
9. Try to achieve the highest possible score!

---

# 🕹️ Gameplay Flow

```text
             START
                │
                ▼
       Create Game Window
                │
                ▼
        Create Snake Head
                │
                ▼
          Create Food
                │
                ▼
        Initialize Score
                │
                ▼
       Wait for Keyboard
                │
                ▼
         Move the Snake
                │
                ▼
      Check Border Collision
                │
                ▼
       Check Food Collision
          /           \
        No             Yes
        │               │
        │        Move Food Randomly
        │               │
        │        Increase Snake Size
        │               │
        │        Increase Score
        │               │
        │        Update High Score
        │               │
        └───────┬───────┘
                ▼
       Move Snake Body
                │
                ▼
      Check Self Collision
          /           \
        No             Yes
        │               │
        │        Reset Snake
        │        Reset Score
        │               │
        └───────┬───────┘
                ▼
          Continue Game
```

---

# 🧩 Main Components

## 1. Game Variables

The game starts with:

```python
delay = 0.1
score = 0
highestscore = 0
bodies = []
```

These variables control:

* Game speed
* Current score
* Highest score
* Snake body segments

---

# 🐍 Creating the Snake

The snake's head is created using Turtle:

```python
head = turtle.Turtle()
head.shape("square")
head.color("white")
head.fillcolor("blue")
head.penup()
head.goto(0,0)
```

The snake starts at:

```text
(0, 0)
```

Its initial direction is:

```python
head.direction = "stop"
```

---

# 🍎 Creating the Food

The food is created as a Turtle object:

```python
food = turtle.Turtle()
food.shape("circle")
food.color("yellow")
food.fillcolor("red")
food.goto(0,200)
```

When the snake eats the food, the food is moved to a random location.

```python
x = random.randint(-290,290)
y = random.randint(-290,290)
food.goto(x,y)
```

---

# 🎮 Direction Functions

The project uses separate functions for movement.

### Move Up

```python
def moveup():
    if head.direction != "down":
        head.direction = "up"
```

### Move Down

```python
def movedown():
    if head.direction != "up":
        head.direction = "down"
```

### Move Left

```python
def moveleft():
    if head.direction != "right":
        head.direction = "left"
```

### Move Right

```python
def moveright():
    if head.direction != "left":
        head.direction = "right"
```

### Stop

```python
def movestop():
    head.direction = "stop"
```

These checks prevent the snake from directly reversing its direction.

---

# ⌨️ Keyboard Event Handling

The Turtle screen listens for keyboard input:

```python
s.listen()

s.onkey(moveup,"Up")
s.onkey(movedown,"Down")
s.onkey(moveleft,"Left")
s.onkey(moveright,"Right")
s.onkey(movestop,"space")
```

This connects keyboard keys to the snake's movement functions.

---

# 🚧 Border Collision

The game checks whether the snake reaches the screen boundaries.

For example:

```python
if head.xcor() > 290:
    head.setx(-290)
```

This means that when the snake reaches the right side, it appears on the left side.

The same logic is applied to all four borders.

---

# 🍎 Food Collision

The game checks the distance between the snake's head and the food:

```python
if head.distance(food) < 20:
```

If the distance is less than 20 pixels, the snake is considered to have eaten the food.

The program then:

### 1. Moves food

```python
x = random.randint(-290,290)
y = random.randint(-290,290)
food.goto(x,y)
```

### 2. Creates a new body segment

```python
body = turtle.Turtle()
body.shape("square")
body.color("red")
body.fillcolor("yellow")
bodies.append(body)
```

### 3. Increases the score

```python
score += 10
```

### 4. Updates the highest score

```python
if score > highestscore:
    highestscore = score
```

---

# 🐍 Snake Body Movement

The body segments follow the previous segment.

```python
for index in range(len(bodies)-1,0,-1):
    x = bodies[index-1].xcor()
    y = bodies[index-1].ycor()
    bodies[index].goto(x,y)
```

The first body segment follows the snake's head:

```python
if len(bodies) > 0:
    x = head.xcor()
    y = head.ycor()
    bodies[0].goto(x,y)
```

This creates the classic Snake movement effect.

---

# 💥 Self-Collision

The program checks every body segment:

```python
for body in bodies:
    if body.distance(head) < 20:
```

If the head touches the body:

```text
Collision detected
       ↓
Pause
       ↓
Move head to center
       ↓
Stop snake
       ↓
Hide body
       ↓
Clear body list
       ↓
Reset score
       ↓
Continue game
```

The highest score is not reset.

---

# 📊 Scoring System

| Action         |      Score |
| -------------- | ---------: |
| Start Game     |          0 |
| Eat 1 Food     |        +10 |
| Eat 2 Food     |        +20 |
| Eat 3 Food     |        +30 |
| Eat 10 Food    |       +100 |
| Self Collision | Reset to 0 |

The highest score is retained during the current program session.

---

# 🎨 Game Design

The current game uses the following visual elements:

| Element    | Appearance       |
| ---------- | ---------------- |
| Background | Green            |
| Snake Head | Blue/White       |
| Snake Body | Yellow/Red       |
| Food       | Red/Yellow       |
| Window     | 600 × 600 pixels |

The game window is created using:

```python
s.setup(width=600, height=600)
```

---

# 🔧 Game Speed

The game starts with:

```python
delay = 0.1
```

The delay controls how quickly the game loop runs.

After eating food, the current code changes the delay to:

```python
delay = 0.01
```

This makes the snake move significantly faster.

After a self-collision, it resets to:

```python
delay = 0.1
```

---

# 🧠 Python Concepts Used

This project demonstrates several important Python concepts.

### Variables

```python
score = 0
highestscore = 0
delay = 0.1
```

### Lists

The snake body is stored in a list:

```python
bodies = []
```

New body segments are added using:

```python
bodies.append(body)
```

### Functions

The project uses functions for movement and game operations:

```python
moveup()
movedown()
moveleft()
moveright()
movestop()
move()
```

### Loops

A `while True` loop continuously runs the game:

```python
while True:
    s.update()
```

A `for` loop is used to move the snake's body.

### Conditional Statements

The program uses `if` statements to detect:

* Direction
* Food collision
* Border collision
* Body collision
* Score updates

### Random Numbers

The `random` module generates new food positions:

```python
random.randint(-290,290)
```

### Object-Oriented Programming

The Turtle library uses objects such as:

```python
turtle.Turtle()
```

Different Turtle objects represent the snake, food, and scoreboard.

---

# 📚 Learning Outcomes

By building this project, I learned how to:

* Use Python Turtle graphics
* Handle keyboard events
* Create game objects
* Control object movement
* Detect collisions
* Use random coordinates
* Work with Python lists
* Create and use functions
* Implement a continuous game loop
* Manage game score
* Implement basic game logic
* Work with Python's standard libraries

---

# ⚠️ Current Limitations

The current version is a simple implementation and has some limitations:

1. There is no dedicated **Game Over screen**.
2. The highest score is not saved permanently.
3. The game does not have sound effects.
4. There is no start/restart button.
5. There are no difficulty levels.
6. The food can potentially appear close to or on the snake.
7. The game uses a basic Turtle interface.
8. The snake speed changes sharply after eating food.
9. The game does not have a pause menu.
10. The game does not have multiple lives.

---

# 🔮 Future Improvements

Possible improvements include:

* 🏆 Persistent high-score storage
* 🔊 Sound effects
* 🎵 Background music
* 🎮 Start and restart buttons
* ⏸️ Pause functionality
* 🎚️ Difficulty levels
* 🧱 Obstacles
* 🍎 Different types of food
* ❤️ Multiple lives
* 🏅 Level system
* 🎨 Improved graphics
* 🖥️ Modern GUI
* 📱 Mobile-friendly version
* 🌐 Web-based version
* 👥 Multiplayer mode
* 📊 Detailed score statistics
* 💾 Save player progress

---

# 🐛 Troubleshooting

## Turtle Window Does Not Open

Make sure Python is installed correctly.

Check the Python version:

```bash
python --version
```

You should see something similar to:

```text
Python 3.x.x
```

---

## Arrow Keys Are Not Working

Click inside the Turtle game window first and then use:

```text
↑ ↓ ← →
```

The program needs keyboard focus to receive the key events.

---

## Python Command Not Found

Try:

```bash
python3 snake_game.py
```

If Python is not installed, download it from:

https://www.python.org/downloads/

---


# 📄 License

This project is created for **educational and personal use**.


---

# 👨‍💻 Author

## MD Atiku Rahman

**B.Tech Computer Science Engineering**
Galgotias University

### Connect With Me

* 💻 GitHub: [MdAtiku007](https://github.com/MdAtiku007)
* 🔗 LinkedIn: [Atiku Rahman](https://www.linkedin.com/in/atiku-rahman/)

---

# ⭐ Support

If you enjoyed this project or found it useful, consider giving the repository a ⭐ on GitHub!

---

## 🏷️ Tags

```text
python
snake-game
python-game
turtle
turtle-graphics
python-turtle
game-development
beginner-python-project
python-project
keyboard-events
collision-detection
game-programming
```

---

## 📌 Project Highlights

```text
🐍 Classic Snake Game
🎮 Keyboard Controls
🍎 Random Food Generation
📈 Score Tracking
🏆 Highest Score Tracking
💥 Collision Detection
🧱 Border Wrapping
🐍 Dynamic Snake Growth
⌨️ Real-Time Keyboard Input
🐍 Built with Python Turtle
```
