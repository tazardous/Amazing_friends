# Super Pals Rescue Run

A gentle platformer for little learners. Kellan, Diana and their dog Bernie are
a team of caped heroes who rescue their pals (Bun, Foxy, Robo-Bo and Whiskers)
from Doctor Grumble's goo bots. Nobody can lose: no lives, nothing hurts, and a
wrong answer is just "try again". The heroes, pals, villain, art, levels and music
are all original.

One self-contained `index.html`, no build step. The only network request is the
Press Start 2P font from Google Fonts; offline it falls back to a system
monospace font.

## Super powers

- **Cape glide.** Hold JUMP while you are in the air and the cape opens so you
  float down slowly. It makes the wide gaps easy.
- **Bop.** Land on a goo bot to bop it. Bumping into one from the side only pushes
  you back.
- **Bubble rescue.** Fall in a gap and Bernie floats you back to the last green flag.
- **Mushroom springs** reach the high ledges. Berries are just for fun.

## What it teaches

Captain Hoot the owl guards a rock gate in each level. Answer his question and it opens.

| Level | Topic | Easy (about age 4) | Harder (about age 6) |
|-------|-------|--------------------|----------------------|
| 1 ABC Rooftops | Letters | find a letter, first letter of a picture | match big to small letters, what letter comes next |
| 2 Count Subway | Numbers | count 1 to 6 things, what number is next | count to 10, add numbers, skip count by 2, 5, 10 |
| 3 Shape Harbor | Shapes | circle, square, triangle, star, heart | adds rectangle, oval, diamond, hexagon; name the shape; count sides |
| 4 Color Carnival | Colors | find a color, finish an AB pattern | more colors, mixing colors, harder patterns |
| 5 Hero HQ | Mixed | one of each topic | the harder version of each |

Questions are random, so every play is a little different. Each question is read
aloud with the browser's built-in voice (tap the panel to hear it again, TALK turns
it off). A hint shows after a wrong answer, and after two the right answer glows.
A star goes to each gate answered correctly on the first try.

## Playing

| Action | Keyboard | Touch |
|--------|----------|-------|
| Walk | Left and Right arrows (or A and D) | ◀ ▶ |
| Jump, then hold to glide | Space, Z or Up | JUMP |
| Pick an answer | Left and Right, then Space | tap the answer card |
| Pause | P or Esc | II |
| Music and sound | M | ♪ |
| Voice | V | TALK |

Pick Kellan or Diana and EASY or HARDER on the title screen. Choices are saved.

## Deploy

Settings -> Pages -> Deploy from a branch -> main -> / (root). Open the URL in
Chrome on the phone and use the menu to Add to Home screen. It opens full screen
in landscape.

## Making levels and questions

Levels are in `LEVELS` at the top of `index.html`: width in tiles, pits
(`[x, width]`), platforms (`[x0, x1, row]`), gate positions, critters, springs,
flags and which question types each gate asks. Keep pits to 3 tiles or less, put
the last gate 6 tiles from the end, and keep platforms away from gates. Question
types live in `GEN`, and `diff` is 0 for easy, 1 for harder.

## Testing

`tests/run.py` loads the game in headless Chromium and plays every level at both
difficulties with a bot (answering every other gate wrong on purpose), checks that
falling into a pit respawns, that tapping an answer card works, and runs a real-time
keyboard session. `tests/shots.py` saves screenshots of every screen.

```
pip install playwright
python -m playwright install chromium
python tests/run.py
```

## Updating

Edit, bump `CACHE` in `sw.js`, push.
