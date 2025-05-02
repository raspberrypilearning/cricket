## Batting

The player needs to move their bat to the stump that the ball is moving towards.

Some code is already added for you.

### Complete the bat controls

--- task ---

Select the **Bat** sprite.

--- /task ---

--- task ---

Add code to move the bat to the `Right` stump when the <kbd>d</kbd> key is pressed.

Copy the format used for the <kbd>a</kbd> and <kbd>s</kbd> key controls.

```blocks3
when [d v] key pressed
show
set [Shot v] to [Right]
```

--- /task ---

### After a ball is bowled

A `ball bowled`{:class="block3event"} event is broadcast after the ball reaches its target stump

In the `when I receive [ball bowled v]`{:class="block3event"} block:

--- task ---

Check if the bat sprite is touching the **Ball** sprite.

```blocks3
when I receive [ball bowled v]
+if <touching (Ball v)?> then
else
```

--- /task ---

--- task ---

If the bat is touching the Ball sprite, the player scores some runs!

```blocks3
when I receive [ball bowled v]
if <touching (Ball v)?> then
+set [Runs v] to (pick random (1) to (6))
else
```

**Notice**: The number of runs scored is a random number between `1` and `6`.

--- /task ---

--- task ---

Tell the player how many runs they scored.

```blocks3
when I receive [ball bowled v]
if <touching (Ball v)?> then
set [Runs v] to (pick random (1) to (6))
+if <(Runs) = (1)> then
say [1 run!] for (.5) seconds
else
say (join (Runs) [ runs!]) for (.5) seconds
else
```

**Notice**: The code checks if the player scored just 1 run, because it wouldn't sound right to say “1 runs!” instead of “1 run!”. It says something different if the score is between 2 and 6 runs.

--- /task ---

--- task ---

Update the Score variable.

```blocks3
when I receive [ball bowled v]
if <touching (Ball v)?> then
set [Runs v] to (pick random (1) to (6))
if <(Runs) = (1)> then
say [1 run!] for (.5) seconds
else
say (join (Runs) [ runs!]) for (.5) seconds
+change [Score v] by (Runs)
else
```

**Notice**: The code checks if the player scored just 1 run, because it wouldn't sound right to say “1 runs!” instead of “1 run!”. It says something different if the score is between 2 and 6 runs.

--- /task ---

--- task ---

If the bat was not touching the ball wen it arrived at a stump, then the player loses a wicket.

Add a broadcast{:class="block3event"} so this can be handled by the **Middle** stump sprite.

```blocks3
when I receive [ball bowled v]
if <touching (Ball v)?> then
set [Runs v] to (pick random (1) to (6))
if <(Runs) = (1)> then
say [1 run!] for (.5) seconds
else
say (join (Runs) [ runs!]) for (.5) seconds
change [Score v] by (Runs)
else
+broadcast (wicket! v)
```

--- /task ---