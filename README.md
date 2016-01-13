# morse
`morse` is a python library for controlling [Wonder Workshop's](https://www.makewonder.com/)
[Dash and Dot](https://www.makewonder.com/?gclid=CPOO8bC8k8oCFdaRHwodPeMIZg) robots.

The robots are controlled with commands sent over Blutooth, specifically [GATT](https://developer.bluetooth.org/TechnologyOverview/Pages/GATT.aspx). Morse provides an high level abstraction of this command protocol. Exposing control of eye, neck, head and ear colors through python methods.

## Motivation
There exist smartphone apps which allow remote-controlling Dash and Dot, and even "writing programs" for them.
However, the programming functionality is limited to drag-and-drop style and does not allow interaction with
any industry programming languages.

That doesn't need to be the case - young kids can get started with the simple
drag-and-drop interface to get some exposure and instill interest, then graduate to a programming API interface in order
to create more complicated and complete implementations of their creative ideas.

`morse` provides that programming interface, in a language that is easy to pick up even for non-engineers: Python.

## Installation
This is only tested on Debian, though it should work on other Linux flavors. OSX and Windows are NOT supported.

Steps:

 * first clone this repo and `cd` into it
 * `apt-get install bluez`  # version 5+ is required by pygatt
 * `git clone https://github.com/peplin/pygatt`
 * `pip install -r requirements.pip`

## Completeness
Dash and Dot have many different commands. Morse implements only fraction there of:

 * LED Lights:
  * Ears
  * Top of Head
  * Neck / Eye backlight
  * Individual iris LEDs
  * Iris brightness
  * ~~tail light~~
 * Motion (Dash only)
  * Head pitch and Yaw
  * Move back and forth
  * Turn left and right
 * Sound
  * Playback of built in sounds
  * ~~Uploading new sounds~~
 * Sensor feedback
  * Microphone volume
  * Proximity Sensing
  * Head pitch / yaw
  * wheel rotation
  * ~~Dash sensing of Dot~~
  * ~~Sound direction~~
  * ~~Gyro~~
  * ~~Battery state~~
 * ~~Robot discovery~~
   * ~~feature discovery (Dash & Dot have different feature sets)~~


## Example
Run:

```
python -m morse/examples/clock.py C0:F0:84:3C:51:FA
```

where `C0:F0:84:3C:51:FA` should be the bluetooth address of your bot

```
$ cd morse
$ python
>>> from control import WonderControl
>>> bot = WonderControl("C0:F0:84:3C:51:FA")
>>> bot.say("hi")
>>> bot.move(100)
>>> bot.turn(45)
>>> bot.ear_color("red")
>>> bot.head_yaw(10)
>>> bot.eye(255)
>>> bot.eye(100)
```
