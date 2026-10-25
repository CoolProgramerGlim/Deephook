# Deep Hook

A touch-controlled fishing game for Android phones. Cast your line, steer the hook through the deep, haul in fish for points, and avoid the jellyfish and poison fish. Clear 12 levels, earn coins and upgrade your gear.

Deep Hook is a single HTML5 file (`index.html`). It runs in any modern mobile browser and can also be packaged as an Android app with AdMob ads.

## How to play

Open the website: https://coolprogramerglim.github.io/Deephook/ to play the game!

1. **Aim and cast.** Touch and drag to aim. A dotted arc shows where the hook will land. Release to cast.
2. **Steer.** While the hook sinks, drag left or right to steer it toward fish.
3. **Reel in.** Tap to pull the line up early. It also reels in on its own when you reach the bottom or catch a fish.
4. **Bank your catch.** Points are added when the catch reaches the surface. Then cast again.

Each level has a timer and a score goal. Reach the goal to clear the level and unlock the next one.

## Fish and hazards

| Catch | Points | Notes |
|---|---|---|
| Sardine | 1 | Shallow and common |
| Perch | 3 | Mid-water |
| Tuna | 6 | Deep and fast |
| Golden fish | 15 | Rare, found deepest |
| Legendary fish | 30 | Pink boss fish, appears from level 2 (see below) |
| Poison fish | -5 | Green with purple spots. Touching one takes 5 points off your score straight away. Your score never drops below 0 |
| Jellyfish | lose catch | Touching one while carrying fish makes you drop your whole catch |

## Scoring tips

- **Combos:** banking 3 fish at once gives 1.5x points, 4 gives 2x and 5 gives 2.5x.
- **Lucky ring:** a pulsing ring appears on the water. Cast into it and a school of extra fish spawns around your hook.
- **Stars:** reaching the goal earns 1 star, 1.4x the goal earns 2 stars, and 1.8x the goal earns 3 stars.

## Legendary fish fight

From level 2 a large pink fish swims through the deep. If your hook touches it, a tension meter appears:

- **Hold** the screen to reel (tension rises).
- **Release** to ease off (tension falls).
- Keep the marker in the **green zone** to fill the catch bar.
- If tension hits the limit, the line snaps and you lose your whole catch. If the bar fills, you land a 30-point fish.

## Levels

| # | Level | Goal | Time | Look |
|---|---|---|---|---|
| 1 | Calm Cove | 20 | 60s | Sunrise peach and teal |
| 2 | Kelp Bay | 35 | 60s | Green |
| 3 | Dusk Reef | 50 | 60s | Purple and orange dusk |
| 4 | Storm Shelf | 70 | 55s | Stormy grey |
| 5 | Midnight Trench | 90 | 55s | Navy night |
| 6 | The Abyss | 120 | 50s | Deep violet |
| 7 | Glacier Bay | 140 | 50s | Ice blue |
| 8 | Coral Garden | 160 | 50s | Rose and magenta |
| 9 | Lava Vents | 185 | 50s | Dark red |
| 10 | Turquoise Flats | 210 | 45s | Bright turquoise |
| 11 | Aurora Deep | 240 | 45s | Green aurora night |
| 12 | Kraken Gate | 280 | 45s | Black and gold |

Later levels have faster fish, more jellyfish, more poison fish and more deep-water fish.

## Coins and the shop

After every round you earn coins equal to your score, plus 10 per star. Spend them in the Shop on three upgrades, each with 5 levels:

| Upgrade | Effect per level |
|---|---|
| Strong line | Carry 1 more fish per cast (starts at 4) |
| Fast reel | Reel in 12% faster |
| Sweet bait | Wider catch zone around the hook |

Upgrade cost is 25 x (current level + 1)^2 coins.

## Sound

The game has a menu melody, a separate in-game track that speeds up on higher levels, and sound effects for casting, catching, banking points, poison, jellyfish and the final seconds of a round. Phones only allow sound after a first tap, which is why the game opens on a "Tap to play" screen. Use the **Sound** button on the menu to turn sound and vibration off.

## Saving

Progress (unlocked levels, stars, coins, upgrades, best score, sound setting) is saved on the device in the browser's local storage. Clearing site data resets it.

## Ads

The game supports three ad setups. It ships with placeholder test ads only, so no real ads show until you configure one.

- **Test placeholders (default):** a banner strip, an interstitial after every 3rd round, and a rewarded "+10 seconds" ad after a failed level.
- **Google AdSense (web):** fill in the `ADSENSE` block near the top of the script (`client`, `bannerSlot`, `testMode`). This needs an approved AdSense site and the H5 Games Ads programme, and the file must be hosted on your own domain with an `ads.txt` file. AdSense ads do not load on the claude.ai preview link.
- **AdMob (Android app):** the Android project in `DeepHook-Android.zip` shows a native banner, interstitial and rewarded ads. The game talks to the app through `window.AndroidAds.showInterstitial()` and `showRewarded()`, and the app replies with `window.__adDone(true|false)`. It uses Google's test ad ids and includes the EU consent (UMP) flow.

Before publishing, replace the test ids (AdMob app id in `AndroidManifest.xml`, and the three unit ids in `MainActivity.kt`), set your own `applicationId`, and raise `targetSdk` to Google Play's current requirement. Set up a GDPR consent message in AdMob for players in the EEA.

## Project files

| File | What it is |
|---|---|
| `fishing-game.html` | The whole game: gameplay, menus, levels, shop, sound and ad hooks |
| `DeepHook-Android.zip` | Android Studio project that wraps the game in a WebView and adds AdMob |
| `README.md` | This file |

### Running it

- **In a browser:** open `fishing-game.html` on your phone, or host it on any web server. In Chrome, use "Add to Home screen" to launch it like an app.
- **As an Android app:** unzip `DeepHook-Android.zip`, open the folder in Android Studio, let Gradle sync and press Run.

### Customising

Everything is in `index.html` (copied to `app/src/main/assets/index.html` in the Android project):

- `LV` holds the levels (name, goal, time, jellyfish count, fish speed, fish mix and colour theme).
- `TYPES` holds the fish types and point values.
- `P` holds the saved-progress defaults, and `UP` holds the shop upgrades.
- `ADSENSE` and the `Ads` object hold the ad settings.

## Status

The game and Android project were written without being compiled or tested on a physical device. Expect to tune the cast arc, fish speeds and level difficulty once you play it, and let Android Studio update the Gradle and SDK versions if it asks.
