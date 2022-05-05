# Factorio Movie Maker

This project encodes a 178x100 3-bit color movie in a [Factorio](http://www.factorio.com) map, now updated for Factorio version 1.1.57.
The original script for generating the movies has been updated and preserved, as well as a new method using blueprint strings via my python module [factorio-draftsman].

## Contents:

* `movie.zip` is the save file, compatible with Factorio 0.15.
* `movie-updated.zip` is the updated save file, compatible with Factorio version 1.1.
* `build.lua` is the original script with some modifications for migrations
* `build.py` is the alternative method to generate blueprint strings instead of console commands

Some parts of the original design have been changed due to migrations from the original version. Specifically, the `raw-wood` signal was changed to `artillery-wagon`.

1. Install [FFmpeg](http://www.ffmpeg.org/download.html) and [Lua](http://lua-users.org/wiki/LuaBinaries) if you don't already have them.

2. Obtain a source picture or video.  It must have a 16:9 aspect ratio or it will be stretched.  In this example it is called source.mp4.

3.     cd factorio-movie-maker
        ffmpeg -i source.mp4 -i palette.bmp -filter_complex "fps=20,scale=178:100:flags=lanczos,paletteuse" -pix_fmt bgr24 images/%04d.bmp
        lua build.lua

4. Start Factorio and load movie.zip.

5. Open each file in the script directory, select all, and copy/paste it into the Factorio console.

6. Open the constant combinator at position {-183,-1}.  Change the red signal to the frame count of your movie.

