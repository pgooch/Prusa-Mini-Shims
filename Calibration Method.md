# Prusa Mini X/Y Skew correction
This document will go through the process I used to calibrate my skewed Prusa Mini. As a foreword I'd like to make it clear that I am no a 3d printing expert, just a guy who was stupid enough to mess up my X/Y skew up and _just_ smart enough to fix it. Anything I state is this guide should not be taken as fact, I simply wrote this guide because there wasn't one on correcting this problem when it happened to me, but there are undoubtedly better ways to go about this. If you have any tips or a better solution leave it in the comments and they will be recompiled into this guide. I may also move this guide to GitHub if there is interest.

For all prints used when creating this guide I printed with Prusament PETG, previous to writing this I did the calibration with some cheap PLA I had on hand. Material seems to not matter much, and the only reason Prusament was used this time is so that the shim would match the rest of the printer. 

## The calibration print.
Before we start printing shims to fix the skew we should print a baseline. While you could use any pre-existing skew calibrator or create your own I suggest using [YACS (Yet Another Calibration Square) by Paciente8159](https://www.thingiverse.com/thing:2563185), it's the one I used and it prints quickly and seems to get the job done.

Calibration prints were sliced in PrusaSlicer at 0.2mm layer height with the default QUALITY setting. Prints should be made on a smooth surface as the texture could effect the layer height (and even small changes can cause inconsistency). You'll probably just want to keep the gCode on at hand so you don't have to re-slice between tests.

Also, __label your calibration prints__, or you will quickly forget which is which. Your gonna want to keep track of each print so you know if your skew is getting better or worse.

## The correction process.
First, print a calibration square. Then, measure the cross angles, A/C and B/D. In my case they were the following.

```
A/C = 141.6
B/D = 140.0
```
Now it's time to start placing shims and re-printing test calibration squares. From previous testing on this I found a good place to start is the difference of A/C and B/D, in my case that was 1.6mm, so that will be the fist shim I try. From there you can adjust the shim and print calibration squares until you are happy with the result. In general if A/C is longer than B/D you need a thicker shim, and the reverse is also true.

This time that was dead on and the 1.6mm shim corrected the skew. That was not the case the first time, and differences in prints and material may mean you making several attempts to get it dialed in. 

Just because I nailed it on the first attempt down't mean you will. I made countless shims and calibration prints the first time I was doing it in PLA, so don't fret if it doesn't work just swap out the shim and try again.

## Printing the shims
The shims were designed to be printed with the shimming side down to take advantage of the greater resolution when building layers. All prints were done with the 0.05MM ULTRADETAIL preset. It's a good idea to watch the first layer go down, as even minor problems with it can cause big problems down the line due to the tiny layer height.

When you slice you may notice this shimming surface has a slight taper to it. This was done in order to help the control box better sit against this shim and is intended.

Also note that printing at such high resolutions takes a long time. Printing 1 set took around 9 hours, so consider printing batches as needed so you can run multiple calibration squares between shim printing sessions. You could also use the adaptive layer heigh option, just make sure it's maxed out for the entire height of the shim. Even then there can be issues with the print, so the parts tend to need a bit of cleanup at the least. Just make sure to leave the shim surface alone or you'll make the process take longer by not knowing the _real_ thickness of the ones you've installed.

## Installing the shims
The shim goes on the back of the right Y axis bar, all the way up against the back lip that the control box uses for alignment. See "Shim Installation Location.jpg" (The first image on Thingiverse) for an image of the exact location, it's that odd orange bit between the axis rail and the control case.

To gain access to this location your going to need to remove a few screws. I have marked the locations on the "Oh the Screws You'll Remove.jpg" (The second image on Thingiverse) image. Technically I'm sure your _supposed_ to re-tighten them all when testing however I left the one marked with a * off, as well as the display (it was getting in the way) and it seems to have been OK.

If you shim is thick enough (around 1.5mm or greater) then the lip at the back of the printer will no longer hit the control box, in that case you just need to line it up as if it all fixed. You do have a little flexibility (maybe a millimeter or two) since the print bed is just a bit larger then the printers print area so exact positioning isn't important.

## How to know when your done
How fine you want to re-calibrate the printer is up to use. With a suitably fine measurement and enough time you could spend the rest of your life aiming for perfection. In reality however the 3D printing has tolerances (not just to to printer variation but also due to material properties). 

I found I had good results using the calipers as the gauge for my success. First I could measure A/C and use the locking screw on my calipers to hold the calibration square tight enough I could lift it off the table just by the calipers. Then, without touching the locking screw, I would slip the calibration square out of the calibers and kinda clip it on the other direction. Once it could pick up the square from all corners without touching the locking screw I considered it "good enough".

## What are all those STLs
The STLs can be broken into two categories. First is the master STL, this contains every shim on it's side (as thats how they were generated). If you want to print from this you'll need to break the STL apart and some them. There are more shims than will print on the Prusa mini at a single time, so after you have some idea how bad your skew is then you can print only a few around the target size.

The other STL files are shims grouped into roughly 1mm batches. These STL files are pre-faced and can be printed with minimal fuss, just remember to set it to the 0.05mm preset.