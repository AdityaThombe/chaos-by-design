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

Movie page → Showtimes → **Seat map** → **Hold to book** → Checkout: **Account → Identity → Age → Mobile + OTP → Security** → *"Synchronizing Seat F12 Record…"* → Ticket (**TEST CASE COMPLETE: SEAT F12 BOOKED & CONFIRMED**)

| Step | The catch |
|---|---|
| Ticket count | Always starts at **4**, with no popup asking. Picking a seat grabs up to 4 in a row and Book stays locked. The only way to change it is the small **"4 Tickets ✎"** button on the seat map. |
| Seat map | Other customers book or hold seats **near your cursor** in real time. F12 always gets held once when your cursor gets close. The layout and numbering are randomised every attempt. |
| Book | You have to **hold** the button. Letting go resets it. |
| Express checkout | Pressing **Ctrl + P** during **Sign in** or **Mobile verification** blocks the print dialog and reveals a **Skip** button. Skipping sign-in assigns a random guest username (shown once; you need it for the identity step). Skipping mobile skips the number and OTP. This is documented only on the **☰ menu → Help & Support** page. |
| Account: sign in | Asks you to log in, with no Register button anywhere. No accounts exist, so it always fails: *"Invalid credentials! No active reservation profile found."* Only then does **Register** appear. |
| Account: register | 8 password rules, shown **one at a time** (Requirement *n* of 8, Prev/Next). The rules **hide while you're typing in any field**. A failed submit **wipes all four fields** and jumps to the first failed rule. |
| Identity | Type `#` + **your username** at the end of the URL in the address bar. |
| Age | Age = **window width ÷ 40**, must be 13–30. |
| Mobile | A valid Indian mobile number (starts 6–9, 10 digits) → Send OTP. The OTP appears in the **browser tab title** and you type it by tapping **Caps Lock**. |
| Security | An **"I'm not a robot"** checkbox opens a SnatchGuard grid. The rule (*"To proof you are human, click all the circles"*) is buried in a ~500-word **Instructions** page that vanishes as you click. 4 circles hide among ~45 rounded-square decoys. A wrong Verify locks the grid until **Refresh**. |

### The 8 password rules

1. At least 12 characters, with at least one uppercase and one lowercase letter.
2. Starts with a special symbol and ends with a **different** one (`! @ # $ % ^ & * _ -`).
3. The digits add up to exactly **10**.
4. The digits are in **strictly increasing** order.
5. Every digit except the last is immediately followed by a **lowercase** letter.
6. All uppercase letters sit in **one block of exactly 5**, with no vowels.
7. At least **3 uppercase one-letter chemical element symbols** (B C F H I K N O P S U V W Y).
8. No repeated characters (case-sensitive), and no `password`, `admin` or your username.

A password that passes all 8: **`@1n2s3h4MVKNR#`**

Everything is solvable: no dead ends, no invisible hitboxes, no fake success screens, no flashing and no sound. The tuning knobs (hold times and so on) are at the top of the script.

## The proof run (target: under 35 seconds)

1. **Book tickets** → any **showtime**.
2. Seat map: **4 Tickets ✎** (top right) → **1** → **Select Seats**.
3. Click **F12**. If it's striped (on hold), wait about 2.5 seconds and click again.
4. **Hold Book** until the bar fills.
5. Press **Ctrl + P** → **Skip sign-in** → read the guest username (for example `popcorn42`) → **Continue**.
6. Address bar → `End` → type `#` + that username → `Enter`. It moves on by itself.
7. **Win + ←** (snap to half the screen) → **Verify age**.
8. Press **Ctrl + P** → **Skip mobile verification**.
9. Tick **I'm not a robot** → click the 4 circles at **r1c7, r4c10, r7c15, r10c2** → **Verify**.

(The long way, without the shortcut, is still there: fail sign-in → Register with `@1n2s3h4MVKNR#` → mobile `9876543210` → Caps Lock OTP.)

**Before the judge or the neighbouring team plays:** maximise the window again and open `localhost:5517/?reset`.

---

`formality.html` is our earlier warm-up prototype: an 11-step sign-up form ("Formality®").
