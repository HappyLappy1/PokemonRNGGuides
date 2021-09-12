---
title: 'Initial Seed Pokewalker RNG Guide'
description: 'A guide explaining the process of aiming for initial seeds for Pokewalker RNG, advancing IV and PID frames to aim for a specific spread, and to troubleshoot if an attempt fails. Essentially Parts 0-6 of the original gide without reseed info.'
slug: 'retail-initial-seed-hgss-pokewalker'
subCategory: 'Retail'
---

```
Note: This guide assumes that you have some knowledge of gen 4 retail RNG already. It is highly recommended that you have completed at least 1 gen 4 Egg RNG, and have successfully hit an initial seed on eontiemr, before attempting this.
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
- Lincoln/Porycyon Tools: **This stuff should probably go on a reseed or event pokemon guide. Move it there when one is created**
- A Palm m500, updated to Palm OS 4.1: This may seem like a weird one, and believe me it is, but until code for 3DS CFW is free from certain "side effects", the Palm is the safest way to inject watts, steps, items, and event pokemon.
- [WalkePoker](https://dmitry.gr/?r=05.Projects&proj=28.%20pokewalker), by dmitrygr: Dmitry's Palm OS app is capable of injecting watts, steps, items, and custom event pokemon, which can be RNGed. The ROM dump doesn't seem to work, I'd advise against using it. If nothing else, this will save you time grinding watts, if you're willing to invest in this RNG. 

### Introduction and Disclaimer
So, you want to do Pokewalker RNG? Before we get started, know that I've spent over two years researching and documenting Pokewalker RNG. 
There is a LOT to learn and study from the little pedometer, from how it communicates with the DS, to how it "creates" pokemon. 
That said, Pokewalker RNG can also be pretty tedious. 
Watt grinding will be time consuming without proper setup (or hacks), PID is not entirely within your control, and there is no seed/frame verification. 
This will be a challenging RNG to those not familiar with it, and a tedious RNG for perfectionists. 
Shinies are impossible (They can be injected with a Palm, but are legally unobtainable), Quirky nature does not exist (unless you inject shinies with a Palm), 
and frame advancement requires catching pokemon. With that out of the way, let's do this!

## Part 0: Species and Course
The first step of this process is to decide on the Pokemon you want to RNG. [Serebii](https://www.serebii.net/heartgoldsoulsilver/pokewalker-area.shtml) 
has a full list of every Pokewalker course, and displays the Unlock Criteria for each course, as well as some advantageous pokemon types that will lower the minimum step 
requirements for encountering rare pokemon by 25%. 

![image](https://user-images.githubusercontent.com/86489014/132967237-0222f970-83c6-4002-bb43-1b9fd1c691a6.png)

If you’re unsatisfied with the selection of pokemon, see **Insert Event Pokemon Guide Here** for information on customizable event pokemon. 
After you know which Pokewalker course you want to use, the next step is to find out what encounter group your target pokemon falls under. 
Each time you send a pokemon from the DS into the pokewalker, it determines 3 species of wild pokemon that will be encountered. 
These pokemon are each pulled from a different group, referred to as groups A, B, and C respectively. 
Each group contains exactly two pokemon, and one will be taken from each group at random. These are the groups for Refreshing Field.

![image](https://user-images.githubusercontent.com/86489014/132967233-ff6d802e-b325-4304-9f50-de129fed0792.png)

In this example, Group C contains Sentret and Pidgey, Group B contains the Nidoran pair, and Group A contains Kangaskhan and Doduo. 
When you send in your walking buddy, your Slot C pokemon could be either Pidgey or Sentret, your Slot B could be one of the two Nidoran, and Slot A would be Doduo or Kangaskhan. 
If you encounter a wild Pidgey, you will never see a Sentret, until your pokemon returns home, and vice versa. 
The step count below each Pokemon shows the minimum number of steps that need to be taken before this pokemon can be encountered. 
On steps 0-499, you could only ever encounter Pidgey or Sentret, but on step 500 you would gain a 75% chance of finding a Nidoran instead. 
However, if you bring an advantageous type (Fire, Bug, or Flying on this course), the minimum step count for groups A and B will be decreased by 25%. 
In other words, if you happen to have selected a Slot A pokemon, bring an advantageous type to speed up the next step of this process. 
Next, you should unlock your route, which may or may not take a significant number of watts to do. 
You may want to first [Find your Mini TSV] **Link Guide Here** if you don’t know your SID and have a specific PID dependent trait 
(such as wurmple evolution, ability, characteristic, or magikarp size) in mind. 

## Part 1: Finding Target IV Frame
Before deciding anything else, you need to find a hittable IV frame. 
This is kind of tricky for Pokewalker mons specifically, though the general method is similar to other Gen 4 RNGs. 
There is the possibility to aim for a “reseed”, that will create a new seed depending on the DS clock. 
It is more difficult to hit these seeds than using the initial seed provided, but there are many benefits to doing so, such as being able to hit certain spreads sooner, 
and having access to some form of seed verification. There will be a separate guide on using reseeds, though this guide will focus exclusively on using a 
standard initial and target seed. Assuming you aren’t planning to calibrate your Mini TSV (or have already done so), you should encounter your target pokemon in the Pokewalker. 
[Encounter Slot Manipulation] exists, and would be more efficient than blind luck for high step count pokemon such as Spiritomb or Flying Pikachu, but it may just be more 
efficient to brute force it, especially for something in Slot C that could be found super easily. Anyway, Pokewalker IVs are generated through the “Gen 4 Wonder Card IVs” Method 
in RNG Reporter (Or Pokefinder, though at the time of writing this RNG Reporter is more useful for a future step). Do note, there IS a “Pokewalker IVs” method in some newer 
versions of RNG Reporter, though it is primitive at best, so I would recommend sticking to “Wondercard IVs” for the time being. 
Pokewalker initial seeds can only have a natural delay of 0, though we can stretch this from a delay between 0 and 99 by adjusting the year later on. 
There is no need to worry about even or odd delay, you will always hit your delay if you set your target year correctly. 
That’s good, because outside of changing the year, nothing else will modify the delay. 
Also, Pokewalker pokemon can only be generated on odd IV frames using the initial seed, because we can only advance IV frames in sets of 2, starting from frame 1. (for those who prefer advancements, that would be advancement 0)
That means that frames 1, 3, 5, 7, 9, etc are valid, whereas 2, 4, 6, 8, or 10 would not be. This is what your window should look like in RNGReporter. 

![image](https://user-images.githubusercontent.com/86489014/132967480-60ea957e-8772-4c51-b5cd-c54334a57c51.png)

The year inputted should always be 2000, because if it isn’t, delay will be automatically added based on the year. 
Unfortunately, Frame 164 and 298 are even frames, which means they are both unobtainable with this method. 
As a result, the soonest obtainable frame for a 31/x/31/31/31/31 pokewalker pokemon is frame 333. 
If there are multiple potential seeds, make note of both of them, as one may be more convenient than the other for RNGing PID/nature. 
You may even find that a later IV frame is more convenient for PID purposes. 
That said, Pokewalker frames are rather time consuming to advance, so it might be easier to learn the ropes on a practice RNG, with a low frame of 1, 3, 5, or 7, before going for a behemoth such as frame 333.

## Part 2: Finding IRNG Frame
For this section of the guide, I strongly recommend using my Pokewalker RNG Google Sheets Tool, linked above. 
For the most part, things should be pretty self explanatory on the sheet, though there will still be a full explanation of if/when each tool will be used in the process 
here as well. First, you should navigate to IRNG Searcher, the second tab on the bottom. It may look a bit overwhelming, but it’s a lot simpler than it looks.
Before doing anything else on the sheet, you’ll need to insert your **Input Frame** at B1 of the sheet. 
This is your IV target frame, which in this example will be frame 333. Simply type in your frame if you are using one, but if you are using advances, be sure to convert to frames
first, or the sheet will assume you are using a reseed. If you have an odd frame, the sheet will assume you are rolling with your initial seed.

![image](https://user-images.githubusercontent.com/86489014/132967587-03e4f459-cb08-473d-92b4-f5d44f17e940.png)

Once you do this, take note of the IRNG Min A and IRNG Min B values directly below it. These are the minimum IRNG values for frame advancement methods A and B respectively. 
While the IV RNG advancement occurs, at a rate of 2 frames per Pokemon, the PID RNG, often referred to as “IRNG”, is a bit more variable in how it advances frames. 
If the DS sends a pokemon into the Pokewalker for a reseed, 308 frames are advanced. 
For each time the DS connects with the Pokewalker to receive a gift or return from a stroll, it typically advances 192 frames, 
an additional 40 frames if your walking buddy returns home on that connection, then 1 additional frame for each Pokemon caught on the journey. 
Methods A, B, and C are patterns by which to advance both the IV RNG and IRNG in efficient ways, and are ordered by convenience to execute, then efficiency. 
Method A for IRNG advancement makes use of the maximum of 4 transferred pokemon per connect, done through sending a walking buddy home, 
then walking around alone long enough for a wild pokemon to join you, before catching 3 pokemon with watts, then selecting the “Return from a Stroll” option to send all 4 
pokemon back at once. This is generally the more efficient method for transferring pokemon, at least for further frames, though both methods have their pros and cons. 
Method B is similar to method A, instead making use of 3 pokemon per connection instead of 4, opting to use the receive gift option instead of ending the stroll, never 
sending the walking buddy home for the entirety of the RNG. Method C is more efficient than Methods A and B, but is far less convenient, requiring external tools. 
As a result, it will be covered extensively in it's own [guide], but not here. This segment of the guide will assume you use either Method A or B. 
Anyway, because transferring pokemon advances the IRNG, as do many other things that are necessary to advance the IV RNG frames, there is a lower boundary for what it can be,
which is different depending on the method used. The tool will automatically assume you plan to use the method with the lower IRNG minimum, 
but if you wish to use the other method, there is a manual **Method Override** box near the center of the sheet.

![image](https://user-images.githubusercontent.com/86489014/132967660-33ca8080-f9c0-4bc8-865e-f4a9746ba002.png)

Because it seems more efficient than it truly is, Method C requires manual selection, so as to not tempt those unable or unwilling to use it. 
For this example, I will be using method A, as 41 connections sounds like a better deal to me than 55. 
Since I’m going with method A, my **Minimum IRNG** frame is 9871, which is already displayed in A9 on the spreadsheet.

Anyway, now that you have an advancement method and a minimum IRNG frame, the next step is to go back to RNG Reporter. 
This time you’ll need the main tab, your initial seed, and your minimum IRNG frame. Before you do that though, you’re going to need to adjust one of your settings. 

![image](https://user-images.githubusercontent.com/86489014/132967731-e98cc0ff-58cc-4a3d-8a83-18038a7b5ead.png)

In the upper right corner of RNGReporter is the options tab, under which you can adjust your PID display from hexadecimal to decimal. 
Google sheets is stupid, and sometimes confuses hex values with scientific notation, so this needs to be set to decimal. 
Pokefinder doesn’t currently have an option for decimal PIDs, but if you are unable to convert your PIDs to decimal form, 
there is a separate tool in my spreadsheet (under **Other Tools**) that can convert a line of PIDs from Hexadecimal to Decimal, though this will only work for most Hex values, 
as anything containing E and numbers will be treated as scientific notation instead... Assuming you have RNG Reporter and decimal PIDs set though, you’re good to go.

![image](https://user-images.githubusercontent.com/86489014/132968014-e18e4884-0dfe-4ec1-a039-0ce34ca28342.png)

Pokewalker PIDs are generated in a very unique way that isn’t currently incorporated in RNG Reporter or Pokefinder, but the calculations start with normal Gen 4 Egg PIDs, 
so this is the method you should select. I would recommend doing 6000 results to start, because that’s how many rows I have by default for PID. 
Your starting frame should be the minimum IRNG frame you just selected, in this case being the 9871 from earlier. 
The initial seed you use should be the one you have from Seed Finder for your IV frame, because unlike with egg RNG, both target frames must come from the same seed.
Pokefinder does not currently have a simple Egg PID method, though in Researcher there is a “Mersenne Twister” option, which will also work. 
Anyway, after clicking generate, RNG Reporter will give you a list of PIDs, and some other information about those frames. 
None of this other info is actually correct, as natures are selected by mod 24 instead of 25, meaning Quirky nature is unobtainable. 
Anyway, there isn’t a way to just copy the PID column in RNG Reporter, so you will need to export this entire thing to TXT. 
This can be done by right clicking on a frame, and this menu will pop up.

![image](https://user-images.githubusercontent.com/86489014/132968042-e29b6251-843e-41ce-ae62-e5104119f493.png)

Anyway, after selecting this option it will ask you where you want to save this text document. 
Anywhere will work, though somewhere you can easily find it would be best. 
I believe this Output to TXT is an option in the majority of Pokefinder, though I couldn’t get it to work in Researcher. 
Anyway, the next thing you need to do is open that text file you just created.

![image](https://user-images.githubusercontent.com/86489014/132968057-78bdbe1b-67b6-40e6-92ce-33649bd70955.png)

Now that you have it opened, use CTRL+A to select the entire document, and CTRL+C to copy it to your clipboard. 
We only need the PIDs, and maybe the frame column too, but isolating those in Notepad isn’t an easy task. 
So, return to your copy of the google sheets tool, and navigate to **Copy and Paste Here**, the 5th tab from the left, and CTRL+V to paste your PIDs wherever you like on the sheet. 
It may take a minute for google sheets to catch up with you, but it will load eventually. Next, select your entire PID column, starting from the first PID, and copy that.

![image](https://user-images.githubusercontent.com/86489014/132968094-ef0b1bcc-37bf-45ff-b83c-226f1cac61d0.png)

Make sure that you don’t copy the column header “PID”, and that you got all 6000 of your PIDs. 
Next, paste those under the Initial PID column in the IRNG Searcher tab of the spreadsheet. 
Be sure that you lined up your PIDs with the proper frame they correspond to, only pasting in blue boxes. 
If you pasted more than 6000 PIDs (which may be necessary if you have your heart set on a specific IV frame and nature), you may need to add more rows to the bottom of the sheet. 
This should be as easy as simply copying and pasting everything except the PID down by one row. 
Once you paste your PIDs in properly, the sheet should once again adjust itself to the new PIDs, and once it’s done calculating, you can begin searching for specific natures.

![image](https://user-images.githubusercontent.com/86489014/132968147-2b251ad2-46e8-4325-a085-5bc2d6b49d5a.png)

On the top middle of the sheet is a set of search tools you can use. On the very top are Desired Natures, simply type up to 10 natures you would accept on your target pokemon. 
The blue box is required, as you need at least one nature for the nature searcher to work, while the yellow boxes are for additional natures you wouldn’t mind taking. 
For this example I am inexplicably dead-set on a bold nature, though if I would accept a modest or timid nature, 
I could add that to my search by typing those natures in the yellow boxes. 
Below that is the TID, SID, and Gender section, containing a section for your Trainer ID and Secret ID, as well as the gender ratio and target gender of your pokemon. 
You will not need your Secret ID to find only nature, but if you need to see PID, or care about a PID dependent characteristic such as ability, 
you will either need your Secret ID, or your “Mini TSV”, which can be found in the guide linked previously. 
Since the shiny lock formula adjusts ability, not all save files can obtain an adamant male 50% male pokemon with ability 1. 
Additionally, you will need to fill out the Gender Rate of your target (the probability it will be male, easy to find on Bulbapedia or Serebii) and its Target Gender, 
the gender your target pokemon is locked to in the course. The Serebii page you visited before has this information. 
The “Predicted Offset”, “Lower Bound” and “Upper Bound” fields should not be adjusted until you’ve completed your first few attempts, though they may come in handy later on. 
“Method Override” is for Reseeds (see the guide for more info), and “Shiny Event” is for injected events. (see the guide for more info)

![image](https://user-images.githubusercontent.com/86489014/132968251-29190d12-20f8-4344-ae17-fb867c79e683.png)

The **Soonest Nmatch** will search for the soonest hitable frame (frame a multiple of 192 frames away from your target) with one of your desired natures. 
**Soonest Lmatch** is not important at the moment, but will also come in handy if you encounter an offset. 
**Soonest Cmatch** will utilize the IRNG frame you type into the yellow box if you prefer a later frame, though generally the Soonest Nmatch is all that you need. 
Depending on which Soonest Match you prefer, check the corresponding box for it on the right. 
Uncheck all other boxes, as the display in the center will prioritize the highest checkbox. Once you do that, you have your target IRNG frame. (11791 for Nmatch) 
On the right of the checkboxes is a display that tells you how many of each different type of connection you will need to do.

![image](https://user-images.githubusercontent.com/86489014/132968806-ba3f71af-e72d-4f4d-a79c-4efdf90f38a8.png)

**Full Connects A** represents the number of times you’ll need to connect to the pokewalker and send 4 pokemon home with “Return from Stroll” assuming you are using Method A. 
Each Full Connect A advances approximately 236 IRNG frames and exactly 8 IV frames each. 
**Full Connects B** represents the number of times you’ll need to connect to the pokewalker and send 3 pokemon home as gifts with “Receive Gifts”, assuming you are using Method B.
Each Full Connect B advances approximately 195 IRNG frames and exactly 6 IV frames each. 
If you are using Method A, ignore all Full Connects B, and if you are using Method B, ignore all Full Connects A. 
**Full Connects C** is used for Method C, and will be explained more fully in the Event Pokemon Guide. The sheet will highlight in red the Full Connect values you should ignore. 
Below that is Blank Connects, or the number of times you will need to select “Receive Gifts" and connect to the pokewalker, without actually having any gifts to send. 
Blank Connects only advance the IRNG by approximately 192 frames, and do not advance the IV RNG at all. 
For the purposes of tracing your progress later on, it will be easiest to complete all Blank Connects after completing your Full Connects, 
because my IRNG Tracer works best if connections of the same type are clumped together. Beneath the Blank Connects is the number of Partial Connects, 
or the number of times you will need to transfer pokemon after the Blank Connects. You should have exactly 1 Partial Connect (unless you’re using Method C), 
though the number of Pokemon it contains will vary depending on your IV frame and your method. Extra Pokemon tells you how many pokemon should be in your Partial Connect, 
and will be between 1 and 4. If Extra Pokemon is 1, 2, or 3, you will use “Receive Gift”, and if it is 4 you will be “Returning From a Stroll”. 
The above is untrue for Method C, though supplementary information will be provided in the Event Pokemon guide. 
Your target pokemon will be generated as the last pokemon sent in the partial connection, so make sure you catch your target pokemon in whatever the last slot will be for each connection. 
If you are happy with this number of connections, you can continue to the next step, but I would recommend trying to get the lowest number of Total Connects possible, 
which will vary depending on the seed you use and the number of IV frames you have. 
10 Blank Connects is much easier than 10 Full Connects, but the less Blank Connects you have to do, the lesser the risk of random frame loss/gain is. 
We will get to explaining what that is after the RNG, but there is the possibility of being 4, 8, 12, 20, 24, etc frames early or late on IRNG specifically, and I have no idea why. 
That said, if your desired nature is not close enough for your liking, you may be able to choose a different initial seed to have an easier RNG. 
It may be tedious, but repeating the above process to get the PIDs into the sheet for a few different initial seeds may be necessary to find a good nature (or cluster of natures). 
With that out of the way, there are only a few more things you need to do before you begin the RNG. 
Before you begin, I strongly recommend making box space/moving pokemon around so that you have room for all of the pokemon that will be coming in. 
You can determine how many pokemon will be transferred by the **RNG Advances** field on the far left of the spreadsheet. 
In the example that would be 167 Pokemon, or approximately 5 full boxes and 17 extras. 

![image](https://user-images.githubusercontent.com/86489014/132969227-d41c14ef-6288-443f-aadb-9a6c5ed10bc2.png)

You will need to see the nature of every single one of these pokemon after the RNG is over if you mess up (or get unlucky), so make sure you know which box they generate in, 
and that you have enough room for them all. Even with an empty PC, the highest IV frame you could reasonably hit is 1079 with Initial seed and 1082 without. 
(You must have at least 5 empty spaces in the PC to use the Pokewalker) If you have access to CFW such as checkpoint, I’d recommend creating a save state before beginning the RNG 
so you don’t have to release all of those pokemon between attempts. Do note however, that you will likely need to save your game a few times after loading a save mid-pokewalker RNG,
as there is some weird dynamic between the save file and communication data that sometimes causes corruption. In my testing this only affects the current save file, not the backup,
but it may be worth saving after loading the backup, rather than jumping right back into it. 
## Part 3: Hitting the Seed
Once you are all set to hit your initial seed, open up RNG Reporter, this time navigating to “Seed to Time” under “4th Gen Tools” on the top menu. 
Paste in your initial seed, and click generate. Your seed to time should look something like this, though forcing a seconds value of 16 is not necessary.

![image](https://user-images.githubusercontent.com/86489014/132969331-b4209b45-63c9-4e28-ad77-d377f365ad3c.png)

As you can see, each and every single one of these Date and Time combinations gives us a delay of 45. 
Depending on the year in your Year box, this delay may be either positive or negative. We want to adjust our year so that the delay is exactly 0. 
To do this, simply add the delay it gives you to the year. In this case, 2000 + 45 = 2045, which is the only valid year for this initial seed. 
So by changing our year in this way, Seed to Time will give us a delay of 0.

![image](https://user-images.githubusercontent.com/86489014/132969341-32410ab8-c7e0-4309-8e42-705d4f47c903.png)

Once you’re certain that the year you’ve selected will give you a delay of 0, you can select a date and time. In a normal gen 4 RNG, 
your next step would be to type in your delay and seconds value into Eontimer, however the Pokewalker initial seed is generated sooner than the typical gen 4 initial seed is, 
when the screen finishes fading to white upon launching the game. As a result, the gen 4 tab of Eontimer will not be sufficient for this RNG, 
though we can still use the tab for a starting value for manual testing, if we tweak it slightly.

![image](https://user-images.githubusercontent.com/86489014/132969363-2071a071-d67d-43a1-8f4e-557c06f7090d.png)

You know the “Calibrated Seconds” value, that you’re never supposed to touch for gen 4 RNG? We're going to touch it!
Change that from 14 to 9, and insert the calibrated delay that you tend to use for gen 4 RNGs (if you don’t have a magic number that you usually hit your delays with, just go with 490 for now)
and set your target delay to 0. Your target second should be whatever seconds value you have in Seed To Time. 
Don’t start the timer though, this number isn’t entirely accurate. Instead, navigate over to “C” on the far right, and type the time you found in the gen 4 tab out in milliseconds.

![image](https://user-images.githubusercontent.com/86489014/132969403-55424c50-95c2-46bb-9ae0-6500ce66e809.png)

Then, hit the little plus button to add this to your custom timer, which should now display exactly the same as your Gen 4 timer. 
Now, you will want to test this millisecond value and see if you can consistently hit your desired seconds value. 
If you’re not doing a very long RNG, as in less than 3 total connections, you may only want to do a single test to ensure you can hit it, 
but if you’re in for the long haul and intend to go for something more than 10 connections, attempts may take days, and if you intend to follow the example of 55 connections, 
even weeks. What you’ll need to do is set your date, and click start on Eontimer the instant you enter in your time. 
When the timer hits 0, open HeartGold or SoulSilver. Open the Pokewalker menu, close your DS, plug it in if necessary, and catch a wild pokemon in the pokewalker.
Part 4 of this guide will cover efficient Watt generation and use, though you won’t need more than maybe 20 to successfully catch a Pokemon for these tests.
Send it back to the DS through “Receive Gift”, determine what IVs it has by whatever means at your disposal, then compare those against the first IV frame of your target initial seed.

![image](https://user-images.githubusercontent.com/86489014/132969448-343c632a-ee43-4eb0-ab18-1360ee4d2965.png)

Be sure to switch back from PID to Wondercard IVs, and compare frame 1 of your seed to these IVs. If they do not match perfectly, you hit the wrong second value. 
If this is the case, navigate back to Seed to Time, adjust the window to have +/- 0 delay, and +/- 1 seconds. 

![image](https://user-images.githubusercontent.com/86489014/132969464-3863e77f-6afd-4552-b269-bce2c17aef08.png)

Now check if the Wondercard IV frame 1 of either of these seeds match the IVs of your target. 
Keep expanding the seconds range until you find a match, and once you do, subtract a few milliseconds if you were late, and add a few milliseconds if you were early. 
You can reset the custom timer by clicking the - button next to the +. If you’re more than 1 second off, maybe adjust by entire second values too. 
The goal is to get the right second even if you’re early or late, so keep doing this until you’re confident in your value or at the very least willing to give the real RNG a try. 
I myself didn’t have to adjust much, though I found that 15.200s worked a little bit better for me than 15.190s. 

![image](https://user-images.githubusercontent.com/86489014/132969529-5235060b-9e5c-45eb-a1db-e9051a6d8d53.png)


For future RNGs, I always aim for second 16, so I don't need to test it again. Unfortunately, if you are doing this on 3DS, 
your success rate won't be very good no matter what you do. Once you’re confident in your ability to hit your initial seed, either release or move elsewhere your testing pokemon, 
they probably won’t be necessary for anything. If you happen to be doing Method A, send your partner pokemon back from its stroll, and don’t send anything back in. 
Leave your walking buddy in the Pokewalker if you’re using Method B. Once you’ve done that, set up your date and time to hit your initial seed,
and keep trying until you feel like you’ve nailed it. You are going in blind after all, you want a good chance to hit the right initial seed.

## Part 4: The Long Haul
Once you’ve hit that initial seed, and entered the pokewalker main menu, find a safe place for your DS, plug it into the wall, and close it. 
In case of a power outage of some kind, a DS Lite can survive for approximately a week with its lids closed, and it will contribute the least to any electricity bill this way. 
I strongly recommend keeping a journal or log of some kind to keep track of your connections and ensure you don’t miss any, skip any, lose track, or anything like that. 
This is a record from a Method B RNG I did, though digital means are just as effective as pencil and paper. 

![image](https://user-images.githubusercontent.com/86489014/132969576-fbc4ff58-fe97-42d1-a675-39e59ae9e473.png)

To act against the possibility of counting a connection twice in this log, I wrote down a timestamp for the connection when I selected “Receive Gift”, 
and beneath that the species of Pokemon I caught on that connection when they were displayed on the DS screen. 
I created a box for each connection I would need to do, so I knew when I would need to switch to blank connections or my partial connection. 
You don’t have to do this, though most people can’t remember more than 7 things at a time, so if you have to take breaks to eat, work, sleep, or walk with the pokewalker, 
a simple tally system may not be enough to keep you on track. Anyway, as far as watt grinding tech goes, there isn’t exactly a consensus on the best way to do it. 
If you have access to a Palm m500 series device, or are willing to buy one, Dmitry’s WalkePoker app can add 9999 watts to your walker with a press of a button. Update it to
Palm OS 4.1 if you are able, as 4.0 users had trouble using WalkePoker. 
There is 3DS CFW in the works that can inject Watts or Steps, but it has known side-effects such as deleting Steps, Deleting Watts, and deleting Caught Pokemon. 
I may link them in my other guides, but that would be a more advanced tool. 
I hear Palm devices aren’t exactly expensive, but this might feel cheaty to you, idk. 
When this guide was first written, 3 people claimed to have done a Pokewalker RNG, and all of us have used different methods to grind watts. 
Wild Eep claimed to have built a lego contraption with a “bicycle pedal motion” 10 years ago, so if you can automate the watt grinding process, that might be smart. 
Upper90175, also known as Jay, claims to have grinded watts to unlock courses through a mobile phone app that got the Pokewalker watts while they slept, 
though I was unable to replicate this (The physics check out though, this may be a viable method). 
As of recently, I was able to borrow a friend’s “inertial balance”, a wiggly tool astronauts use to weigh things in space. 
It works best with 200g of weight inside of it, though before I got one, I had a less high tech way of doing things. 
This method of generating watts will require your pokewalker to have the belt clip. 
Get a jumbo popsicle stick from your local craft store, slide it into the Pokewalker belt clip on one end so it’s nice and taut, like so.

![image](https://user-images.githubusercontent.com/86489014/132969712-72483c9c-1e63-4dcb-8425-0f1848f5c77d.png)

Now, grab the other end of the popsicle stick, and bang it up and down gently on a pillow or thick carpet at a moderate pace, to simulate walking or running. 
The maximum speed I’ve been able to “walk” before the pokewalker suspects foul play (if you shake it too quickly it will stop counting steps) was approximately 190 BPM, 
which is remarkably close to the speed of Gourmet Race. Bonking a pillow to the beat of Gourmet Race for approximately 5 minutes will yield you between 40 and 50 watts, 
plenty for you to start catching pokemon. If you’re using Method B, it may take a tad longer than 5 minutes for wild pokemon to join you, 
but usually that happens between 5 and 10 minutes of carpet assault. Then again, you could always actually walk with the pedometer designed for walking, or design your own method. 
You don’t have to listen to Gourmet Race either, it gets boring after the 10th time through. 
By the way, try your best to not get a communication error when sending your pokemon to the DS. 
if you do, your IRNG frames are going to be off by some value between 0 and 192, though your IVs will be unaffected. 
The belt clip doesn’t exactly line the pokewalker up well for connection with the DS, though I do have a good connection setup.

![image](https://user-images.githubusercontent.com/86489014/132969743-412ae7e5-bf63-4966-ad8d-971e5148e786.png)

If you slide the popsicle stick to the center of the pokewalker, you can hold down both ends of it to lock your pokewalker in place. 
I have a Pokemon Soul Silver Case for the DS to sit on, and a Pokemon Sword Case for the pokewalker, and that elevation difference is pretty optimal for a connection. 
If the DS case is too small for you, a Wii or Gamecube game case works too. Anyway, as far as battle strategy goes, the opposing pokemon can only run away if you evade. 
If you attack when it tries to flee, you score a critical hit and deal double damage. This is a good thing, unless it has exactly 2 HP, in which case you will accidentally murder it. 
It’s always better that you kill it though, rather than it killing you. 
If your walking buddy faints, you lose 10 additional watts, so if you’re down to 1 HP, spam evade until it runs or you can catch it. 
Make sure you follow your method properly, and with that out of the way, good luck, and come back if you don't hit your target for Part 5. 

## Part 5: Troubleshooting

So, you’ve completed your attempt, and your target has the wrong IVs or PID? Well, before you throw yourself at it again, you’re going to want to determine what went wrong. 
The first step in doing that is determining if you even hit your initial seed, which can be done by looking at the IVs of the first pokemon you transferred, 
and comparing it to Initial Seeds full seconds before and after your target, like you did for calibration. 
Once you do that, write down what initial seed you hit, because there is more room for error than just hitting the initial seed properly. 
If you hit your initial seed correctly, use it for this next step. If not, use the one you actually hit. Take that initial seed, 
and generate egg PIDs for it in the main window of RNG Reporter. Have the search start on frame 1, and set max results to your target frame plus a buffer of ~200 frames. 
(if this is larger than 12,000, you may need to add more rows and paste in some cells) This is in case you overshot your frame, which is more likely with Method A than Method B. 
With my previous example, it should look something like this. 

![image](https://user-images.githubusercontent.com/86489014/132969823-82274761-3871-4241-a6d9-030e0a463184.png)

Now, save the list of PIDs and other stuff to a text document like you did before, copy that, and paste that in **“Copy and Paste Here”** of the spreadsheet, 
preferably not on top of your other pasted data. Once it’s done loading, copy the full list of PIDs, and navigate to the **IRNG Tracer** tab of your spreadsheet. 
Paste your PIDs in the PID1 column. 

![image](https://user-images.githubusercontent.com/86489014/132969844-0b447e50-211b-4633-929b-b40b4d37d22a.png)

Once you’ve done that, you’re going to be filling in the **Connection Type** field, as well as **# of Connections** (F2:P2 and F3:P3 respectively). 
There are a total of 14 different types of connections, though there are only a handful you need to know the signature for at the moment. 
All connection types are explained briefly in the sheet, if you’re curious. Anyway, your boxes should look something like this.

![image](https://user-images.githubusercontent.com/86489014/132969856-6828d745-227a-402c-ac9c-ef04cda51361.png)

This is the initial seed example I’ve been using throughout the guide. 
**F(A)** represents Type **A F**ull connections, of which I completed **41**. I type F(A) in the first box, and put 41 directly beneath it. 
If I were to use Method B, I would use **F(B)** instead, for Type **B F**ull connections. 
**F(C)** is the terminology for Type **C F**ull connects, which will be covered in depth in the Event Guide. 
**B(G)** is Blank Connects, if you hadn’t already guessed, though **B(G)** specifically refers to **B**lank connects where you selected “Receive **G**ift”, 
and **B(R)** (**R**eturn from stroll) exists if you decide you need it for something (and it even works at all, since I have yet to test it). 
I completed 10 Blank Connects, so I put 10 beneath B(G). 
Finally, **PG(3)** is shorthand for **P**artial Connections in which you received a **G**ift, and transferred **3** pokemon. 
**PG(2)** and **PG(1)** do the same thing, for **2** and **1** Pokemon respectively. 
I completed one of these, so I slotted a **1** beneath PG(3). 
If you have 4 pokemon in your partial connection, you’ll use **PR(4)** instead, standing in for Partial Connections which you Returned from a stroll with 4 pokemon. 
**PR(5)**, **PR(3)**, **PR(2)**, and **PR(1)** also exist, assuming you need them for some reason.
This sandbox-esque layout is utilized because more complex IRNG manipulation may involve a sort of Hybrid method between A, B, and C, where F(A) and F(B) are utilized, 
as well as multiple partial connections, blank connections, and Reseeds. The sheet can trace it back, if you can make it happen. 
If you happen to have too many or too few, (which you shouldn’t if you followed my advice in Part 4) you will want to punch that in instead. Alright, let’s actually do some tracing. 
Remember when I told you to hold on to every fodder pokemon you caught during the RNG, and to keep them in order? You’re going to trace back the IRNG advancement for each Pokemon. 
Make sure you remove all check boxes from Column E (Frame Hit?) prior to starting this. But first, we’re going to filter the sheet for frames close to where your IRNG should be. 
Click the little upside down line triangle next to **“Frames Off”** (at E8), and you should get a menu that looks like this. 

![image](https://user-images.githubusercontent.com/86489014/132969961-bfaff97a-976d-441b-afe6-a9817f40c3a8.png)

The plan will be to select **Filter by condition**, and in the drop-down menu select **Is Between**, and at the moment your range can be -8 to 8. 
This range may need to increase midway through the process, though once you finish it should look like this.

![image](https://user-images.githubusercontent.com/86489014/132969976-f979cd4e-6c1e-4604-b061-a00e81afff52.png)

Click OK, and now IRNG Searcher is filtering by frames that are 8 early or 8 late of a frame a connection ended on. Look at the nature of the first Pokemon you transferred. 
It should match the nature of the green 0 frame. If you use Method A, you will be looking for groups of 4 consecutive matching natures, 
and checking off the boxes to the right of them if they match. For Method B, you will be looking for groups of 3 matching natures instead. 
In my example, following Method A, my first 4 Pokemon had the natures “Careful, Lonely, Adamant, Impish”. 
These 4 pokemon were transferred in my 1st connection, and their species are written down in my journal entry. As a result, my chart looks like this.

![image](https://user-images.githubusercontent.com/86489014/132969986-04b90177-b2ab-432e-9ebe-6c805d0ba0f9.png)

There is the possibility that these natures do not line up with the green zero, and if that is the case, attempt to locate the closest set of 3/4 natures that match. 
The first pokemon’s nature will likely be 3-4 frames early or late from 0. 
Once you locate your first set of 4, scroll down to the next green 0, and look at the next set of 3 to 4 pokemon, depending on your method. 
Mark them down using your checkbox system, and repeat this process for each connection of pokemon you did, until you find a set of natures that doesn’t line up with 0. 
If you find an offset, or a point where your connection of pokemon does not line up with the predicted green zero, your next connection will likely be that far off of zero as well.
If you find an offset, make sure to adjust your boundaries in the filter, so that you can locate more offsets as you continue. 
Once you get close to your last 4 pokemon, keep an eye on the column right of the checkboxes. Eventually, you won’t find a match anywhere near you. 
Click the checkbox anyway, and you should see “Blank?” pop up on the right of your checkbox. 
As you can see, I’ve been offset by +12 frames so far in this example. (You will likely get a number after “Blank” as well, though this screenshot is a tad outdated)

![image](https://user-images.githubusercontent.com/86489014/132970007-e63b167f-66b1-4b65-ae4c-5d8f072e9148.png)

This means you’ve reached the end of your full connections.
Scroll down a number of green zeroes (or in my case 8’s, since I filtered out the green zeroes) equal to your blank connects. 
If you look on the far left column, you should be near your target frame. Click a checkbox there to verify you’re past the blank connections. 
Once you are, try to locate your nature(s), and check the corresponding boxes. It may be ahead or behind your last offset. 
My last 3 pokemon were Docile, Serious, Brave, which is 4 frames earlier than the +12 I had before.

![image](https://user-images.githubusercontent.com/86489014/132970021-632317bf-653b-41e7-b7ce-1e14cc9552f6.png)

Once you’ve checked your boxes, turn off your filter and scroll all the way back up to the top. 
You should have a convenient offset table that shows when each offset occurs, and by how much it happened. 
The first row that displays an offset of 0 is irrelevant, it just displays the original starting point, and will not occur if your first connection was offset. 

![image](https://user-images.githubusercontent.com/86489014/132970036-a59db904-2da2-4fa9-915f-13f1b86872f3.png)

If you happen to have had a connection error, you will likely see a spike in offset on the connection you had the connection error. 
However, as you can see, there seem to be somewhat random offsets occurring at inconsistent intervals, usually in increments of +4 or -4. 
This is possible even if you do everything perfectly, and I currently have no clue what causes it. 
There are some things I do know about it, detailed in Part 6, but if you happen to see something weird besides these unexplained increases and decreases of 4, 
such as a random increase of 56, 102, 93, 20, 175, or something like that, you probably had a connection error and didn’t notice. Be more careful connecting your DS to your pokewalker. 
This process is also a great way to double check if you have the right number of each connection, so if you did one extra or one too little, you would likely notice this as you are punching in your natures.

## Part 6: Accounting for Offsets
So, there are offsets that can happen even if you do a pokewalker RNG perfectly, and I have not figured out definitively what causes them, though not for lack of trying.
Part 11 of my [original guide](https://docs.google.com/document/d/1-etPYFvFmDarEiIjhETrKkl7fJjo01tcH3K8SOEe5iM/edit?usp=sharing) is a chronological log I have been keeping of the 
things I have tried, the variables I have attempted to isolate, and the conclusions I have about them. It may actually be nothing more than superstition and coincidence, but as of now there’s no way to know for sure. 
So anyway, these offsets are happening, at least to you and I, and now they’ve successfully ruined your day. Now what? Welp, that’s an interesting question. 
How do you account for the possibility of being off by 4, 8, 12, 16, 20, 24, 30, 36, 40, or even more frames than that? There really isn’t a good answer. 
You could repeatedly try the RNG over and over and over until you actually get it right, if these things are even random. 
Assuming these offsets are tied to initial seeds though, you may never hit the right seed. If you think you’ve got a consistent offset, there is something you could try. 
In IRNG Searcher of the spreadsheet, there is an option to apply an offset to your search. 

![image](https://user-images.githubusercontent.com/86489014/132970547-bc487d2c-27b0-4184-9bb1-2d505ed0b4a1.png)

If you adjust **“Pred. Offset”** to a positive number, you can search for late PIDs, frames with a positive offset. 
If you notice that you’re hitting +16 every single time, put 16 in for your predicted offset, and you can search for your desired nature/ability at +16. 
If you notice that you’re hitting -4 every single time, then put -4 into the predicted offset, and start searching. 
If you happen to be crazy enough to try and manipulate communication errors, plop whatever number you feel like in there, and search for your optimal nature. 
Another idea I had was to aim for frames with clusters of acceptable natures, and hope you hit one of them. So I added a nature cluster searching tool, which can be seen above.
By inputting a range through **Lower Bound** and **Upper Bound**, as well as an **Increment** for the offsets (4 by default), you can look for frames that are near your target
(or potential target), and see if they are also the nature(s) you want. 

![image](https://user-images.githubusercontent.com/86489014/132970578-535932f0-529c-49ea-9825-b14f94894086.png)

The **Desired?** and **Incremented** columns are used in calculating the **Local Match** column, which states exactly how many frames near each frame have a desired nature. 
However, as I mentioned previously, the more blank connections that are used, the higher the chance of being offset by additional frames. 
That’s where **Blank Scaling** comes in. Set at 10 by default, it will determine how often the offset range should expand to compensate for being further out. 
I even added a **Max Locals** field, which will tell you the highest number of local matches and where that frame is, as well as a **Max LMatch** which will display the IRNG frame
with the most local matches that is a multiple of 192 frames off of the IRNG minimum, and where it is. 
This is where **Soonest LMatch** comes from, though you may need to input a lot of desired natures to make this work.

![image](https://user-images.githubusercontent.com/86489014/132970596-c9f0f25e-7485-4853-9bbe-0e40bc3fd298.png)

Finally, the Japanese user [bowline_lab](https://bowline-lab.hatenadiary.org/entry/2020/09/06/162015#%E3%82%B3%E3%83%BC%E3%82%B9%E5%87%BA%E7%8F%BE%E3%83%9D%E3%82%B1%E3%83%A2%E3%83%B3%E3%81%AE%E5%8F%8D%E6%98%A0) 
found that these IRNG offsets are displayed by 1 extra or one fewer ball of light being present during the gift receiving animation. 
If you were to watch that carefully, or record it each and every time you made a connection, you could determine your offset in the middle of an RNG, 
if you fancy counting 47-78 balls of light each time you complete a connection. 
In a similar vein, there are some loose ends regarding the use of external tools with IR capabilities that can beam in pokemon such as Spinda 
(which would allow you to extract it’s exact PID from the position of it’s spots by looking at it in the “Go for a Stroll” pokemon selection menu), 
as well as some loose ends regarding the use of ROM dumping to extract the Pokewalker’s RNG state, which I suspect to be an output of the DS’s IRNG, 
but the former is rather complex and will be covered in it's own [guide], and the latter is untested and unconfirmed.
