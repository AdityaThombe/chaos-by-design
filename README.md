# Formality® — Sign Up, Eventually

An intentionally frustrating (but fully working) registration form, built for **CSI-VIT's _Chaos by Design_** UI challenge.

Single file, no build step: plain HTML, CSS and JavaScript.

## Run it

Use Chrome and serve it locally (the mic, pop-up and keyboard steps behave best on `localhost`):

```bash
python -m http.server 5517
```

Then open <http://localhost:5517>.

- Allow pop-ups (the stamp step opens a second window).
- Allow the microphone, or use the space-bar fallback on the "Louder" step.
- Progress survives reloads. Open <http://localhost:5517/?reset> to wipe a run for the next player.

## The steps

| # | Step | The catch |
|---|------|-----------|
| 01 | Name | No text field — type `#YourName` in the address bar |
| 02 | Age | Window width ÷ 40, must be 30 or under |
| 03 | Volume | Browser zoom is the volume control |
| 04 | Phone | A dog on a leash re-enters your number; squirrels distract him |
| 05 | Robot? | Tick 300 boxes in one second (console welcome) |
| 06 | OTP | Hidden in the page source, entered with Caps Lock taps |
| 07 | Louder | Say "I love filling forms" into the mic |
| 08 | Terms | Ten cursors, one is real |
| 09 | Stamp | Drag a second browser window onto the target |
| 10 | Review | Our records misspell your name; dispute by typing it backwards |
| 11 | Submit | The submission code only appears in print preview (Ctrl + P) |
