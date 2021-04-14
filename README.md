# FieldMill PCB Files
This is the Repo for the hardware associated with our Fieldmill project [link TBD]

# A short guide of how to make one yourself
### Component procurement. You'll need the following:

  - The PCBs: 
    There are exported gerbers packaged into .rar archives in the Gerber/V{number] folder, all four are needed. You can order these from whatever PCB manufacturer you prefer or make them yourself
    They are all single layer and I have made the demo mill with home-etched pcbs too.
    (JLC would charge 11,70€ plus shipping for all required PCBs as of April 2021)
  - The Components: 
    You will need approximately 25€ worth of components. Almost all smd parts, but non smaller than 0805. 
    I have created a ready to import bom document for DigiKey ("Full BOM - DigiKey.xlsx"). Simply import it to your card with the "Upload a File" Tab above the manual part adding box on the top of the page. You can ignore the warning about better options and just hit the submit button if it warns you about that.
    
    __IMPORTANT__ the ESP32 dev kit is not included in the BOM, you will need to find it somewhere else. Doesn't need to be anything special and you'll probably find it on any of the common websites (aliexpress, amazon, ebay...)
    You will also need a set of M2 (or comparable imperial size) standoffs and screws to mount the boards together, I used some from a multi box set from amazon but anything that is kind of the right size will work.
    
### Assembly.

1.  Assemble the individual PCBs. (For reference on the orientation of some through hole components check out this album of pictures: [TBD])
    If you have never soldered SMD parts before I recommend looking at some of the how to videos for it on youtube, but don't worry it's really not that hard (Just remember: you can't ever have too much flux ;) )
    The component values should all be marked on the silkscreen, but if I forgot any or you made the board at home you can always look at the parts list in the PDF docs ("ESP32 Board.PDF" and "Front End.PDF")
   
2.  Prepare the case. 
    The STL files for this are in the "3D Models" Folder. There are three pieces that need to be made. The precision does not need to be very high, for reference I had a friend print this on a 5 year old filament printer with no issues.
    If the screw threads don't quite work out you can use a bit of sand paper or a file to get them to fit.
    
    Then you will need to cover the top part (the one that has no closed ends) in copper tape or something else conductive to prevent charges building up on it and ruining the readings. 
    You will also need to cover one half of the middle part, specifically the one where the sensor fits. To figure out which one that is you can always test fit the front-end PCB on the part and see on which side it fits, that is the one that needs to be covered.
    
    After you've done that you should screw the top and middle parts together (maybe even glue them with a bit of CA glue) and tape across the gap to electrically connect them (make sure you test this with a multimeter!).
    The bottom part will be the only removeable one.
    
3.  Assemble the sensor.
    Start off by screwing the motor and four male-female 5mm standoffs to the stator board (the standoffs go into the four outer holes). The parts all go onto the side that has the exposed motor.
    
    Then solder some single header pins onto the pads facing the same diretion as the motor does, and push the front end board onto it. The 8 pin header on it should face away from the stator.
    **IMPORTANT** make sure that the optical sensor (IC2) is located underneath the slot in the stator board or the mill will not work!
    
    Next you can solder the pins to the front end board too (make sure it is sitting flat), and screw some female-female 10mm standoffs onto the threads of the standoffs from the previos step to hold the PCB in place.
    
    To screw the parts into the case you need to cut 20mm pieces off of an M2 threaded rod (or just cut apart some screws) and screw them through some female-female 5mm standoffs, which then screw the assembly made before into the half of the case we covered with copper tape.
    Before you screw it in you should make sure that the pin header on the front end board is located over the hole in the part so it can be connected to in the next step.
    
    Finally you have to push the ESP32 board onto the back of what we just made, so it connects with the pins on the front end, and screw it on with either some more f-f m2 standoffs (no longer than 10mm though) or just some m2 washers.
    To access the USB port you'll need to leave the bottom cover off, but once the code is programmed you can close that and only connect the power in.
    
  ### Profit
    
  That's it :) If you have any questions feel free to contact us on our website and we look forward to hearing your feedback.
    
# Notes

VIn needs to be between 6V and 24V, the mill can also run from just USB.

The firmware is here: https://github.com/ArcAttack/FieldMill-Firmware
