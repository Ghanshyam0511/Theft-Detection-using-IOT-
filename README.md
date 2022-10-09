# /*********************
 This is a simple demo of sending and receiving some data.
 Be sure to check out other examples!
*********************/
// Template ID, Device Name and Auth Token are provided by the 
Blynk.Cloud
// See the Device Info tab, or Template settings
#define BLYNK_TEMPLATE_ID "TMPL-bsrMTEX"
#define BLYNK_DEVICE_NAME "Quickstart Device"
#define BLYNK_AUTH_TOKEN 
"d_KVbUgiQP4HKJ17BHPcv_YH_ObkqoYB"
// Comment this out to disable prints and save space
#define BLYNK_PRINT Serial
#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>
/* HC-SR501 Motion Detector */
int Pir_Sensor = 13; // Digital pin D7
int Motion ;
char auth[] = BLYNK_AUTH_TOKEN;
// Your WiFi credentials.
// Set password to "" for open networks.
char ssid[] = "EGIPL";
char pass[] = "Staunch_54321";
BlynkTimer timer;
// This function is called every time the Virtual Pin 0 state changes
BLYNK_WRITE(V0)
{
 // Set incoming value from pin V0 to a variable
int value = param.asInt();
 // Update state
 Blynk.virtualWrite(V1, value);
}
// This function is called every time the device is connected to the 
Blynk.Cloud
BLYNK_CONNECTED()
{
 // Change Web Link Button message to "Congratulations!"
 Blynk.setProperty(V3, "offImageUrl", "https://staticimage.nyc3.cdn.digitaloceanspaces.com/general/fte/congratulations.png");
 Blynk.setProperty(V3, "onImageUrl", "https://staticimage.nyc3.cdn.digitaloceanspaces.com/general/fte/congratulations_pressed.
png");
 Blynk.setProperty(V3, "url", "https://docs.blynk.io/en/getting-started/whatdo-i-need-to-blynk/how-quickstart-device-was-made");
}
// This function sends Arduino's uptime every second to Virtual Pin 2.
void myTimerEvent()
{
 // You can send any value at any time.
 // Please don't send more that 10 values per second.
 Blynk.virtualWrite(V2, millis() / 1000);
}
void setup()
{
 // Debug console
 Serial.begin(115200);
 pinMode(Pir_Sensor, INPUT); // declare sensor as input
 Blynk.begin(auth, ssid, pass);
 // You can also specify server:
 //Blynk.begin(auth, ssid, pass, "blynk.cloud", 80);
 //Blynk.begin(auth, ssid, pass, IPAddress(192,168,1,100), 8080);
 // Setup a function to be called every second
 timer.setInterval(1000L, myTimerEvent);
}
void loop()
{
 // You can inject your own code or combine it with other sketches.
 // Check other examples on how to communicate with Blynk. Remember
// This function is called every time the device is connected to the 
Blynk.Cloud
BLYNK_CONNECTED()
{
 // Change Web Link Button message to "Congratulations!"
 Blynk.setProperty(V3, "offImageUrl", "https://staticimage.nyc3.cdn.digitaloceanspaces.com/general/fte/congratulations.png");
 Blynk.setProperty(V3, "onImageUrl", "https://staticimage.nyc3.cdn.digitaloceanspaces.com/general/fte/congratulations_pressed.
png");
 Blynk.setProperty(V3, "url", "https://docs.blynk.io/en/getting-started/whatdo-i-need-to-blynk/how-quickstart-device-was-made");
}
// This function sends Arduino's uptime every second to Virtual Pin 2.
void myTimerEvent()
{
 // You can send any value at any time.
 // Please don't send more that 10 values per second.
 Blynk.virtualWrite(V2, millis() / 1000);
}
void setup()
{
 // Debug console
 Serial.begin(115200);
 pinMode(Pir_Sensor, INPUT); // declare sensor as input
 Blynk.begin(auth, ssid, pass);
 // You can also specify server:
 //Blynk.begin(auth, ssid, pass, "blynk.cloud", 80);
 //Blynk.begin(auth, ssid, pass, IPAddress(192,168,1,100), 8080);
 // Setup a function to be called every second
 timer.setInterval(1000L, myTimerEvent);
}
void loop()
{
 // You can inject your own code or combine it with other sketches.
 // Check other examples on how to communicate with Blynk. Remember
// This function is called every time the device is connected to the 
Blynk.Cloud
BLYNK_CONNECTED()
{
 // Change Web Link Button message to "Congratulations!"
 Blynk.setProperty(V3, "offImageUrl", "https://staticimage.nyc3.cdn.digitaloceanspaces.com/general/fte/congratulations.png");
 Blynk.setProperty(V3, "onImageUrl", "https://staticimage.nyc3.cdn.digitaloceanspaces.com/general/fte/congratulations_pressed.
png");
 Blynk.setProperty(V3, "url", "https://docs.blynk.io/en/getting-started/whatdo-i-need-to-blynk/how-quickstart-device-was-made");
}
// This function sends Arduino's uptime every second to Virtual Pin 2.
void myTimerEvent()
{
 // You can send any value at any time.
 // Please don't send more that 10 values per second.
 Blynk.virtualWrite(V2, millis() / 1000);
}
void setup()
{
 // Debug console
 Serial.begin(115200);
 pinMode(Pir_Sensor, INPUT); // declare sensor as input
 Blynk.begin(auth, ssid, pass);
 // You can also specify server:
 //Blynk.begin(auth, ssid, pass, "blynk.cloud", 80);
 //Blynk.begin(auth, ssid, pass, IPAddress(192,168,1,100), 8080);
 // Setup a function to be called every second
 timer.setInterval(1000L, myTimerEvent);
}
void loop()
{
 // You can inject your own code or combine it with other sketches.
 // Check other examples on how to communicate with Blynk. Remember
Blynk.run();
timer.run();
 if ( WiFi.status () == WL_CONNECTED )
{
 Serial.println("Device is online Program Started");
 Motion = digitalRead(Pir_Sensor);
 if(Motion == HIGH) 
 {
 Blynk.notify("Motion detected"); 
 Serial.println("Motion detected");
 delay(1000);
 }
 else 
 {
 Serial.println("Motion absent!");
 Blynk.notify("No Motion detected"); 
 delay(1000);
 }
 Blynk.run();
}
else
{
 Serial.println("Device is offline plese restart device or check WiFi 
connection");
 Motion = digitalRead(Pir_Sensor);
 if(Motion == HIGH) 
 {
 // Blynk.notify("Motion detected"); 
 Serial.println("Motion detected");
 delay(1000);
 }
 else 
 {
 Serial.println("Motion absent!");
 // Blynk.notify("No Motion detected"); 
Delay (1000);
}}
}






# Theft-Detection-using-IOT-
