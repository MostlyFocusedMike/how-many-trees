# How Many Trees?
## A challenge lovingly ripped off from advent of code
[source](https://adventofcode.com/2020/day/3)

## Setup
You are sledding down a hill in a very strong sled, so you can hit trees. The question is: how many trees WILL you hit?

You have a grid of squares, and your sled moves 3 to the right, and 1 down. If you start in the top left corner, what is the number of trees that you will encounter. Your starting square will never have a tree in it. Note that trees have no impact on your velocity. Like I said, your sled is STRONG.

## The Terrain
In each cell there is either a tree `(#)` or nothing `(.)`

```plaintext
..##.......
#...#...#..
.#....#..#.
..#.#...#.#
.#...##..#.
..#.##.....
.#.#.#....#
.#........#
#.##...#...
#...##....#
.#..#...#.#
```

In the actual input, it will be much longer (that's 10 rows long, the real input is hundreds). But it's not just long, it's wide. That input will repeat horizontally, forever so that you can never run out of horizontal space:

```plaintext
..##.........##.........##.........##.........##.........##.......  --->
#...#...#..#...#...#..#...#...#..#...#...#..#...#...#..#...#...#..
.#....#..#..#....#..#..#....#..#..#....#..#..#....#..#..#....#..#.
..#.#...#.#..#.#...#.#..#.#...#.#..#.#...#.#..#.#...#.#..#.#...#.#
.#...##..#..#...##..#..#...##..#..#...##..#..#...##..#..#...##..#.
..#.##.......#.##.......#.##.......#.##.......#.##.......#.##.....  --->
.#.#.#....#.#.#.#....#.#.#.#....#.#.#.#....#.#.#.#....#.#.#.#....#
.#........#.#........#.#........#.#........#.#........#.#........#
#.##...#...#.##...#...#.##...#...#.##...#...#.##...#...#.##...#...
#...##....##...##....##...##....##...##....##...##....##...##....#
.#..#...#.#.#..#...#.#.#..#...#.#.#..#...#.#.#..#...#.#.#..#...#.#  --->
```

## Example answer
So with the following rows:
```js
const inputs = [
    '..##.......',
    '#...#...#..',
    '.#....#..#.',
    '..#.#...#.#',
    '.#...##..#.',
    '..#.##.....',
    '.#.#.#....#',
    '.#........#',
    '#.##...#...',
    '#...##....#',
    '.#..#...#.#',
];

getNumberOfTrees(inputs)
// returns 7
```

And you can see it here:

```plaintext
0.##.........##.........##.........##.........##.........##.......  --->
#..O#...#..#...#...#..#...#...#..#...#...#..#...#...#..#...#...#..
.#....X..#..#....#..#..#....#..#..#....#..#..#....#..#..#....#..#.
..#.#...#O#..#.#...#.#..#.#...#.#..#.#...#.#..#.#...#.#..#.#...#.#
.#...##..#..X...##..#..#...##..#..#...##..#..#...##..#..#...##..#.
..#.##.......#.X#.......#.##.......#.##.......#.##.......#.##.....  --->
.#.#.#....#.#.#.#.O..#.#.#.#....#.#.#.#....#.#.#.#....#.#.#.#....#
.#........#.#........X.#........#.#........#.#........#.#........#
#.##...#...#.##...#...#.X#...#...#.##...#...#.##...#...#.##...#...
#...##....##...##....##...#X....##...##....##...##....##...##....#
.#..#...#.#.#..#...#.#.#..#...X.#.#..#...#.#.#..#...#.#.#..#...#.#  --->
```

Now, using the inputs from the file, how many trees would you hit? Hint: It's more than 100 and less than 500.

# Bonus
So your sled goes 3 right and 1 down, but what would it do if the pattern changed?

- Right 1, down 1. = ???
- Right 3, down 1. = answer from main question
- Right 5, down 1. = ???
- Right 7, down 1. = ???
- Right 1, down 2. = ???

Take the answer from each one of those new trajectories, and multiply them together, what answer would you get? hint: It's around a billion
