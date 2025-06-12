🛡 Spellmaster Report: AI Human Warrior – Minimal Kit
Zadání bylo jasné: 2 útočné ability, maximum Arduino jednoduchosti, přesto jasný PvP tlak
jako správný Arms Warrior.
Tady je hotový balíček – elegantní, agresivní, bez zbytečného balastu. 🧠⚔️
---
🪓 THARG SKULLBREAKER – SPELLSET (AI verze)
🔹 Spell #1: CHARGE
> ⚡ Přeskoč dopředu a otevři boj – klasika všech klasik.
Efekt: Warrior se posune o 1 pole dopředu a způsobí 1 DMG.
Cooldown: 6 s
LED: Bílé pulzující světlo během pohybu → krátký červený záblesk při zásahu (impact)
Trigger logika:
Trigger přes IR detekci cíle do 2 polí
Pokud pole před sebou je volné → proveď Charge
Arduino poznámka: millis() cooldown + IR senzor (nebo line-of-sight logika)
---
🔹 Spell #2: SHIELD BREAKER
> 💥 Silný vertikální úder, který ignoruje nebo ničí obranný efekt
Efekt: Způsobí 2 DMG a zruší štít (např. Divine Shell nebo Soulbind Shield)
Cooldown: 7 s
LED: Žlutý dvojzáblesk + silnější červená na dopad
Trigger logika:
Pokud detekován obranný efekt na cíli (v Arduino může být “isShielded = true”)
Pokud ne, použije se jako silný úder (není plýtvání)
Arduino poznámka:
Trigger buď na základě komunikace mezi figurkami (I²C?) nebo pomocí stavu uloženého v
paměti o cíli – jednoduchý bool targetShielded.
---
🔸 (Volitelná pasivka): BATTLE HARDENED
> 🛡 Každý útok do Tharga je o -1 DMG menší po dobu 3 sekund po jeho vlastním útoku.
Efekt: Po použití spellu aktivuje obranu – snižuje příchozí damage o 1.
Trvání: 3 s po každém spellu
LED: Měkký modrý glow během trvání efektu
Arduino poznámka:
Po použití libovolného spellu → nastav battleHardened = true, uložit čas přes millis(), a
ignorovat +1 DMG z příštího zásahu, pokud efekt trvá.
---
✅ Shrnutí Spellsetu
Název Typ Efekt Cooldown LED
Charge Aktivní Posun +1, 1 DMG 6 s Bílá→Červená
Shield Breaker Aktivní 2 DMG + remove štít 7 s Žlutá→Červená
Battle Hardened Pasivka -1 DMG z příštího zásahu Auto Modrý glow
---
🎯 Tento set je ideální pro AI ovládání: Warrior detekuje vzdálenost, štíty a rotuje dvě
tlakové ability. Není třeba komplikovaných rozhodovacích větví – jasné signály, jasný boj.
# Tharg Skullbreaker – Dwarf Warrior (AI-Controlled)
**Role:** Frontline Bruiser (AI)
**Race:** Dwarf
**Origin:** Tribute to OG Arms Warriors from the WotLK PvP era
---
## 🧠 Design Philosophy
This Warrior is AI-controlled, focused on simple, clean interactions and low-complexity
behavior. Only two active spells and one passive, optimized for easy programming and
physical readability via LED signals.
---
## ⚔️ Spellset Overview
### 1. `Charge` – Quick Gap Closer
- **Type:** Active
- **Effect:** Move 1 tile forward and deal 1 DMG to the first enemy in path
- **Cooldown:** 6 seconds
- **LED:** White pulsing → Red flash upon impact
- **Arduino Notes:** Trigger move function + damage LED + cooldown reset logic
---
### 2. `Shield Breaker` – Anti-Defense Slam
- **Type:** Active
- **Effect:** Deal 2 DMG and remove target’s defensive shield if active
- **Cooldown:** 7 seconds
- **LED:** Double yellow flash + red burst
- **Arduino Notes:** Check for "shield" state on target, cancel buff
---
### 3. `Battle Hardened` – Auto Defense Buff
- **Type:** Passive
- **Effect:** Reduces next incoming DMG by 1, triggered automatically after any of Tharg’s
own spells. Duration: 3 seconds
- **LED:** Faint blue glow while active
- **Arduino Notes:** Activate short-duration resistance timer after spellcast
---
## 🛠 Technical Notes
- All spells are designed to be **visibly distinct via LEDs**
- Spell logic avoids random chance and AoE zones
- Perfect for use as first AI test model
---
## 🏅 Arena Legacy Context
Tharg represents the **unshakable frontline fighters** of the golden WoW PvP era
(2008–2012), specifically Arms Warrior mains who controlled the field through pressure,
timing, and controlled aggression.
He is paired in-game with a Holy Paladin AI partner in honor of legendary 2v2 comps.
> *Let the roar of dwarven steel echo across the arena once more…*