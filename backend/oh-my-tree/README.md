# Oh My Tree

Implement a small console program that draws one or more ASCII Christmas trees.

- Time limit: Aim to complete as much as you can in 30 minutes.
- Tools: Any programming language and IDE
- Restrictions: Do not use AI/code generators. Write the code yourself.

## Tier1: Basic tree (4 levels)

Write a program that prints a centered fir tree to console using `*` character.

Example (4 levels):

```
   *
  ***
 *****
*******
```

## Tier 2: Add a trunk

Add a trunk centered beneath the tree, using `H` character.

Example (4 levels + trunk):
```
   *
  ***
 *****
*******
   H
```

## Tier 3: Read instructions from file

Read instructions from [tier3.csv](./tier3.csv) file, one tree per line.

Each line has `<levels><branchSymbol><trunkSymbol>`.

- levels is a positive integer (e.g., 4)
- branchSymbol is one character (e.g., *)
- trunkSymbol is one character (e.g., H)

Example:
```
4*H
6+Y
2O#
```

For each line:

- Draw the corresponding single tree.
- Assume branchSymbol and trunkSymbol are single characters. (So 5OU means levels=5, branch='O', trunk='U'.)

## Tier 4: Matrix of trees (grid from file)

Read a matrix of tree specs from [tier4.csv](./tier4.csv) file where each line contains a comma-separated list of Tier-3 specs. Draw the trees as a grid.

Example input (3×3 grid):

```
3*H,5*H,4*H
5OU,6OU,2OU
4+Y,4+Y,4+Y
```
