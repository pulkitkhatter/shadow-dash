# Shadow Dash

A fast 2D neon endless runner. Plain HTML5 canvas, no dependencies, no third-party assets
(all art and sound are generated in code, so you own everything).

## Controls
- Jump / double jump: Space, Up, W, or tap the right side of the screen
- Slide (or fast-fall in the air): Down, S, or tap the left side
- Pause: P / Esc. Mute: M. Menu: Left/Right change skin, B buys it.

## Features
- Obstacles: crates, spikes, drones (slide under), tall walls (double jump)
- Power-ups: Shield (absorbs one hit), Magnet (pulls coins for 7s)
- 4 character skins unlocked with coins (Classic, Crimson, Ghost, Gold) - coins persist between runs
- Best score, wallet and skin saved in the browser
- Installable on phones (PWA) and works offline
- Ad hooks: rewarded "Revive" and an interstitial every 3rd death (see below)

## Files
- `index.html` - the whole game
- `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png` - mobile install + offline
- `shadow-dash.zip` - upload this to itch.io (contains all of the above)

## Publish on itch.io (free)
1. https://itch.io -> Dashboard -> Create new project. Kind of project: **HTML**.
2. Upload `shadow-dash.zip`, tick "This file will be played in the browser".
3. Viewport 960 x 540, tick "Mobile friendly" and "Fullscreen button".
4. Pricing: "$0 or donate" (suggest $1-3), or paid. Add 3-5 screenshots and a short description.

## Ads and revenue
Ads are OFF until you plug in an ad SDK. The game never shows fake ads. Each portal gives you its own SDK;
connect it by defining `window.AdSDK` before the game loads (e.g. in a small script tag above the game script):

    window.AdSDK = {
      showRewarded(done){ /* show a rewarded ad, then */ done(true /* or false if skipped */); },
      showInterstitial(done){ /* show a full-screen ad, then */ done(); }
    };

- When `AdSDK.showRewarded` exists, the Game Over screen shows a "Revive (watch ad)" button (once per run).
- When `AdSDK.showInterstitial` exists, one ad shows every 3rd death, at most once every 90 seconds.
- Test the flow without an SDK by opening the game with `?adtest=1` on the URL.

Where to get an SDK:
- CrazyGames, Poki, GameDistribution: apply with the game; they run the ads and share revenue.
  Each has its own review and rules, so read their docs before changing the ad code.
- Google AdSense for Games / AdMob (for an app): needs your own account and approval.
Only use ad networks you have signed up for, and follow their policies (no clicking your own ads).

## Android app (optional)
Wrap the folder with Capacitor (`npm i @capacitor/core @capacitor/cli @capacitor/android`,
`npx cap init`, `npx cap add android`, `npx cap sync`, then build in Android Studio).
Google Play needs a one-time $25 developer account. Use AdMob for ads in the app.

## Honest note
Most games earn little. Traffic is what pays: post short gameplay clips (TikTok, YouTube Shorts,
Reddit r/WebGames), read feedback, and keep adding content.
