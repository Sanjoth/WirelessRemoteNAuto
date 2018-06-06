/*
* Author : Sanjoth Shaw
* Description : A program to implement a working model of remote & automatic control Home/Office appliances using a temperature sensor as reference.
*/

#include<SoftwareSerial.h>
SoftwareSerial HC05(10,11); // TX,RX
char junk;

String inputString="";
String manString="";

int a=1;
int b=1;

int lm35=0;

int n=120;

void setup()                    // run once, when the sketch starts
{
  HC05.begin(9600);
 Serial.begin(9600);            // set the baud rate to 9600, same should be of your Serial Monitor
 pinMode(13, OUTPUT);
 delay(5000);
 HC05.println("Created by Sanjoth.");
 delay(1000);
  HC05.println("A program to implement a working model of remote & automatic control Home/Office appliances using a temperature sensor as reference.");
  delay(5000);


}

void loop()
{

  HC05.println("-=|| Home/Office Control Applicances Control ||=- \n OPTIONS :- \n 1. MANUAL \n 2. AUTOMATIC \n 3. EXIT \n");
  delay(4000);
  manString ="";
      if(HC05.available()){
        while(HC05.available())
          {
            char manChar = (char)HC05.read();
            manString += manChar;
          }
      }



  while(manString == "1"){

    if(b==1)
    {
    HC05.println("Manual Mode Selected");
    delay(1500);
    HC05.println("Please input 'a' for ON, 'b' for OFF or 'e' for EXIT");
    delay(2500);
    }
    b++;
    if(HC05.available())
    {
      while(HC05.available())
     {
      char inChar = (char)HC05.read(); //read the input
      inputString += inChar;        //make a string of the characters coming on serial
     }
    }

    HC05.println(inputString);
    //while (HC05.available() > 0)
    //{ junk = HC05.read() ; }      // clear the serial buffer
    if(inputString == "a"){         //in case of 'a' turn the LED on
      digitalWrite(13, HIGH);
      //Serial.println("High");
      HC05.println("High signal sent");
      inputString="";
    }else if(inputString == "b"){   //incase of 'b' turn the LED off
      digitalWrite(13, LOW);
      //Serial.println("Low");
      HC05.println("Low signal sent");
      inputString="";
    }
    else if(inputString =="e"){
      inputString="";
      manString="";
    }
    else{
    inputString = "";//Clear buffer
    delay(3000);
    }
  }


  while(manString == "2"){

    if(a==1)
    {
      HC05.println("Automatic Mode Selected");
    }

    inputString="";
    int val = 0;
  for(int i = 0; i < 10; i++) {
      val += analogRead(lm35);
  }
       float temp = val*50.0f/1023.0f;
  Serial.println(temp);


  if(temp>35.0)
  {
    digitalWrite(13,HIGH);
  }
  else
  {
    digitalWrite(13,LOW);
  }
if(a==1)
{
  HC05.println("Please enter 'e' for exit");
}
a++;
  delay(1000);
  if(HC05.available())
  {
    while(HC05.available())
  {
      char exChar = (char)HC05.read(); //read the input
      inputString += exChar;        //make a string of the characters coming on serial
  }
  HC05.println(inputString);
  }
     if(inputString == "e")
     {
      manString ="";
      inputString ="";
     }
  }
  while(manString =="3"){
    HC05.println("Thank you for using this software");
    HC05.println("Made by Sanjoth Shaw");
    exit(0);
  }
}
