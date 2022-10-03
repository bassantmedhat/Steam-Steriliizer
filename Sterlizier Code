//Temperature Monitoring System using Arduino, LM35 and Hc-05 
#include <SoftwareSerial.h>
SoftwareSerial mySerial(0, 1); // RX, TX

#include <LiquidCrystal.h>
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
int tempPin = A0;   // the output pin of LM35
int buzzer=13;
int read_ADC= 0;
double temp = 0;
double tempC = 0;



void setup() {
Serial.begin(9600); 
mySerial.begin(9600); 
Serial.println("Ready");
mySerial.println("Ready");

pinMode(tempPin, INPUT);
lcd.begin(16,2);  

}
 
void loop(){

read_ADC =analogRead(tempPin); 
temp = (read_ADC / 1023.0) * 5000; // 5000 to get millivots.
tempC = temp * 0.1; // 500 is the offset


lcd.setCursor(0,0);    
lcd.print("   Temperature  ");
lcd.setCursor(0,1); 
lcd.print(tempC,1);
lcd.print((char)223); //degree symbol 
lcd.print("C  ");
  if(tempC>=100){
    tone(buzzer, 1000); // Send 1KHz sound signal...
    delay(1000);        // ...for 1 sec
    noTone(buzzer);     // Stop sound...
    delay(1000);        // ...for 1sec
  }

Serial.println(tempC);
mySerial.print("S");
mySerial.print(";");
mySerial.print(tempC,0); //send distance to MIT App
mySerial.print(";");

delay(1000);
}
