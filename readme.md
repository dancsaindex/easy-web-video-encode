# Easy Web Video Encode

Easily encode nearly any video format into an MP4 and WEBM for browser streaming via 
a simple shell script and FFmpeg -- without installing FFmpeg!

## Motiviation

I wanted to host some videos for a private site, and I wanted them to last indefinitely.
Thus Youtube/Vimeo/etc were not really viable options. I found a great set or articles
discussing how to encode for [webm][webm] and [mp4][mp4] -- the two current required 
video formats to cover _most_ browsers. I do not currently include ogg. Combined with 
a bit of shell scripting, and you can easily turn any video that ffmpeg can read into
a streamable asset.

[webm]: https://www.virag.si/2012/01/webm-web-video-encoding-tutorial-with-ffmpeg-0-9/
[mp4]: https://www.virag.si/2012/01/web-video-encoding-tutorial-with-ffmpeg-0-9/

## Requirements

 * [Docker](https://www.docker.com/)
 * BASH

Yeah, no much. The vast majority of the work is done inside the docker container.

## Usage

```
./encode.sh path/to/video/file.ext
```

You'll see a lot of output and eventualy be left with two more file right next to
your original. You can then use this snippet in browsers to embed the video:

```html
<!-- Embed a video, 720p resolution; auto scaling width to fit space, up to full resolution -->
<video width="1280" height="720" controls style="width: 100%; max-width: 1280px; max-height: 720px">
  <source src="your-video-here.mp4" />
  <source src="your-video-here.webm" />
</video>
```

## Caveats

I really only made this for my specific purposes, so there are some caveats. The script:

 * won't produce nearly as many options as something like Youtube/Vimeo/etc can deliver
 * only outputs two formats (mp4/webm)
 * there is no flash fallback player
 * doesn't support multiple resolutions; hard coded to 720p at a relatively high bitrate
 * has no concept of an overlay JS library to spruce up the whole affair

Overall, if your userbase is limited and you can get away with it, this is basic enough
to work for you. 
