# logitech_craft_experiment
Dials are the future!

## Background
The Logitech Craft is a beautifully made albeit ordinary wireless keyboard. Setting it apart is a touch sensitive knob in the upper left corner that can be used to control applications through touching, clicking and turning.

As is often the case with logitech, the abilities of the hardware exceed the features of the software that accompany it. The set point software for the touch surface mouse for instance; permits a two finger tap gesture, middle click, swipe left and right... but no pinch zoom? I've learned to accept it in the case of this mouse, but for €200 a keyboard with a smart dial that only works in Microsoft Office and Adobe CS, this is not acceptable.

### What can the Logitech Craft actually do?
The Craft is a keyboard much like any other, except that it features a touch senstive rotary encoder dial in the upper left corner. This dial is not unlike a Surface Dial though attached to a keyboard.

As well as provding relative rotation information the dial reports 4 states:
- nothing
- touch
- push
- proximity*

*The proximity state appears intermittent - it often needs the dial to be "lifted" first - and is perhaps why this feature is not available when customising the dial. In my experiments I have found the keyboard reports this state when the hand is a few centimeters from the dial. Useful for preloading touch menus no doubt, or even preconfiguring the state of the ratchet feature in the dial - which with the current driver is very bad at. Firmware may improve the consistency of the 4th proximity state though I have yet to venture into reverse engineering this part of the device.

### The Existing Driver is Typically Terrible
The stock driver for the keyboard ships with an application, Logitech Options, that will allow the user to configure the top row and dial per application. It let's the user choose from a given list of arguably useless options when configuring for new applications; turn dial to adjust volume and switch tasks are technically as good as it gets. The incredibly important touch feature cannot be configured at all, and proximity sensing might as well never have existed.

Despite the expected inadequacies, if you want to support the craft dial in your own application the stock software is easy to understand. The logitech options application runs a socket server on a local loopback connection and you can connect to this from your application to receive messages when keyboard events occur. Take a look at the existing plugins where they reside on your system to see how this works. The Microsoft Office addins are easy enough to decompile with ilspy, and the javascript extensions for Adobe CS can be manually deobfuscated/decrunched with a 'crafty' regular expression.
