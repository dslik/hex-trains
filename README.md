## Hextile Train System

Small PCB-based hex tiles that snap together using magnets to allow you to build various simulated rail networks:

- Train position on track, track conditions, moving block, signals, etc, shown using small RGB LEDs.
- Run virtual consists across physically reconfigurable networks to deliver goods or passengers.
- Configure schedules and signalling
- Customize tiles with stickers for different landscape, station and industries.

Can also be used to create multi-player games.

![image](https://github.com/dslik/hex-trains/assets/5757591/df82bd30-581c-41eb-806f-b2df1476deca)

# Build Journal

_Feel free to ask questions by opening an issue!_

## 2023-07-23

Here's a rough placement of the components on each tile, including the microcontroller. I'm using panelization with V-cuts to reduce manufacturing costs during the prototyping stage. If this were to go into production, each tile type would be manufactured separately to ensure that all the edges are uniform.

![image](https://github.com/dslik/hex-trains/assets/5757591/f559e85b-f893-4c13-8f27-fc5c3897388f)

This is a straight track segment, and three tiles allowing you to make arbitary length sidings.

The following tile types are planned, though many more are possible (add your own!):

* Straight track
* Siding right
* Siding track
* Siding left
* Curve right
* Curve left
* Point right
* Point left

Various stickers attached to the front panel board will allow further customization of the above eight tiles.

One additional tile that I am strongly tempted to add is a short siding track, since that's very useful for passenger trains layouts (as the trains are much shorter). These can be then customized with stickers to create various stations.

## 2023-07-21

Each tile is 1.8 inches across (45.72 mm), and each RGB smart LED represents a single train car, with the colour corresponding to the colour of the car. Since train cars are of different lengths, this is an approximation, with the scale set to one LED = 60 feet (based on a Pullman standard flatcar/Gunderson boxcar). This results in each tile, at 0.15 feet in length, representing 1260 feet of track, a scale ratio of 1:8400. This allows for the modelling of relatively long railways in a very compact space, as 10 km of track requires only 26 tiles, which fits on a typical refrigerator door.

![image](https://github.com/dslik/hex-trains/assets/5757591/f56e5c2b-7961-418d-9db1-100664d3d111)

This straight track segment can hold 21 60' train cars.

This also allows for dense yards, as a #10 turnout only requires 4 LED's worth of space:

![image](https://github.com/dslik/hex-trains/assets/5757591/c9056e01-ea16-4b3f-a2d5-95c5488fbcb6)

Tiles are constructed from multiple stacked PCBs:

* Bottom PCB - Acts as the botton cap and holds the magnets vertically
* Magnet spacer PCBs - Holds the magnets horizontally
* LED PCB - Holds the magnets vertically and has the LEDs, microcontroller, and tile-to-tile connectors
* LED spacer PCBs - Sit on top of the LED PCB
* Front Panel PCB - Acts as the top cap, and has the landscape sticker applied to it

Depending on the magnet size (which will need a number of experiments to determine the trade-off between attractive force and size), the tiles will either be 6mm thick or 8mm thick.
