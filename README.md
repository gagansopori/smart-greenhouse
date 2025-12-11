# smart-greenhouse

smart-greenhouse is a cost-effective, IoT driven micro-ecosystem that helps maximize crop yield & helps plants 
survive harsh climactic conditions. The project focuses on optimizing conditions that are of significant impact for crop 
yield as well as for plant health. It uses a combination of 3 control-systems to achieve this:
 - Climate Control System
 - Irrigation/Nutrient Cycling System
 - Lighting Control System

### Climate Control System
This subsystem monitors and corrects the greenhouse's internal climate based on the following 5 factors: 
 - Temperature
   - Optimal Range for growth: 65°F to 85°F
   - Temperatures trigger the mini-HVAC system (forced air heater or cooling fans) when temps go out of range.
 - Humidity
   - Optimal humidity levels: 40% to 70%
   - Extended drought like conditions (48-72 hrs) trigger misting pump to maintain moist air. 
 - CO2 Levels
   - Higher CO2 levels -> Faster Photosynthesis -> Faster Growth
 - NH3 Levels
   - High levels are dangerous to plants but, controlled levels help with the yield.
   - Triggers ventilation for high levels & misting for lower levels.
 - Pressure
   - Monitor and log for analytics. No active control.

### Irrigation/Nutrient Cycling System
This subsystem monitors the soil moisture levels using capacitive sensors & provide the plants with nutrients & water 
in the following way: 
 - Greenhouse is divided into multiple zones & each zone is assigned the following:
   - Soil moisture sensor
   - PWM Water pump (PWM pumps can alter speed) corresponding to the sensor. 
   - Nutrient reservoir with a pump that can mix nutrients in the water tank. 
 - Each sensor has a pump dedicated to it Soil moisture levels < threshold -> Pump triggered to water the soil region of soil/pot. 