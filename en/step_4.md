## Out!

--- task ---

Select the **Middle** stump sprite.

--- /task ---

This sprite tells the player they are out and reduces the number of wickets by 1.

If the player has lost all their wickets, then this sprite gives the player their score.

--- task ---

Add a `when I receive [wicket! v]`{:class="block3events"} block.

```blocks3
when I receive [wicket! v]
```

--- /task ---

--- task ---

Reduce wickets by 1.

```blocks3
when I receive [wicket! v]
+change [Wickets v] by (-1)
```

--- /task ---

--- task ---

Check if no wickets remain.

```blocks3
when I receive [wicket! v]
change [Wickets v] by (-1)
+if <(Wickets) = (0) > then
else
```

--- /task ---

--- task ---

Tell the player their 'team' is out.

```blocks3
when I receive [wicket! v]
change [Wickets v] by (-1)
if <(Wickets) = (0) > then
+say [ALL OUT!] for (1) seconds
else
```

--- /task ---

--- task ---

Use **four** `join`{:class="block3operators"} blocks to tell the player the score.

```blocks3
when I receive [wicket! v]
change [Wickets v] by (-1)
if <(Wickets) = (0) > then
say [ALL OUT!] for (1) seconds
+say (join [You scored: ] (join (Score) (join [ from ] (join (Deliveries) [ deliveries!])))) for (2) seconds
else
```

--- /task ---

--- task ---

If the player has wickets left, tell them the batter is out.

```blocks3
when I receive [wicket! v]
change [Wickets v] by (-1)
if <(Wickets) = (0) > then
say [ALL OUT!] for (1) seconds
say (join [You scored: ] (join (Score) (join [ from ] (join (Deliveries) [ deliveries!])))) for (2) seconds
else
+say [OUT!] for (0.5) seconds
```
--- /task ---

--- task ---

**Test:** Press <kbd>n</kbd> then <kbd>b</kbd> and get out **three** times - check the player is told each batter is ‘OUT!’ and, when all three wickets are lost, check the player is told the team is ‘ALL OUT!’ and the score is given.

--- /task ---
