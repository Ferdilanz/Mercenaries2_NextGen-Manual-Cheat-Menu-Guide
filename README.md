# Mercenaries2-Manual-Modding-Guide
A guide explaining how to set up SecuROM Bypass with Logging Console, Mercs2 Native CheatMenu via Lua-Bridge, and an early Multiplayer-revival ASI mod while Mercenaries 2 NextGen modding is still in its infancy

# Getting Started
## Step 1: Secure the Keys
### Required Materials

| Item                                             | Source                                                                  | Purpose                                                                  |
| ------------------------------------------------ | ----------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| AustinKregel's SecuROM Bypass Patcher            | https://github.com/Mercenaries-Fan-Build/mercs2-securom-bypass/releases | Create a SecuROM-less Mercenaries2.exe. Recommend the x86_64 version. Current version 0.4.1 sha256:60e29e... |
| AustinKregel's `pmc_bb.dll`                      | https://github.com/Mercenaries-Fan-Build/pmc-blackbox/releases | Set up the logging console. Current version 0.2.0 sha256:d598ee... |
| LoganW234's `Mercs2Fix.asi` (WITH LUA) + DXWrapper | https://github.com/loganw234/Mercenaries2/releases/tag/Alpha            | Lua-bridge on localhost for direct Lua injection, a multiplayer fix & ASI loader. Current version 1.1.1 |
| LoganW234's `lua_repl.py`                        | https://github.com/loganw234/Mercenaries2/blob/main/tools/lua_repl.py | Using the Lua-bridge on localhost via CMD/Terminal |
| Python                                           | Type `python` in CMD as Administrator to install Python | Required to run `lua_repl.py` |
| Retail/Origin/EA Play copy of Mercenaries 2      | Rip a Retail disk or something, I can't help you commit software piracy | Acquire the game, you know, so you can mod it |

### Optional or Unnecessary Materials

| Item | Source | Purpose |
| --------------- | ---------- | ------------------------- |
| AustinKregel's Mercs2 ModKit | https://github.com/Mercenaries-Fan-Build/mercs2-modkit/releases | Optional, but it will definitely make modding Mercs2 NextGen easier in the future. It probably makes it easier now, too. |
| ElishaCloud's DXWrapper | https://github.com/elishacloud/dxwrapper/releases | It's an ASI loader. Unnecessary since LoganW234 already prepackages the required files with his Lua-bridge. |
| ThirteenAG's Ultimate ASI Loader | https://github.com/ThirteenAG/Ultimate-ASI-Loader/releases  | It's an ASI loader. Completely unnecessary for what we're doing since DXWrapper AND the SecuROM bypass have ASI loaders built into them. |

### Valid Executables
You **must** take a hash of your Mercenaries2.exe to determine whether it's usable for the SecuROM Bypass Patcher **and** the Lua-bridge. You can do this with any newer version of 7Zip through the context menu via right-clicking Mercenaries2.exe.
After getting the SHA256 hash, copy it to your clipboard by double-clicking it to highlight, CTRL + C to copy, CTRL + F on this page to FIND, then paste the hash into the search field using CTRL + V. If your SHA256 hash matches one of these, you may proceed. <ins>**If it doesn't, find a different copy of the game.**</ins>

| Version + Source                   | Size in bytes | Lua-Bridge Compatible? |  SHA256                    |
| ---------------------------------- | ------------- | ------------------------- | ------------------------ |
| 1.0 Origin/EA Play  (Signed EXE)   |  | Not thoroughly tested | a1532b4c7652fe9feee1191f5bd04aa073cd0f036e49831c754e7d895241dfa8 |
| 1.1 Retail + Repack (Unsigned EXE) |  | Confirmed | 7a348847e103d71e8c17e7a51a0f3b4d4422e0c9cb46ec6acc9fe5e4e6be36b5 |
| 1.1 ALL SecuROM Bypassed EXEs      |  | Confirmed | 958eb22776067c2dbb7d684e472c5045d419ec0ecfb49bfea7d23fcf4a83f115 |

## Step 2: Ascend from Darkness
### For the Sake of Neatness
It would be a good idea to create a `scripts`, `plugins`, or `update` folder in your `\Mercenaries 2 World in Flames\` game folder, where the Mercenaries2.exe file is, so as place any future ASI mods inside to keep the game folder as neat as possible. You'd really hate to be looking for an old ASI mod in the root folder because your game keeps crashing. Just make the folder, it makes future modding way easier on yourself. For this guide, I will be using `\Mercenaries 2 Worls in Flames\scripts\`.

## Step 3: Rain Fire

## Step 4: Unleash the Horde

## Step 5: Skewer the Winged Beast

## Step 6: Wield an Iron Fist

## Step 7: Raise Hell

## Step 8: Freedom
