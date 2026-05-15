/*
========================================
HAPTIC PROXIMITY WEARABLE SYSTEM
========================================

Components:
- Arduino
- HC-SR04 Ultrasonic Sensor
- Vibration Motor

Behavior:
Distance controls vibration intensity
and pulse speed.

========================================
*/

// -------------------------------
// PIN DEFINITIONS
// -------------------------------

const int trigPin = 9;
const int echoPin = 10;
const int motorPin = 3;

// -------------------------------
// DISTANCE VARIABLES
// -------------------------------

long duration;
float distance;

// -------------------------------
// TIMING VARIABLES
// -------------------------------

unsigned long currentMillis;
unsigned long previousMillis = 0;

// -------------------------------
// SETUP
// -------------------------------

void setup()
{
    pinMode(trigPin, OUTPUT);
    pinMode(echoPin, INPUT);
    pinMode(motorPin, OUTPUT);

    Serial.begin(9600);

    Serial.println("Haptic Wearable System Started");
}

// -------------------------------
// MAIN LOOP
// -------------------------------

void loop()
{
    distance = getDistance();

    Serial.print("Distance: ");
    Serial.print(distance);
    Serial.println(" cm");

    hapticFeedback(distance);

    delay(30);
}

// -------------------------------
// DISTANCE FUNCTION
// -------------------------------

float getDistance()
{
    // Clear trigger
    digitalWrite(trigPin, LOW);
    delayMicroseconds(2);

    // Send pulse
    digitalWrite(trigPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(trigPin, LOW);

    // Read echo
    duration = pulseIn(echoPin, HIGH, 30000);

    // Timeout protection
    if (duration == 0)
    {
        return 400;
    }

    // Convert to cm
    float dist = duration * 0.0343 / 2;

    return dist;
}

// -------------------------------
// HAPTIC FEEDBACK SYSTEM
// -------------------------------

void hapticFeedback(float dist)
{
    // VERY CLOSE
    if (dist < 20)
    {
        analogWrite(motorPin, 255);
    }

    // CLOSE
    else if (dist < 50)
    {
        pulseMotor(220, 100);
    }

    // MEDIUM
    else if (dist < 100)
    {
        pulseMotor(180, 250);
    }

    // FAR
    else if (dist < 150)
    {
        pulseMotor(120, 500);
    }

    // OUT OF RANGE
    else
    {
        analogWrite(motorPin, 0);
    }
}

// -------------------------------
// MOTOR PULSE FUNCTION
// -------------------------------

void pulseMotor(int strength, int interval)
{
    currentMillis = millis();

    if (currentMillis - previousMillis >= interval)
    {
        previousMillis = currentMillis;

        static bool motorState = false;

        motorState = !motorState;

        if (motorState)
        {
            analogWrite(motorPin, strength);
        }
        else
        {
            analogWrite(motorPin, 0);
        }
    }
}
