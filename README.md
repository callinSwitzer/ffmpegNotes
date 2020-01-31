# ffmpegNotes
notes about ffmpeg


## converting mov to mp4, and scaling
```ffmpeg -i 01_rotatedKalmia.mov -qscale 0 -vf “scale=trunc(iw/2):trunc(ih/2)” -c:v libx264 -pix_fmt yuv420p -y output.mp4```

## converting a directory of png images to a video
- files are saved with leading zeros
- ```-r``` is output frame rate
- first image is 0001.png
- this allows the file to be played on many platforms: -c:v libx264 -pix_fmt yuv420p
- this specifies the scaling algorithm, but doesn’t do any actual scaling: -vf “scale=trunc(iw/2)2:trunc(ih/2)2″

```ffmpeg -start_number 1 -r 29 -i %04d.png -vf “scale=trunc(iw/2)2:trunc(ih/2)2″ -c:v libx264 -pix_fmt yuv420p -y output.mp4```

## speed up video
```ffmpeg -i beeStringPulling.MP4 -filter:v “setpts=0.5*PTS” output.mp4```

## trim video
```ffmpeg -i output.mp4 -ss 00:00:00 -t 00:00:07 -async 1 cut_ballRoll.mp4```
