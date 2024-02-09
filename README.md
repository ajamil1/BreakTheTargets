# BreakTheTargets
Unreal Engine Project, a mod for the VR title, "Pavlov"

This was a project I underwent while being unemployed during the pandemic, as a recreational project to hone in on my conceptual knowledge of programming, and to be treated as my inrto into the world of Unreal Engine.

This mod features a net-synced leaderboard, target placement, and score system. I will be going over how each system works.

The first task of this project was to create a target. Each target has a percentage chance on collision with a damage-dealing projectile to upgrade the target to its next tier, and raising the score of the target.
When a target is shot, there is a sound-indicator, and a short animation, as well as an action of moving the target.
There are a set ammount of spots on the target grid where a target may be placed. If a target is shot, it will move to another spot. If the spot is occupied, the target will continue to move to different spots until it has reached a vacant spot.
There are not more targets than there are spaces on the grid. No matter what, the targets will find a spot when damage is dealt.

On initialization of the game, there will be a timer to gather more players into the lobby. Once the game initialization timer reaches zero, we take every present player in the lobby, and add them to a map with their score set to zero.

Everytime a player hits a target, we will obtain the score value of the target, then cross reference the player ID of the damage dealer to the current map of players and scores, and increment accordingly to that players score.
Everytime we increment the players score, we update the in-game leader scores, 1st through 3rd. 
This is done by taking the current map of player and player scores, and splitting the player IDs and scores into two separate arrays. We obtain the index of the player ID, then match it with the index in the score array.
We then check through several if-else statements on if the player's score is greater than third place, then second place, then first place.
In addition to iterating through the current-game scores, we also have a separate server leaderboard that holds ten places for score holders and their names. The current players score from the latest target hit will be checked, iterating through all ten score positions on the leaderboard, similarly to how the current-game leaderboard check works.

A game will last for 120 seconds. When a game ends, we take the player who had the highest score within the game, and displays their name as the winner on round end. Then a timer to reset the game starts. When the timer hits zero, everyones score gets overwritten when the map sets all the players scores to zero, then the loop begins again.
