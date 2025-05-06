### Knock the bails off!

Start with the `BailL` sprite

--- task ---

Add a `when I receive [wicket! v]`{:class="block3events"} block.

```blocks3
when I receive [wicket! v]
```

--- /task ---

To create a spinning bail, your code will repeat some motion many times.

--- task ---

Add a `repeat`{:class="block3control"} block.

```blocks3
when I receive [wicket! v]
+repeat (10)
end
```

--- /task ---

--- task ---

Add your `motion`{:class="block3motion"} blocks.

```blocks3
when I receive [wicket! v]
repeat (10)
+turn cw (pick random (300) to (10000)) degrees
+move (pick random (1) to (10)) steps
end
```

--- /task ---

Change the size to add perspective.

--- task ---

Add a `size`{:class="block3looks"} block.

```blocks3
when I receive [wicket! v]
repeat (10)
turn cw (pick random (300) to (10000)) degrees
move (pick random (1) to (10)) steps
+change size by (pick random (-2) to (3))
end
```

--- /task ---

--- task ---

Experiment with different values for turn and move

--- /task ---

The bails need resetting.

--- task ---

Add a wait block then reset the `size`{:class="block3looks"}, `position`{:class="block3motion"} and rotation `(direction)`{:class="block3motion"}.

```blocks3
when I receive [wicket! v]
repeat (10)
turn cw (pick random (300) to (10000)) degrees
move (pick random (1) to (10)) steps
change size by (pick random (-2) to (3))
end
+wait (1) seconds
+set size to (6) %
+go to x: (-6) y: (2)
+point in direction (90)
```

--- /task ---

--- task ---

Drag the complete code from the `BailL` sprite to the `BailR` sprite.

--- /task ---

--- task ---

Change the reset position of the `BailR` sprite.

```blocks3
when I receive [wicket! v]
repeat (10)
turn cw (pick random (300) to (10000)) degrees
move (pick random (1) to (10)) steps
change size by (pick random (-2) to (3))
end
wait (1) seconds
set size to (6) %
+go to x: (6) y: (2)
point in direction (90)
```

--- /task ---