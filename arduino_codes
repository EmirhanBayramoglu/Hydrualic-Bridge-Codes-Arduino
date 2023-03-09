//PID DC motor control library
#include <PID_v1.h>
//bluetooth library
#include <SoftwareSerial.h>
//servo library
#include <Servo.h>
//lcd library
#include <LiquidCrystal.h> 
//bluetooth module connections
#define BT_SERIAL_RX 0
#define BT_SERIAL_TX 1

//lcd connections
LiquidCrystal lcd(14, 50, 51, 48, 49, 46);
//bluetooth connection
SoftwareSerial BluetoothSerial(BT_SERIAL_RX, BT_SERIAL_TX);
//servo motor variable
Servo servo;

using namespace std;

//led connecitons green light red light for trafic light
int green = 52;
int red = 53;

//8 segment displays for Countdown

//variables for right 8 segment display
int upright = 26;
int up = 28;
int leftup = 30;
int mid = 32;
int letdown = 34;
int down = 36;
int rightdown = 38;

//variables for left 8 segment display
int uprightt = 27;
int upp = 29;
int leftupp = 31;
int midd = 33;
int letdownn = 35;
int downn = 37;
int rightdownn = 39;

//force sensor connections A0-A1-A2
int sens=A0;
int senss=A1;
int sensss=A2;
//force sensor calculation variable
int sens_deg=0;

//l298n to arduino connections motor speed and turn direction
int dc_pin=9;
int dc_pin2=10;

//calculate movement of motor (signal impact) 
signed long int darbe = 0; //impact
double referans = 0;
double sistem_konum; //system location
double kontrol_sinyali; //control signal

//dc motor connetion with arduino (encoder connection for calculate turning direction and amount of turn)
int encoder_a=2;
int encoder_b=3;


String konum=""; //location
char girilen_deger; //entered value
int start = 0;

const int buzzer = 5; //buzzer to arduino pin 5
//button for reset system 
int buttonState = 0; 
const int buttonPin = 6;
//b for some if statement entegration (b rising when force sensor pass certain value)
int b=0;

void timer()
{
    ooneON();
    zzero();
}

void one()
{
    digitalWrite(sagust,HIGH);
    digitalWrite(sagalt,HIGH);
    delay(1000);
    digitalWrite(sagust,LOW);
    digitalWrite(sagalt,LOW);
}
void two()
{
    digitalWrite(enust,HIGH);
    digitalWrite(orta,HIGH);
    digitalWrite(enalt,HIGH);
    digitalWrite(sagust,HIGH);
    digitalWrite(solalt,HIGH);
    delay(1000);
    digitalWrite(enust,LOW);
    digitalWrite(orta,LOW);
    digitalWrite(enalt,LOW);
    digitalWrite(sagust,LOW);
    digitalWrite(solalt,LOW);
}
void three()
{
    digitalWrite(enust,HIGH);
    digitalWrite(enalt,HIGH);
    digitalWrite(orta,HIGH);
    digitalWrite(sagust,HIGH);
    digitalWrite(sagalt,HIGH);
    delay(1000);
    digitalWrite(enust,LOW);
    digitalWrite(enalt,LOW);
    digitalWrite(orta,LOW);
    digitalWrite(sagust,LOW);
    digitalWrite(sagalt,LOW);
}
void four()
{
    digitalWrite(solust,HIGH);
    digitalWrite(sagust,HIGH);
    digitalWrite(orta,HIGH);
    digitalWrite(sagalt,HIGH);
    delay(1000);
    digitalWrite(solust,LOW);
    digitalWrite(sagust,LOW);
    digitalWrite(orta,LOW);
    digitalWrite(sagalt,LOW);
}
void five()
{
    digitalWrite(enust,HIGH);
    digitalWrite(orta,HIGH);
    digitalWrite(enalt,HIGH);
    digitalWrite(solust,HIGH);
    digitalWrite(sagalt,HIGH);
    delay(1000);
    digitalWrite(enust,LOW);
    digitalWrite(orta,LOW);
    digitalWrite(enalt,LOW);
    digitalWrite(solust,LOW);
    digitalWrite(sagalt,LOW);
}
void six()
{
    digitalWrite(enust,HIGH);
    digitalWrite(orta,HIGH);
    digitalWrite(solust,HIGH);
    digitalWrite(solalt,HIGH);
    digitalWrite(sagalt,HIGH);
    digitalWrite(enalt,HIGH);
    delay(1000);
    digitalWrite(enust,LOW);
    digitalWrite(orta,LOW);
    digitalWrite(solust,LOW);
    digitalWrite(sagalt,LOW);
    digitalWrite(enalt,LOW);
    digitalWrite(solalt,LOW);
}
void seven()
{
    digitalWrite(enust,HIGH);
    digitalWrite(sagust,HIGH);
    digitalWrite(sagalt,HIGH);
    delay(1000);
    digitalWrite(enust,LOW);
    digitalWrite(sagust,LOW);
    digitalWrite(sagalt,LOW);
}
void eight()
{
    digitalWrite(enust,HIGH);
    digitalWrite(orta,HIGH);
    digitalWrite(enalt,HIGH);
    digitalWrite(sagust,HIGH);
    digitalWrite(sagalt,HIGH);
    digitalWrite(solust,HIGH);
    digitalWrite(solalt,HIGH);
    delay(1000);
    digitalWrite(enust,LOW);
    digitalWrite(orta,LOW);
    digitalWrite(enalt,LOW);
    digitalWrite(sagust,LOW);
    digitalWrite(sagalt,LOW);
    digitalWrite(solust,LOW);
    digitalWrite(solalt,LOW);
}
void nine()
{
    digitalWrite(enust,HIGH);
    digitalWrite(sagalt,HIGH);
    digitalWrite(orta,HIGH);
    digitalWrite(sagust,HIGH);
    digitalWrite(enalt,HIGH);
    digitalWrite(solust,HIGH);
    delay(1000);
    digitalWrite(enust,LOW);
    digitalWrite(sagalt,LOW);
    digitalWrite(orta,LOW);
    digitalWrite(sagust,LOW);
    digitalWrite(enalt,LOW);
    digitalWrite(solust,LOW);
}
void zero()
{
    digitalWrite(enust,HIGH);
    digitalWrite(solust,HIGH);
    digitalWrite(solalt,HIGH);
    digitalWrite(sagust,HIGH);
    digitalWrite(sagalt,HIGH);
    digitalWrite(enalt,HIGH);
    delay(1000);
    digitalWrite(enust,LOW);
    digitalWrite(solust,LOW);
    digitalWrite(solalt,LOW);
    digitalWrite(sagust,LOW);
    digitalWrite(sagalt,LOW);
    digitalWrite(enalt,LOW);
}

void ooneON()
{
    digitalWrite(sagustt,HIGH);
    digitalWrite(sagaltt,HIGH);
    Serial.println("Last 19 seccond");
    nine();
    tone(buzzer, 5000);
    noTone(buzzer);
     Serial.println("Last 18 seccond");
    eight();
    tone(buzzer, 5000);
    Serial.println("Last 17 seccond");
    seven();
    noTone(buzzer);
    Serial.println("Last 16 seccond");
    six();
    tone(buzzer, 5000);
    Serial.println("Last 15 seccond");
    five();
    noTone(buzzer);
    Serial.println("Last 14 seccond");
    four();
    tone(buzzer, 5000);
    Serial.println("Last 13 seccond");
    three();
    noTone(buzzer);
    Serial.println("Last 12 seccond");
    two();
    tone(buzzer, 5000);
    Serial.println("Last 11 seccond");
    one();
    noTone(buzzer);
    Serial.println("Last 10 seccond");
    zero();
    digitalWrite(sagustt,LOW);
    digitalWrite(sagaltt,LOW);
    digitalWrite(enustt,HIGH);
    digitalWrite(enaltt,HIGH);
    digitalWrite(solustt,HIGH);
    digitalWrite(solaltt,HIGH);
    digitalWrite(sagustt,HIGH);
    digitalWrite(sagaltt,HIGH);
}
void twelve()
{
    digitalWrite(enustt,HIGH);
    digitalWrite(ortaa,HIGH);
    digitalWrite(enaltt,HIGH);
    digitalWrite(sagustt,HIGH);
    digitalWrite(solaltt,HIGH);
}

void zzero()
{
    digitalWrite(enustt,HIGH);
    digitalWrite(enaltt,HIGH);
    digitalWrite(solustt,HIGH);
    digitalWrite(solaltt,HIGH);
    digitalWrite(sagustt,HIGH);
    digitalWrite(sagaltt,HIGH);
    Serial.println("Last 9 seccond");
    nine();
    tone(buzzer, 5000);
    Serial.println("Last 8 seccond");
    noTone(buzzer); 
    eight();
    tone(buzzer, 5000);
    Serial.println("Last 7 seccond");
    seven();
    noTone(buzzer);
    Serial.println("Last 6 seccond");
    six();
    tone(buzzer, 5000);
    Serial.println("Last 5 seccond");
    five();
    noTone(buzzer);
    Serial.println("Last 4 seccond");
    four();
    tone(buzzer, 5000);
    Serial.println("Last 3 seccond");
    three();
    noTone(buzzer);
    Serial.println("Last 2 seccond");
    two();
    tone(buzzer, 5000);
    one();
    Serial.println("Last 1 seccond");
    noTone(buzzer);
    Serial.println("Count ended");
    zero();
    digitalWrite(enustt,LOW);
    digitalWrite(enaltt,LOW);
    digitalWrite(solustt,LOW);
    digitalWrite(solaltt,LOW);
    digitalWrite(sagustt,LOW);
    digitalWrite(sagaltt,LOW);
}
  void ooneOFF()
  {
    digitalWrite(sagustt,LOW);
    digitalWrite(sagaltt,LOW);
  }
  void ttwoOFF()
  {
    digitalWrite(enustt,LOW);
    digitalWrite(ortaa,LOW);
    digitalWrite(enaltt,LOW);
    digitalWrite(sagustt,LOW);
    digitalWrite(solaltt,LOW);
  }

//PID entegration
PID DC_hiz(&sistem_konum,&kontrol_sinyali,&referans,3,2,0,DIRECT);

void setup()
{
  lcd.begin(16,2);
  pinMode(26, OUTPUT);
  pinMode(27, OUTPUT);
  pinMode(28, OUTPUT);
  pinMode(29, OUTPUT);
  pinMode(30, OUTPUT);
  pinMode(31, OUTPUT);
  pinMode(32, OUTPUT);
  pinMode(33, OUTPUT);
  pinMode(34, OUTPUT);
  pinMode(35, OUTPUT);
  pinMode(36, OUTPUT);
  pinMode(37, OUTPUT);
  pinMode(38, OUTPUT);
  pinMode(39, OUTPUT);

  //leds connection
  pinMode(red, OUTPUT);
  pinMode(green, OUTPUT);
  digitalWrite(red, HIGH);
  digitalWrite(green, LOW);

  pinMode(buzzer, OUTPUT);
  pinMode(10, OUTPUT);
  pinMode(11, OUTPUT);
  servo.attach(7);
  servo.write(40);
  delay(2000);

  pinMode(buttonPin, INPUT_PULLUP);
  
  //bluetooth port entegration
  Serial.begin(9600);
  BluetoothSerial.begin(9600);
  
  //motor connection
  pinMode(dc_pin,OUTPUT);
  pinMode(dc_pin2,OUTPUT);
  
  //encoder entegration
  attachInterrupt(0,encoder_kesme_a,CHANGE);
  //speed limits (left and right side)
  DC_hiz.SetOutputLimits(-255,255);
  //delay for motor
  DC_hiz.SetSampleTime(5);
  DC_hiz.SetMode(AUTOMATIC);
  
  //force sensors entegration
  pinMode(sens,INPUT);
  pinMode(senss,INPUT);
  pinMode(sensss,INPUT);
  //lcd options
  lcd.setCursor(0,0); //first row
  lcd.print("   Welcome To");
  lcd.setCursor(0,1); //second row
  lcd.print(" MirEmi  Bridge ");
}

void loop()
{
  //servo entegration
  servo.write(80);
  buttonState = digitalRead(buttonPin);
  //force sensor values summation
  sens_deg =analogRead(senss)+analogRead(sens)+analogRead(sensss);
  
  if(sens_deg>60)
  {
    b++;  
  }
    if((sens_deg>=60 && b==5) || buttonState == LOW){
      analogWrite(dc_pin,abs(kontrol_sinyali));
    digitalWrite(dc_pin2,LOW);
      referans=-200;
      start = 0;
      lcd.clear();
      lcd.setCursor(0,0);
      lcd.print("Counter Started");
      lcd.setCursor(0,1);
      lcd.print("Bridge Will Open");
      timer();
      lcd.clear();
      lcd.setCursor(0,0);
      lcd.print(" Bridge Openning");
      lcd.setCursor(0,1);
      lcd.print("   Please Wait  ");
      Serial.println("Bridge is openning");
   }
   if(sistem_konum<=-200){
    if(start == 0)
    {
      
      digitalWrite(red, LOW);
      digitalWrite(green, HIGH);
      
      servo.write(25);
      digitalWrite(dc_pin,LOW);
      lcd.clear();
      lcd.setCursor(0,0);
      lcd.print("Bridge is Open");
      lcd.setCursor(0,1);
      lcd.print("Bridge'll Close");
      Serial.println("Bridge is open");
      timer();
      Serial.println("Bridge is closing");
      start=1;
    }
    referans=0;
    digitalWrite(red, HIGH);
    digitalWrite(green, LOW);
    lcd.clear();
    lcd.setCursor(0,0);
    lcd.print("   Welcome To");
    lcd.setCursor(0,1);
    lcd.print(" MirEmi  Bridge ");
   }
  DC_hiz.Compute();


  if(kontrol_sinyali < 0)
  {
    analogWrite(dc_pin,abs(kontrol_sinyali));
    digitalWrite(dc_pin2,LOW);
    }

  else
  {
    analogWrite(dc_pin2,kontrol_sinyali);
    digitalWrite(dc_pin,LOW);
    }
  
  //system location so showing your motor location (it can be your motor angle)
  sistem_konum = int(360*((darbe/(2*40*224.4-1))));

  //after certain point of system location this function will work
  if(abs(720*((darbe/(2*40*224.4-1))))>= 720)
  {
    darbe=0;
    }
    if(sistem_konum>-20 && referans==0){
      //these lines will show on bluetooth screen on your phone
     Serial.print("Bridge is close   ");
     Serial.print("The weight that you need % ");
     Serial.println((sens_deg*100)/60);
     delay(500);
    }
    
  
    Serial.flush();
}

//count to motor turn function
void encoder_kesme_a()
{
  if (digitalRead(encoder_a)==HIGH)
  {
    
    if (digitalRead(encoder_b)==HIGH)
      {
        darbe = darbe-1;
        }
    else
    {
      darbe++;
      }
      
    }
  else
  {
    if(digitalRead(encoder_b)==HIGH)
    {
      darbe++;
      }
      else
      {
        darbe = darbe -1;
        }
    }
  }
