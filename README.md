# FieldMill PCB Files
This is the Repo for the hardware associated with our Fieldmill project [link TBD]

# A short guide of how to make one yourself
### Component procurement. You'll need the following:

  - The PCBs: 
    There are exported gerbers packaged into .rar archives in the Gerber/V[number] folder, all four are needed. You can order these from whatever PCB manufacturer you prefer or make them yourself
    They are all single layer* and I have made the demo mill with home-etched pcbs too.
    (JLC would charge ~11€ plus shipping for all required PCBs as of April 2021)
    
    *The stator and rotor are double layer but have no structures on the bottom one. The rotor just needs to be cut from double sided base material. The stator boards needs to have the holes connecting the four electrodes (the ones that are in the middle of them) slightly counter-sunk on the bottom side to prevent shorting against the back plane.
    
  - The Components: 
    You will need approximately 25€ worth of components. Almost all smd parts, but non smaller than 0805. 
    I have created a ready to import bom document for DigiKey ("Full BOM - DigiKey.xlsx"). Simply import it to your card with the "Upload a File" Tab above the manual part adding box on the top of the page. You can ignore the warning about better options and just hit the submit button if it warns you about that.
    
    __IMPORTANT__ the ESP32 dev kit is not included in the BOM, you will need to find it somewhere else. Doesn't need to be anything special and you'll probably find it on any of the common websites (aliexpress, amazon, ebay...)
    You will also need a set of M2 (or comparable imperial size) standoffs and screws (four a few mm long plus four >20mm ones that get cut apart) to mount the boards together, I used some from a multi box set from amazon but anything that is kind of the right size will work.
    
### Assembly.

1.  Assemble the individual PCBs. (check out the Pictures folder for some reference images showing how it should look and which side the components go onto)
    
    If you have never soldered SMD parts before I recommend watching some of the how to videos about it on youtube. Don't worry it's really not that hard :) (just remember: you can't ever have too much flux ;) )
    The component values should all be marked on the silkscreen, but if I forgot any or you made the board at home you can always look at the parts list in the PDF docs ("ESP32 Board.PDF" and "Front End.PDF")
    
    **IMPORTANT** make sure to clean the front-end board VERY THOROUGHLY with a brush and IPA or ethanol after assembly. Even the slightest residue will cause leakages that ruin the Sensor
   
2.  Prepare the case. 

    The STL files for this are in the "3D Models" Folder. There are four pieces that need to be made. The precision does not need to be very high (I had a friend print this on a 5 year old filament printer with no issues).
    If the screw threads on the middle part don't quite work out you can use a bit of sand paper or a file to get them to fit.
    
    Then you will need to cover the top part (the one that has no closed ends) in copper tape or something else conductive to prevent charges building up on it and ruining the readings. 
    You will also need to cover one half of the middle part, specifically the one where the sensor fits. To figure out which one that is you should check on which side the header on the front end board lines up with the hole in hte center part. 
    
    After you've done that you should screw the top and middle parts together (maybe even glue them with a bit of CA glue) and tape across the gap on the inside to electrically connect them (make sure you test this with a multimeter!). (It should look like Image-2.jpg after this)
    
3.  Assemble the sensor. (to see on which side things should go look at Image-5.jpg)

    Start off by screwing the motor and four male-female 5mm standoffs to the stator board (the standoffs go into the four outer holes). The parts all go onto the side that has the exposed pad in the middle.
    
    Then solder some single header pins onto the pads facing the same diretion as the motor does, and push the front end board onto it. The 8 pin header on it should face away from the stator.
    **IMPORTANT** make sure that the optical sensor (IC2) is located underneath the slot in the stator board (as Image-4.jpg shows) or the mill will not work!
    
    Next you can solder the pins to the front end board (make sure it is sitting flat), and screw some female-female 10mm standoffs onto the threads of the standoffs from the previos step to hold the PCB in place.
    
    To screw the assembly into the case you need to cut 20mm pieces off of an M2 threaded rod (or a long screw) and screw them through some female-female 5mm standoffs (compare Image-7.jpg, the nut is to allow screwing it in with a screwdriver). It should go inside the copper coverd side of the case we made before.
    Before you screw it in you should make sure that the motor wires are pulled through the hole in the center part and pin header on the front end board is located over it (as in Image-6.jpg) so the ESP board can be connected to it in the next step. 
    
    Now you need to ground the motor shaft, which we do with the spring pluger. If your screw take solder you can just solder it right onto them like you see in Picture-5.jpg. If they don't you can take a male-female standoff and use a file or some rough sandpaper to make it ~0.5mm tall and then solder onto that (thats the way I did it). I also used a triangular file to cut a little vertical groove into the plunger to give it some larger contact area, but I'm not sure if that really does much. You might also want to add a tiny dab of lithium grease to the shaft after this to reduce friction and wear.
    
    We also need to make the rotor. To mount it on the shaft and electrically connect the two you'll need the hub from the 3D Models folder: solder a ~0.4mm wire into the small off-center hole on the rotor, pull it through the hub and glue the hub down onto the rotor PCB. Make sure that you orient the hub so the wire can go into the little groove in the side of it. Just press fit it onto the shaft and make sure it is sitting sort of square (best seen when looking at it from the side and turning it).
    
    **IMPORTANT** If you made these boards yourself or you ordered them with gold plating you might need to cover the bottom of the Rotor (the exposed side) with aluminium tape, as the opto-interrupter might not get enough signal otherwise.
    
    Finally you have to push the ESP32 board onto the back of what we just made (should look like Image-9.jpg), so it connects with the pins on the front end, and screw it on with either some more f-f m2 standoffs (no longer than 10mm though) or just some m2 washers. You might have to cut the pin header down a bit though, the one I found on digikey is not the same lengh as the one I used.
    To access the USB port you'll need to leave the bottom cover off, but once the code is programmed you can close that and only need access to the power input, which should line up with the hole in the side.
    
### Software 
  
  To programm the ESP you should follow the steps detailed in the firmware repo: https://github.com/ArcAttack/FieldMill-Firmware
  
### Profit
    
That's it :) If you have any questions feel free to contact us on our website and we look forward to hearing your feedback.
    
# Notes

VIn needs to be between 6V and 24V, the mill can also run from just USB.

To connect the motor you can either solder in the wire directly or use some JST XH connectors. You can buy those in kits too, just look for XH connector set on the internet and you'll find them. The wires from the motor are so small that you might have to solder them into the crimp-contacts though.
