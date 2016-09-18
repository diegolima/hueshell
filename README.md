# hueshell
##### A collection of Shellscripts to manage the Philips Hue

## What is it?
Hueshell is a way to control your Philips Hue bridge from the comfort of your terminal. No need to start up pesky user interfaces, memory hungry web browsers or, god forbid, monstrous Java Virtual Machines.

## How do I install it?
Just clone this repo. Or download the zip file and uncompress.
TODO: Write a step-by-step installation guide for dummies.

## How does it work?
When you first start hueshell you need to connect it to your bridge, which takes only 2 steps (might be a bit more depending on your distance to your physical bridge; YMMV):

1. Go to the directory where hueshell is located and type this:
`./hue init`

2. Follow the on-screen instructions.

If you have nmap available on your system the initialization routine will try to automagically find your bridge. If you don't or it can't detect it you'll need to manually enter its address.

Once you're done setting up, you can start controlling your lights.

### Listing available lights
`./hue light list`

### Turning on and off a light
`./hue light set [light number from previous listing] on`

`./hue light set [light number from previous listing] off`

### Changing the light's color
Colors are declared as hue values that range from 0 to 65535.

`./hue light set [light number from previous listing] hue=0`

`./hue light set [light number from previous listing] hue=25000`

### Changing the light's brightness
Brightness are declare as values that range from 0 to 255.

`./hue light set [light number from previous listing] bri=0`

`./hue light set [light number from previous listing] bri=255`

### Doing everything at once
You can combine the commands above as you please. 

`./hue light set [light number from previous listing] on hue=37000 bri=125`

## Dependencies

* curl: For communication with the bridge.
* jq: For handling JSON data. The init script will donwload it if you don't have it on your system, so don't worry.
* nmap (optional): For scanning the network for bridges.

## Components

hueshell comes with 2 parts: the main script and libhueshell.

The hue script contains all the logic and handles user interaction and settings.

libhueshell contain all functions that actually communicate with the hue bridge and may be used on other projects directly.

## Why shellscript?

Because there were already nice implementations in other languages and I couldn't really find anything in bash that pleased me.
