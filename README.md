# IOT-IBM-ASSIGNMENT
home automation with sensor


Description:

The sensors connected to the microcontroller board are LM35, PIR and LDR sensor. LM35 is used to sense the temperature level in the house while LDR sensor is to sense the light intensity. ... The data sensed by the sensors are then used as feedback for automatic control of home appliances. The Main thing about these project is the the whole project is only works when Somebody is present infront of PIR sensor Otherwise is turend OFF at all time.
Just follow the steps below and you are ready to get yourself one Smart Home Automation Project!
Things that you need
• Arduino
• PIR
• LDR
• LM35
• Dc power source (Any 12v)
  Relay Board of 2 channel


Code:

float x,y,z,temp;
void setup()
{
  pinMode(8, INPUT);
  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(A5, INPUT); 
  pinMode(A4, INPUT);
Serial.begin(9600);
}
void loop()
{
  x= digitalRead(8);
  y= analogRead(A5);
  z= analogRead(A4);
  Serial.println(x);
  Serial.println(y);
  Serial.println(z);
  temp = (double)z / 1024;       
  temp = temp * 5;                 
  temp = temp - 0.5;               
  temp = temp * 100;               
  if ( (x>0) )
  {
    if ((y<550)&&(temp>30))
    {
      digitalWrite(5, HIGH);
      digitalWrite(6, HIGH);
    }
    else if((y<550)&&(temp<30))
    {
      digitalWrite(5, HIGH);
      digitalWrite(6, LOW);
    }
    else if((y>550)&&(temp>30))
    {
      digitalWrite(5, LOW);
      digitalWrite(6, HIGH);
    }
    else if((y>550)&&(temp<30))
    {
      digitalWrite(5, LOW);
      digitalWrite(6, LOW);
    }
  }
  else
  {
    digitalWrite(5, LOW);
    digitalWrite(6, LOW);
  }
}



