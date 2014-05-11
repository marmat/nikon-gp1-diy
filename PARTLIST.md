Parts
=====

All parts listed here are subject to change.

|  Item description |     Part No.    |  Size | Qty | Est. Price (Total, €) |
| ----------------- | --------------- | ----- | --- | --------------------: |
| GPS Module        | Maestro A2235-H |       |   1 |                 19.07 |
| Voltage Regulator | LP29985-33      | SOT23 |   1 |                  0.84 |
| Tactile Switch    | Various         | SMD?  |   1 |                  0.60 |
| Resistor          | 10 kOhm         | 0805  |   3 |                  0.30 |
| Resistor          | 1 kOhm          | 0805  |   1 |                  0.10 |
| Resistor          | 2.2 kOhm        | 0805  |   2 |                  0.20 |
| Transistor        | tbd             | SOT23 |   1 |                  0.05 |
| PCB               |                 |       |   1 |                 ~5.00 |
| Housing           |                 |       |   1 |                 ~3.50 |
| **Grand Total**   |                 |       |     |            **~29.50** |

2 x 10kOhm resistors are needed as pull-up for the ON/OFF pin and GPIO6 of GPS
module (to enable UART mode). A switch could be mounted either flat or sideways,
depending on what will be better to incorporate in the case design. The
remaining resistors and the transistor are required for the level shift from
3.3V GPS TX to 5V GPS DATA input of the camera. For Baudrate 4800, the GPS
module needs two pull-ups (2k2) on GPIO0 and GPIO1.

The PCB price is a very rough approximation if we manufacture just a single
prototype. If you have the equipment to make PCBs on your own, or if one would
order a large batch, the effective cost per PCB would be much lower. The housing
cost is based on off-the-shelf components glued together (see below, option B).
A 3D-printed case might be cheaper in terms of pure material cost.


## Housing

### Option A: fully self-designed case, 3D printed

If we case completely on our own, we have the benefit of being able to make it
as small as physically possible to fit all the components. Using the dimensions
of the A2235-H and adding some space for the cable and additional components,
the case could have approx 20mm x 28mm x 7mm inner dimensions, plus width of
plastic about 24mm x 32mm x 11mm:

![Sketch](sketch.png)

I do not know anything about 3D printing yet, thus it would have to be evaluated
if such dimensions are viable for printining (in terms of thickness etc.) at
all. The cost of material should be pretty cheap for such a small case.

The exact hot shoe dimensions are only available through ISO 518:2006, but it
should be sufficient to precislety measure a regular hot shoe protection cap.
Furthermore, [thingiverse](http://www.thingiverse.com/thing:7992) does have
models for protection caps that could be used as a base.

### Option B: Commercially available housing + mount glued together

We could also use a regular hot shoe cap (e.g. Nikon BS-1 or third party
variants, ~1€) and mount a simple plastic case (e.g. Hammond 1551NBK, ~2.50€) on
top of it. Advantage: easy to acquire, no special hardware needed. Disadvantage:
might look not as clean and possibly larger than needed.

The case Hammond [1551NBK](http://www.farnell.com/datasheets/2872.pdf) looks
pretty good: 35mm x 35mm x 15mm with max. inner dimensions of 28.7mm x 28.7mm x
11mm. Also, it's very cheap, so we might want to consider it at least for the
first prototype.


## Optional: indicator LED on 1PPS pin

We might want to include a led to indicate some sort of status. However, this
will require slightly more energry, thus faster drain of the camera batter (but
probably negligible) and more space on the PCB. With the Hammond case mentioned
above, there should be enough room for that, though. The additional parts are as
follows and the transistor could be connected to the GPS module's 1PPS pin
(resulting in 1 brief flash per second if GPS signal is present):

| Item description |    Part No.    |  Size | Qty | Est. Price (Total, €) |
| ---------------- | -------------- | ----- | --- | --------------------- |
| LED              | Various, green | G1206 |   1 |                  0.16 |
| Resistor         | 40 Ohm         | 1206  |   1 |                  0.10 |
| Resistor         | 100k           | 1206  |   1 |                  0.10 |
| Transistor       | tbd            | SOT23 |   1 |                  0.05 |
