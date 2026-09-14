# Changelog — SHD Loadout Bench

A Division 2 build planner. Pick gear, assign attributes, see what the loadout actually totals.

Current version is shown in the top left of the app, next to the title. **Please include it when reporting anything.**

This tool calculates expected statistical totals from gear, mods and set bonuses. It does not simulate damage.

---

## v0.6.1 beta — 14 September 2026

**Fixed:** the settings panel opened by itself on page load and would not close. A styling rule was overriding the attribute that hides it, so the panel was always visible and the Close button had nothing to do. Introduced in 0.6.0 and fixed the same day.

---

## v0.6.0 beta — 14 September 2026

**Settings panel**

A Settings button in the header opens a panel holding everything that is a setting rather than part of a build. Three things moved into it, and none of them changed behaviour:

The **base values** — skill cooldown, duration and reload — were sitting in the Character card next to your specialization, which made them look like build choices. They are not. They are the starting numbers the derived figures are calculated from, and the panel now says so.

The **SHD Watch toggle** and the **hazard stacking model**, which was previously buried inside the hazard panel where it read as part of the data rather than a choice you were making.

**Two settings are listed but not built**, with the reason stated rather than left blank.

Units, an imperial and metric toggle, is blocked because the game reports distance three different ways for one weapon: Range in feet, Damage Drop Off in yards, and Optimal Range with no unit at all. Converting a figure whose unit is unknown produces a confidently wrong number.

Colour blind mode is blocked on capturing the game's own accessibility settings, because the point is to match the palette the game uses rather than pick a different one.

---

## v0.5.0 beta — 14 September 2026

**Specialization weapon pool**

Pick a specialization and seven weapon damage nodes appear, each with a dropdown for how many tiers you have bought. 5% weapon type damage per tier, three tiers per node, five points each, against a 45 point budget with a running counter.

45 points at 5 per tier is nine tiers, which is exactly three nodes at maximum. There is no allocation that both uses the budget and spreads further than three.

**They resolve against your Equipped weapon**, the same as a brand's weapon type bonus. Max Running The Gun for 15% shotgun damage, equip an assault rifle, and it greys out. That is the honest picture: the points are spent either way, but only the matching one is paying out.

**Each node shows which exclusive mod it gates.** Firewall's Tactical Short Grip sits behind Running The Gun, Sharpshooter's Digital Scope behind This Is My Rifle, and so on. That makes the real cost visible: taking your specialization's mod means one of your three picks is decided for you.

**Still not built:** the 120 point main tree. Picking a specialization on its own still adds almost nothing, and the +50% Pulse Resistance every specialization grants is not yet shown.

---

## v0.4.3 beta — 14 September 2026

**Eight brands and one gear set were missing from the tool entirely**

Gila Guard, Walker Harris & Co., Badger Tuff, Belstone Armory, Richter & Kaiser GmbH, 5.11 Tactical, Zwiadowka Sp. z o.o., Brazos de Arcabuz, and the Ember Engine gear set.

All nine were captured in the project catalogue but had never been carried into the mechanics table the tool builds from, so they were absent from every version up to and including 0.4.2. **Any build using one of them simply could not be made.** The tool now holds 37 brands and 28 gear sets.

Brazos de Arcabuz is worth a look: its 2pc grants a full Skill Tier, which only one other brand does.

**Seven of the new brands have no core attribute recorded.** The values were captured but the core type never was, so the tool lets you pick freely on those. That is a gap in the data, not a design choice.

**Ember Engine's chest talent is flagged.** Flashpoint reads "increase the chance of applying Burn to 20%", which would halve the 4pc's 40% chance. The tooltip has been confirmed as transcribed correctly, so the anomaly is in the game rather than in the data. Treat that one talent with suspicion.

---

## v0.4.2 beta — 14 September 2026

**Weapons**
Three slots: Primary, Secondary and Sidearm. All 81 craftable weapons are selectable with base damage, rate of fire and magazine size.

A check mark marks exactly one weapon as **Equipped**. Only that weapon is active, whatever the other two are. Checking one clears the others.

**Gear bonuses now resolve against what you are holding**
This is the part worth playing with. A weapon type bonus goes inactive, dimmed and struck through, when your Equipped weapon does not match, with a line explaining why. Put Unit Alloys 2pc on and equip an LMG and its 24% Assault Rifle Damage greys out, because that part of your gear budget genuinely is doing nothing until you switch.

**Weapon data is incomplete on purpose**
Only the 15 Assault Rifles have the full detail pass: reload, range and attributes. The other 66 carry base stats only. Blank means not captured, not zero, and the tool says so rather than showing you a plausible looking number.

**No weapon damage output**, and it will stay that way for now. A crafted weapon reads 38.6% above its base damage while its two attributes account for only 32.6%. Until the missing 6% is understood, any damage figure would be invented.

**Fixed**
- Removed a Gunner specialization value that never existed. The tool showed +10% Magazine Size for Gunner; the captured specialization trees contain no such node.

**Note on build codes:** the saved format changed to carry weapons. Codes from 0.4.1 and earlier still load, with weapons left empty and a warning.

---

## v0.4.1 beta — 14 September 2026

**Gear data moved out of the app**
The builder now loads its data from a separate file generated from a master spreadsheet, rather than having it written into the code. Corrections are a spreadsheet edit rather than a code change, and the generator validates the data before it ships.

**Fixed**
- **Česká Výroba pieces showed no core attribute.** The brand name carries accented characters and the internal mapping did not match. Found by the new validation checks on their first run.

**Note:** from 0.4.1 the app cannot be opened by double clicking the file. Browsers block the data fetch from disk, so use the link.

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
