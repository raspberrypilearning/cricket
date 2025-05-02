## Bowling

The starter project contains some starter code and all the sprites you need.

--- task ---

Open the [starter project](https://scratch.mit.edu/projects/1168845390/editor/){:target="_blank"}.

--- /task ---

--- task ---

Select the **Ball** sprite.

--- /task ---

### Start bowling

When a player presses the <kbd> b </kbd> key, the contents of the `Stumps` `list`{:class="block3list"} is deleted, then three items are added: `Left`, `Middle` and `Right`.

One of these will be chosen at random as the target for the ball.

--- task ---

Add code to reduce by 1 the number of balls left in the 'over', after a ball is bowled.

```blocks3
when [b v] key pressed
delete all of [Stumps v]
add [Left] to [Stumps v]
add [Middle] to [Stumps v]
add [Right] to [Stumps v]
+change [Balls v] by (-1)
```

--- /task ---

--- task ---

Add 1 to the number of deliveries bowled in the match.

```blocks3
when [b v] key pressed
delete all of [Stumps v]
add [Left] to [Stumps v]
add [Middle] to [Stumps v]
add [Right] to [Stumps v]
change [Balls v] by (-1)
+change [Deiveries v] by (1)
```

--- /task ---

--- task ---

`Broadcast`{:class="block3events"} a message to tell other sprites that a ball is being bowled.

```blocks3
when [b v] key pressed
delete all of [Stumps v]
add [Left] to [Stumps v]
add [Middle] to [Stumps v]
add [Right] to [Stumps v]
change [Balls v] by (-1)
change [Deiveries v] by (1)
+broadcast (New Ball v)
```

--- /task ---

### Take aim!

The player needs to move their bat to the stump that the ball is moving towards.

--- task ---

In the `when I receive`{:class="block3events"} block, randomly set the stump to bowl at.

```blocks3
when I receive [New Ball v]
set size to (80)%
go to x: (120) y: (80)
+set [Stump v] to (item(pick random (1) to (3)) of [Stumps v])
```

--- /task ---

--- task ---

Tell the player which stump is chosen (so they know where to move their bat later)

```blocks3
when I receive [New Ball v]
set size to (80)%
go to x: (120) y: (80)
set [Stump v] to (item(pick random (1) to (3)) of [Stumps v])
+say (Stump) for (0.5) seconds
```

--- /task ---

### Move the ball to the target

--- task ---

To move the ball to the chose stump, it needs to point towards that stump and then move towards it, until it reaches it.

```blocks3
when I receive [New Ball v]
set size to (80)%
go to x: (120) y: (80)
set [Stump v] to (item(pick random (1) to (3)) of [Stumps v])
say (Stump) for (0.5) seconds
+repeat until <touching (Stump)?>
point towards (Stump)
move (4) steps
end
```

--- /task ---

### Get some perspective

--- task ---

As the bowl moves to the stump, it is moving further away so should look smaller as it does so.

```blocks3
when I receive [New Ball v]
set size to (80)%
go to x: (120) y: (80)
set [Stump v] to (item(pick random (1) to (3)) of [Stumps v])
say (Stump) for (0.5) seconds
repeat until <touching (Stump)?>
point towards (Stump)
move (4) steps
+set size to ((size) - (3)) %
end
```

--- /task ---

### Let other sprites know a ball has been bowled

--- task ---

Add a `broadcast`{:class="block3events"} message.

```blocks3
when I receive [New Ball v]
set size to (80)%
go to x: (120) y: (80)
set [Stump v] to (item(pick random (1) to (3)) of [Stumps v])
say (Stump) for (0.5) seconds
repeat until <touching (Stump)?>
point towards (Stump)
move (4) steps
set size to ((size) - (3)) %
end
+broadcast (ball bowled v)
+wait (1) seconds
```

--- /task ---

### Over!

There are 6 balls in each over.

--- task ---

Check if it is the end of an over.

```blocks3
when I receive [New Ball v]
set size to (80)%
go to x: (120) y: (80)
set [Stump v] to (item(pick random (1) to (3)) of [Stumps v])
say (Stump) for (0.5) seconds
repeat until <touching (Stump)?>
point towards (Stump)
move (4) steps
set size to ((size) - (3)) %
end
broadcast (ball bowled v)
wait (1) seconds
+if <(Balls) = (0)> then
end
```

--- /task ---

--- task ---

If it is, tell the player and reset the number of balls to 6.

```blocks3
when I receive [New Ball v]
set size to (80)%
go to x: (120) y: (80)
set [Stump v] to (item(pick random (1) to (3)) of [Stumps v])
say (Stump) for (0.5) seconds
repeat until <touching (Stump)?>
point towards (Stump)
move (4) steps
set size to ((size) - (3)) %
end
broadcast (ball bowled v)
wait (1) seconds
if <(Balls) = (0)> then
+say [That's over!] for (1) seconds
+set (Balls v ) to (6)
end
```

--- /task ---