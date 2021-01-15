---
layout: post
title:  "Figuring out Soundgoodizer"
date:   2021-01-15 02:53:00 -0500
description: Soundgoodizer is Image-Line's single-knob mastering plugin, but what does it even do?
img: soundgood0.png
fig-caption: Maximus in action
tags: [music,tutorial]
---

Okay, so one of my friends on Discord has been asking about Soundgoodizer and YOUWASHOCK (the latter being something of a joke rebrand of the former) and how specifically to reproduce their functionality with something else, so I decided to literally make a blog so I could have somewhere to post this. I thought about Youtube, but you know... maybe not~

## What are Soundgoodizer and YOUWASHOCK?

Basically, both these plugins are extremely limited versions of the mastering plugin [Maximus](https://www.image-line.com/fl-studio-learning/fl-studio-online-manual/html/plugins/Maximus.htm) from FL Studio. Instead of having full control over Maximus, you're given 4 presets and a single knob to control the amount of "soundgoodizing." The lucky thing here is that the 4 presets (A,B,C,D) are available in Maximus, so we can see exactly how the presets work with a demo of FL Studio. 

But first, let me try to figure out what Maximus even does.

## What does Maximus even do?

The link above refers to Maximus as a "multiband maximizer." A maximizer (to my understanding anyway) is just something that applies gain and then a limiter. Maximus seems to be a little bit more than that. It has three bands for compression, which are then sent to a master limiter with the same controls. For all four bands, you have the following settings:

* Normal compressor stuff like pre/post gain, threshold, ratio, etc
* Saturation, which is closely related to compression.
* Stereo separation

There is also a low cut knob, and one labeled `LMH Mix`, which is a sort of wet/dry: If you turn it all the way down, the three LMH compressors will be sent to the master unprocessed. Turning it up gives you a combination of the compressed signal and the uncompressed one -- this is often called NY style compression -- until you've finally turned it all the way up and you are only hearing the "soundgoodized" signal. In fact, this knob corresponds to the single knob you're given in Soundgoodizer.

So if you want to replace Maximus with something, you'll need to find a plugin (or combination of plugins) that does all of the above. Since I only ever use FL Studio, I don't know of any other multiband compressors with per-band stereo separation and saturation -- I have a feeling iZotope Ozone or some sort of Waves thingy could accomplish this, but I suppose the problem is finding something else that is cheaper than Maximus for the same functionality.

Sorry I can't be of more help there hehe, but for now, let's go over the 4 presets so if we **do** find an alternative plugin, we will have some idea of how to set it up.

## What do the 4 presets do?

Okay so just to recap, Maximus works like this:

* Low cut / high pass
* 3 bands of compression (or no compression and you can just apply gain)
* Tube style saturation and stereo separation for each band
* LMH Mix knob sends some ratio of the compressed signal to the master
* The master then has its own compressor, stereo separation, saturation, etc.

For all four of these presets, the low cut is 20hz (easy enough). In Maximus, the LMH mix is all the way up by default, but Soundgoodizer defaults to something like 60%. I have included an image for each preset, but one thing to keep in mind with Maximus is that you can't see everything at once -- the UI is tabbed with low/mid/high/master on the left. So I will just describe the rest of it for now. 

The source I am using to tell what a compressor or limiter or expander looks like in Maximus is (once again) [Image-Line's documentation](https://www.image-line.com/fl-studio-learning/fl-studio-online-manual/html/plugins/Maximus_Tutorials.htm). I may edit this post later with more images of the various compression curves if you, the audience, deem it necessary :)

### Preset A

![Soundgoodizer preset A](/assets/img/soundgoodA.png)

I think this is everybody's preferred preset for mastering. It sounds very bassy to me sometimes. For whatever reason, this applies an expander and saturation to the lows and highs, but not the mids. Maybe a smartypants can explain why that works but I can't.

#### Bands:
* Low: 20-200Hz
* Mid: 200-3000Hz
* High: 3000Hz+

#### Low:
* Stereo separation: 100% merged
* Pre-gain: 5.0dB
* Curve shape: Expander
* Post-gain: 5.6dB
* Saturation threshold: 100% Saturation mode A
* Saturation ceiling: 5.4dB

#### Mid:
* Stereo separation: 38% separated
* Pre-gain: 6.4dB
* Curve shape: Soft knee
* Post-gain: 0dB
* Saturation threshold: No saturation
* Saturation ceiling: 0dB

#### High:
* Stereo separation: Original
* Pre-gain: 6.9dB
* Curve shape: Bigger expander
* Post-gain: 2.9dB
* Saturation threshold: 100% mode A
* Saturation ceiling: 0dB

#### Master:
* Stereo separation: Original
* Curve shape: Hard knee
* Pre/Post-gain: 0dB
* Saturation threshold: 20% mode A
* Saturation ceiling: 0db

### Preset B

![Soundgoodizer preset B](/assets/img/soundgoodB.png)

This preset uses the same bands as before, but no compression on any of them! So this preset uses no compression curves or pre-gain on any of the LMH bands. 

#### Bands:
* Low: 20-200Hz
* Mid: 200-3000Hz
* High: 3000Hz+

#### Low:
* Stereo separation: 56% merged
* Post-gain: 8.4dB
* Saturation threshold: 100% Saturation mode A
* Saturation ceiling: 0dB

#### Mid:
* Stereo separation: 23% separated
* Post-gain: 10.4dB
* Saturation threshold: 24% mode A
* Saturation ceiling: 7.2dB

#### High:
* Stereo separation: Original
* Post-gain: 9.2dB
* Saturation threshold: 100% Saturation type A
* Saturation ceiling: 10.9dB

#### Master:
* Stereo separation: Original
* Curve shape: Soft knee
* Pre/Post-gain: 0dB
* Saturation threshold: 30% type A
* Saturation ceiling: 0db

### Preset C

![Soundgoodizer preset C](/assets/img/soundgoodC.png)

These settings seem much more mild than the previous presets. I think this preset is meant to be used on inserts.

#### Bands:
* Low: 20-200Hz
* Mid: 200-1906Hz
* High: 1906Hz+

#### Low:
* Stereo separation: 75% merged
* Pre-gain: 8.5dB
* Curve shape: Slight expander
* Post-gain: 1.5dB
* Saturation threshold: 100% Saturation type A
* Saturation ceiling: 2.2dB

#### Mid:
* Stereo separation: 35% separated
* Pre-gain: 12.7dB
* Curve shape: Soft knee
* Post-gain: 2.8dB
* Saturation threshold: No saturation
* Saturation ceiling: 0dB

#### High:
* Stereo separation: Original
* Pre-gain: 11.3dB
* Curve shape: Slight expander
* Post-gain: 2.9dB
* Saturation threshold: 100% Saturation type A
* Saturation ceiling: 0dB

#### Master:
* Stereo separation: Original
* Pre/Post-gain: 0dB
* Curve shape: Soft knee
* Saturation threshold: No saturation
* Saturation ceiling: 0db

### Preset D

![Soundgoodizer preset D](/assets/img/soundgoodD.png)

I already had a pretty good idea how this preset worked! It appears to be a 1 band maximizer like you would get from something like TLS Maximizer. I actually really like this preset for when I want to bring an insert (or the master) up without changing its character. This is by far the simplest of the four -- Image-Line appears to have arranged them by how hard they are to figure out.

#### Bands:
* Low: Off!
* Mid: 20Hz+
* High: Off!

#### Mid:
* Stereo separation: Original
* Pre-gain: 14.1dB
* Curve shape: Soft knee
* Post-gain: 0dB
* Saturation threshold: No saturation
* Saturation ceiling: 0dB

#### Master:
* Stereo separation: Original
* Curve shape: Limiter
* Pre/Post-gain: 0dB

## Conclusion
So there you have it! That is all four of the Soundgoodizer presets and how they work in the context of Maximus, though a few things aren't clear. For example, what is saturation type B and why is it never used? And more importantly, is there another plugin that does all of this stuff? I would think so, but testing a bunch of them is a little beyond my abilities at the moment. Anyway, I hope this post was helpful to Luney and the other people on Discord. If not, well at least I learned a lot while writing it ❤️

~Jessica
