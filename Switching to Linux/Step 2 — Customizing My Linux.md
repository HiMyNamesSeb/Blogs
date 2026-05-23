# Step 2 — Customizing My Linux

Now that Fedora was set up, my next challenge was customization — and this is where I made what I think was my biggest mistake so far.

## Step 1 — Hyprland (The Mistake) (~4 hours wasted, lol)

I saw Hyprland on TikTok and assumed it was something simple I could just install and use like an app. It is not.

I struggled with everything: I ran into dependency issues downloading it, then needed to write configs after installing it, then couldn't figure out how to switch sessions (rookie mistake, but it frustrated me). Once I got past all that, actually *using* it was a mess — system settings wouldn't open and I was stuck with a nearly unusable interface. I tried installing some dotfiles and it just made things worse, so I switched back to Plasma.

## Step 2 — Plasma Themes and Wallpapers

I'll admit I leaned on Claude for some of this because I hadn't watched the full YouTube tutorial yet — I thought I could figure it out on my own, lol. I found the right settings, installed a theme from the KDE Store, and called it done. You can absolutely find themes elsewhere online too, but I'm happy with mine.

Not hard at all, just had to know where to look.

## Step 3 — Panels and Widgets

This was the best and most frustrating part. Panels were mostly drag-and-drop — I just arranged things how I liked and tweaked orientation and sizing. For desktop widgets, I added a Spotify link, some audio visualizers, and a few utility widgets like a calendar and quick settings.

## Step 4 —  .bashrc Config

Used the tutorial from earlier to set up a few aliases for `vim`, `eza`, and `dnf`, plus some `cd` shortcuts. I wanted more so I used Claude to add things like default flags, more helpful aliases, expanded history, and a cleaner prompt.

## Step 5 — Firefox

Downloaded a GitHub repo that sets up a privacy-focused Firefox profile, then added a theme and the following extensions:

**GitHub Repo:**
- [arkenfox/user.js](https://github.com/arkenfox/user.js/)

**Extensions** (yes, I know I have too many tracker blockers):
- **uBlock Origin** — ad and content blocker
- **SponsorBlock** — skips sponsored YouTube segments
- **Decentraleyes** — tracking blocker
- **ClearURLs** — strips tracking parameters from URLs
- **Privacy Badger** — blocks hidden trackers

## Step 6 — System Settings

Went through miscellaneous settings like keyboard shortcuts (should have done this sooner), startup apps, and animations.

## Step 7 — Login Screen / SDDM

Easier than I expected. All I did was apply a theme I liked and set a wallpaper. I don't think I've scratched the surface of what's configurable here yet.