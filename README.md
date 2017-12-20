## The Video Editor's Render Script for Blender

**Universal Blender Script:**
(This universal script should work for every version of blender 2.7.0 and up.)

Please right click and "save as" script here: 
https://github.com/mikeycal/the-video-editors-render-script-for-blender/raw/master/video_editors_render_script.py

# NOTICE (GIF rendering issue):
FFmpeg **3.3.4 and 3.4.0** have a bug that causes the program to hang during the GIF palettegen process. Fortunatly, developers have fixed the problem in **3.4.1**.   

## Table of Contents:
- [Core Features](#core-features)
- [What you need](#what-you-need)
- [Watch the video Demo](https://www.youtube.com/watch?v=rgwP5L1bICk)
- [Microsoft Windows 10 Setup](#microsoft-windows-10-setup)
- [Apple OSX Setup](#apple-osx-setup-kernel-is-called-darwin)
- [GNU/Linux Setup](#gnulinux-setup)
- [Configuring the Script Settings on ALL Platforms](#configuring-the-script)
- [The story of how this script came to be](#the-story-of-how-this-script-came-to-be)
- [The feature that I want the most](#the-feature-that-i-want-the-most)
- [Side note](#side-note)
- [Support Me or Lend a Hand](#support-me-or-lend-a-hand) 

[![Send a Donation to Mikeycal](https://github.com/mikeycal/the-video-editors-render-script-for-blender/blob/master/imgs/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=2EU5ANN3XVLH4)

***

## Core Features:
1.  Perform non-3D renders in _HALF_ the time on multi-core CPUs.
     - Speed up render times for the following:
        - Videos
        - Image Sequences
        - Node Based effects using the following node groups:
           - Distort, Matte, Map, Vector, Filter, Converter, and Color
             - _Note: 3D [Render Layers] node must be omitted_

2.  Supports all Blender audio, video and image codecs.
3.  Use 8kb/s - 640kb/s compressed audio instead of Blender's 32kb/s - 384kb/s limit.
4.  Create animated GIFs with your Blender video project
     - Uses high quality palettegen, supports all dither methods and allows scaling   
5.  Fully cross platform 
     - Windows
     - OSX
     - GNU/Linux
     - Any platform that supports Bash Shell, FFmpeg and Blender.

6.  Uses Blender's render property settings by default, or set script override settings.
7.  Make videos that are streamable and will process faster on services like YouTube.
8.  Use the most current version of FFmpeg, or even use a custom build with libfdk_aac
9.  Double click rendering. The script creates a reusable, clickable, executable.
10. It's a well commented script, so you can easily review it and edit it without compiling.
11. Render on headless video rendering server by installing Linux, FFmpeg and Blender on a spare computer.
12. It's GPL licensed, so you can adapt it, improve it, and redistribute it.
13. Developed and maintained by [Blender Video Editing Series](https://www.youtube.com/playlist?list=PLjyuVPBuorqIhlqZtoIvnAVQ3x18sNev4) instructor, "Mikeycal." ;) 

***

## What you need:
- Windows requires cmd.exe (Command Prompt) or powershell.exe (PowerShell)
- OSX, GNU/Linux and other Operating Systems require Bash Shell access
- All Operating Systems require Blender 2.7+ and FFmpeg 3.2+
- CPU with, at least, 2 Logical Cores for render Speedup
- Source Code Editor with Syntax Highlighting to edit the Script

## Download a Source Code Editor that supports Python:
![Source Code Editor](https://github.com/mikeycal/the-video-editors-render-script-for-blender/blob/master/imgs/syntax_highlight.JPG)

At times you will need to edit this Python Script. So I would advise that you download a free Source Code editor for your platform of choice. Here are my recommendations (I use Gedit):
  - Windows: https://notepad-plus-plus.org/, https://atom.io/
  - OSX: https://atom.io/
  - GNU/Linux: https://atom.io/, https://wiki.gnome.org/Apps/Gedit, kate

## Tested and Working:
- Windows 10 (v1709)[Creators Update]
- OSX 10.11
- GNU/Linux (Ubuntu 16.04 LTS) (Arch Linux [tested 3/30/17])

## Untested, but should work:
- Windows Vista, 7, 8 and all older versions of Windows 10
- OSX 10.9+ 
- Any modern GNU/Linux distribution supporting Bash Shell, FFmpeg 3.2+ and Blender 2.7+
- Any OS that has access to Bash Shell, FFmpeg 3.2+ and Blender 2.7+
- Windows XP should work, although, Blender support ended after version 2.76
- OSX 10.6 to 10.8 should work when using http://www.ffmpegmac.net/ build. )

## Microsoft Windows 10 Setup

### 32-BIT or 64-BIT Windows ? (3 Steps)
![System Type](https://github.com/mikeycal/the-video-editors-render-script-for-blender/blob/master/imgs/systemtype.JPG)
1.  On Windows 10, Click 'Start Menu.'
2. Type: About Your PC (press enter). 
3. See what it says next to 'System Type'. If "System Type" says '64-bit operating system', then your computer should use the 64-bit version of ffmpeg, otherwise use 32-bit version of ffmpeg

### Setup FFmpeg (6 Steps)
![get ffmpeg for windows](https://github.com/mikeycal/the-video-editors-render-script-for-blender/blob/master/imgs/ffmpeg_win.jpg)
1. Download the latest build of ffmpeg for Windows at the following URL: https://ffmpeg.zeranoe.com/builds/ That URL is the Official URL recommended by the official website: https://ffmpeg.org/download.html#build-windows 
2. Get the Static 'Release' (3.2.4 or higher), for your Architecture
3. Unzip the ffmpeg-version-date-static.zip file by right clicking on it and selecting 'Extract All...' 
4. Extract All to C:\ ( The root directory for Windows )
5. Change the folder's name to C:\ffmpeg\ [ This is scripts default location for FFmpeg]
6. FFmpeg is now installed and will work with this script

### Blender Setup (Assumes default install path of .msi installer)
![Blender Windows](https://github.com/mikeycal/the-video-editors-render-script-for-blender/blob/master/imgs/blender_win.JPG)

This script assumes that blender is saved to the following default path: "C:\Program Files\Blender Foundation\Blender\blender.exe" this is the default path when you install blender using the *.msi* Installer. You can get that Installer at the following link: https://www.blender.org/download/ If you choose to install Blender in a different place, please set a custom path in this script.

### Running the Script (9 Steps)

1. If necessary, use your source code editor to set the path to FFmpeg and Blender. You need to go to line 97 and 98 in video_editors_render_script.py

 By default Line 97 and 98 are set to the following paths:
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
       Windows: "C:\Program Files\Blender Foundation\Blender\blender.exe"
                 C:\ffmpeg\bin\ffmpeg.exe
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

2. Put the script in any folder and "SAVE AS..." your custom blend file as "1.blend" to the same folder. 

3. Open cmd.exe and go to the directory with your files.

4. Run this script from the same folder using cmd.exe:
(use the quotation marks for paths with spaces)
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
`"C:\Program Files\Blender Foundation\Blender\blender.exe" -b 1.blend -P video_editors_render_script.py`
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
5. The script will create a clickable executable, in the same directory, that you can use for all future renders.
 (Windows_Click_to_Render.bat)

6. While the script is running, You can see logical CPU core usage and RAM usage in your Windows 'Performance Monitor' (Press [Windows Key] + R) Type: **perfmon /res**

7. After script finishes, you will see a Render time in the Command Prompt. See how much it improved your render time by looking at the final script time.

8. Improve the look of CMD.exe by right clicking on the "Title Bar" of CMD.exe and changing the "Defaults" to the recommended settings:

![CMD.exe Fonts](https://github.com/mikeycal/the-video-editors-render-script-for-blender/blob/master/imgs/cmdfont-size.JPG)

9. [Goto the "Configuring the Script" Section](#configuring-the-script)

***

## Apple OSX Setup (Kernel is called Darwin)

### Setup FFmpeg (2 Steps)
![ffmpeg osx](https://github.com/mikeycal/the-video-editors-render-script-for-blender/blob/master/imgs/ffmpeg_osx.JPG)

1. Go to https://evermeet.cx/ffmpeg/ and download the Static FFmpeg build, on the right, called ffmpeg-3.2.4.dmg (or higer version). Make sure that you download the DMG and not the .7z version. (Note: https://evermeet.cx/ffmpeg is the
official link that is pointed to from ffmpeg.org: http://ffmpeg.org/download.html#build-mac) (Alteratively, there are FFmpeg builds for OSX 10.6 - 10.8 here: http://www.ffmpegmac.net/) 
2. Open ffmpeg-3.2.4.dmg and place the "ffmpeg" program in the OSX "/Applications/" folder.

### Setup Blender (4 Steps)

1) Go to https://www.blender.org/download/ and download the OSX zip file of Blender. 
2) Create a folder in the OSX "Applications" folder called "Blender" (with a capital B)
3) Place all Blender files in the "/Application/Blender" folder. 
4) This script is already setup to look for Blender in this location.

### Running the Script (7 Steps)

1. If necessary, use your source code editor to set the path to FFmpeg and Blender. You need to go to line 103 and 104 in video_editors_render_script.py

 By default Line 103 and 104 are set to the following paths:
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
          OSX: /Applications/Blender/blender.app/Contents/MacOS/blender
               /Applications/ffmpeg
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

2. Put the script in any folder and "SAVE AS..." your custom blend file as "1.blend" to the same folder. 

3. Open the "TERMINAL" program, from Spotlight, and change to the directory with the files.

4. Run this Script from the same folder using Terminal: 
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
`/Applications/Blender/blender.app/Contents/MacOS/blender -b 1.blend -P video_editors_render_script.py`
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
5. The script will create a clickable executable, in the same directory, that you can use for all future renders. (OSX_Click_to_Render.command)

6. Check CPU and RAM usage by typing "top" into the terminal

7. [Goto the "Configuring the Script" Section](#configuring-the-script)

***

## GNU/Linux Setup
### Setup Blender and FFmpeg from Repository (3 Steps)
1. On Debian/Ubuntu based Distros (DEB):

`apt-get install blender ffmpeg`

2. On Arch Linux 

`pacman -S blender ffmpeg`

3. On Redhat/Fedora/CentOS (RPM):

`dnf install blender ffmpeg`
or 
`yum install blender ffmpeg`

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Alternatively:
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
### Setup latest FFmpeg from website  (2 Steps)
1. Download ffmpeg static build from https://www.johnvansickle.com/ffmpeg/ (This is the URL that is pointed to on http://ffmpeg.org/download.html#build-linux 

![ffmpeg Linux](https://github.com/mikeycal/the-video-editors-render-script-for-blender/blob/master/imgs/linux_ffmpeg.JPG)

2. Unzip archive with `tar -xvf ffmpeg-release-64bit-static.tar.xz`

### Setup latest Blender from website (2 Steps)
1. Download Blender from https://www.blender.org/download/, just make sure that you add the correct paths to line 109 and 110 of the script.

2. Unzip with `tar -jxvf blender-2.78c-linux-glibc219-x86_64.tar.bz2`

### Running the Script (9 Steps)

1. If necessary, use your source code editor to set the path to FFmpeg and Blender. You need to go to line 109 and 110 in video_editors_render_script.py

 By default Line 109 and 110 are set to the following paths:
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
     GNU/Linux: (Install from repository, and call programs directly):
                blender
                ffmpeg
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
2. Linux and other *nix platforms can set a specific terminal program to run the script from. Some popular options include the following:
    -  `"gnome-terminal -e"`, `"konsole -e"`, `"xterm -e"`, `"guake -e"`, `"terminator -e"`
        - If no terminal is specified on Linux or *nix systems, the "click_me" fearture (line 112) will run, hidden, in the background.

3. Put the Script in any folder and "SAVE AS..." your custom blend file as "1.blend" to the same folder. 

4. Open Terminal window and go to the directory where your files are located.

5. Run this script from the same folder using the Terminal:
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
`blender -b 1.blend -P video_editors_render_script.py`
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
6. The script will create a clickable executable, in the same directory, that you can use for all future renders. (Linux_Click_to_Render.sh)

7. It's important to note that often linux environments are setup to prohibit executing .sh scripts by clicking. But you can usually turn that feature on in the preferences of your favorite linux file manager. On my linux setup, I set clicking an .sh file to PROMPT me. The prompt dialog asks if I would like to open in an editor or run the script. This is the option I recommend using. 

8. Check CPU and RAM usage by typing "top" into the terminal

9. [Goto the "Configuring the Script" Section](#configuring-the-script)

***

### Configuring the Script

1. **Blender and FFmpeg PATH settings**
     - Blender and FFmpeg can be called directly if the programs are in your main PATH. Otherwise, you must enter the absolute path to each program in the Script Settings for your Operating System. Window 10 and OSX are set to use Absolute paths by default, while Linux is set to call both programs directly, since most people install from a repository that puts the programs in the main path automatically.(Absolute path settings will always work for every platform - so it is preferred.)

- - - - - - - - - - - - -
**Where to Set Program Paths:**

**Windows:** GOTO line 98, 99 

**OSX:** GOTO line 104, 105 

**Linux:** GOTO line 110, 111

**Other:** GOTO line 117, 118
- - - - - - - - - - - - -

2. **Where should I place this Script?**
     - This script can be placed in any folder of your choosing. I would recommend that you place it in your "Videos" folder in your "User" or "Home" directory.

3. **How does the script use my .blend File?**
     - This script will look in the same folder for a .blend file named, **1.blend** .
     - In order to guarantee that your projects media-file-paths work, I would recommend opening your blender (.blend) project by going to "Save As...", and Saving as **1.blend** to the Script's directory. Don't simply move your .blend file manually to the script folder because the blend file paths may not work if they are using relative paths. 

4. **How do I render with this script?**

The first time that you render with this script, you will need to run the following Terminal Commands:

- `cd c:\Users\mikeycal\Video` (Change to the directory with this script and 1.blend file.)

- `"c:\PATH\ TO\ blender" -b 1.blend -P video_editors_render_script.py` (Use Quotes with Spaces)

- - - - - - - 
This script will automatically generate a "clickable" render file that you can use for all future renders. After you have run the script 1 time, you can move the "Click_to_Render" file and "video_editors_render_script.py" file to any folder you like, it will render any project named 1.blend from any folder you place those 2 files in.
 
**Windows:** `Windows_Click_to_Render.bat`

**OSX:** `OSX_Click_to_Render.command`

**Linux:** `Linux_Click_to_Render.sh`

**Other:** `Click_to_Render.sh`
- - - - - - - 

5. **How do I change the number of CPU cores that the Script can use?**
     - To be clear, this process doesn't actually let you directly control the CPU Cores. It will allow you to control how many Blender instances you are running simultaneously. It just turns out that each Blender instance tends to utilize a single core of your CPU. By default, the script will create a Blender instance for each CPU core it detects, but you can virtually reserve cores using the "reserved_cpu_logical_cores" setting on line 141. A setting of 0 means reserve nothing, 1 means reserve 1 core. So on and so forth...

6. **What are the RAM requirements? (1.6GB - 3GB per Core)**
     - The more RAM you have the better. From my test, on Blender 2.79, it appears that each Logical Core creates an instance of Blender that requires approximately 1.6GB of RAM per blender instance. My results are based on rendering a 3840 x 4320 (4K, Quad-Full-HD x 2), video provided here http://bbb3d.renderfarming.net/download.html, on a 4 core Intel i5-3570K with 16GB RAM. If each instance does not have enough RAM, you will notice that the render will slow down to a crawl. So make sure that you set "reserved_cpu_logical_cores" to a number that keeps you under the RAM requirement. The more cpu cores you reserve, the less RAM is used. I believe that the highest RAM useage I have ever seen, per core, was about 3GB. I would test your system with different "reserved_cpu_logical_cores" settings and see what setting works best on your system. 
     
7. **Can I deactivate multi-core rendering and use this script for rendering 3D projects?**
     - Yes, you can set the "force_one_instance_render" setting to "True" (line 142) and use this script to render anything you created with blender. It is equivalent to rendering the "standard way", only without the interface. It will allow you to access the additional FFmpeg features of this script with any blender project.

8. **How do I alter the MUX settings to add custom FFmpeg arguments to the final video?**
     - If you choose, you can alter the FFmpeg mux settings on line 163 and 164. By default this script uses these lines to add stuff like "FastStart" to your final video. 

9. **How do I use FFmpeg's range of bitrate settings instead of Blender's?**
     - set "use_ffmpeg_audio_bitrates" setting to "True" on line 172 and enter a desired bitrate setting where it says, "custom_audio_bitrate" on line 175. This script will automatically detect if your bitrate is out of range, for you audio codec, and set it to the nearest in-range setting. By default, Blender locks your audio bitrate to 32kb/s - 384kb/s. But when you use FFmpeg bitrate settings, you can set the bitrate to 8kb/s - 640kb/s. The audio is extracted from the Blender project as lossless PCM audio before conversion. 

10. **How do I render an Animated GIF?**
     - Go to Line 184 and set "render_gif" setting to "True". You can set the other gif settings in the same section. It's important to note that you must render using a Video Format (mp4, avi, mov, ...) in order to get GIF conversion to work. 
If you would like to see how different GIF settings alter your video, refer to the source material I used to write this feature: http://blog.pkh.me/p/21-high-quality-gif-with-ffmpeg.html

 - Settings that you can alter:

   - **gif_framerate**: if set to "" (empty), it will use the Blender Frame Rate ("15" is the default)
   - **stats_mode**: ["full" or "diff"] ("full" is default)
   - **custom_gif_scale_x_value**: If you set this to "" (empty), it will default to blender's render settings resolution. Y value will be proportionate. 
   - **dither_options**: ("none" is default)  
      - _Dither Options_:
         - "none"
         - "bayer:bayer_scale=1" 
         - "bayer:bayer_scale=2" 
         - "bayer:bayer_scale=3"
         - "floyd_steinberg" 
         - "sierra2"
         - "sierra2_4a" 
         - "heckbert"
   - **the_scaler**: ("lanczos" is default)  
      - _Scaler Options_:
         - "lanczos"
         - "bicubic" 
         - "bilinear" 
         - see more options: https://ffmpeg.org/ffmpeg-scaler.html
         
I rendered the same video using different _dither_ and _stat_mode_ settings. Here are the file size results to compare. (See image quality difference [here](http://blog.pkh.me/p/21-high-quality-gif-with-ffmpeg.html). )

![gif file size](https://github.com/mikeycal/the-video-editors-render-script-for-blender/blob/master/imgs/comparegif.JPG)
                                                                              
11. **How do I set Automatic .blend file settings?**
     - On line 203 you can add settings that you want to be used as overrides. These settings will override anything that you have set in the _Blender Render Properties_ window of blender. It's important to note that `scene.render.ffmpeg.audio_codec = 'NONE'\n` must be included. It turns off the audio for your project. Audio is rendered separately with this script, so it must be turned off when the video is rendering. Leaving audio on will simply slow down the render.

- - - - - - - 
**Some common override settings you can use include the following:**

(Python requires 4 spaces before scene.render.*)

`"    scene.render.resolution_x = 800\n"`

`"    scene.render.resolution_y = 600\n"`

`"    scene.render.resolution_percentage = 100\n"`

`"    scene.render.image_settings.file_format = XVID\n"`

`"    scene.render.ffmpeg.format = MPEG4\n"`

`"    scene.render.ffmpeg.codec = H264\n"`

`"    scene.render.ffmpeg.video_bitrate = 8000\n"`

`"    scene.render.ffmpeg.gopsize = 18\n"`

`"    scene.render.ffmpeg.use_lossless_output = False\n"`

`"    scene.render.ffmpeg.minrate = 0\n"`    

`"    scene.render.ffmpeg.maxrate = 9000\n"`

`"    scene.render.ffmpeg.muxrate = 10080000\n"`  

`"    scene.render.ffmpeg.packetsize = 2048\n"` 

`"    scene.render.ffmpeg.buffersize = 1792\n"` 

`"    scene.render.fps = 24\n"` 

`"    scene.render.fps_base = 1.001\n"`


Note blender frame rate is determined by the following formula:

 round(scene.render.fps / scene.render.fps_base,2)     [23.98]
- - - - - - - 

***

### The story of how this script came to be 
In February of 2017, I came across a post on stackexchage.com (http://blender.stackexchange.com/questions/7738/how-to-make-vse-render-faster) A user named "Isti115" pointed out that a person could speed up video rendering by using the Blender background instance feature in conjunction with FFmpeg's concatenation feature. 

I soon decided that I would create a cross platform python script that would use the built-in version of python, included with Blender, to automate the multicore render process. I wanted a script that would work everywhere, and was easy to read, edit, and adapt. By March 27, 2017, after weeks of cross platform coding and testing, I had finished the first Release Candidate of the Python Script.

In the process of writing this script, I made some discoveries about Blender. I learned that, not only could you speed up the rendering of video processing, but you could equally speed up image processing done with the compositor. The only thing that Blender couldn't do is speed up video renders that include keyframed 3D objects. Basically, keyframes applied to 3d objects lose sync with this method of rendering. But, image processing, like removing a Green Screen from footage, works well.

As soon as my initial programming goals were achieved, I decided to see if there were other FFmpeg features that I could automate. I came across ubitux's website (http://blog.pkh.me/p/21-high-quality-gif-with-ffmpeg.html) where he described how to properly create animated gifs with FFmpeg. So that feature got added to this script as an option.

This Script represents my passion to continue to help Blender to become a more usable video editing program. In addition to my [Blender Video Editing Series](https://www.youtube.com/playlist?list=PLjyuVPBuorqIhlqZtoIvnAVQ3x18sNev4), I invest a lot of time into making Blender easier to use because I like that it is Open Source, Cross Platform and has an amazing community dedicated to developing new features that enable us all to be more creative. 

***

### The feature that I want the most

If anyone can figure out how to add an option that would show render progress in the terminal window, that works with Windows Prompt and Bash shell, that feature would be greatly appreciated. It would be nice if it could be turned on or off since such a feature may cause a slight render slow down. It's important to note that this Python Script is my first time using Python. So I'm still learning and any helpful tips on using Python would also be appreciated. :)

***

### Side note:
Isti115 has developed his own program that also utilizes the multi-core process that is written in C# and even has a GUI. You can check it out here: https://github.com/Isti115/BlenderRenderController. I actually started developing my script at nearly the same time he was working on his program. As of version 1 of this script, our projects share no code. Not because I wouldn't want to, but because I had already developed the majority of my code by the time I learned he had made his code available. I feel that this is actually a good thing because it means we both attacked a similar problem in our own unique ways. This should make newer versions of our projects even better. Anyway, send your love and support Isti115's way. We need to support all developers that are making Blender better. :)

***

 ### Support Me or Lend a Hand
 
 I consider this script a work in progress. I hope to add features as needed.  It's important to note that this Python Script is my first time using Python. So I'm still learning and any helpful tips on using Python would also be appreciated. If you have any suggestions on features, find bugs, or if you have added some feature that you think I should include, send me an email at mikeycaldotcom@yahoo.com . If you want to help me out, you can [send me a Paypal donation](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=2EU5ANN3XVLH4) at my Yahoo address or help me make the code better. In addition, visit my website at http://Mikeycal.com and see what I'm up to lately. I am dedicated to providing cross platform resources and instructional videos free of charge. Checkout my Blender Video Editing Series at the following link:
 https://www.youtube.com/playlist?list=PLjyuVPBuorqIhlqZtoIvnAVQ3x18sNev4

[![Send a Donation to Mikeycal](https://github.com/mikeycal/the-video-editors-render-script-for-blender/blob/master/imgs/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=2EU5ANN3XVLH4)
