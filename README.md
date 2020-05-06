# Physical Volume Control for Home Assistant

I wanted to start this project for a long time, but I'm the type of person that really likes to follow a guide when im doing something in new territory, and as I never found one... I kept putting it off. I eventually came across a guide about volume control using straight up arduino and mqtt, and then later found one about making a light dimmer knob using a potentiometer, but neither of these really met my need. Just a note: Limiting the knob to only register 0-100 and feeding the value directly to media_player.volume_set seems like a good idea at first, but then you realize that it will get out of sync as soon as you change the volume through HA, so that option was out.

There are likely better ways to do everything that I did, but I'm happy that I actually got it all to work

## Goals
Here were the goals I gave myself for a "complete" project:  
* Simple to set up
* Use free spinning rotary encoder
* Handle different button presses (single click/double click/long press)
* Fit nicely into a 3D printed package (instead of a mess of wires and circuit boards like most of my projects)

## Functionality
Twisting the knob clockwise will call `media_player.volume_up`  
Twisting counter-clockwise will call `media_player.volume_down`  
Single click will call `media_player.media_play_pause`  
Double click will call `media_player.media_next_track`  
Long press will call a script to start playing a specific Spotify playlist.

## Hardware
Rotary encoder with push button  
d1 mini  
Access to 3D printer (or of course, smush it into whatever box you have laying around :)  
