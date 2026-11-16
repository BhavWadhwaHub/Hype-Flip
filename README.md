# Hype Flip

A sneaker-flipping idle game that runs in the browser. Start with $40 and one beat-up pair, clean and legit-check your kicks, sell when the hype is high, win drops, and grow from a bedroom reseller into a pop-up stall owner.

This is a playable web prototype. Purchases and ads are placeholders: nothing is charged and no real ads run.

## What's in the game

- **Core loop:** buy pairs (Thrift Bin or online listings), clean them, legit-check them, sell them.
- **Hype market:** all 42 sneakers change price continuously, with spikes and dips announced on the Hype Wire.
- **Mini-games:** scrub-to-clean, Spot the Fake, and a tap race for drops.
- **Order board:** customers post timed orders that pay 1.6×–3.3× market price.
- **Restoration lab:** send a pair away and it comes back Deadstock.
- **Sneaker book:** 12 collectible sets with permanent income bonuses and trophies on the shop wall.
- **Idle income:** five side hustles, four crew members who automate work, and earnings while you're away.
- **Daily hooks:** three daily goals, a 7-day login streak, mystery packages, and drops.
- **Characters:** a customizable 3D player, Uncle Dez (mentor), Kiki (rival), The Plug (supplier), crew and walk-in customers.
- **Guided tutorial:** seven steps that walk a new player through their first flip.
- **Three career stages:** Bedroom Flipper, Campus Plug, Pop-Up Stall.

## Screen sizes

The layout adapts to the browser width:

- **Phone (under 600px):** one column with tabs fixed at the bottom of the screen.
- **Tablet (600–979px):** the same single column, a little wider.
- **Desktop (980px and up):** a sidebar with your stats, the Hustle button and the tabs, next to a wide play area with the 3D shop and two-column content. On a keyboard, Space works as the Hustle button.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole game: layout, styles and code in one file. This is what you deploy. |
| `hype-flip-source.html` | The same game without the page wrapper, used for the Claude artifact version. Not needed for deployment. |
| `README.md` | This file. |

There is no build step and no server code.

## Run it on your computer

Open `index.html` in a browser. For the closest match to how it runs online, serve the folder instead:

```bash
npx serve .
```

Then open the address it prints (usually http://localhost:3000).

## Deploy to Vercel

**With the command line**

```bash
npx vercel          # first deploy, accept the defaults
npx vercel --prod   # publish updates
```

**With GitHub**

1. Create a repository and upload `index.html` (and this README).
2. In Vercel, choose **Add New → Project** and import the repository.
3. Leave the framework as "Other" with no build command. Vercel serves `index.html` as the site.
4. Every new upload to the repository redeploys the site.

Vercel's free Hobby plan is for personal, non-commercial use. Check their current terms before adding real ads or payments.

## How saving works

- Progress saves automatically every few seconds in the player's browser (`localStorage`, under the key `hypeflip-proto-v1`).
- A save stays on that device and browser. It doesn't follow the player to another device.
- Private or incognito windows don't keep saves.
- iPhone Safari can clear a site's data after about a week without a visit. Adding the game to the Home Screen avoids this.
- **Start over** in the Store tab wipes the save.

There are no accounts and no cloud save yet.

## What it loads from the internet

| Resource | From | If it fails |
|---|---|---|
| three.js 0.149.0 (3D graphics) | cdn.jsdelivr.net | The game falls back to a flat 2D shop and flat sneaker art. |
| Lilita One and Nunito fonts | Google Fonts | The game uses the device's default fonts. |

Everything else is inside `index.html`. Once loaded, the game doesn't contact any server.

## Test settings to change before a real launch

Timers are sped up so testers can see everything quickly. They are constants in the script inside `index.html`. Search for the name to find each one:

| Setting | Now | Planned for launch |
|---|---|---|
| `DROPLEN` (seconds between drops) | 180 (3 minutes) | About 3 hours |
| `LAB_T` (restoration time) | 180 (3 minutes) | About 4 hours |
| `ORDER_T` (order time limit, min and max seconds) | 240–480 (4–8 minutes) | Hours |
| Online listings refresh | Every 60 seconds | Slower |

Other placeholders:

- **Ads:** "Watch ad" buttons show a 3-second placeholder screen, then give the reward.
- **Store:** purchase buttons give the item for free.
- **Balance:** prices, income and stage costs haven't been tuned with real players.

## Known limits

- The 3D characters and sneakers are built from simple shapes in code. They are stand-ins for final art.
- Only three of the six planned career stages exist. Prestige ("Launch Your Own Label") isn't built.
- No sound or music.
- No notifications.
- Tested in a desktop test browser at phone, tablet and laptop sizes, not on a range of real devices. Older phones may run the 3D shop slowly.

## Next steps for the web version

1. Cloud save with login so progress follows players across devices.
2. Real timers and balance tuning.
3. Real reward ads and payments (a game portal's ad system, or Google H5 Games Ads and Stripe on your own site).
4. Install-to-home-screen support and offline play.
5. Privacy policy, terms and a cookie notice.
6. Sound, more stages, and the prestige system.

## Note on names

All sneaker brands, models and characters are fictional. Don't add real brand names, logos, shoe designs or celebrity names: game portals and app stores reject them, and the brands can demand a takedown.
