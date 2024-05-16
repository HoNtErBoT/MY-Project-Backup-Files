#  NeoPixel LED Interface with ESP32



```
/*
      Name  : Rajeev TR
      Code  : This Code is used to controll pixel LED
      Date  : 16/05/2024
      Github: https://github.com/HoNtErBoT/MY-Project-Backup-Files/tree/main/01_Embedded_R&D/01_ESP32/01_NeoPixelLED

*/
/*******************************************************************/
#include <Adafruit_NeoPixel.h>

#define PIN_NEO_PIXEL 16  // The ESP32 pin GPIO16 connected to NeoPixel
#define NUM_PIXELS 11     // The number of LEDs (pixels) on NeoPixel LED strip

Adafruit_NeoPixel NeoPixel(NUM_PIXELS, PIN_NEO_PIXEL, NEO_GRB + NEO_KHZ800);
/*******************************************************************/
int r=255,g=0,b=0,s=50;
void setup() 
{
  Serial.begin(9600);
  NeoPixel.begin();  // initialize NeoPixel strip object (REQUIRED)  
}
/*******************************************************************/
void loop() 
{
  char x;
  if(Serial.available())
  {
    x=Serial.read();
    if(x=='r')
    {
      r=Serial.parseInt();
    }
    if(x=='g')
    {
      g=Serial.parseInt();
    }
    if(x=='b')
    {
      b=Serial.parseInt();
    }
    if(x=='s')
    {
      s=Serial.parseInt();
    }
  }
  NeoPixel.clear();  // set all pixel colors to 'off'. It only takes effect if pixels.show() is called
  for (int pixel = 0; pixel < NUM_PIXELS; pixel++)                // for each pixel
  {           
    NeoPixel.setPixelColor(pixel, NeoPixel.Color(r, g, b));  // it only takes effect if pixels.show() is called
    NeoPixel.show();                                             // update to the NeoPixel Led Strip
    delay(s); 
  }
}

/*******************************************************************/
```
