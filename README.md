# Simple Mixer
Simple Mixer is a real-time and video mixing tool built entirely in TouchDesigner. It's currently tested and working in 099 stable build 26750. It should also work in the latest experimental build too.

[Watch the explanation video](https://www.youtube.com/watch?v=P8iLnwoWyAI)

[Watch the Post FX update explanation video](https://youtu.be/DhKZlpO24m4)

##### Update

SimpleMixer is no longer in development for build 26750. I'm waiting for the next experimental before adding new features as I imagine it'll be a whole new can of worms. I will be bugfixing this version and keeping up to date with official builds bugfix wise so let me know if there's anything needs fixed.


##### How It Works

Simple Mixer uses four banks at the top left of the screen which can have clips and tox files loaded into them. They can then be mixed between using the sliders and the compositing mode can be set.

Toxs are shown in the panel on the bottom left. These can be loaded by placing the tox file into the Assets/Tox directory.

For a tox to be compatible with Simple Mixer at the bare minimum it must have a TOP operator named 'out1' and another named 'thumb' in order to function. If your tox file is a container or has custom parameters these parameters will be exposed on the bottom right of the display when the tox is loaded into a bank and that bank is selected in the Current Visuals tab. If you want to set your tox files to the correct resolution then you can use the expressions op.output.par.w and op.output.par.h. To hook audio up to your component it's recommended to expose those parameters via custom parameters and then hook them up via the interface.

For audio analysis the system uses the audioanalysis component created by Greg Hermanovic. This has three different spectrum tabs you can select between and options for analysing particular frequencies. The CHOP itself is exposed ready to be hooked up to custom parameters directly in the interface.

At the very top of the screen is a tab to switch into mapping mode. Currently this is the standard TouchDesigner stoner however it will likely soon be replaced by a Resolume style poly drawing and warping system. You can also choose an output monitor and toggle the output on and off.

##### Changelog

###### 1.0.0

Bug Fixes
- Sliders reverting to 0 should be fixed
- Right clicking on a bank now reverts to the original functionality of setting that bank as the active parameter window.

###### 0.9.8

New Features
- Upgraded the TOX preview pane on the bottom right hand side to show Base COMPs as well as panels.
- The TOX selector grid is now adaptable in size to avoid scrollbars and make everything quickly draggable. (Thanks Dith_Id for that one)

###### 0.9.7

Bug Fixes
- The drag drop bug workaround broke PostFX dragging. You can now drag to Post FX slots again but right clicking is disabled as drag drop is fixed. SimpleMixer now only works in 25850 ONLY.
- Menus now have scrollbars so they don't go off the screen if they are too large.

###### 0.9.3  - BETA

Bug Fixes
- Drag Drop can now be avoided by selecting the TOX/Movie you wish to assign and right clicking the bank you want to assign it to. For PostFX you can simply select a bank and then left click the Post Effect you want to apply to it.
- Movie thumbnails should load properly now (seriousssslllyyy)
- UI error fixes when there are no secondary monitors present.
- Clear All Mappings button in settings now actually clears all mappings rather than just erroring.

Things To Note
- There seems to be an issue with menus loading slowly in some scenarios. This will be addressed in the next version.

###### 0.9.0 - BETA

New Features
- Gal is gone! We now have a completely new UI system that is both scaleable and MIDI/OSC/Key/UDP/Artnet Mappable.
- The new settings tab allows you to specify which inputs you are using and customize the highlight colour.
- Remove mappings in Settings by clicking the "Clear All Mappings" button.
- Halfway to the 1.0.0 release in which I hope to rebuild the Parameter COMP into a fully mappable system. For now you can use the container setup to map things in.

Notes
- Would really love it if people could report issues as I imagine there will be quite a few with this build.

###### 0.5.0

New Features
- You can now change the levels and hue parameters directly on movie clips.

Bug Fixes
- Second pre-viz window was broken on last update. This should now be fixed. You can now properly drag the line between the two to resize them.
- Movie thumbnails should now load properly.

###### 0.4.8

New Features
- added in a second pre-viz window. You can now choose between the four visuals in the banks and output. To make the window on the left or right bigger drag the border between the two.
- Cube matrix now has a colour offset parameter.
- New cloth TOX.
- Upgraded to latest version of gal.
- Right clicking on a bank will now auto switch the Current Visuals parameter window to that particular bank.
- Clicking on the previz window whilst viewing a particular bank will now switch the Current Visuals parameter window to that particular bank.
- Save Button.

Bug Fixes
- fixed re-initialization issue on toxs.


###### 0.4.0

- New Post Effects. Feedback Effect and Tile Effect Added.
- New Box Matrix TOX.

###### 0.3.7

- Upgraded to TouchDesigner build 22800.
- BPM + - buttons for adjustment.
- Clicking the bpm indicator now sets the system timeline to frame 1.
- bpm_pulse channel added into audioanalysis component.
- Post Effects will now fade in and out rather than snapping.
- Post Effects now have opacity sliders. This allows preparing a post effect before sending it to the main output.

###### 0.3.6

- If there is no second monitor SimpleMixer will now use /simplemixer/container_outputs "Emulate Output Resolution" parameter.
- Externalised container_output.

###### 0.3.5

- Updated to Experimental 21670
- Always on top bug has been fixed in TouchDesigner so is re-enabled in SimpleMixer
- Tested on TouchScreen. All functionality is working but certain buttons could be bigger.

###### 0.3.4

- Updated to Experimental 21150
- Opening the Post FX browser auto-switches the effect editor to Post FX Mode and vice versa.
- Dropping a Post Effect onto a TOX bank will no longer load it into the bank by mistake.
- Dropping a TOX onto a Post FX slot will no longer break the system.
- Removed random "hi" print from base_mix