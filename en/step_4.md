## Out!

--- task ---

Select the **Middle** stump sprite.

--- /task ---

This sprite tells the player they are out and reduces the number of wickets by 1.

If the player has lost all their wickets, then this sprite gives the player their score.

--- task ---

Add a `when I receive [wicket! v]`{:class="block3events"} block.

```blocks3
when I receive [wicket v]
```

--- /task ---

--- task ---

Reduce the wickets by 1.

```blocks3
when I receive [wicket v]
+change [Wickets v] by (-1)
```

--- /task ---

--- task ---

Check if all wickets have been lost.

```blocks3
when I receive [wicket v]
change [Wickets v] by (-1)
+if <(Wickets) = (0) > then
else
```

--- /task ---

--- task ---

Tell the player their 'team' is all out!

```blocks3
when I receive [wicket v]
change [Wickets v] by (-1)
if <(Wickets) = (0) > then
+say [ALL OUT!] for (1) seconds
else
```

--- /task ---

--- task ---

Use `join`{:class="block3operators"} blocks to tell the player what they scored.

```blocks3
when I receive [wicket v]
change [Wickets v] by (-1)
if <(Wickets) = (0) > then
say [ALL OUT!] for (1) seconds
+say (join [You scored: ] (join (score) (join [ from ] (join (Deliveries) [ deliveries!])))) for (2) seconds
else
```

--- /task ---

--- task ---

If the player still has wickets left, tell them the current batter is out.

```blocks3
when I receive [wicket v]
change [Wickets v] by (-1)
if <(Wickets) = (0) > then
say [ALL OUT!] for (1) seconds
say (join [You scored: ] (join (score) (join [ from ] (join (Deliveries) [ deliveries!])))) for (2) seconds
else
+say [OUT!] for (0.5) seconds
```
--- /task ---
