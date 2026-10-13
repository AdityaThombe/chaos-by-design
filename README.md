# Ciné Chaos: Seat F12

Our entry for **CSI-VIT's _Chaos by Design_**, problem statement 3:

> **Cinema seat selection.** Test case: select seat **F12** from an interactive seat map and confirm the selection.

It's one HTML file with plain HTML, CSS and JavaScript. No build step.

## Run it

```bash
python -m http.server 5517
```

Then open <http://localhost:5517> in Chrome.

- An attempt survives reloads, and the clock keeps running.
- Open <http://localhost:5517/?reset> to clear a half-finished attempt.
- "New attempt" on the ticket screen starts a fresh, re-randomised hall.
- The start screen keeps a practice log of your times on that laptop.

## What makes it slow

| Mechanic | What happens |
|---|---|
| Lights off | You only see the seats near your cursor (a torch). The torch dims when you stop moving, so shake the mouse to recharge it. |
| Real-cinema rows | Row letters skip **I** and **O**, like real cinemas. They're painted on one side wall only, and only visible in torchlight. |
| Random every attempt | The screen can be at the top or the bottom (row A is always nearest the screen). The aisle layout and the seat numbering scheme change too: left→right, right→left, zig-zag, or odds on one side and evens on the other. Watching someone else's run doesn't give the answer away. |
| Slow labels | A seat's label appears only after you hover it for about half a second. |
| Other customers | People book seats, or put them on hold, near your cursor in real time. The first time you get close to F12, someone else holds it for about 4 seconds. |
| Complimentary friends | Selecting a seat also selects its free neighbours on both sides. Click them again to deselect them. |
| Hold to confirm | You have to hold Confirm for 2.5 seconds. Letting go early jams the ticket printer. Confirming the wrong seat cancels the booking and the clock keeps running. |

Everything is solvable: no dead ends, no invisible hitboxes, no fake success screens, no flashing and no sound.

## How to do it in under a minute (the proof run)

1. Keep the mouse moving so the torch stays bright.
2. Find which wall has the row letters and where the screen is, then sweep along that wall to row **F**.
3. Hover any free seat in row F and read its number. Hover one more to work out which direction the numbers run, then jump to 12.
4. If F12 is "on hold", wait about 4 seconds.
5. Click F12, then click the friends it added to deselect them.
6. Hold **Confirm F12** until the bar fills.

Practised, this takes about 20–30 seconds.

---

`formality.html` is our earlier warm-up prototype: an 11-step sign-up form ("Formality®").
