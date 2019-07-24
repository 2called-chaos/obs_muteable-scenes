# OBS - muteable scenes

This is a little Javascript that allows you to have all audio devices muted automatically by having a specially named source in your scene.

**Note: This script requires you to have the OBS plugin [obs-websocket](https://github.com/Palakis/obs-websocket/releases) (with at least version 4.6) installed** 

### Installation

1. [Download the zip](https://github.com/2called-chaos/obs_muteable-scenes/archive/master.zip) and extract it somewhere "permanent"
2. Add the index.html as a browser source to one of your scenes. You probably want to set the height & width to 1/1 as you are actually able to open this in your browser and have totally (not) fancy volume controls. Just make sure to not check "Shutdown source when not visible".
3. If you choose to set a password for obs-websocket (which you should) you will get a prompt. You will only have to enter the password once (it's being stored in local storage), just be aware it will be visible while you type it in.

### Usage

Create a source in the scene you want to be muted. It doesn't matter what it is (I suggest text) it just has to be named either "mute_scene" or "muted_scene" and you are good to go.

From now on, every time you switch to this scene, all audio outputs will be muted. It will remember the mute states before doing that and will restore those settings when you switch to a different scene. It will also remember the states across OBS restarts (by using local storage) so you are fine to quit OBS while being on a muted scene (when you restart it still knows your old settings when you switch to an unmuted scene).

### You want some automation?

If you look at the source of this script, it's pretty easy to extend functionality if you want to. Just look at all the [possibilities](https://github.com/Palakis/obs-websocket/blob/4.x-current/docs/generated/protocol.md)

### Clarifications

* [LocalStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage): permanent storage accessible to JS
* Audio Outputs: This script will mute all sources that have type "wasapi_input_capture" or "wasapi_output_capture". If there is a problem with that in your configuration let me know and create an issue.
