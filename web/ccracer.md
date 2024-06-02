# CCRacer
## Description
This is a simple 2.5D racing game written in JS, where the player has to make 2 laps around the track. After a test race, it's pretty clear that this game isn't fair at all, the other cars are much, much quicker than the player's car (even though they have the same sprites). There's no clue about the flag location.
## Exploit
As one might guess, the flag is shown on screen when the player wins the race. Of course it's impossible to win the race playing fair, so a bit of cheating is involved.
There are many type of cheats to implement quite easily, i.e. stopping the bots cars, force the 1st position on the ladder, or cut a lap.
The one I used is the easier to find (and probably the funniest): speed hack. The game handles the player car data via the ```player``` object, and one of its attributes is ```player.maxSpeed```, which is hardcoded to 20000.
Adding a *little* boost to the max speed allows to fly through the race and grab the flag.
