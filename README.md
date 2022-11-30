# Project NightWatch

The NightWatch project is an open source sonar module that thinks is a radar module.

Why?

Because radar is expensive and hard, but ultrasonics are cheap and (relatively) easy. For most hobby applications, sonar can do everything we need, and it can be cheaper. The goal isn't to replace radar across the board, only in the low(er) cost market.

Also I wanted a signal processing platform where I could work with real data pretty easily. Sonar seemed fun.

# Features
There are a few features I definitely wanted to include:

- Multiple echo detection
  - I want the ability to detect and process multiple echos from a single emitted pulse. This is something that's impossible with the ubiquitous HC-SR04.
- Long range
  - Processing multiple return echos is kind of irrelevant for if there is only one object within range, so I am aiming for about 60' (roughly 18m) of range, which is proving to be its own challenge on the analog electronics front.
- Adjustable power
  - Long range is great, but I might want/need to see up close too, so I want to be able to adjust the transmit power of the emitter.
- Pulse shaping
  - I want to be able to change the shape of the pulse based on what I'm trying to sense. Maybe I want a (relatively) low frequency pulse, maybe I want to chirp my pulse, etc. If I know the outgoing frequency/frequencies I can calculate doppler shift if I'm careful and clever, which will get me speed information.
- Sensor networking
  - I want to be able to use many sensors together, odds are that will be easiest with some kind of CAN bus, but if I want to coordinate readings, I'd like to be able to do that with extreme precision... So I'm including a trigger pin whose behavior can be configured to sequential reads or synchronous reads.

