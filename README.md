Arduino-Led-Strip
=================

Arduino Led Strips using Adafruit Library

Lots of input from adafruit, instructables, arduino commmunity.

The only part of code i can say is mine - or at least i had to work out myself is this and the others bits using the memory pointers - the code needs some tidying up and optimising - some time.


     int red, green, blue;
     uint8_t  c;
     for (int j=0; j<strip.numPixels(); j++) {      
       if(chkBtn(digitalRead(BUTTON))) { break; }                       
       uint8_t  *ptr = strip.getPixels();     
       c      = *ptr;
       red = ptr[0];
       green = ptr[1];
       blue = ptr[2];
       for (int i=0; i<((strip.numPixels()-1)*3); i++) {
         c      = *ptr;
         ptr[0] = ptr[3];
         ptr[1] = ptr[4];         
         ptr[2] = ptr[5];         
         *ptr++;
       }
       ptr[0] = red;
       ptr[1]= green;
       ptr[2] = blue;
       strip.show();
       delay(wait);    
     }
     
I wanted to access the individual RGB values to dim the lights. 

this function - 
void Adafruit_NeoPixel::setBrightness(uint8_t b)
dims the entire strip, i wanted to dim particular LEDS.

Basically i wanted to achieve - "scoffelrainbow" 

Attach LED strip and button - or fake the button.

Some patterns work best on shorts strip and others on long strips - ie 20Leds or 120 LEDS

Clive
