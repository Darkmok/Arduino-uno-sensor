const int Trigger = 6; //Pin digital 2 para el Trigger del sensor
const int Echo = 7; //Pin digital 3 para el Echo del 
const int pinBuzzer = 13;
#include <Adafruit_NeoPixel.h>
#include <LiquidCrystal.h>
#define PIN 9 //Pin Digital que se Utilizara
#define NUM_LEDS 16 //Cantidad de Luces Led
Adafruit_NeoPixel strip = Adafruit_NeoPixel(NUM_LEDS, PIN, NEO_GRB);
int sine[] = {0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15};
LiquidCrystal lcd(12,11,5,4,3,2);

void setup() {
  Serial.begin(9600);//iniciailzamos la comunicación
  pinMode(Trigger, OUTPUT); //pin como salida
  pinMode(Echo, INPUT); //pin como entrada
  digitalWrite(Trigger, LOW);//Inicializamos el pin con 0
  strip.begin();
strip.show(); // Iniciar los Pixels
strip.setBrightness(40); // 40/255 Intensidad del Brillo

//LCD
  lcd.begin(16,2);
  //indicamos el texto a mostrar al inicio

  lcd.setCursor(0,0);
  lcd.print("*** MEDIDOR ***");
  
}
void loop()
{
  long t; //tiempo que demora en llegar el eco
  long d; //distancia en centimetros
  digitalWrite(Trigger, HIGH);
  delayMicroseconds(10); //Enviamos un pulso de 10us
  digitalWrite(Trigger, LOW);
  t = pulseIn(Echo, HIGH); //obtenemos el ancho del pulso
  d = t/59; //escalamos el tiempo a una distancia en cm
  int R, G, B;
 if (d<20){
  R=255;
  G=0;
  B=0;
    tone(pinBuzzer, 650);
  delay(1000);
  }else{
    if (d>20 && d<30){
  R=0;
  G=255;
  B=0;
    tone(pinBuzzer, 450);
  delay(1000);
    } else {
      if (d>30 && d<50) {
         R=0;
  G=0;
  B=255;
    tone(pinBuzzer, 250);
  delay(1000);
      } else {
        R=0;
        G=0;
        B=0;
        noTone(pinBuzzer);
        delay(500);
      }
  }
  }
    uint32_t color =
strip.Color(R, G, B);
for(int i=15; i<16 && i>-1; i--) {
strip.setPixelColor(sine[i], color);
strip.show();
delay(40);
 }
  lcd.setCursor(0,1);
  lcd.print(d);
  lcd.print(" cm");
}
