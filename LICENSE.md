
#define TouchSensor 2 

int relay = 8; 

boolean currentState = LOW;
boolean lastState = LOW;
boolean RelayState = LOW;
 
void setup() {
  Serial.begin(9600);
  pinMode(relay, OUTPUT);  
  pinMode(TouchSensor, INPUT);
}
 
void loop() {
  currentState = digitalRead(TouchSensor);
    if (currentState == HIGH && lastState == LOW){
    Serial.println("pressed");
    delay(1);
    
    if (RelayState == HIGH){
      digitalWrite(relay, LOW);
      RelayState = LOW;
    } else {
      digitalWrite(relay, HIGH);
      RelayState = HIGH;
    }
  }
  lastState = currentState;
}
