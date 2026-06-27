# 📄 Project Report — Classic Snake Game

---

## 1. Project Overview

| Field | Details |
|---|---|
| **Project Title** | Classic Snake Game |
| **Developer** | Faiza |
| **Roll No** | F24-1783 |
| **Program** | BS Artificial Intelligence |
| **Semester** | 4th Semester, Section D |
| **Department** | Information Technology |
| **University** | University of Haripur |
| **Language** | Python 3.x |
| **Library** | Pygame 2.5.2 |

---

## 2. Objective

The objective of this project is to develop a fully functional **Classic Snake Game** using Python and the Pygame library. The game demonstrates practical implementation of **Object-Oriented Programming (OOP)** concepts learned during the semester.

---

## 3. OOP Concepts Applied

### 3.1 Abstract Class
```python
from abc import ABC, abstractmethod

class GameObject(ABC):
    def __init__(self, x, y, size):
        self.x = x
        self.y = y
        self.size = size

    @abstractmethod
    def draw(self, surf): pass
```
`GameObject` is an abstract base class. It cannot be instantiated directly and forces all child classes to implement the `draw()` method.

---

### 3.2 Inheritance
```python
class Segment(GameObject):   # Snake body — inherits GameObject
    def draw(self, surf):
        pygame.draw.rect(surf, GREEN, self.rect)

class Food(GameObject):      # Food — inherits GameObject
    def draw(self, surf):
        pygame.draw.rect(surf, RED, self.rect)
```
Both `Segment` and `Food` inherit from `GameObject`, reusing the `__init__` and `rect` property.

---

### 3.3 Polymorphism
Both `Segment` and `Food` override the `draw()` method differently:
- `Segment.draw()` → draws green rectangle with dark border
- `Food.draw()` → draws red rectangle

Same method name, different behavior = **Polymorphism**.

---

### 3.4 Properties
```python
@property
def rect(self):
    return pygame.Rect(self.x, self.y, self.size, self.size)
```
The `rect` property is defined once in the base class and used by all child classes automatically.

---

### 3.5 Encapsulation
All game logic (movement, collision, scoring, rendering) is encapsulated inside the `SnakeGame` class. Internal state (`snake`, `direction`, `score`, `food`) is managed privately within the class.

---

## 4. Game Features

| Feature | Description |
|---|---|
| Snake Movement | Moves in 4 directions using arrow keys |
| Food Spawning | Random position, never overlaps snake |
| Score System | +10 points per food eaten |
| Speed Increase | Speed increases every 50 points |
| Collision Detection | Wall + self-collision ends game |
| Game Over Screen | Displays score and restart option |
| Restart | Press **R** to restart instantly |

---

## 5. Class Diagram

```
           ┌─────────────────┐
           │  GameObject      │  ← Abstract Base Class
           │─────────────────│
           │ + x, y, size    │
           │ + rect (prop)   │
           │ + draw() [abs]  │
           └────────┬────────┘
                    │ Inherits
         ┌──────────┴──────────┐
         │                     │
  ┌──────▼──────┐       ┌──────▼──────┐
  │  Segment    │       │    Food     │
  │─────────────│       │─────────────│
  │ + draw()   │       │ + draw()   │
  └─────────────┘       └─────────────┘

  ┌─────────────────────────┐
  │       SnakeGame         │  ← Main Controller
  │─────────────────────────│
  │ + snake: [Segment]      │
  │ + food: Food            │
  │ + score, direction      │
  │ + move()                │
  │ + spawn_food()          │
  │ + draw()                │
  │ + handle_events()       │
  │ + run()                 │
  └─────────────────────────┘
```

---

## 6. How to Run

```bash
# Step 1: Install Pygame
pip install pygame

# Step 2: Run the game
python snake_game.py
```

---

## 7. Controls

| Key | Action |
|---|---|
| ↑ Arrow Up | Move Up |
| ↓ Arrow Down | Move Down |
| ← Arrow Left | Move Left |
| → Arrow Right | Move Right |
| R | Restart after Game Over |

---

## 8. Screenshots

### 📸 Gameplay — Snake in Action
![Gameplay Screenshot](gameplay.png)

*Snake starts at center, moves right, eats food (red block) to grow longer*

---

### 📸 Game Over Screen (Score: 140)
![Game Over Screenshot](gameover.png)

*Game Over screen appears when snake hits wall or itself. Press R to restart.*

---

## 9. Conclusion

This project successfully demonstrates the application of OOP principles in a real-world game development scenario. Through this project, I learned how abstract classes enforce structure, how inheritance promotes code reuse, and how encapsulation keeps code organized and maintainable.

---

## 10. References

- Python Official Documentation: https://docs.python.org
- Pygame Documentation: https://www.pygame.org/docs
- OOP in Python: https://realpython.com/python3-object-oriented-programming
