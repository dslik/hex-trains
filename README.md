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

## 2024-01-19

New magnets from JLCPCB's mechatronics store. They fit perfectly.

![image](https://github.com/dslik/hex-trains/assets/5757591/0845b53d-f8a6-4d6f-91cc-dfd16bfa3e9b)

The magnet snap-action when the two tiles are put together is perfect. Just the right amount of force, and a satisfying snap. They will stay together on a table, and stick nicely to a fridge.

But I will have to re-do the PCB design, since putting them at the corner causes snapping all three of them together to not be as strong as I would like. If I put each magnet in the centre of the mating surface, I can keep the same number of magnets per tile, and bring them closer together, increasing the strength to compensate for only having one magnet pair.

## 2023-10-02

Got the prototype boards in, and they tesselate and connect together very nicely!

![image](https://github.com/dslik/hex-trains/assets/5757591/34975d51-346b-4a55-a5d0-375e2cfafbbb)

I will need to tweak the pads to handle hot-plugging, and I still need to figure out the best way to connect all the boards in a given stack, but this is looking workable! I will have four contacts per hex tile to hex tile connection, which is enough for power and bi-directional data.

Next steps will be to figure out the stacking of PCBs, and to slightly enlarge the magnet holes.

## 2023-08-11

Figuring out a way to allow the hex tiles to be snapped togehter in such a way that you can rotate each tile into the six different orientations, and still be able to connect them when two or more are connected together, turned out to be quite a challenge.

![image](https://github.com/dslik/hex-trains/assets/5757591/f893f0bc-73f5-4a31-8c3b-fcb909cc8b0f)

Any sort of square connector that will slide in and mate with the top left tile will have trouble mating with the top right tile if you can also rotate it.

I was able to rule out standard rectangular headers immediately, but the other options I had originally considered didn't fare much better.

Pogo pins won't mate very well against each other, and is also a mechanical challenge to attach to the boards. And they would blow my BOM targets out of the water.

So after around 20 different iterations, I finally settled on this:

![image](https://github.com/dslik/hex-trains/assets/5757591/d8d9f308-ad55-44ed-8d41-fad2cef29ebc)

This is a 100% PCB-based solution, where the ENIG fingers press against each other.

This allows me to have:

* Four electrical connections between each board
* The ability to connect a third board to the concave section formed by two boards
* No shorting and proper power sequencing when connecting boards, regardless of the angle.

![image](https://github.com/dslik/hex-trains/assets/5757591/bd6bd4b9-a130-4028-abfb-d30ff94acf28)

Going with a 100% PCB-based approach also dramatically reduces the costs.

Next step will be to get some fabricated and see how reliable this approach is.

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

One additional tile that I am strongly tempted to add is a short siding track, since that's very useful for passenger trains layouts (as the trains are much shorter). These can be then customized with stickers to create various stations. Two other tiles on the shortlist are a crossing tile (which can have bridge or tunnel stickers), and a wye tile.

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
