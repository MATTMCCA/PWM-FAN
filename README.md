



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

I have no idea how old the **6D237** is, google can't find it..... Still works though, so I'm a happy camper.


# Update
Boards came today, everything turned out great. Fan spins, speed is adjustable.

- I did notice, the resistors used to control min and max values from the pot arnt quite right. The min setting looks to be about 5% duty, max is still 100% duty, not 95% like projected. I'm not spinning another revision, so ill have to live with it. *The boards could be reworked, I may do that in the future*.

- I may also add an activated charcoal filter, affixed with zip ties... because... *Function Over Form*...?

---

### Board Measurements 

|   | Vcc | 5%  | 95% |
|---|---|---|---|
|Target|12.00 V|140 mV|890 mv|
|Actual| 12.31 V| 137.1 mV | 920 mV |

*After look at the potentiometer tolerance... of 20%!!!... this kinda make since. I should have picked something with a tighter tolerance, oh well, lesson learned. Functionally everything still works.*

Out of circuit one pot measured `5.30k`, in circuit the other pot measured `5.25k`.

Also, turning the knob to the right lowers the duty, turning it to the left raises the duty. I don't like it, it feels backwards (see note in schematic). I think I wired the pot backwards... so that's fun, Murphy's first law at work.

On a whim, I shorted R6. when I did that the fan kept spinning, this tells me that the fan has a min RPM that is impossible to override by driving the PWM pin to ground (as mentioned above). So it looks like there is no way to turn the fan completely off via PWM, I assume this is a safety feature, seeing as how it is a cooling fan?

---


![alt text](https://github.com/MATTMCCA/PWM-FAN/blob/main/pics/002.png?raw=true)


