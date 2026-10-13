# SeatSnatch: Seat F12

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
- "Book again" on the confirmation page starts a fresh, re-randomised attempt.
- The confirmation page shows your best time on that laptop, for practice.

## What it is

**SeatSnatch** is a parody movie-ticket site. You go Movie page → Showtimes → "How many seats?" → Seat map → Pay → OTP → Ticket. Every step looks normal, and most of them aren't.

| Where | The catch |
|---|---|
| How many seats? | The ticket count defaults to **4**. Picking a seat grabs that many seats in a row, like real sites do. The test needs F12 on its own, so you have to change the count to 1. |
| Seat map | **Biscuit the usher dog does the clicking.** He follows your cursor slowly on a leash and presses whatever seat he's standing on. Now and then popcorn appears and he runs after it. |
| Seat map | Other customers book or hold seats near the dog in real time. The first time the dog gets close to F12, someone holds it for about 4 seconds. |
| Seat map | Randomised every attempt: row A can be at the back or the front, the aisle layouts change, and seat numbers run left→right or right→left, sometimes skipping numbers across the aisles. |
| Pay | Hold the pay button for 2.2 seconds. Let go early and it resets. Paying for anything other than F12 alone is declined, and the clock keeps running. |
| OTP | The OTP is sent to the **browser tab title**. You type it by tapping **Caps Lock** once per number. |

Everything is solvable: no dead ends, no invisible hitboxes, no fake success screens, no flashing and no sound.

## How to do it in under a minute (the proof run)

1. **Book tickets** → click any showtime → choose **1** → **Select Seats**.
2. Find F12. Keep your cursor just **above** the seat; the dog walks below it. When the dog's tag says **F12**, click.
3. If F12 is on hold (striped), wait about 4 seconds.
4. Hold **Pay** until the bar fills.
5. Read the 3-digit OTP in the tab title. Tap Caps Lock that many times for each digit, pausing between digits.

Practised, this takes about 25–35 seconds.

---

`formality.html` is our earlier warm-up prototype: an 11-step sign-up form ("Formality®").
