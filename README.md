# Notes and config for parquette audio measurement

This repo is to store protocols and data for acoustic measurements we take for parquette

## Thursday May 15th and May 16th

We are testing with the Danely using 4 corner stacks. Rear stacks have vertical tops with JBL tweeters unconnected as spacers sitting on subs. Rear stacks have subs with black wood block spacer and horizontal tops on angled holders. Additionally there are two subs in the front in endfield config. There is Danji's normal 6k rolloff in the high end + the endfield config. Rough testing suggests there is no significant phase issues with the subs but we haven't exhaustively tested and measured. Room is currently untreated with little inside.

After some preliminary testing it's clear that audio triggered timing ref in REW will not work as there's too much attenuation in those bands. If we want that kind of full measure we have to run XLR and output from the same machine we're recording. Instead I will do a pink and sin sweep measurement in the real time analyzer instead. We will run at 40pct alsamixer, with the scarlett a

Data sets
1. a coarse horizontal grid positioned window center and brick center horizontall and window center height verticially from the outter eastern building edge to past the first bakery window (window 5). This coarse grid will be at 3 heights, window center, brick above window center and roof join + 10cm. Naming scheme coarse-{signal}-{x}-{y} (x left to right), (y bottom to top). Some roof measurements at y=2 go b,c,d moving back onto the roof surface
2. a fine grid over the 2nd window - room middle - every 50cm with n points extending up past the roof lip by 1 or 2 points. Naming scheme fine-h-{signal}-{x}, x left to right
3. a fine grid over the 2nd window - room middle - every 30cm with 7 points 2 above and one at the rim below vertically Naming scheme fine-v-{signal}-{y} (y bottom to top).
4. AB measurement on bathroom vent bathroom-close / bathroom-far measured direct at each vent and 30cm above
5. A set of specific position reference measurements annotated in drawings as ref-{signal}-{letter}
6. A set of individual speaker configs takes at the second window center (0-3) speaker-{signal}-{speaker} where {speaker} is tf, tf, sf, sfe, sr (t/s = sub), (f/r = front/rear), (e = endfield also firing for the sub in question). Note the front subs are mono so there's no l/r
Done at ref A at alsa 45pct some wind
7. Reference inside measurements take at the rough room center and room front (measurements to be noted) inside-{center/front}. Inside front is room center (l/r center and 8m or so front and back). Center is speaker center

{signal} can be baseline, pink, sweep

For all these coarse and fine grid tests the mic will be pointing 90d with the mic head 10cm from the surface (this will mean it moves slighting between brick and glass)

Note that for the reference measurements there was a truck and for the other measures there was a lot of kids in parks

### Setup
* Playback via pi -> scarlett4i4 -> chan1/2 -> elastique setup
* 4i4 physical volume at max 
* 4i4 soft volumes at 0db
* VLC vol at 100%
* generating files at -12db
* alsa volume at 40%
* run via `aplay {./file}` on the default interface, e.g. 4i4

### Qualitative tests
It seems like we get limited improvement with a cliff filter under 30/40 hz, the band from 70-300 seem like the biggest contributor to sound

## Notes
* Use `alsamixer` to set volume on pi
* pi is parquette@audiosource.local, has ssh and vnc onboard, same password as wifi, ssh with my private key only
* aplay no settings uses default vol from alsa otherwise it can ignore vol

## TODO
* Position of drawing of setups
* Capture and save photos of setups with notes
* Need a way to interpret the relative differences, how much worse is one curve or another? Probably measure while turning down loudness to know
* Reference measurement points between us and building
* Test with subsets of speakers
* Complete the inside ref measurements