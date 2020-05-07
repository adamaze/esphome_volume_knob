# Physical Volume Control for Home Assistant
![knob](https://github.com/adamaze/esphome_volume_knob/blob/master/images/knob.jpg)

I wanted to start this project for a long time, but I'm the type of person that really likes to follow a guide when im doing something in new territory, and as I never found one... I kept putting it off. I eventually came across a guide about volume control using straight up arduino and mqtt, and then later found one about making a light dimmer knob using a potentiometer, but none of the ones I ever found met my needs. Just a note: Limiting the knob to only register 0-100 and feeding the value directly to media_player.volume_set seems like a good idea at first, but then you realize that it will get out of sync as soon as you change the volume through HA, so that option was out.

There are likely better ways to do everything that I did, but I'm happy that I actually got it all to work

I currently have 5 of these around the house controlling volume for different sets of speakers, and they have been working pretty well!

## Goals
Here were the goals I gave myself for a "complete" project:  
* Simple to set up
* Use free spinning rotary encoder (that never has to be in sync with HA)
* Handle different button presses (single click/double click/long press)
* Fit nicely into a 3D printed package (instead of a mess of wires and circuit boards like most of my projects)

## Functionality
Twisting the knob clockwise will call `media_player.volume_up`  
Twisting counter-clockwise will call `media_player.volume_down`  
Single click will call `media_player.media_play_pause`  
Double click will call `media_player.media_next_track`  
Long press will call a script to start playing a specific Spotify playlist.

## Hardware
FYI, these are amazon afiliate links.  
[Rotary encoder with push button](https://amzn.to/2xGrBkF) box of 5 ~$2   each  
[d1 mini](https://amzn.to/3fn6O6K) bag of 5 ~$3.5 each  
Access to 3D printer (or of course, smush it into whatever box you have laying around :)  


## Setup
1. [Home Assistant](https://www.home-assistant.io/hassio/installation/)  
2. [ESPHome](https://esphome.io/guides/getting_started_hassio.html)  
  * Make sure to use the "Secrets Editor" found under the three dots at the top right hand corner of the ESPHome dashboard to set up your secrets - see example [secrets.yaml](https://github.com/adamaze/esphome_volume_knob/blob/master/secrets.yaml)  
  * use example [knob.yaml](https://github.com/adamaze/esphome_volume_knob/blob/master/knob.yaml) and replace `media_player.spotify` with your media_player for play/pause control, `media_player.kitchen_speakers` with your media_player for volume control, and `kitchen` with the name of the room the knob will be in.

## Wiring  
![wiring](https://github.com/adamaze/esphome_volume_knob/blob/master/images/wiring.jpg)

Notice that some of the parts of the knob had to be bent so that it would fit flush with the case, and make room underneath. Knob on right is final.  
![knob_bending](https://github.com/adamaze/esphome_volume_knob/blob/master/images/knob_bending.jpg)

## Case
I went through many iterations, and I'm brand new to 3D printing, so dont expect much from the case, but I'm pretty happy with it. Some of my spare usb cables are weirdly large, which is why the opening for the usb port is so large.  
I suppose it may depend on the printer, but the tolerances were such that the top and bottom just kinda snapped together tightly, so there was no need for a close/lock mechanism. These base was printed using supports for the USB port section, although it likely wasnt needed, as I realized later that the gap is about the same width as the window on Benchy, and that prints just fine with no supports :) I printed four of these out of Prusament Galaxy Black PLA, and the original is orange Prusament PETG.
I ended up sticking each one in place with a command strip cut to size for a nice steady solid twist feel.
![case_top](https://github.com/adamaze/esphome_volume_knob/blob/master/images/case_top.jpg)
![case_bottom](https://github.com/adamaze/esphome_volume_knob/blob/master/images/case_bottom.jpg)
View the STL files right here inside github!:  
[knob_case_top.stl](https://github.com/adamaze/esphome_volume_knob/blob/master/knob_case_top.stl)  
[knob_case_bottom.stl](https://github.com/adamaze/esphome_volume_knob/blob/master/knob_case_bottom.stl)  

## Known Issues
1. If you spin the knob super fast, it may get locked at the value at either end and not update again until you spin the other way.  
2. You have to spin the knob two clicks for it to update.
