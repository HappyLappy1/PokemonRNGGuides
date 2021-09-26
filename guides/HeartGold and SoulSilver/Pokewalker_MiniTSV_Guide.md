---
title: 'Pokewalker Mini-TSV Finding Guide'
description: 'A guide that describes the process for finding the Mini TSV of a save file, a value which can be used in place of SID, for pokewalker RNGs. Part 7 of the original guide.'
slug: 'retail-minitsv-hgss-pokewalker'
subCategory: 'Retail'
---
```
Note: This guide uses aprijuice tech, so no RNG experience will be necessary, but you will need to be patient enough to walk or bike ~150,000+ steps in HGSS, which will be taxing. 
```
## Required Tools
- A Pokewalker Pokemon: You do NOT need a Pokewalker to complete this guide, only a Pokemon that came from a Pokewalker (Met Location must be Pokewalker). This pokemon will only be able to tell you the Mini TSV of the save file it came from, but if you lost your Pokewalker a decade ago, but still have a Sentret, you can do this. 
- [Lappy's Pokewalker RNG Google Sheets Tool](https://docs.google.com/spreadsheets/d/1J0fD1pzn5EW3XjzKpW-ubcZ3nUAI8A6bEzt2n1ZWecU/edit?usp=sharing): Until a proper substitute is developed, a copy of my google sheets will be necessary for Mini TSV calculation. 
- A Copy of HGSS: You need HGSS to Blend Aprijuice, DPPt do not have apricorns in them. 
- Apricorns, and the Aprijuice Blender: You will need a healthy amount of apricorns to make aprijuice, but you also need the blender itself. The Aprijuice Blender can be obtained from the Aprijuice Saleswoman to the left of the Pokeathlon Dome, and will be crucial to making juice.  
## Optional Items
-[Psypokes Pokeathlon Stats](http://www.psypokes.com/hgss/pokeathlon_stats.php):
-[Psypokes Apricorn Locations](http://www.psypokes.com/hgss/apricorns.php):
-A Pokewalker:
## Introduction
So, you want to RNG a PID dependent trait like ability or wurmple evolution? You’re going to need your Mini-TSV, which can be done with apricorns, walking, and almost any pokewalker pokemon. Before I explain the process of how to do this, I should probably define “Mini TSV’, since it’s a new term that I literally made up. First though, I’m going to need to start by explaining how shiny pokemon work. Shiny pokemon generate when the Pokemon Shiny Value (PSV) of pokemon’s PID is equivalent to a trainer’s Trainer Shiny Value (TSV). TSV can be represented by the following equation.
```
TSV = (TID ^SID) >> 3
```
Now ^ isn’t exactly important here, bitxor is pretty much a different form of subtraction, but the >> in this equation represents “bitrshift”, in which the bits of the number, or the digits of the number in binary, are shifted to the right by the following number. 
As a result, the last 3 bits are lost in the process. In other words, no matter what those 3 bits were, the TSV will be the same, meaning essentially that there are 8 SID values that, when combined with your TID, will yield the same TSV. The pokewalker uses a similar calculation with the TID and SID to prevent the PSV from matching the TSV, though the bitrshift is by 8 bits instead of by 3, then is bitxor-ed with 255. 
This value, which I dub the “Mini TSV”, will then be shifted 24 bits to the left to create PID1, the basis of all pokewalker PIDs. So by finding the PID of the pokemon you catch in the pokewalker, you can reverse engineer your “Mini TSV”, and even get a good guess as to where your SID is, though you won’t be able to determine the last 8 bits with a Mini TSV alone. The current method for this process requires 2-5 specific aprijuice recipes, depending on your species, nature, and hidden PID digits. 
You will need roughly 20-50 total apricorns for this process. The sheet will attempt to minimize the number of apricorns you end up needing, but should you run out of an apricorn type you need, the Psypokes Apricorn Locations link under **Optional Items** can be used to find out which trees you can obtain more at. 
After collecting an apricorn type at all available trees, you can boot up the game at 23:59, then let the clock roll over to regenerate apricorn trees. With that out of the way, the first thing you need to start this process is almost any pokewalker pokemon. 
This choice of pokemon is extremely important, as some pokemon have pokeathlon stats that make finding digits of their PID impossible. You can find the full Pokeathlon Stats of a pokemon using the Psypokes Apricorn Locations link (also under **Optional Items**) Below are the stats for Kangaskhan.

![image](https://user-images.githubusercontent.com/86489014/134789713-888dc6a3-3fcf-4bb8-9766-88692c014418.png)

Kangaskhan would be a poor choice for this process because of its Jump Stat. It has a Min Jump of 2, a Base Jump of 2, and a Max Jump of 2. Because it cannot be raised nor lowered, no information about it’s PID can be extracted from it, making it a terrible choice for Mini TSV Calculation. Now let’s take a look at Duskull’s Pokeathlon Stats.

![image](https://user-images.githubusercontent.com/86489014/134789722-1d99f426-02ae-43b5-b520-d2d59731c29b.png)

As you can see, Duskull starts with 4 Speed, and cannot have more than 4 Speed. It can have less than 4 Speed though, so the speed PID digit can be found, though it will require more apricorns and aprijuice to do so. I will be using duskull for this example for demonstrational purposes, as some segments of this guide are only applicable to rare circumstances, but this duskull is likely to check every box. 
You should consider using a pokemon like Sentret instead, which is much less likely to run into the issues Duskull will have, as there are some recipes I haven’t created yet, that only Duskull might need. These are Sentret’s Pokeathlon Stats.

![image](https://user-images.githubusercontent.com/86489014/134789729-4f5597de-0152-407b-91d6-cbd03974ed0c.png)

As you can see, there is an upper and lower range for all 5 pokeathlon stats. This allows for cheaper recipes, and less aprijuices, to get the data needed to find PID. Anyway, once you have selected your pokemon and caught it from the Pokewalker, open up my google sheets tool, and navigate to **Aprijuice Species Data**. 
You will need to input the Min, Base, and Max Pokeathlon stats of your pokemon, as well as its gender ratio, unless it is already there in the sheet.

![image](https://user-images.githubusercontent.com/86489014/134789749-339e7a9e-8fd9-4b5f-b313-4fbaf2ed1227.png)

This should be done in the format “Min|Base|Max”, and the gender ratio should be in the chance of being Male. The regions at the top link to the psypoke page for that region. With that out of the way, it’s time to start this process.

## Part 1: No Juice
First, navigate to the **Aprijuice Mini-TSV** sheet, and scroll to the far left. Make sure you keep track of which table you are at. While they may look similar, the top left corner of each table displays which segment of the guide it relates to, and is color coded.
On the far left, beneath **No Juice**, input the nature, gender, and species of the Pokemon you caught. It should look something like this.

![image](https://user-images.githubusercontent.com/86489014/134789824-a792a7ab-b445-4fae-9d23-b4c18de52d50.png)

My pokemon is a Male Duskull, with a Lonely Nature. Now that the sheet knows this, we can start plugging in star values. Pokeathlon stats fluctuate based on the day of the month. While these fluctuations are not strong enough to change star values on their own, they can make the difference between 2 or 3 stars when factors such as nature and aprijuice are applied. 
So the next step will be to set your DS clock to January 1st of any year (or February, March, April, etc. The month does not matter), and booting up the game.

![image](https://user-images.githubusercontent.com/86489014/134789838-6e6f1328-816f-4da7-b2b7-11b0cc66a925.png)

View the summary of your caught pokemon, and input the number of Power, Stamina, Skill, Jump, and Speed stars for your pokemon in the sheet. Do note, the order of these stats is not consistent with their order in the game: Speed, Power, Skill, Stamina, Jump. Once you have correctly input these stats, power off your game, and change the date to January 2nd, and input the stats for day 2. Continue this process all the way to January 10th. 
Odds are, you’re seeing some numbers highlighted in green, which are fluctuations in star counts. If this is the case, you should read this for info on how to blend aprijuice, but you don’t need to make any juice until **Juice A**. However, if you chose a pokemon like duskull and/or got unlucky with nature, you might see something like this instead.

![image](https://user-images.githubusercontent.com/86489014/134789864-c9255151-fd9a-4400-b09e-a40ccdeaa127.png)

Unfortunately, because Lonely lowers power by 2 stars (below duskull’s minimum) and raises Stamina by 2 (above Duskull’s maximum), the fluctuations are not displayed in game. Sentret is less likely to have this issue, though it is technically possible for any pokemon without a neutral nature. 
When this occurs, an aprijuice needs to raise/lower the affected stats back above the minimum, or below the maximum, so fluctuations can be seen. Once you input all 10 days, an optimal recipe will be selected which will make these fluctuations visible.

![image](https://user-images.githubusercontent.com/86489014/134789878-5158b88d-07f7-4e07-8c3c-09be3ba30010.png)

The recipe displays the number of apricorns required, the order they need to be put into the blender, and their “Mildness”. If you do not have enough apricorns to complete the recipe, do not start until you have gathered the ones you are missing. This recipe requires 1 White, 1 Black, 4 Yellow, and 6 Pink Apricorns. 
The **Apricorn Sequence Required** displays the order that these apricorns need to be added, which is important to getting the right stats. The “|” throughout the sequence represents where the blender will require the player to walk 100 steps before adding more apricorns. It does this each time you add 5 apricorns, so make sure you keep track of how far you’ve gotten. If you are curious, the index of the recipe you are using is displayed to the right of the sequence, allowing you to view it in **Aprijuice Recipes**. 
“Mildness” is increased by 1 for every 100 steps the player walks, and only affects the juice in increments of 25. The game will explicitly tell you how mild your juice is whenever you scroll over the apriblender itself. Under certain circumstances, Mildness does not matter for a recipe, and obviously it would be a waste of time to walk all those steps if it isn’t necessary. When Mildness is highlighted in green, you need it, and when it is highlighted in red, feel free to ignore it.
According to the sheet, I need a **Mildness** of 100-124 for this recipe, meaning I need to walk ~100,000 steps to blend your juice, after putting all the apricorns in. You may need to walk more for other recipes. While this is a lot of steps, there are a few good ways of tackling it. Cycling road is nice and long, if you don’t mind holding up periodically.
However, there is a way to walk infinitely in HGSS. By entering the Ecruteak Gym and holding the up arrow (or using a coin of some sort for a 3ds) you can fall into the void infinitely, respawn, and walk back up endlessly. This is slower than just riding your bike, but it is infinite. Just make sure you don’t walk for too long, this will ruin your juice. You can check it at any time by opening your apricorn box and scrolling over the juice.
## Part 2: Juice A
Once you’ve finished biking a marathon of your own to get the right mildness, feed it to your pokemon, and save the game. On your sheet, scroll over to the next table, which should be labeled **Juice A**. If you didn’t need to make aprijuice yet, simply copy over the stats from **No Juice**, but if you had to blend an aprijuice, you’ll have to input the stats for days 1-10 again, this time with the aprijuice modifier. These are my duskull’s stars.

![image](https://user-images.githubusercontent.com/86489014/134789941-8c34b751-ef58-4108-bed9-e19357ae9d8c.png)

Now you should have two digits displaying, but if you don’t by this point, it means you either made a mistake inputting Stars, or you have a rare case where your Juice A doesn’t have a recipe yet. Either way, you’ll need to start over, likely with a different pokemon. Anyway, assuming you get here, you should have two PID digits already.

![image](https://user-images.githubusercontent.com/86489014/134789949-6de142b1-c861-41e2-9f4d-52192a75749b.png)

You may have 3 digits known at this point, as power can be found using stamina and nature. Anyway, your next step is to blend the aprijuice displayed for Juice A. Like before, you need to ensure that you have enough apricorns before you begin, follow the sequence exactly, and reach the correct mildness if the cell is green. In this case, I need 1 white, 1 yellow, and 4 blue, as well as 150k steps. Before you start blending, make sure you get rid of your last blend by feeding what’s left of it to other pokemon.
A pokemon can only be influenced by 1 juice at a time, but the new and old juices will combine in the blender if you aren’t careful. This may be the last (and only) apriblend, if you got an easy PID. Add the apricorns in the correct order, bike the needed steps, feed the juice to your pokemon, save, then move on to **Juice B** in the sheet.
## Part 3: Juice B
Scroll over to **Juice B** on the sheet. You are very likely to see a variation in at least one of the unknown stats, but I chose this duskull because it checks every box. I got no reaction, as you can see below. 

![image](https://user-images.githubusercontent.com/86489014/134789972-a2045571-88f5-4a0b-b4fd-4070738b143f.png)

You may be wondering what that “7 to 9” is about on the top left. Essentially, the hidden stat value for each stat fluctuates between -9 and 9, and this juice will cause a star increase on “7 to 9” for stats that increase, and will cause a star decrease on “-7 to -9” on the stat that decreases. A “5-9” would be optimal in distinguishing PID digits from each-other, but that type of juice is either extremely expensive, or outright impossible. 
Both “7 to 9” and “3 to 9” juices can potentially create “lookalike digits”, which have identical star patterns to each other, despite being different values. This happened to my Duskull, as an unchanging star value for an increased stat is indicative of either 1 or 6, as shown below.

![image](https://user-images.githubusercontent.com/86489014/134789980-498167c6-fb94-4191-8f90-fab71300be44.png)

At this point, you may have 3 “Half Known” digits, or know all 5 digits already. If all 5 digits are known, you don’t need to do any more work. Scroll ahead to **Part 6: Juice E** in the guide, you already found your Mini-TSV. That said, if you have a half known digit, or worse a “?” like I do, you will need to complete the next recipe, just like you did before. 
So, collect missing Apricorns, empty the old juice, follow the prescribed order, then take enough steps for the correct mildness, if necessary. Once you do, feed it to your pokemon, save your game, and scroll over to **Juice C** in the sheet.
## Part 4: Juice C
Like before, copy in the star counts in for days 1-10 with the new juice. You should see at least one star count fluctuate this time, if you did everything correctly.

![image](https://user-images.githubusercontent.com/86489014/134790011-06e409cc-2481-4bbc-8422-fbb3a924531c.png)

At this point, you are highly likely to find all 5 digits, because there is no overlap between lookalike digits for 3-9 and 7-9. If you have, skip to **Part 6: Juice E** to claim your Mini TSV. However, if you had a ? as one of your digits, like I did for this extremely improbable duskull, you will need to make more juice.

![image](https://user-images.githubusercontent.com/86489014/134790019-f9854b05-6a2e-4f89-b29b-6b55aa89921c.png)

Once again, go through the motions of collecting the necessary apricorns, emptying out residual juice, blending your concoction, and walking the necessary steps, if mildness is highlighted in green. Unfortunately, my duskull needs the minimum speed from this juice, but you are much more likely to not need mildness on this blend, if you need it at all. Once you have the proper mildness, feed the completed juice to your pokemon, and save the game, and scroll over to **Juice D** in the spreadsheet.
## Part 5: Juice D
Once again, input your pokemon’s performance stats for days 1-10 of the month into the sheet. You are highly likely to see a variation in your missing stat, however...

![image](https://user-images.githubusercontent.com/86489014/134790025-39307d0e-820c-4d82-a1c3-57e5fb2b2b6b.png)

Because this is another 7 to 9 juice, there is a chance for lookalike digits, and this duskull has one of them. My Speed digit is either a 2 or a 7, as shown below.

![image](https://user-images.githubusercontent.com/86489014/134790036-698fb670-6255-4fb3-b6e9-1bdd1d2496e2.png)

If you happened to get all 5 digits, you don’t need to blend anything else. Head over to **Part 6: Juice E** to find your Mini-TSV. However, because I still have a half-known digit, I have one more recipe to do. For the final time, empty your residual aprijuice, collect any missing apricorns, complete the recipe in the order given, and if it’s green, walk enough steps for the desired mildness. Once you do, give the juice to your pokemon, save the game, and scroll over to **Juice E** in the sheet.
## Part 6: Juice E
If you just saved after brewing Juice E, input stats for days 1-10, just as you did for all other juices so far. 

![image](https://user-images.githubusercontent.com/86489014/134790049-b8b7eb4a-71dd-47ba-850d-81acfb38b6db.png)

Feel free to leave this blank if you have all 5 digits already. Anyway, by this point, you should have all 5 digits. If not, you made a mistake somewhere along the line. After that final juice, I have 5 known digits of my Duskull’s PID, shown below.

![image](https://user-images.githubusercontent.com/86489014/134790054-45962756-7624-4245-95f4-8fd91d577b74.png)

Your Mini-TSV is highlighted in green, and in this case mine is 120, but if you plan to find your SID at some point, I have good news for you. You can narrow it down to 1 of 256 values by inputting your TID in the blue box.

![image](https://user-images.githubusercontent.com/86489014/134790062-0d34fed7-46e0-423d-805f-41ae964f3c50.png)

My SID for this save file is somewhere between 56320 and 56575. This may not help you much if you use traditional means to find your SID, but with the proper knowledge, you could have your SID in 32 RNGs, now that you know this. Anyway, you can use your Mini TSV in **IRNG Searcher** (click the checkbox at **I7**, input the value at **J7**), and **Other tools** (click the checkbox at **F7**, input the value at **G7**), shown below.

![image](https://user-images.githubusercontent.com/86489014/134790073-dc649dc1-51ef-4284-9ca5-1c202b8ff805.png)
![image](https://user-images.githubusercontent.com/86489014/134790081-5d07a4c1-af34-4c51-92ca-db8d2f059c0e.png)
