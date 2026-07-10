# Line-following-robot

Arduino code ;
// Define motor control pins
#define ENA 10
#define ENB 5
#define IN1 9
#define IN2 8
#define IN3 7
#define IN4 6

// Define IR sensor pins
#define LEFT_SENSOR A0
#define RIGHT_SENSOR A1

void setup() {
  // Set motor control pins as outputs
  pinMode(ENA, OUTPUT);
  pinMode(ENB, OUTPUT);
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);

  // Set sensor pins as inputs
  pinMode(LEFT_SENSOR, INPUT);
  pinMode(RIGHT_SENSOR, INPUT);

  // Initialize motor speed
  analogWrite(ENA, 255); // Full speed
  analogWrite(ENB, 255); // Full speed
}

void loop() {
  // Read sensor values
  int leftSensor = digitalRead(LEFT_SENSOR);
  int rightSensor = digitalRead(RIGHT_SENSOR);

  // Determine robot movement based on sensor values
  if (leftSensor == LOW && rightSensor == LOW) {
    // Move forward
    moveForward();
  } else if (leftSensor == LOW && rightSensor == HIGH) {
    // Turn right
    turnRight();
  } else if (leftSensor == HIGH && rightSensor == LOW) {
    // Turn left
    turnLeft();
  } else {
    // Stop (both sensors detect white)
    stop();
  }
}

void moveForward() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
}

void turnRight() { 
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, LOW);
  
}

void turnLeft() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
 
}

void stop() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, LOW);
}
