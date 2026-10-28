# Project: Timers

> - **Files:** timer.html, timers.html
> - **Dates:** 2026-10-20 → 2026-10-27 (from git)
> - **Defaults:** tool TBD · model TBD
> - **Status:** prototype
> - **Use:** TBD
> - **Reusability:** artifact TBD · prompt pattern TBD
> - **Tags:** single-file-html, classroom-tool, audio, theming, localStorage
> - **Takeaway (draft):** Five prompts of iteration on one idea, from a single countdown to sand and tea views to a multi-timer page.
> - **Story value:** TBD
> - **Surprises:** A layout bug (the top view switcher clipped on short windows) was invisible to the assistant's first checks and only found by using it.

# Prompt 1 (class timer):

Generate me a standalone HTML file that I can use as a timer for in-class activities. There should be options for 10 and 15 minute timers for sure. Maybe also +1 and +5 options that work as 1, 5, but also will add those amounts?

Also it should be able to be paused and reset (stopped).

There should be a gentle, optional noise but sound like an alarm. Maybe like a bell? Options for sounds would be fantastic.

And make it colorful!

## Output 1:

I built the timer as a single file, [class-timer.html](class-timer.html). I haven't opened it in a browser yet, so none of it, including the sounds, has been tried. It needs no internet connection, so you can double-click it or keep it on a USB stick.

- **Timers:** The 10 and 15 buttons start a countdown straight away. +1 and +5 start a 1- or 5-minute timer when nothing is running. If a timer is running or paused, they add that time instead. I also added a custom-minutes box.
- **Pause and reset:** Pause turns into Resume. Reset stops everything and clears the clock.
- **Colors:** The background is an animated gradient, and the progress ring is a rainbow. The colors shift to amber when one minute is left, to blue while paused, and to flashing red-orange when time is up.
- **Sounds:** Bell, wind chime, soft gong, marimba, harp sweep, digital beeps, or silent (visual only). All of them are synthesized in the browser, so there are no audio files. You can set the volume, preview a sound, and choose to play it once, three times, or until you press Stop alarm.
- **Shortcuts:** Space pauses or resumes, R resets, 1 starts 10 minutes, 2 starts 15, + adds 1 minute, and 5 adds 5.

The countdown also shows in the browser tab title. Your sound, repeat and volume choices are remembered between visits. Browsers only allow sound after you've clicked something, so press any button once before class. The Preview button is a quick way to check the volume.

If you want to keep this work, I can move this session to a folder you choose.


# Prompt 2 (updating class timer):

Update with two features:

1. sand timer variant for ticking down. Sand should flow proportionately & also show the x:xx time remaining
2. tea brewing variant. I don't have a specific "look" that feels right, so use creative liberties.

## Output 2:

Direct file access isn't available, so I'll serve the file locally.

Tea view renders correctly. Now I'll check mid-brew and mid-drain colors with a short 6-second timer.

Both views work. I'll reset the timer and shut down the test server.

I added both variants to [class-timer.html](class-timer.html). A switcher at the top of the card (⭕ Ring · ⏳ Sand · 🫖 Tea) changes between them, and pressing **V** cycles through them. I opened the page in a browser and watched both views run, and the console showed no errors. I didn't test the alarm sounds or the finished state of these views.

**⏳ Sand timer**
- It's a hourglass with a pink-to-purple frame. The sand drains from the top bulb into the bottom one, with a thin stream of falling grains while it runs.
- The sand drains by volume, so the top bulb empties at a steady rate. A simple height-based drain would run fast at first and slow near the end.
- The time left (such as `9:57`) shows large beneath the glass.

**🫖 Tea brewing**
- It's a glass teacup on a rainbow saucer, with a teabag and tag hanging in the water.
- The water starts clear and steeps to pale gold, amber and a deep brown as time passes. The teabag bobs gently and steam rises while it runs.
- The status line shows the strength: *Just water → Light → Golden → Strong → Perfect*. At zero it says "Tea's ready!" with sparkles.
- Four tea presets appear only in this view: Green (3 min), Oolong (4), Black (5) and Herbal (6). The usual 10, 15, +1 and +5 buttons still work.

Pause, reset, the alarm sounds and the keyboard shortcuts work in every view, and the page remembers which view you last used. Sand and Tea show the full, ready-to-start picture when idle, while the Ring starts empty.

One thing to know: pressing +1 or +5 mid-brew lengthens the timer, so the tea's color moves back toward the start. That seemed right for "a bit longer", but I can change it to keep the current color if you'd prefer.

# Prompt 3 (tweaking sand/tea timer):

Hitting the buttons does update the time, but doesn't switch to the tea cup. I also don't see a sand timer variant.

There does seem to be a button or something at the top that I can't quite click. Maybe I clicked it once, but it didn't seem to do anything...

Also can you make the page background a bit lighter in color? It's rather intense. I like it, but another option is like a gently swirling tye-dye? Actually, I realize it's changing colors, but again, can you make it lighter?

## Output 3:

Everything checks out, so I'm cleaning up the test server and resetting the timer.

I fixed all three problems in [class-timer.html](class-timer.html). Please reload it, since an older copy open in your browser won't show the changes.

**Why you couldn't switch views.** The **Ring · Sand · Tea** switcher was the button you couldn't quite click. The page was centered in the window, so on a shorter window the top of the card was cut off and couldn't be scrolled to. The card now starts at the top and scrolls normally. That also explains the missing sand timer: the switcher was the only way to reach it. I loaded the page in a browser, switched to Sand and Tea, and ran each with a short timer. Both switch and animate correctly.

**Lighter background.** I went with the swirling tie-dye. It's now a soft pastel (pink, lavender, sky blue, mint, butter yellow, peach) that rotates slowly. The page still changes color with the timer's state:
- warmer peach and pink in the last minute
- cool blue when paused
- a faster swirl in warm reds when time is up

To keep everything readable, I switched the text to deep purple. The card is now frosted white. The hourglass and teacup outlines are purple, and the steam is lavender. If it's still too bright or too pale, the six colors are at the top of the file and easy to adjust.

**One more fix.** The tea presets (Green, Oolong, Black, Herbal) were showing in every view. They now appear only in Tea view.

# Prompt 4 (multiple timers page):

create a standalone HTML app that will let me set different little timers. For example, I could set one about tea steeping for 3 minutes, one for an hour from now to turn off my mug warmer, and one for two hours about a call/task.

it should be a simple/minimal interface that lets you modify them independently

## Output 4:

I built [timers.html](timers.html), a single file with no dependencies. I haven't opened it in a browser yet, so it's untested. Double-click the file to open it.

**Adding timers**
- Type an optional label and a duration, then press Enter. Durations can be `3m`, `1h`, `2h 30m`, `90s` or `1:30`. A bare number counts as minutes.
- The preset chips (3m, 5m, 10m, 25m, 1h, 2h) start a timer in one click, using whatever label you've typed.

**Each timer runs on its own**
- It shows a countdown, a progress bar, and the clock time it will ring (for example "rings at 3:42 PM").
- You can rename it by clicking the label.
- Buttons: Pause/Resume, −1m, +1m, +10m, Restart, and × to delete.

**When a timer finishes**
- It plays three beeps, sends a desktop notification (the browser asks for permission the first time you add a timer), and the card turns orange and says "Done". Dismiss removes it, and Restart runs it again.
- The browser tab title shows the next countdown, so you can see it from another tab.

**Persistence and layout**
- Timers are saved in the browser and keep counting if you close and reopen the page. One that expired while the page was closed shows as Done.
- It follows your light or dark mode and works at phone width.

Browsers throttle background tabs, so a timer may alert up to about a second late. Keep the tab open for the alerts to fire.

# Prompt 5:

I didn't hear a sound; I'd also like to be able to drag them, while running, to prioritize/order.

And by default, new timers should be inserted into the list according to amount of time, ascending

## Output 5:

I've made all three changes in [timers.html](timers.html), but I haven't run it in a browser, so none of it is tested.

- **Sound:** Browsers block audio until you've interacted with the page, and my first version tried to play from a background timer. The page now unlocks audio on your first click or keypress, and the alert is louder: two sets of three beeps. If you still hear nothing, make sure you've clicked or typed in the page since loading it, and check the tab isn't muted.
- **Dragging:** Each card has a ⋮⋮ handle on the left. Grab it and move up or down, and the other cards shuffle out of the way. It works on running, paused and finished timers, and the order is saved. Timers keep counting while you drag. Pointer events should make this work on touch screens too.
- **Sorted insertion:** A new timer goes into the list by time remaining, shortest first. A 3-minute timer lands above a 1-hour one. After that you can drag them into any order, and adding another timer doesn't re-sort the ones you've arranged.

Finished timers show 0 remaining, so new timers land below them.



