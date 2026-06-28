# Mercenaries 2 World in Flames "NextGen": Guide to Manually Access the Cheat-Menu

A guide explaining how to set up SecuROM Bypass with Logging Console, Mercs2 Native CheatMenu via Lua-Bridge, and an early Multiplayer-revival ASI mod while Mercenaries 2 NextGen modding is still in its infancy. Guide deprecates when this process becomes automated.

# Getting Started
## Step 1: Secure the Keys
### Required Materials

| Item                                             | Source                                                                  | Purpose                                                                  |
| ------------------------------------------------ | ----------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| AustinKregel's SecuROM Bypass Patcher            | https://github.com/Mercenaries-Fan-Build/mercs2-securom-bypass/releases | Create a SecuROM-less Mercenaries2.exe. <br/> Recommend the x86_64 version. <br/> Current version 0.4.1 <br/> sha256:60e29e... |
| AustinKregel's `pmc_bb.dll`                      | https://github.com/Mercenaries-Fan-Build/pmc-blackbox/releases | Set up the logging console. <br/> Current version 0.2.0 sha256:d598ee... |
| LoganW234's `Mercs2Fix.asi` (WITH LUA) + DXWrapper | https://github.com/loganw234/Mercenaries2/releases/ | Lua-bridge on localhost for direct Lua injection, a multiplayer fix & ASI loader. <br/> Current version 1.1.1 |
| LoganW234's `lua_repl.py`                        | https://github.com/loganw234/Mercenaries2/blob/main/tools/lua_repl.py | Using the Lua-bridge on localhost via CMD/Terminal |
| Python                                           | Type `python` in CMD as Administrator to install Python | Required to run `lua_repl.py` |
| Retail/Origin/EA Play copy of Mercenaries 2      | Rip a Retail disk or something, I can't help you commit software piracy | Acquire the game, you know, so you can mod it |

### Optional or Unnecessary Materials

| Item | Source | Purpose |
| --------------- | ---------- | ------------------------- |
| AustinKregel's Mercs2 ModKit | https://github.com/Mercenaries-Fan-Build/mercs2-modkit/releases | Optional, but it will definitely make modding Mercs2 NextGen easier in the future. It probably makes modding easier now, too. |
| ElishaCloud's DXWrapper | https://github.com/elishacloud/dxwrapper/releases | It's an ASI loader. Unnecessary since LoganW234 already prepackages the required files with his Lua-bridge. |
| ThirteenAG's Ultimate ASI Loader | https://github.com/ThirteenAG/Ultimate-ASI-Loader/releases | It's an ASI loader. Completely unnecessary for what we're doing since DXWrapper AND the SecuROM bypass have ASI loaders built into them. |

### Valid Executables
You **must** take a hash of your Mercenaries2.exe to determine whether it's usable for the SecuROM Bypass Patcher **and** the Lua-bridge. You can do this with any newer version of 7Zip through the context menu via right-clicking Mercenaries2.exe. <br/>
After getting the SHA256 hash, copy it to your clipboard by double-clicking it to highlight, CTRL + C to copy, CTRL + F on this page to FIND, then paste the hash into the search field using CTRL + V. If your SHA256 hash matches one of these, you may proceed. <ins>**If it doesn't, find a different copy of the game.**</ins>

| Version + Source                   | Size in bytes | Lua-Bridge Compatible? |  SHA256                    |
| ---------------------------------- | ------------- | ------------------------- | ------------------------ |
| 1.0 Origin/EA Play  (Signed EXE)   |  | Not thoroughly tested | a1532b4c7652fe9feee1191f5bd04aa073cd0f036e49831c754e7d895241dfa8 |
| 1.1 Retail + Repack (Unsigned EXE) |  | Confirmed | 7a348847e103d71e8c17e7a51a0f3b4d4422e0c9cb46ec6acc9fe5e4e6be36b5 |
| 1.1 ALL SecuROM Bypassed EXEs      |  | Confirmed | 958eb22776067c2dbb7d684e472c5045d419ec0ecfb49bfea7d23fcf4a83f115 |

## Step 2: Ascend from Darkness
### For the Sake of Neatness
It would be a good idea to create a `scripts`, `plugins`, or `update` folder in your `\Mercenaries 2 World in Flames\` game folder, where the Mercenaries2.exe file is, so as to place any future ASI mods inside to keep the game folder as neat as possible. You should use only one of these unless you know what you're doing. Even I don't know what I'm doing. Trust me, you'd really hate to be looking for an old ASI mod in the root folder because your game keeps crashing. Just make the folder, it makes future modding way easier on yourself. For this guide, I will be using `\Mercenaries 2 Worls in Flames\scripts\`. <br/>

## Step 3: Rain Fire
### Move the Downloaded Files
Place these files into your \Mercenaries 2 World in Flames\ game folder:
- AustinKregel's SecuROM Bypass Patcher
  - Rename `apply_crack-windows-x86_64.exe` to `apply_crack.exe`, this will make patching Mercenaries2.exe easier later.
- AustinKregel's `pmc_bb.dll`
- `lua_repl.py`
- ElishaCloud's DXWrapper (provided by LoganW234)
  - `d3d9.dll`
  - `dxwrapper.dll`
  - `dxwrapper.ini`

Place these files into your \Mercenaries 2 World in Flames\scripts. If you use \plugins or \update, put them there.
- LoganW234's `Mercs2Fix.asi`

## Step 4: Unleash the Horde
### Patch Mercenaries2.exe
Here comes the hard part for some of you. You need to open up CMD; as Administrator is preferred. <br/>
In your file explorer, navigate to your `\Mercenaries 2 World in Flames\` game folder. In the address bar at the top, copy (CTRL + C) the path to your game, shown there. For example, mine looks like this:
`F:\Games\Origin Games\Mercenaries 2 World in Flames`. <br/>
Back to CMD, type `cd ""` (AKA call directory) and then move the cursor with your arrow keys to between the two quotes, then PASTE (CTRL + V) your game folder's path. Without the quotes, CMD will throw an error if you have a space in your game folder's path. Press ENTER to continue. <br/>
CMD will show the path it started with instead. Why is it doing this? Well, if your game is on another drive, you need to call the drive letter. Since my game is on drive `F:`, I can type `f:` and my game folder's path will be called. I don't know why, don't ask, but it works. <br/>
So CMD will now be pointed at your game folder's path. <br/>
What you can do next is type `apply_crack Mercenaries2.exe` and it will start patching your executable. It will create an entirely NEW executable called `Mercenaries2 cracked.exe`. If you open this now, it will start the game with the logging console and load the `Mercs2Fix.asi` mod file. The logging console will show that it has indeed loaded the ASI. But what about the Lua-bridge? To verify that's working, you need to find `Mercs2Game.log` in your game folder. Open that with a text editor, and you'll see that it's listening to 127.0.0.1:27050 which is localhost on port 27050. Mercenaries 2 is now hosting a tiny Lua server on your computer, completely offline I might add, and is listening & waiting for you to send it messages; in this case, something called a "poke" I think. You can read more about that elsewhere if you want, but you want the damn Cheat Menu, right? I know you do, because I do too. <br/>

## Step 5: Skewer the Winged Beast
### Installing and Running Python (a snake, but pretend it has wings)
So now that you're in-game and itching to use the Cheat Menu, let me tell you real quick how to send Lua across the bridge. CMD can't do it alone, it requires some help. <br/>
You should still have CMD open and pointed to your game folder.<br/>
Type `python` and CMD will install python. I haven't figured out where it does this yet, but bear with me. After it finishes, you'll see that it no longer lists your current game folder path. It should look like three arrows pointing to the right, like this `>>>`. CMD is now running python. <br/>
Type `exit()` to return to CMD's normal functions. <br/>
< insert image here

## Step 6: Wield an Iron Fist
### Setting up a Comm Outpost At the Lua Bridge
Now that you can run python in CMD, you need to run `lua_repl.py`. To do this in CMD, make sure that it's pointed to your game folder. Remember when I told you to put that python file in the game folder? This is why. <br/>
Type `python lua_repl.py`. <br/>
CMD will start python with that file loaded. You should see that it's waiting for you to type something. Pay attention to the instructions or else you're going to wonder why it's not doing anything after you start typing. I know I did, when I started doing this. Shut up, don't judge me. <br/>
< insert image here

## Step 7: Raise Hell
## Sending Messages Across the Lua Bridge
Accessing the Cheat Menu is super simple. The game just waits for the input and executes it without a second thought. Isn't that crazy? <br/>
Type `Cheat.DisplayOptions()` and press enter.
Then type `<<<RUN>>>`, press enter, and you'll see a weird but reassuring return-message. <br/>
Go back in-game and you'll see: behind the pause menu is the Cheat Menu. Unpause and you can browse the options while the rest of the game is in slow motion! Be very careful, however. You can mess up your save pretty quick if you hit a mission sequence-breaker accidentally. <br/>
< insert more Lua pokes and images here

## Step 8: Freedom
### Join the Mercenaries-games Modding Discord, `menace.pro`
