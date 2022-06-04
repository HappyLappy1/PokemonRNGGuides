---
title: 'Retail Pokewalker Reseed RNG Guide'
description: 'A guide explaining the process of using Reseeds for Pokewalker RNG, and how the process is different from Initial seeding. Essentially Parts 0-6 of the original guide with only reseed info.'
slug: 'retail-reseed-hgss-pokewalker'
subCategory: 'Pokewalker'
---

```
Note: This guide assumes that you have some knowledge of gen 4 Pokewalker RNG already. It is highly recommended that you have completed a Pokewalker Initial Seed RNG, as a Reseed RNG is essentially a more complex variant of that.
```
## Required Tools
- A Pokewalker: Pokewalkers need CR 2032 watch batteries, which can be found at most convenience stores. Be sure your Pokewalker is paired with the HGSS cartridge you plan to RNG with.  
- RNG Reporter: RNG Reporter will be necessary to find wondercard IV frames, and extract egg PIDs. I will eventually rewrite this guide to work with Lincoln's toolbox when reseeds are added, but until then, RNG Reporter is more efficient.  
- Notepad, or some other .txt opener: You'll need to copy and paste very large lists of PIDs and extraneous information, though in this guide I use Notepad.  
- [Eontimer] or [Flowtimer]: Eontimer is recommended if you can use it, though flowtimer would work about as well, if you knew what you were doing with it. I believe there are online versions of eontimer, but those may not be as effective for this RNG.
## Optional Items For Convenience
- [Lappy's Pokewalker RNG Google Sheets Tool](https://docs.google.com/spreadsheets/d/1J0fD1pzn5EW3XjzKpW-ubcZ3nUAI8A6bEzt2n1ZWecU/edit?usp=sharing): Until a proper substitute is developed, a copy of my google sheets will be necessary for IRNG optimization. 
- A Non-3DS: The 3DS cannot reach years 2051-2099, and year is essential to Pokewalker RNG. You will be more limited on spreads using a 3DS than anything else. Also, target second is extremely crucial to hitting the initial seed, and the 3DS isn't exactly good at doing that on command. 
- A 3DS with CFW: The 3DS can be useful for other purposes, if it has CFW. People have and are continuing to create programs that can allow the 3DS to interact with and manipulate the pokewalker. It is still a work-in-progress, but watt injection can be done through the 3DS, with some minor hiccups.
- Twilight++: That said, the 3DS cannot currently use it's own infrared to connect to the pokewalker. it instead must use the IR from a HG or SS cart, which Twilight++ can do. 
- Checkpoint: Useful to avoid releasing large amounts of pokemon, but otherwise not a super important part of the RNG. 
- A Palm m500, updated to Palm OS 4.1: This may seem like a weird one, and believe me it is, but until code for 3DS CFW is free from certain "side effects", the Palm is the safest way to inject watts, steps, items, and event pokemon.
- [WalkePoker](https://dmitry.gr/?r=05.Projects&proj=28.%20pokewalker), by dmitrygr: Dmitry's Palm OS app is capable of injecting watts, steps, items, and custom event pokemon, which can be RNGed. The ROM dump doesn't seem to work, I'd advise against using it. If nothing else, this will save you time grinding watts, if you're willing to invest in this RNG. 
### Introduction and Disclaimer
So, you have a taste for Pokewalker RNG now, do you? Well, that or you skipped over the main guide, and really need to do reseed RNG.
If that's you, you should read the initial seed guide first, and do a test run on that, because I will only be describing the differences and additional steps for reseeds.
Parts identical to initial seed RNG will be glossed over or omitted. I will give brief reminders as to what needs to be done for each segment, but they will be brief. With that out of the way, it's reseed time!

### Part 1: Target IV Frame
Do not encounter your target Pokemon yet, as you may have the opportunity to verify your reseed if you don’t. Unlike on an initial seed, reseeds have some elements of verification to them. This will be explained later in the chapter, first though some details about reseeding. This Reseed Mechanism was documented on a japanese blog by user [bowline_lab](https://bowline-lab.hatenadiary.org/entry/2020/09/06/162015#LCG%E3%81%AE%E6%B6%88%E8%B2%BB). 
This method is mostly theirs, though they didn’t have access to RNG Reporter, and did their calculations using a different, self-made [tool](http://2style.jp/bowline/ds/tool/random/walker.html). Anyway, the reseed is almost entirely independent of the initial seed, meaning all of the limitations on initial seed do not apply to the reseed. That said, there are some limitations unique to the reseed, which is determined by the in-game clock at the time. The formula for this is as follows:
```
seed = Hours x 3600 + Minutes x 60 + Seconds
```
This formula essentially converts the DS time into seconds, and uses that as the initial seed, meaning the reseed range is between 0x00000000 and 0x0001517F.  Anyway, Pokewalker IVs are still generated via “Wondercard IVs” in RNG Reporter (Or Pokefinder, though at the time of writing this RNG Reporter is still more useful for a future step), though that’s about all there is for similarities. You want to max out your delay range, and set your year to 2000.
Your frame window is limited only by your PC space, as every 2 frames is a pokemon you need to catch. (A completely empty PC would give you room for an IV frame of up to 1082, I selected 2000 as my max for demonstrational purposes). You may have more difficulty finding a flawless spread with this method, though if you’re willing to settle with a 30 instead of a 31, this will be eons faster. 

![image](https://user-images.githubusercontent.com/86489014/134817688-4404a606-08cc-463d-b296-0654fa0b7c60.png)

RNG Reporter should look like this after you click generate. As convenient as it may be to have a frame 12 31/0/31/31/31/31 spread, we can only hit seeds below 0001517F. You can sort the seeds from least to greatest by clicking on the top of the “Seed” column, poorly circled in red. Once you do that, RNG Reporter will look something like this instead.

![image](https://user-images.githubusercontent.com/86489014/134817808-cfb0f10b-cd1a-43b1-ab3c-68781dbb79e3.png)

There are significantly fewer options now, as there are only 9 reseeds that are below 0001517F. 0000E14C may be the closest option, though reseeding the LCRNG advances 3 frames, meaning instead of only being able to hit odd, we can now only hit even. Of the 5 even frames, 00012F2A is the best option, at a monstrous 704 frames. There is no need to keep track of any seed outside of this one, as any initial seed can net you this reseed value. Again, I strongly recommend going for a less perfect spread, on a lower frame than what I’m doing.
It takes me ~15 minutes to advance every 2 frames, and that’s with practice, strategy, and all the bells and whistles. It could take days or weeks of step grinding to have a chance to hit this frame. Do a test run, at the very least. Something on frame 4, 6, or 8 maybe. Once you have your reseed, you’re going to need to make a copy of my spreadsheet tool, and navigate over to **Other Tools**.
On the right, below and slighly left of the PID Generation formula, is the **Reseed to Encounter Slot Calculator**. After putting in the reseed I’m aiming for and the name of the course, the calculator displays the Pokemon that will be generated in Slots A, B, and C.

![image](https://user-images.githubusercontent.com/86489014/134817885-e9327225-e91a-4e2a-ad11-e57b8cf4d8c2.png)

Luckily I want a Flying Pikachu (Despite Fly being physical). If I hit the reseed I aim for, I will have a Female Pikachu holding an Oran berry (Or for any other course, a different species of pokemon. Yellow Forest makes things complicated, and I would suggest Method A so you can verify gender in the Go for a Stroll menu.) 
If I wanted to RNG Surfichu instead, I would have to RNG that in advance, and have a pokemon already in the Pokewalker when I began the RNG. This is nice, though having a pokemon already in the walker means you forfeit the right to any and all reseed verification, and because you aren’t connecting to the Walker for the reseed, you’ll have to do a few future steps differently.
 Anyway, **Reseed Time** to the left of the slots displays what the DS time needs to read when you confirm the course selection. That time is important, and we will come back to it later. Anyway, onto finding IRNG frames. 
### Part 2: Finding IRNG Frame
Now then, navigate to **IRNG Searcher**, the second tab on the bottom. Before you do anything else, if you are planning to connect to the Walker to send in your Pokemon (Flychu), you’ll need to check the Reseed +308 box shown below. If you do not intend to connect to the walker to update your encounter slots (Surfichu), ensure this box is unchecked.

![image](https://user-images.githubusercontent.com/86489014/134818405-7f917675-8817-4881-99cd-81d9b4bd870f.png)

After that, you’ll need to insert your **Input Frame** at B1 of the sheet. This is your IV target frame, which should be an even value, because you are using a reseed. Like with initial seeding, make a decision on which method you want to use. If you have the Reseed +308 box checked, I recommend Method B, because returning from a stroll with a pokemon sent in by the Reseed advances 1 less IRNG frame, and 2 less IV frames, than a followed Pokemon, which could screw you over. 
For Yellow Forest, you need to use Method A if you want to verify encounter slots, and to do that you’d need to add an additional Pokemon into your Partial connections, so as to compensate for the one missing from your first connection. This would need to be accounted for in IRNG Tracer, as PR(3) for the first connection, and +1 to the partial connection.
Once you have an advancement method, find the corresponding IRNG minimum frame you want. **IRNG Min A** is for Method A, and **IRNG Min B** is for Method B. The tool will automatically assume you plan to use the method with the lower IRNG minimum, but if you wish to use the other method (or Method C), there is a manual Method Override box near the center of the sheet. 

![image](https://user-images.githubusercontent.com/86489014/134818881-e1c9bb43-b1d7-4788-9083-1112eee3108a.png)

Simply type in the letter of the method you prefer to use in H5, and the sheet will adjust to compensate for your method selection.
Once you have your minimum IRNG frame, the next step is to go back to RNG Reporter. This time you’ll need the main tab, your initial seed, and your minimum IRNG frame. Before you do that though, you need to set your PIDs to decimal, just like you would for an initial seed. You want 6000 results, because that's how many the sheet can hold. 

![image](https://user-images.githubusercontent.com/86489014/134818994-c918e6c3-dd83-4083-a952-b4d5b7349b1f.png)

However, because you’re using a reseed to hit the frame you want, you have almost infinite choices for what your initial seed can be. The reseed only affects the IVs, so you can pick any value you like. However, unless you feel like waiting multiple hours, you will want to select your initial seed in a specific way. 
Because You need to hit this initial seed, then wait on a specific menu for your DS clock to line up with a certain time, so I would start with initial seeds near your target hour and minute value. 
To do that, I need to briefly explain how initial seeds are created. The initial seed is made based on the DS day, month, minute, second, hour, year, and delay, as shown below. 
```
0xAABBCCCC, 0xAA = Day x Month + Minute + Second, 0xBB = Hours, 0xCCCC = Delay + Year (minus 2000) 
```
Because you have a required hour, minute, and second for your reseed, 0xBB is pretty much set in stone, but with the right day and month, 0xAA can be almost any value, and 0xCCCC can be any year value (0-50 for 3DS, 0-99 for anything else). 
This gives you a lot of options, so I would start with 0x00HH0000 for now (HH = your hour value in hexadecimal), then if you end up not liking that seed, repeat these next few steps for 0x00HH0001, 0x00HH0002, 0x00HH0003, ... 0x00HH0063, 0x01HH0000, etc. Until you find the seed you want to RNG with. 
You may even want to look for seeds with good nature clusters or local matches (Part 6 of the initial seed guide) if you anticipate offsets becoming an issue. 
Anyway, input an initial seed you want, then click generate. RNG Reporter will give you a list of PIDs, and some other information about those frames. None of this other info is actually correct, as natures are selected by mod 24 instead of 25, meaning Quirky nature is unobtainable. Anyway, there isn’t a way to just copy the PID column in RNG Reporter, so you will need to export this entire thing to TXT. This can be done by right clicking on a frame, and this menu will pop up.

![image](https://user-images.githubusercontent.com/86489014/134821069-b97afd93-9576-423c-a9db-b9995078ce87.png)

Anyway, after selecting this option it will ask you where you want to save this text document. Anywhere will work, though somewhere you can easily find it would be best. Like before, open the text file, copy the contents into the **Copy and Paste Here**, select the entire PID column, and paste that into the **Initial PID** column of the **IRNG Searcher** tab. 
From there, select desired Natures, and perhaps check for good nature clusters. Once you find a frame you're satisfied with, you can select it via **Soonest Nmatch**, **Soonest Lmatch**, or if neither of those work for you, select it manually via **Soonest Cmatch**. 
Be warned, if you get a mess of decimal places with Soonest Cmatch, you chose a frame that isn't a multiple of 192 from the selected IRNG Min. Again, if you don't like your initial seed, there are thousands more that you can use. Once you have your finalized initial seed, you're ready to try hitting it.

### Part 3: Hitting The Reseed
You will have to calibrate to ensure you hit your initial seed, though there are some extra steps you'll need to do first. In seed to time, you will be using the seed that you found most convenient with your target hour. In my case I didn’t have to look far, 00150000 was a perfect fit for what I wanted. 

![image](https://user-images.githubusercontent.com/86489014/134821130-b9d0c86d-7b98-4c88-af38-92525ea21bfc.png)

It should be just as easy as plugging in 07/26/2000 and setting the time to 21:58:16, right? Not quite. 21:58:16 is higher than the time I'm aiming for once I enter the walker menu, 21:33:27. As a result, we will need to be more careful selecting a day and month. 

![image](https://user-images.githubusercontent.com/86489014/134821765-5cc50d52-4858-436b-9eae-02e10cb72062.png)

7/30/2000 is good, as it leaves us with a time of 21:30:16, giving us a full 3 minutes to prepare in-game. That said, you will want to calibrate Eontimer the exact same way as with the Initial Seed method, before you start reseeding anything. You want to be absolutely certain you can hit the right initial seed, even if the IVs don’t depend on it, because your precious nature and PID do. Once you’re feeling confident in your ability to hit your initial seed, there’s more verification to do. You don’t need to use 16 seconds, though I personally like how fast it is. Your Eontimer will look something like this, though your second and millisecond values may be quite different from me.

![image](https://user-images.githubusercontent.com/86489014/134821806-c8f5460b-9464-4e79-b243-d6cab89dd88e.png)

Anyway, I’m calibrated to start up the game at 21:30:16 100% of the time, I need to click yes on the menu below at precisely 21:33:27. 

![image](https://user-images.githubusercontent.com/86489014/134821919-4541fb70-d319-4cbd-b8d5-4cd724eef452.png)

This is an elapsed time problem, hopefully you paid attention in math class. 
```
21:33:27 - 21:30:16 = 00:03:11
```
In this example I need to hit yes 3 minutes and 11 seconds after I begin the game. However, Eontimer doesn’t accept minutes, nor seconds, so you will need to convert to seconds, then milliseconds. Next, this value needs to be plugged into Eontimer, beneath your calibrated initial seed value. 3:11 in milliseconds is 191000, so I put that in beneath 15200. 

![image](https://user-images.githubusercontent.com/86489014/134822173-6a5e8bdf-feea-41bd-b1b5-c2d0e4b670c6.png)

Once you do this, you’re ready to do your first test run with a reseed. If you plan to update the encounter slots, return from any strolls you happen to be on, complete your first timer as before, and hit “Yes” on the course confirmation menu. Connect to the Pokewalker if you want the encounter slots, or cancel out of the menu if you don’t. Once you do that, you’re free to close your DS for now.
If you sent in a pokemon, check all 3 encounter slots on your walker, to see if they line up perfectly with what was predicted in **Other Tools**. If not, you hit the wrong reseed. 
There’s no point in checking these if you cancelled out, as they should be the same as they were before you reseeded. Either way, catch yourself any 3 pokemon, and send them back to the DS. Determine the IVs of any of them (preferably all 3) and plug those into Time Finder.

![image](https://user-images.githubusercontent.com/86489014/134822210-417687d2-2e11-4198-84dc-5b6d5067509d.png)

Sort by seed again, we’re looking for an initial seed starting with “000” after all. It seems like I hit frame 4 of 00012F29, which happens to be 1 second earlier than my target of 00012F2A. Still though, there may be more than 1 seed with this spread that fits these parameters. If frame 4 was the first pokemon in the batch, then frames 6 and 8 should be the second and third pokemon. 

![image](https://user-images.githubusercontent.com/86489014/134822249-07fe3c0e-a3f7-4c8a-8355-b5a136e462bb.png)

If the reseed does fit, then that’s what you hit. In this example, I hit 1 second early, and if I weren’t in Yellow Forest, I would know something is wrong by the encounter slots I saw. Anyway, assuming you don’t land on the right reseed on your first try, you will need to adjust Eontimer. Because I was one second early, I just need to add 1 second, or 1,000 milliseconds, to my second timer.

![image](https://user-images.githubusercontent.com/86489014/134822271-2731b44d-c61c-4b14-8607-71eaa30313a4.png)

After you adjust, try it again, and again, and again, until you feel confident that you can hit the right second. You may want to add 200 milliseconds, 500, or something like that, so you can be late or early without consequence. You may be able to tell what encounter slots correspond to what seconds, but it's best to hit your second value the first time. 
### Part 4: The Long Haul
There isn't much different for reseeds in the main RNG specifically, but keeping track of the number of pokemon you catch, minimizing the possibility for a connection error, and keeping your DS in a safe place are still good habits to keep for an extended RNG like this. Other than that though, good luck on your RNG, and if you need it, Part 5 will be here if you need it. 
### Part 5: Troubleshooting
Welp, if you're reading this, there was a mistake of some sort, and you missed your mon. If your target IVs aren't right, your first step is still to compare the IVs of pokemon 1 to frame 4 of the reseed, then check to see if you had a pokemon too many or a pokemon too few. One of your fodder pokemon might have the IVs you wanted.
As for nature, you have little other choice than to assume you hit the right initial seed, because it would be slow and painful to narrow down what you did hit if you missed. 
Just like you would for initial seed RNG, take a list of Egg PIDs from your initial seed (not your Reseed), save it to txt, paste it in **Copy and Paste Here**, and move the PID Column to **IRNG Tracer**. Once you do that, you'll need to tell the tracer what your RNG was via signatures, with one key difference. 
You need to add a reseed to the beginning, so it would look something like this.

![image](https://user-images.githubusercontent.com/86489014/134823427-ca074989-13eb-400f-84c0-24cc1600a963.png)

You (probably) only did 1 reseed, but if you were doing a more complex hybrid RNG, you might use multiple reseeds to advance multiples of 308 frames, rather than just 192 for a blank connect. As for the other connections you did, Below is the table with each signature. 

| Connection Type                                 | Signature |   |
|-------------------------------------------------|-----------|---|
| Full Connect A                                  | F(A)      |   |
| Full Connect B                                  | F(B)      |   |
| Full Connect C                                  | F(C)      |   |
| Blank Connect (Receive Gift)                    | B(G)      |   |
| Blank Connect (Return From Stroll)              | B(R)      |   |
| Partial Connect (Receive Gift  3 Pokemon)       | PG(3)     |   |
| Partial Connect (Receive Gift  2 Pokemon)       | PG(2)     |   |
| Partial Connect (Receive Gift  1 Pokemon)       | PG(1)     |   |
| Partial Connect (Return From  Stroll 5 Pokemon) | PR(5)     |   |
| Partial Connect (Return From  Stroll 4 Pokemon) | PR(4)     |   |
| Partial Connect (Return From  Stroll 3 Pokemon) | PR(3)     |   |
| Partial Connect (Return From  Stroll 2 Pokemon) | PR(2)     |   |
| Partial Connect (Return From  Stroll 1 Pokemon) | PR(1)     |   |
| Reseed                                          | R         |   |

Other than that, the process of filtering by offset, checking off the boxes to reach your frame, and seeing where and when you got offset is identical to normal, though the reseed itself can be a +4 or a -4, on rare occasions, so it should just be a matter of determining what kind of offset you hit, and accounting that possibility in the future. 
There are no Reseed exclusive methods to getting the upper hand on offsets, so that's about all there is to know about reseed RNG. 
