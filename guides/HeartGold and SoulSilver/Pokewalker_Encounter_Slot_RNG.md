---
title: 'Pokewalker Encounter Slot RNG Guide'
description: 'A guide explaining the process for manipulating the encounters slots selected by the Pokewalker. '
slug: 'retail-encounter-slot-hgss-pokewalker'
subCategory: 'Pokewalker'
---

```
Note: This guide assumes that you have some knowledge of gen 4 retail RNG already. This is in essence hitting a reseed, but compared to a full on Reseed, this is lenient to hit and easy to verify. 
```

## Required Tools
- A Pokewalker: Pokewalkers need CR 2032 watch batteries, which can be found at most convenience stores. Be sure your Pokewalker is paired with the HGSS cartridge you plan to RNG with.   
- [Eontimer] or [Flowtimer]: Eontimer is recommended if you can use it, though flowtimer would work about as well, if you knew what you were doing with it. I believe there are online versions of eontimer, but those may not be as effective for this RNG. 
[Lappy's Pokewalker RNG Google Sheets Tool](https://docs.google.com/spreadsheets/d/1J0fD1pzn5EW3XjzKpW-ubcZ3nUAI8A6bEzt2n1ZWecU/edit?usp=sharing): Until a proper substitute is developed, a copy of my google sheets will be necessary for Encounter Slot Frames and Species. 
## Optional Items For Convenience 
- A Non-3DS: Even though the year range is irrelevent, Target second is extremely crucial to hitting a reseed, and the 3DS isn't exactly good at doing that on command. 
## Introduction
So, you’re planning to RNG your encounter slots? It’s not nearly as bad as normal walker RNG, don’t worry. As far as RNGing encounter slots go, you only really need to understand how Reseeds work. When the game starts a stroll, it resets the LCRNG, to a number equal to the time on the DS clock at that instant. This new seed is calculated as follows:
```
seed = Hours x 3600 + Minutes x 60 + Seconds
```
In other words, the current DS clock is converted to seconds, and that becomes the new seed. As a result, this 8 digit hexadecimal number can be between 0x00000000 and 0x0001517F. Once the seed is reset in this way, 3 frames are advanced. Frames 1, 2, and 3 are used to generate encounter slots A, B, and C, in that order. 
Each enconter slot (A, B, and C) can be one of two pokemon, so you always have a 50% chance of getting the Pokemon you like. 
These may seem like odds not worth RNGing, but Inferno has a 50% chance to land, and some pokemon may be difficult to encounter, even if they are present. Let's say I want to RNG a Flying Pikachu from Yellow Forest. Flying Pikachu is a 2% chance, which may require 1000+ Watts on average (You would only be able to KNOW you hit slot A if you had !!! Pop up on the walker, and flying pikacu can appear with only a !!), potentially more if you're unlucky.
Moreover, you need to walk 10,000 steps to have a chance of laying eyes on a Flying Pikachu, and even if you do, it looks just like Surfing Pikachu until you transfer it to the main games. How confident are you in hitting Zap Cannon now? Wouldn't it be nice to know you have a Flying Pikachu on your course, by spending only 10 watts?  

## Part 1: Reseed to Encounter Slots Calculator
My google sheets tool has a calculator to see the encounter slots created for each second of a seed, for any possible Pokewalker course. Navigate to **Other Tools**, and scroll down and right until you find the **Reseed to Encounter Slots Calculator**. It should look something like this. 

![image](https://user-images.githubusercontent.com/86489014/134790801-ca278dc9-c011-4b05-9d45-d6b902590b3b.png)

Let's say I want to RNG a Munchlax from Winner's Path. In the top left is a place for a reseed, and your Pokewalker Course. Make sure you spell your Pokewalker course exactly as it is spelled in Serebii. I put in a random number, 0x000C5, which is approximately 3 minutes of waiting, though realistically any value would work, if you set your DS time properly. 
You might have a seed in mind if you happened to be doing a Reseed RNG, but the number truly does not matter. As long as it is less than 0x1517F. On the middle right are the 3 pokemon I would find if I used this reseed. Munchlax, Duskull, and Magikarp. 
It is important to note that I have not tested every course myself, though I have RNGed on a good 50% of these courses. I used a source that was said to contain each species in the correct order, though I found it to be wrong in the past, so if there IS an error, I would like to know.
Anyway below that show the encounter slots for being seconds early or late. The tool can only display 11 frames in total, but for the most part, every other nearby frame also has munchlax, duskull, and magikarp. 
In other words, unless I am less than 5 seconds early or late, a magikarp verifies a Munchlax existing, and if all you care about is getting the species, this works! In the center of the tool is **Reseed Time**, which is the DS clock time I would need to have when I press A on the course confirmation screen. 
The Reseed and encounter slot generation occurs ~3 seconds after you confirm the course selection, so by confirming on 00:03:14, I am really aiming for 00:03:17. 
Once you find the reseed you want, you need to set up Eontimer. 
## Part 2: Eontimer Setup & Hitting the Seed
00:03:00 isn’t the time you need to manually set your DS to, as you’ll probably want to give yourself 2-3 minutes to boot up the game and reach this menu. I will need to set the DS clock 2-3 minutes early (00:01:00), start the game immediately, and reach this menu, then press A at 00:03:14.

![image](https://user-images.githubusercontent.com/86489014/134791451-780f44e5-89d4-419a-8d3b-f020ed6a1f06.png)

Open up eontimer, and click the "C" tab on the far right. We won’t be using the gen 4 tab for this RNG, but rather the custom timer on the far right tab. 
In this example, I want to give myself 2 minutes and 14 seconds to reach the menu, since I doubt I can navigate the menus much faster than that. 
Eontimer does not count in minutes, nor seconds, but milliseconds, so we need to convert 2:14 into a number it can understand. 
```
2*60 +14 = 134 seconds, 
134 * 1000 = 134000 milliseconds.
```
Plopping that into Eontimer, it would look like this

![image](https://user-images.githubusercontent.com/86489014/134791533-2631901c-0816-403d-b858-c7dea1bf7ea3.png)

Now, all I need to do is set the game’s timer to 00:01 with any day, month, and year, and I can hopefully hit either the right reseed, or one of the identical copies 2 seconds early and late of it. There’s no reason to wait at the main menu, once you hit the timer you want to get in position as quickly as you can. Once you confirm your course selection on the 6th beep, connect your DS to the Pokewalker and send your pokemon into it. From there, check what Encounter Slot C is, by gaining 10 watts and spending them to catch a pokemon. 
## Part 3: Troubleshooting
Looking back at the Encounter Slot Calculator, it seems like every other slot within 5 seconds of my target has Munchlax, Duskull, Magikarp. 

![image](https://user-images.githubusercontent.com/86489014/134791650-63706131-4cae-48c9-8802-a251958bb9ca.png)

If my slot C pokemon was Bronzor, I hit the wrong second, and need to add or subtract 1000 milliseconds in eontimer and try again. If you happened to be 10+ seconds early or late due to a math mistake, slots C and B could be correct while A is wrong, but if you’re feeling paranoid about it, you can always check Slot A before the RNG starts, if you have the option. That’s it, happy hunting!
