
# PWM-FAN Controller

25Khz PWM fan controller for fume extractor. Duty Range: 5%-95%, requires an external 12v supply.

Designed to control Dell Server Grade cooling fan's (*because I have one already*), or any 4-wire PC case fan.

[4-wire Fan](https://www.digikey.com/short/5pwf955c)

[Another Fan](https://www.newegg.com/p/1YF-00B0-00V81)

[Overkill Fan **2Amps**](https://www.amazon.com/Wathai-5300rpm-Airflow-Brushless-Cooling/dp/B07SGWNV5J)

## Parts-List
[DigiCart](https://www.digikey.com/short/1bbnzr3q)

___
## Notes

Some ```things``` that have caused concern are as follows,

- The Datasheet states the min/max rpm of the fan during pwm operation, ```0 rpm - 4800 rpm```. However, it also implies that the fan will never reach 0 rpm. So what exactly is the minimum speed achievable?
- I didn't add a power switch or pads for an off-board switch :rage1: . Guess ill just unplug it when I want it off? or wire a switch in series with the fan +12v wire? (**which should be rated for 2A**).
- Why do all fan controllers on amazon use high side switching instead of the actual pwm control cooked into the fan assembly? [Note the huge heat sink](https://www.amazon.com/LEDMOMO-1203BB-Controller-Adjustable-Reversible/dp/B07BLWXXQC)
- *R7 doesn't need to be populated, I checked. The fan still works with no tachometer pull-up. I thought maybe it had current sensing or something weird going on.*
- Why didn't I just buy [!!that!!](https://www.amazon.com/Wathai-Controller-Receiver-Playstation-Component/dp/B07VYGQPCZ) :rage1: *....I already sent the board to fab and bought the parts...*
---
### Fan Info

So I guess the fan *I* have is a dell model *6D237*, which has been surpassed by the *8W977*. Which might also be the *5E169*?

 I'm 78% confidant the fan linked above is almost identical, ergo, the datasheet should be a great reference for *my* fan.

### Pinout *[6D237]*
| +12 |   GND |   PWN |  SENSE |
|-----|-------|-------|--------|
| RED | BLACK | GREEN | YELLOW |

I have no idea how old the **6D237** is, but google can't find it..... Still works though, so I'm a happy camper.




