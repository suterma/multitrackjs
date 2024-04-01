# multitrackjs
An HTML5 multitrack player, using plain old audio and video elements.

It is

- working with arbitrary HTML5 media sources (including non-buffered sources)
- free and open source
- browser-based (HTML/Javascript/CSS)

# UNDER CONSTRUCTION
This repo is very much in development.

# Usage (proposal)

In your HTML page, you add multiple `<audio>` or `<video>` elements, each represeting a track (with typically with a left and right channel). The playback of the tracks is then controlled as ensemble.

:todo:


# How it works
Synchronized playback control is achieved using the various events available on [HTML5 media elements](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement). 

## No audio buffers
The modern [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API) is intentionally not used, although it's still possible to create subsequent audio graphs using the [MediaElementAudioSourceNode](https://developer.mozilla.org/en-US/docs/Web/API/MediaElementAudioSourceNode) with the controlled audio or video elements.

The buffered audio sources (with the [AudioBufferSourceNode](https://developer.mozilla.org/en-US/docs/Web/API/AudioBufferSourceNode)) are avoided to allow the use of arbitrary online or offline media sources, even when the sources are cross-origin with regard the set [CORS headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS).

# Alternatives

There are already many existing web-based multitrack players, but none tick all requirements from above:

- [Soundtrap](https://www.soundtrap.com) is commercial
- [Helios audio mixer](https://github.com/heliosdesign/helios-audio-mixer) has no synchronisation and seems very involved
- [Mixjs](https://github.com/kevincennis/Mix.js) needs a build step with precompiled set of resources 
- [Multitrack Player](https://dhulme.uk/multitrack-player/#/) by David Hulme requires local files
- [Waveform Playlist](https://naomiaro.github.io/waveform-playlist/) requires buffered sources

# Notes

- The [HTMLMediaElement: mediaGroup property](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/mediaGroup), which facilitated synchronous playback, has been [deprecated and removed with the Media Controller feature](https://github.com/w3c/html/issues/246).