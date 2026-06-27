# Changelog 📋

All notable changes to this project will be documented here.

---

## [1.0.0] - 2025

### Added
- Classic Snake Game built with Python & Pygame
- Full OOP implementation using Abstract Classes, Inheritance, Polymorphism
- Wall collision detection
- Self-collision detection
- Food spawning (avoids snake body)
- Score tracking system (+10 per food eaten)
- Dynamic speed increase as score grows
- Game Over screen with restart option (Press R)
- Clean black background UI with score display

### OOP Structure
- `GameObject` — Abstract base class
- `Segment` — Inherits from GameObject, draws snake body
- `Food` — Inherits from GameObject, draws food
- `SnakeGame` — Main game controller class

---

## Future Plans
- [ ] Sound effects
- [ ] High score leaderboard
- [ ] Multiple difficulty levels
- [ ] Start menu
- [ ] Snake skin colors
