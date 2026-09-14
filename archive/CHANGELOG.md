# Changelog — SHD Loadout Bench

A Division 2 build planner. Pick gear, assign attributes, see what the loadout actually totals.

Current version is shown in the top left of the app, next to the title. **Please include it when reporting anything.**

This tool calculates expected statistical totals from gear, mods and set bonuses. It does not simulate damage.

---

## v0.4.0 beta — 11 September 2026

**Equipped sets panel**
Every brand and gear set you have on is now listed with its full bonus text, not just a piece count. Tiers you have reached are highlighted. Tiers you have not reached are still shown, dimmed, so you can see what one more piece would get you. Gear set chest and backpack talents are listed too, and only light up when you are at four pieces **and** have that specific piece equipped. Moved to the left column under the gear so sets sit next to the pieces that make them.

**SHD Watch is now per node**
It used to be a single on or off switch locked to a fully maxed watch, which was wrong for anyone still filling theirs in. All 16 nodes now have their own slider and number field, grouped by quadrant, with a running count of points assigned out of 800. Max all and Clear all buttons for the quick cases.

Worth knowing: four nodes give 0.4% per point and the other twelve give 0.2%. Crit Hit Damage, Headshot Damage, Skill Duration and Ammo Capacity are the double rate ones. If you are short on points, that difference matters.

**Every stat now shows where it came from**
Click any stat in the readout to expand it. You get every source that feeds it with its exact value, largest first, labelled by origin, so you see "Unit Alloys 2pc +24%" rather than wondering where a number came from. Under any stat with more than one source there is a proportional bar showing the split at a glance, without clicking.

Colour coded into seven categories with a legend at the top: core, rolled attribute, gear mod, brand bonus, gear set bonus, SHD Watch, specialization. Crit Hit Chance and Skill Tier are expandable too, since those are the ones you budget against a cap.

Rows stay open while you swap gear, so you can watch a single stat update live.

*Requested by a tester who had 24% Assault Rifle Damage on a build and could not work out where it was coming from.*

**Hazard breakdown panel**
Hazard Protection was a single number covering everything. It now breaks out into all eight status effect types, showing the universal protection, that type's own specific resistance, and a combined total.

**Please read this bit:** how those two actually combine is not something we have measured in game, so rather than guess, there is a dropdown to switch between additive and multiplicative. Treat the total column as a way to compare builds, not as a verified number.

**Build codes are now versioned**
Copy build code and Load build code carry the version that made them. A code from an older version still loads, with anything added since left at its default and a note telling you to check it over. A code from a newer version than you are running will tell you to update instead of loading something wrong.

**Fixes**
- Flat and percentage values are no longer added together. An armor core at +170,001 and a 10% SHD armor node are separate numbers, because they are separate things.
- The "you are under the crit cap" warning stopped firing on skill builds with no crit investment, where it was noise.

---

## v0.3.0 and earlier — internal

First working version. Six gear slots, 29 brands, 27 gear sets, 12 attribute pool, 14 gear mods, SHD Watch, specializations, set bonus tallying, crit and Skill Tier cap tracking, and derived cooldown, duration, reload and uptime figures.

---

## Not built yet

Listed so you know these are missing on purpose rather than broken.

| Feature | Status |
|---|---|
| **Weapons** (primary, secondary, sidearm) | Designed and agreed, waiting on data. Next major feature |
| **Named and exotic gear pieces** | Held until every exotic is catalogued. A partly filled list would read as "this does not exist" rather than "not added yet" |
| **Skills and skill mods** | Not started |
| **Colour blind modes** | Planned, and intended to match the modes the game itself offers so colours carry over rather than being a separate scheme |

---

## Known gaps in the data

Things the tool is honest about rather than filling in.

- **Gear set attribute rolls.** Gear set pieces roll their single attribute higher than brand pieces do, but we have only measured this for Crit Hit Chance and Crit Hit Damage. The other ten attributes are shown at the brand value, so gear set pieces rolling anything else are **understated**.
- **Ensnare and Shock resistance** show as `n/a` rather than zero. Those mods exist in game but we have no captured values for them, and `n/a` means "we do not know" while `0` would mean "you have none".
- **Gear set cores.** Six sets have their fixed core locked in the tool. The other 21 let you pick freely, which may not be correct. If you know a set has a fixed core we have not locked, that is worth reporting.
- **China Light Industries** shows "not recorded" on its bonuses. We do not have confirmed values for it yet.
- **SHD Watch Scavenging node** is not in the panel, as it has not been captured.

---

## Reporting something

Include the **version number** from the top of the app and a **build code** if the issue involves a specific loadout, since that lets the build be reproduced exactly.

Most useful reports are a number you think is wrong plus what you expected. Expanding the stat to see its sources usually narrows it down fast, and tells us whether it is bad data or bad maths, which are different problems with different fixes.
