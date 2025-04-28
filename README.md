# The-Little-Knight
The Little Knight is a 2D platformer that tries to bring 4D elements of design along with it. It was also a project submission for a "Introduction to Programming" highschool course's summative assignment.
It is inspired by the game Hollow Knight with most of this project's content containing sprites and music files from Hollow Knight.


# How It's Made:
This project was made entirely using Python with help from the Pygame-zero library.

The **creative process** for The Little Knight was entirely inspired by the game Hollow Knight by Team Cherry. This game was one of the most pivotal 2D platformer games, bringing to it many new creative processes and functions such as in-game skills, 4D art design, etc. This was something I tried to bring along over to The Little Knight. I had hoped to provide a user experience similar to that of Hollow Knight with many of the shockingly-cool skills that followed from the game.

The **early design process** was fairly simple with most the time being dedicated towards simple character movements and functions like in any other 2D platformer games. 
- This included character movements primarly moving left or right which was done through a movement of the character sprite's pixels with respect to the framework. One problem I originally had with this though was that the sprite would face the same direction despite moving the opposite way. To fix this, I just reflected the sprite and had a different sprite display depending on the player's direction. 
- Another key feature added in the early implementation was the camera following the player. This would prevent the player from going off screen. The camera was another fairly simple component, implemented through bounds set by the player's location on the screen and moving the background according to the player's in-game location.

As for the **middle implementation process**, this was where many of the issues as well as cooler features followed.
Player movement
- First was creating the player gravity. Originally, I had just checked whether the player was on the ground or not and had them fall depending on this. This used a constant gravity constant making the player fall in a constant speed. Upon further testing and comparison to other games, I noticed that this seemed unrealistic. As a result, I decided to accelerate the player with respect to the player's airtime. The longer the player stayed off the ground, the faster the player would fall.
- Next was the player's ability to jump which happened to be one of my favourite implementations. This was another part of the player's movements complemented with the gravity component. The intial process for this was just to move the player upwards at a constant speed until they reach their max jump height. However, just like with the gravity, it seemed unrealistic. In a similar way to gravity, I then decided to implement the player's movement when jumping and falling as if it were a parabola. At the highest point, the player would seem like the were floating and they move at a slower rate, then as they fall, they fall at a accelerating pace. This was by far one of my proudest parts of the player's movement in the game matching the movements of the player with the movements of a parabola.
- Another cool feature I added was the stun when the player would fall from a high height. This was a small detail in the original game that I thought would be a cool feature. How I decided to implement this was to check the player's airtime as they touch the ground to see if they stayed in the air past a certain time.

Player combat
- First was the player's attack. This consisted of a slash which extended from the player's sprite. This was done through hitbox detection where the slash would act as a seperate entity and if it collided with another entity that was hittable, it would damage it.
- Next was the player being able to get hurt. Similar to how the player attacked, I added a hitbox for the player and whenever an enemy entity collided with the player hitbox, it hurts the player.
I had also intended to add another function the player's combat where the player was able to shoot a long-ranged spell similar to Hollow Knight. However, due to time constraints, I wasn't able to fit that into the game for the final submission.

Boss/Enemy
Inspired by another game genre, Dark Souls, I wanted to introduce the character straight away to a challenge. This meant that the first enemy they encountered was a boss immediately testing the player's skills.
This boss was the Grub Mother from Hollow Knight, which consisted of two attacks.
- The first attack was when the Grub Mother would slam against the top and bottom of the screen attempting to hurt the player. This was done through first locating the player's location which determines the direction the Grub Mother first moves towards. Then for the actual attack, I would move the Grub Mother's pixel's towards the top and bottom of the screen respectively. To calculate when the Grub Mother would collide with the screen, I checked the location of the very top pixels and the location of the very bottom pixels and compared them to the borders of the screen.
- The second attack was when the Grub Mother would charge towards the player's location. I implemented this by comparing the player and the bosses' location, then moved the boss towards the player at a faster speed.
Overall, the boss design was another really fun process which I would love to do again. It used many of the skills and techniques I used for creating the player's movements in a more elaborate and creative way.

Finally, the **end design**. This was where I made final touches and added some smaller details to the game to enhance user experience.
- I added a starting menu for when the user first enters the game. This just detected the user's mouse click collisions with the buttons.
- Another cool feature was the animations for the characters. This was done through using a function which looped through all the characters animation frames. Each movement had a different frame speed so I had to account for that as well as the direction.
- Music was also added to the game depending on the player's location in-game. For example, the menu music would be different from the music when the player is fighting the boss battle.
- Last is the story line. I added npcs with different lines to steer the player towards the right direction in-game and to add a story element into the game.


# Lessons Learned:
As I made this game entirely through Python, I had many difficulties with things as simple as character movements, hitbox detections, collisions, animations, etc. This made me realize the incredible value that game engines hold for game creators. This also gave me a future project idea in order to create my own game engine.
Another lesson I learned came from the spaghetti code I had created. This was evident in my game since I practically coded everything in one main source file. This had many overlapping and redudant elements which is why I realized how I should've incorporated a more object oriented approach to this game as well as to many future programs I create in the future.


*All rights to the images and music copied from Hollow Knight go to Team Cherry. If requested, content will be taken down.
