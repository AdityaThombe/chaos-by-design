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

**SeatSnatch** is a parody movie-ticket site that looks real and fights you at every step:

Movie page → **Sign in** → **Age check** → **Alert volume** → Showtimes → **How many seats?** → **Seat map** → **Hold to pay** → Checkout (**Bot check → Review → Terms → OTP**) → Ticket

| Step | The catch |
|---|---|
| Sign in | There's no login form. You type `#YourName` at the end of the URL in the **address bar**. |
| Age check | Age = **window width ÷ 40** and must be 13–30. You have to resize the browser. |
| Alert volume | Volume = **browser zoom**. Set it to exactly 67%, then back to 100%. |
| How many seats? | Defaults to **4**. Picking a seat grabs 4 in a row, so you have to change it to 1. |
| Seat map | **Biscuit the usher dog does the clicking.** He follows your cursor slowly and clicks what he's standing on. Popcorn distracts him. |
| Seat map | Other customers book or hold seats near the dog in real time. F12 always gets held once when the dog gets close. The layout and numbering are randomised every attempt. |
| Pay | You have to **hold** the button. Letting go resets it. |
| Bot check | "Tick **200 boxes in 1 second**." A big, friendly tip says to paste a snippet in the console, with a Copy button. **It's a trap:** doing that gets you flagged as a scalper bot. Ticking by hand is always too slow, and every fail needs a manual **Reset**. The real way through is a tiny grey **"i'm a human, let me through"** link in the bottom-right corner. Hints toward it only appear after 3 and 5 failures. |
| Review | Our records say you booked the wrong seat (random every attempt). The only way to dispute it is a tiny grey "report an issue" link, where you type the correct seat **backwards**. |
| Terms | **Ten cursors**, only one real. They reshuffle on mistakes and every 8 seconds. |
| OTP | The OTP appears in the **browser tab title**. You type it by tapping **Caps Lock**. |

Everything is solvable: no dead ends, no invisible hitboxes, no fake success screens, no flashing and no sound. The tuning knobs (dog speed, hold times and so on) are at the top of the script.

## The proof run (target: under 45 seconds)

1. **Book tickets.** Click the address bar, press `End`, type `#a`, press `Enter`, then **Continue**.
2. **Age:** press **Win + ←** to snap the window to half the screen (683px → 17 on a 1366px screen), then **Verify age**.
3. **Volume:** press **Ctrl + −** four times (100 → 90 → 80 → 75 → 67), wait a moment, then press **Ctrl + 0**. It moves on by itself.
4. Click any **showtime** → choose **1** → **Select Seats**.
5. Keep your cursor just **above** F12. When the dog's tag says **F12**, click. If F12 is striped, wait about 2.5 seconds and click again.
6. **Hold Pay** until the bar fills.
7. **Bot check:** ignore the tip. Click the tiny **i'm a human, let me through** link in the bottom-right corner.
8. **Review:** click the tiny **report an issue** link (bottom right) → type `21F`, then **Looks good, continue**.
9. **Terms:** wiggle the mouse to spot the real cursor, tick the box, then **Agree & continue**.
10. **OTP:** read the 2 digits in the tab title and tap Caps Lock that many times for each, pausing between digits.

**Before the judge or the neighbouring team plays:** maximise the window again and open `localhost:5517/?reset`.

---

`formality.html` is our earlier warm-up prototype: an 11-step sign-up form ("Formality®").
