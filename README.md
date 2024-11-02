# Adaptive Horn Control System
This project focuses on reducing noise pollution in traffic by developing an Adaptive Horn Control System. The system modifies the activation logic of a vehicle's horn based on its speed. Specifically, it ensures that only the low horn pad operates when the vehicle speed is below 15 km/h. This initiative aims to decrease sound intensity in congested areas, contributing to a quieter and more pleasant environment.
# Project Details

The Adaptive Horn Control System leverages the vehicle's Body Control Module (BCM) to control the horn pads based on real-time vehicle speed. By updating the BCM's code, the system determines which horn pad to activate:

Conditions:

Vehicle Speed < 15 kmph:

Activates Low Horn Pad Only: If the vehicle's speed is less than 15 kmph, only the low horn pad is activated by it's respective Relay - (Relay-1 in this case). This results in a quieter horn sound, which might be more appropriate for situations where a louder horn might be unnecessary or disruptive, such as in residential areas or crowded parking lots.

Vehicle Speed >= 15 kmph:

Activates Both Horn Pads: If the vehicle's speed is greater than or equal to 15 kmph, both the Relays are activated, which futher activates both low and high horn pads. This produces a louder horn sound, which is more effective in alerting other road users at higher speeds, especially in situations where a quieter horn might not be easily heard.

![Horn Control Flowchart](https://github.com/user-attachments/assets/ee5be1ef-dd5c-49e0-9dda-131e5079677b)

# Schematic and CAN Bus Integration
The diagram illustrates how the vehicle's Body Control Module (BCM) coordinates with the ECU (Here ABS is taken into consideration) and other components to control the horn's behavior based on vehicle speed.

Here's how it works:

Wheel Speed Sensor: This sensor continuously monitors the rotational speed of the wheels and transmits this information to the ABS ECU.

ABS ECU: The ABS ECU processes the wheel speed data to calculate the vehicle's speed. It then transmits this speed information over the CAN bus (CAN H and CAN L lines) to all the ECU's, but here we are taking BCM into consideration as it's the one which deals with the Horn system of the Vehicle.

BCM: The BCM receives the vehicle speed data from the ABS ECU. It uses this information to determine whether to activate the low horn pad or both horn pads, when the Horn Switch is pressed.

Horn Control: The BCM according to the condition, sends a signal to the horn control module.

Relay: The horn control module activates the appropriate relay, which in turn provides power to the selected horn pad. The Relay used here can be either 4-Pin or 5-Pin.

Horn Activation: The activated horn pad produces the desired horn sound.

__**Schematic**__ -  [https://tinyurl.com/2adpjyzu](https://tinyurl.com/2a2w33q8) (The Horn Pad is a Push Switch) 

![Architecture](https://github.com/user-attachments/assets/26886448-3d02-4fc6-8f21-6b00f2539533)




# Safety Precautions
The chosen speed threshold of 15 km/h aligns with typical urban traffic speeds in India, as highlighted by traffic studies. This threshold strikes a balance between maintaining safety and reducing noise pollution.

Article - https://www.indiatoday.in/india/story/bengaluru-traffic-speed-mumbai-delhi-average-traffic-speed-2497696-2024-02-05

The system ensures that the horn's functionality is not compromised in situations requiring more audible alerts (i.e., at speeds above 15 km/h).

