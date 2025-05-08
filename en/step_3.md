## Batting

The player needs to move the bat to the stump the ball is moving towards.

Some code is already added for you.

### Complete the bat controls

--- task ---

Select the **Bat** sprite.

--- /task ---

Set the shot to `Right` stump when the <kbd>d</kbd> key is pressed.

--- task ---

Copy or duplicate the script for the <kbd>a</kbd> or <kbd>s</kbd> key controls.

```blocks3
when [d v] key pressed
show
set [Shot v] to [Right]
```

--- /task ---

### After a ball is bowled

A `ball bowled`{:class="block3events"} event is broadcast after the ball reaches a stump.

--- task ---

Add a `when I receive [ball bowled v]`{:class="block3events"} block.

```blocks3
when I receive [ball bowled v]
```

--- /task ---

--- task ---

Check if the bat sprite is touching the ball.

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

Update the Score variable.

```blocks3
when I receive [ball bowled v]
if <touching (Ball v)?> then
set [Runs v] to (pick random (1) to (6))
+change [Score v] by (Runs)
else
```

--- /task ---

--- task ---

**Test:** Press <kbd>n</kbd> then <kbd>b</kbd> and move the bat - check the player can score runs.

--- /task ---

--- task ---

Tell the player how many runs they scored.

```blocks3
when I receive [ball bowled v]
if <touching (Ball v)?> then
set [Runs v] to (pick random (1) to (6))
change [Score v] by (Runs)
+if <(Runs) = (1)> then
say [1 run!] for (.5) seconds
else
say (join (Runs) [ runs!]) for (.5) seconds
end
else
```

**Notice**: The code checks if the player scored just 1 run, because it wouldn't sound right to say “1 runs!” instead of “1 run!”. It says something different if the score is between 2 and 6 runs.

--- /task ---

--- task ---

If the bat is not touching the ball when it arrives at a stump, lose a wicket.

This is handled by the **Middle** stump sprite.

Add a new `broadcast`{:class="block3events"} message.

```blocks3
when I receive [ball bowled v]
if <touching (Ball v)?> then
set [Runs v] to (pick random (1) to (6))
if <(Runs) = (1)> then
say [1 run!] for (.5) seconds
else
say (join (Runs) [ runs!]) for (.5) seconds
end
change [Score v] by (Runs)
else
+broadcast (wicket! v)
```

--- /task ---

--- task ---

**Test:** Press <kbd>n</kbd> then <kbd>b</kbd> and move the bat to score runs - check the player is told the number of runs scored.

--- /task ---