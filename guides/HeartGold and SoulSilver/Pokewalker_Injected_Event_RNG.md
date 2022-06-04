---
title: 'Injected Event & Method C Pokewalker RNG Guide'
description: 'A guide explaining the process for RNGing event pokemon injected with external tools, and the use of injected pokemon Method C RNG. Essentially Part 9 of the original guide. Spinda will be covered separately.'
slug: 'Injected-Event-Method-C-hgss-pokewalker'
subCategory: 'Pokewalker'
---

```
Note: This guide assumes you have moderate knowledge of Pokewalker RNG, and are able to aim for and hit a given IV frame, properly aim for a PID frame. A Palm AND a CFW 3DS will be necessary for this RNG, ensure you have both available for use during the RNG. 
```
## Required Tools
- A Pokewalker: Pokewalkers need CR 2032 watch batteries, which can be found at most convenience stores. Be sure your Pokewalker is paired with the HGSS cartridge you plan to RNG with.  
- [RNG Reporter](https://github.com/Admiral-Fish/RNGReporter/releases/tag/v10.3.4): RNG Reporter will be necessary to find wondercard IV frames, and extract egg PIDs. I will eventually rewrite this guide to work with Lincoln's toolbox when reseeds are added, but until then, RNG Reporter is more efficient.  
- Notepad, or some other .txt opener: You'll need to copy and paste very large lists of PIDs and extraneous information, though in this guide I use Notepad.  
- [Eontimer](https://github.com/dylmeadows/EonTimer/releases) or [Flowtimer](https://github.com/stringflow/FlowTimer-Java/releases): Eontimer is recommended if you can use it, though flowtimer would work about as well, if you knew what you were doing with it. I believe there are online versions of eontimer, but those may not be as effective for this RNG. 
- A Palm m500, updated to Palm OS 4.1: You need a Palm running Palm OS 4.1 to run WalkePoker. People have had success with m515s as well, but I can confirm an m500 works for injection.
- [WalkePoker](https://dmitry.gr/?r=05.Projects&proj=28.%20pokewalker): As of now, a CFW 3DS cannot inject an event pokemon. You will need a Palm to inject an event pokemon. 
- [Lappy's Pokewalker RNG Google Sheets Tool](https://docs.google.com/spreadsheets/d/1J0fD1pzn5EW3XjzKpW-ubcZ3nUAI8A6bEzt2n1ZWecU/edit?usp=sharing): Until a proper substitute is developed, a copy of my google sheets will be necessary for IRNG optimization. 

## Optional Items For Convenience 
- A 3DS with CFW: You will need a 3DS with CFW to view the pokemon you injected with the ROM, if you want to aim for a specific nature. Dmitry's code sets TID and SID randomly, and the shiny PID generation prioritizes shininess over nature, so to predict nature you need a ROM dumper. 
- [TWiLightMenu](https://github.com/DS-Homebrew/TWiLightMenu/releases): That said, the 3DS cannot currently use it's own infrared to connect to the pokewalker. it instead must use the IR from a HG or SS cart, which TwilightMenu can do.
- [3DS Pokewaker Rom Dumper](https://pcy.be/tmp/miscbin/auxspi-ir.nds): This nds file can be used with Twilight to dump the pokewalker's "eeprom". This ROM contains the TID and SID of any event pokemon stored on the walker, but will also wipe all watts and caught pokemon from the game.
- A Non-3DS: The 3DS cannot reach years 2051-2099, and year is essential to Pokewalker RNG. You will be more limited on spreads using a 3DS than anything else. Also, target second is extremely crucial to hitting the initial seed, and the 3DS isn't exactly good at doing that on command. 
- [Checkpoint](https://github.com/FlagBrew/Checkpoint/releases): Useful to avoid releasing large amounts of pokemon, but otherwise not a super important part of the RNG. 
- [Licoln's eeprom reader]: A more efficient substitute to porocyon's rom dumper, however it's still a WIP right now. 

### Introduction
Before you get too far into this part of the guide, know that by “Event” pokemon, I am not referring to Self Destruct Munchlax or Flying Pikachu, but rather unreleased, unused, and fully customizable event pokemon sent directly to the pokewalker by an external third party device. One could theoretically generate a legal event pokemon that have legal PIDs, met locations, TIDs, SIDs, moves, levels, abilities, etc. However, these pokemon would not be generated in a nintendo approved manner, and would be considered hacking by some, and illegitimate by many. 
Method C was developed for the explicit RNG abuse of these event pokemon, and requires the use of at least 1 event pokemon for advancing frames. If you do not have a Pam m500 series device, you cannot use Method C, as the only person who has created a program for fabricating event pokemon did so for the Palm, of all things. Anyway, Method C is very similar to Method B, though instead of 4 pokemon per connection, 5 are used. 
This can be done by sending in an event pokemon on every single connection, which consumes a total of 237 IRNG frames, and 10 IV frames. This lowers the minimum IRNG frame significantly, for those able and willing to use Method C. However, there are a few downsides to Method C. 
First and foremost, it’s not well tested or documented. As far as I am aware, I am the only one to complete a Method C RNG, and I have only done so 2-3 times. 
Secondly, it mandates the use of a third party tool that not everyone has lying around, to create hacked pokemon for the RNG. This tool is helpful, though it was not designed for RNG, and I have a few gripes with it that I will elaborate on when I describe the PID creation process for event pokemon. 
Third, this is a method for Event pokemon, not any old pidgey or rattata. There are choices I have made in designing my spreadsheet, such as with partial connections, that  inconvenience those NOT RNGing an event pokemon. I will do my best to point those out when we get to them, but unless you know what you're doing, use Method C for events only. 
Method C was named third on the list because it is inconvenient to accomplish, even if it is faster. Are you still down to do Method C? Make sure you’ve read through my Initial Seed and Reseed Guide, I will only cover aspects that deviate from these guides. 
### Part 0: Species Selection
The first major difference is here in Part 0. If you’re RNGing an event pokemon, it can be whatever you like, any species, any gender, any moveset, any level, and any ability. You can even make it shiny if you like, though there is a price for shininess. 
To understand this price, we need to take a deep dive into how Pokewalker PID generation works… and doesn’t work. Feel free to skim or skip ahead if you’ve already decided on a non-shiny. 
For all pokewalker pokemon, there is a base PID 1 determined by the TID and SID. Unlike normal Pokewalker pokemon, event pokemon have pre-determined TIDs and SIDs, which are randomized by the Palm in a currently unknown way. 
For non-shiny pokemon, PID 1 is determined in the same way as normal, in this format.
```
0xXX000000, 0xXX = ((TID ^ SID) >> 8) ^ 255)
```
However, shiny pokemon work differently, with this PID1 format instead. 
```
0xYYYY0000, 0xYYYY = (TID ^ SID)
```
This means that there are a total of 65355 unique Shiny PID 1’s, as opposed to the 255 unique non-shiny PID 1’s. From there, non-shiny pokemon will have a nature adjustment value calculated to convert PID 1 to match the nature selected by PID 0 (PID 0 = current IRNG state). 
Shiny pokemon don’t use a nature adjustment value at all, and will instead simply add PID 0’s nature to itself, which will shift the nature by (pid1 % 25), which already puts nature out of our control, since we cannot reliably predict PID 1. 
From here, shiny and non-shiny PIDs will be altered to suit the target gender if necessary. It is interesting to note that only male shinies will be adjusted in this way, as all shiny PIDs will be female at this point. Gender adjustment is generally dependent on PID 1, except for shinies. 

| % Target + Gender     | 0.75 F | 0.50 F | 0.25 F | 0.125 F | Other | 0.25 M | 0.50 M | 0.75 M | 0.875 M |
|-----------------------|:------:|:------:|:------:|:-------:|:-----:|:------:|:------:|:------:|:-------:|
| Shiny (Even or Odd)   |   N/A  | N/A    | N/A    |   N/A   |   0   |  +200  |  +150  |   +75  |   +50   |
| Non-Shiny (Even)      |  -100  |  -150  |  -200  |   -250  |   0   |  +200  |  +150  |  +100  |   +50   |
| Non-Shiny Event (Odd) |   -75  |  -125  |  -175  |   -225  |   0   |  +175  |  +125  |   +75  |   +25   |
| Non-Shiny (Odd 2)     |  -125  |  -175  |  -225  |   N/A   |  N/A  |  +225  |  +175  |  +125  |   +75   |

For all nonshiny Pokewalker mons, If (pid1 % 25) is even, "even" is used, but if (pid1 % 25) is odd, "odd" is used first, then if the gender isn't flipped, "Odd 2" is applied instead. Shinies will always use static values however, at least in my testing. 
Do note, if an even TID/SID is selected, and you aim for a nonshiny female 1:7 female pokemon like Combee, there is a chance for Combee to end up male, and with the right IDs, shiny. This may be covered in it's own guide, but before that happens a non-random pokemon injector needs to be developed. 
Anyway, after this, non-shiny PIDs are finished, and are assigned to their pokemon, with the nature selected by PID 0. However, the nature and gender adjustments affected shininess, so shiny event pokemon undergo another process to “reshinify” them. 
This process is done by finding the difference between two values. These values are the PSV and TSV without their respective bitshifts, mathematically represented below.
```
PSV'(PID) = ((PID >> 16) ^ (PID & 0xFFFF)),  TSV' = (TID ^ SID)
```
The difference between “PSV” and “TSV”  is then added to the upper half of the PID, making the pokemon shiny without changing gender. However, nature is changed in the reshinification process, in a way not predictable without knowing TID and SID beforehand. 
Because the TID and SID are randomized by the Palm, it is difficult to RNG shiny Pokemon for nature or non-shiny events for PID, though getting quirky natured shinies is more than possible with a Palm and a CFWed 3DS. If you only care about IVs though, you can work with only a palm. 
Knowing that, now is the time to decide if you want to RNG a shiny, or a nonshiny. Once you make that decion, it's target IV time!

### Part 1: Target IV Frame
The process for doing IV frame finding is nearly identical to normal, and can contain a reseed, if you prefer an even IV frame. For the sake of this example, I will be aiming for this frame, which requires a reseed and a near-empty PC.

![image](https://user-images.githubusercontent.com/86489014/134826022-9a2e17e2-ab6f-4573-8df2-2a56681851ed.png)

Yes, frame 982 is stupid high, but I have a few good reasons for choosing it, besides the fact that this staryu’s IVs will be perfect multiples of 5, the number of pokemon per connect. I actually completed this RNG recently using spindas (I used a normal Staryu with Method C and spinda verification)

![image](https://user-images.githubusercontent.com/86489014/134826363-1a12e07d-faf2-4626-ac26-60990ebf46e8.png) ![image](https://user-images.githubusercontent.com/86489014/134826383-9c114d5d-47fe-4acf-b389-d6c6993a052e.png)

Anyway, once you select your IV frame, open up your spreadsheet and paste in your frame count like so.

![image](https://user-images.githubusercontent.com/86489014/134826443-888784cc-b0f7-43a8-a3af-91ee68889dfa.png)

As you can see, **IRNG Min C** is not displaying. I did this to prevent people from choosing **Method C** without knowing what it entails, but it will be disabled by manually selecting Method “C” in **Method Override**.

![image](https://user-images.githubusercontent.com/86489014/134826543-362880e4-5bd1-499d-b744-f37f9244c831.png)

Directly next to **Method Override** is **Shiny Event**, which will convert the PIDs displayed into the PIDs of shiny event pokemon, if we knew what TID and SID the shiny would have. We don't get that information until after the pokemon is injected though,

- How to account for retroactive TID/SID? Method B + Knowing it in advance (boring), Method C + Doing the blank connects after you have the event in hand (Risky) Is Method C really the best?

