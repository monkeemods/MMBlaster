# MM Blaster
This is the core library for basic operation of a blaster. The main goal is trying to unite all blaster to use the same firing logic.
It's originally designed to used in brushless flywheel(HT Diana) but further improved to add support for brushed flywheel and AEB.

## Flywheel/Brushed Flywheel/AEB
For both type of flywheel, there's a pusher and usually 2 or more motors, hence you will need to hook into 2 callback function in the library.

For AEB, usually there's only 1 main motor, hence you only need to hook into the Pusher callback function.

## Trigger
You can set trigger delay for blaster that requires a small delay before firing. For example to spin up the flywheel motor first.

There are 2 types of trigger behavior, `passive` and `reactive`.
In `passive` mode, it will ignore any other trigger pull in mid firing cycle. Example for burstfire, while it fires off all 3 burst shots, if you pull your trigger again, your blaster will fire a total of 3 shots with 2 trigger pull in total.
In `reactive` mode, it WILL NOT ignore the trigge pull in mid firing cycle. While it still firing the first set of 3 shots, if you press the trigger again, a total of 6 shots will be fired.
This applies to semi auto as well but since the speed is too fast, you will barely notice this unless you do it on purpose. Using `passive` trigger might give you the sense of the trigger malfunction so configure this based on your preference.

## Firing Mode
You can set the firing mode. The library will not handle switch changes for trigger or fireselector, so it's up to the main file to implement these. 

You can use `safe`,`semi`,`burst1`,`burst2`,`full`
Safe = Safety
Semi = 1 shot
Burst1 = Shots configured with `setBurstFireAmount1`
Burst2 = Shots configured with `setBurstFireAmount2`
Full = Full auto with maximum limit set in `setFullAutoMaxAmount`

You can limit the full auto to control your maximum mag dump or do 1-X amount of shots, based on the value you set. This will allow better ammo management.

## Library needed
- DigitalPin (https://github.com/monkeemods/digital-pin)

# Note
This is designed for RP2040 using Arduino-Pico, specifically Raspberry Pico W. Minor changes might be needed to support ESP32(pull request is welcomed).
