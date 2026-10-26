<div align="center">

# ⚔️ The Little Knight

**A 2D platformer that tries to bring 4D elements of design along with it.**

![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)
![Pygame Zero](https://img.shields.io/badge/Pygame_Zero-1.x-2E8B57)
![License](https://img.shields.io/badge/License-MIT-blue)

<img width="720" alt="The Little Knight gameplay" src="https://github.com/user-attachments/assets/92358707-44b1-451d-ac61-810842905a5e" />

</div>

---

## Table of Contents

- [Getting Started](#getting-started)
- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [How It's Made](#how-its-made)
- [Project Structure](#project-structure)
- [Lessons Learned](#lessons-learned)
- [Acknowledgments](#acknowledgments)

---

## Getting Started

### Prerequisites

| Tool | Version | Notes |
|---|---|---|
| [Python](https://www.python.org/downloads/) | 3.x | Includes pip |
| [Pygame Zero](https://pygame-zero.readthedocs.io/) | 1.x | Installs Pygame alongside it |

### Install and run

```bash
git clone https://github.com/timliiang/The-Little-Knight.git
cd The-Little-Knight
python -m pip install pgzero
python main.py
```

On Windows, use the `py` launcher instead:

```powershell
py -m pip install pgzero
py main.py
```

> **Note:** run the game from inside the repository folder. Pygame Zero loads `images/`, `music/` and `fonts/` relative to `main.py`.

> **Tip:** if you get `No module named pgzrun`, pip installed Pygame Zero into a different Python than the one running the game. Installing with `python -m pip` (or `py -m pip`) makes sure both use the same interpreter.

### Controls

| Key | Action |
|---|---|
| `←` / `→` | Move left / right |
| `Z` | Jump |
| `X` | Attack |
| `F` | Interact with NPCs and doors |
| `Enter` | Next line of dialogue |
| `Esc` | Open / close the menu |
| `L` | Fullscreen |

---

## Overview

The Little Knight was a project submission for a "Introduction to Programming" highschool course's summative assignment.
It is inspired by the game Hollow Knight with most of this project's content containing sprites and music files from Hollow Knight.

## Tech Stack

This project was made entirely using Python with help from the Pygame-zero library.

| Layer | Technologies |
|---|---|
| **Language** | Python 3 |
| **Game framework** | Pygame Zero, `pgzhelper` |
| **Assets** | Sprites and music from Hollow Knight |

---

## How It's Made

The **creative process** for The Little Knight was entirely inspired by the game Hollow Knight by Team Cherry. This game was one of the most pivotal 2D platformer games, bringing to it many new creative processes and functions such as in-game skills, 4D art design, etc. I had hoped to provide a user experience similar to that of Hollow Knight with many of the shockingly-cool skills that followed from the game.

### 🏃 Early design

The **early design process** was fairly simple with most the time being dedicated towards simple character movements and functions like in any other 2D platformer games.
- This included character movements primarly moving left or right which was done through a movement of the character sprite's pixels with respect to the framework. One problem I originally had with this though was that the sprite would face the same direction despite moving the opposite way. To fix this, I just reflected the sprite and had a different sprite display depending on the player's direction.
- Another key feature added in the early implementation was the camera following the player. This would prevent the player from going off screen. The camera was another fairly simple component, implemented through bounds set by the player's location on the screen and moving the background according to the player's in-game location.

### 🦘 Middle implementation: player movement

As for the **middle implementation process**, this was where many of the issues as well as cooler features followed.
- First was creating the player gravity. Originally, I had just checked whether the player was on the ground or not and had them fall depending on this. This used a constant gravity constant making the player fall in a constant speed. Upon further testing and comparison to other games, I noticed that this seemed unrealistic. As a result, I decided to accelerate the player with respect to the player's airtime. The longer the player stayed off the ground, the faster the player would fall.
- Next was the player's ability to jump which happened to be one of my favourite implementations. The intial process for this was just to move the player upwards at a constant speed until they reach their max jump height. However, just like with the gravity, it seemed unrealistic. In a similar way to gravity, I then decided to implement the player's movement when jumping and falling as if it were a parabola. At the highest point, the player would seem like the were floating and they move at a slower rate, then as they fall, they fall at a accelerating pace.
- Another cool feature I added was the stun when the player would fall from a high height. How I decided to implement this was to check the player's airtime as they touch the ground to see if they stayed in the air past a certain time.

<div align="center">
<img width="640" alt="Player movement" src="https://github.com/user-attachments/assets/a4b2faf8-5a61-486a-81f1-c40a8c5ec0fc" />

*Player movement*
</div>

### 🗡️ Middle implementation: player combat

- First was the player's attack. This consisted of a slash which extended from the player's sprite. This was done through hitbox detection where the slash would act as a seperate entity and if it collided with another entity that was hittable, it would damage it.
- Next was the player being able to get hurt. Similar to how the player attacked, I added a hitbox for the player and whenever an enemy entity collided with the player hitbox, it hurts the player.

I had also intended to add another function the player's combat where the player was able to shoot a long-ranged spell similar to Hollow Knight. However, due to time constraints, I wasn't able to fit that into the game for the final submission.

<div align="center">
<img width="640" alt="Player combat" src="https://github.com/user-attachments/assets/66cbc37f-34d0-429b-a783-5e0292a9b4cd" />

*Player combat*
</div>

### 🪲 Middle implementation: boss

Inspired by another game genre, Dark Souls, I wanted to introduce the character straight away to a challenge. This meant that the first enemy they encountered was a boss immediately testing the player's skills.
This boss was the Gruz Mother from Hollow Knight, which consisted of two attacks.
- The first attack was when the Gruz Mother would slam against the top and bottom of the screen attempting to hurt the player. This was done through first locating the player's location which determines the direction the Gruz Mother first moves towards. Then for the actual attack, I would move the Gruz Mother's pixel's towards the top and bottom of the screen respectively. To calculate when the Gruz Mother would collide with the screen, I checked the location of the very top pixels and the location of the very bottom pixels and compared them to the borders of the screen.
- The second attack was when the Gruz Mother would charge towards the player's location. I implemented this by comparing the player and the bosses' location, then moved the boss towards the player at a faster speed.

Overall, the boss design was another really fun process which I would love to do again. It used many of the skills and techniques I used for creating the player's movements in a more elaborate and creative way.

<div align="center">
<img width="640" alt="Boss fight" src="https://github.com/user-attachments/assets/8d0e7690-ca3a-4bec-b100-5ac945cd052f" />

*Boss fight*
</div>

### ✨ End design

Finally, the **end design**. This was where I made final touches and added some smaller details to the game to enhance user experience.
- I added a starting menu for when the user first enters the game. This just detected the user's mouse click collisions with the buttons.
- Another cool feature was the animations for the characters. This was done through using a function which looped through all the characters animation frames. Each movement had a different frame speed so I had to account for that as well as the direction.
- Music was also added to the game depending on the player's location in-game. For example, the menu music would be different from the music when the player is fighting the boss battle.
- Last is the story line. I added npcs with different lines to steer the player towards the right direction in-game and to add a story element into the game.

<div align="center">
<img width="640" alt="NPCs and story" src="https://github.com/user-attachments/assets/432d7b33-62e9-4d75-adfc-bd0f0f870c4b" />

*NPCs and story*
</div>

---

## Project Structure

```
.
├── main.py          # The whole game: levels, player, combat, boss, menu, dialogue
├── pgzhelper.py     # Helper library for Pygame Zero (sprite flipping, scaling, fullscreen)
├── images/          # Sprites: knight, Gruz Mother, Hornet, backgrounds, menus
├── music/           # Background music for each area
├── fonts/
└── LICENSE
```

---

## Lessons Learned

As I made this game entirely through Python, I had many difficulties with things as simple as character movements, hitbox detections, collisions, animations, etc. This made me realize the incredible value that game engines hold for game creators. This also gave me a future project idea in order to create my own game engine.

Another lesson I learned came from the spaghetti code I had created. This was evident in my game since I practically coded everything in one main source file. This had many overlapping and redudant elements which is why I realized how I should've incorporated a more object oriented approach to this game as well as to many future programs I create in the future.

## Acknowledgments

- [Hollow Knight](https://www.hollowknight.com/) by Team Cherry, the inspiration for the game and the source of its sprites and music
- [Pygame Zero](https://pygame-zero.readthedocs.io/)

---

<div align="center">

*All rights to the images and music copied from Hollow Knight go to Team Cherry. If requested, content will be taken down.*

</div>
