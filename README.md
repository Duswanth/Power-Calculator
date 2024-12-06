# Power-Calculator
Simple IoT project dealing with calculating Household or Industrial power usage and cost using ArduinoIDE and Proteus Design Suit softwares.                                                  

Use an Arduino connected to voltage and current sensors, which measures the used power over a period of time. The program calculates the power, integrates it over time to find energy, and computes the cost based on specific charge per kWh. Let us assume Rs.6 for 1 kWh enrgy. The results are displayed on an OLED display connected to the Arduino with I2C protocol.              

1.Hardware Requirements                                                                                                                                                                      
-->Arduino (e.g., Uno or Nano)                                                                                                                                                               
-->Voltage sensor (e.g., Voltage Divider Circuit or Analog Voltage Sensor like ZMPT101B)                                                                                                     
-->Current sensor (e.g., ACS712 or similar)                                                                                                                                                  
-->OLED Display Module (e.g., SSD1306 128x64)                                                                                                                                                
-->Solar Panel with the given specifications                                                                                                                                                 
-->Connecting wires, resistors for the voltage divider, etc.                                                                                                                                 

2.Implementation
Voltage Divider Circuit for Voltage Measurement:                                                                                                                                             
Reduce the supply voltage (120V) to the Arduino ADC range (0-5V).                                                                                                                          
Use two resistors  R1 and 𝑅2 in series.                                                                                                                                                   
The scaling factor:                                                                                                                                                                        
“Vout​<=Vin​× { R2 / (R1+​R2) }​​”                                                                                                                                                              
Ensure  that  𝑉𝑜𝑢𝑡 ≤ 5.0𝑉 for 𝑉𝑖𝑛=120                                                                                                                                                      
Calculate the R2/R1 ratio according to your specifications, for ex. supply voltage may vary (120V, 240V, etc.) also some ADC voltage range may be 0-6V.                                    

3.Current Measurement:                                                                                                                                                                     
Use a current sensor like ACS712 (20A variant).                                                                                                                                            
The output voltage of ACS712 is directly proportional to the current.                                                                                                                      
Power Calculation:                                                                                                                                                                         
P(t)=V(t)×I(t)                                                                                                                                                                            
                                                                                                                                                                                          
4.Energy Calculation:                                                                                                                                                                      
Energy is calculated by summing power over time:                                                                                                                                           
E=∫P(t)dt                                                                                                                                                                                  
Implemented as:                                                                                                                                                                            
E += P(t)×Δt                                                                                                                                                                               
                                                                                                                                                                                           
5.Cost Calculation:                                                                                                                                                                        
Cost = 𝐸×6 (Rs.)                                                                                                                                                                          

6.Steps to Use                                                                                                                                                                             
-->Calibrate the voltage divider and current sensor.                                                                                                                                       
-->Connect the sensors to the Arduino in Proteus software or in physically.                                                                                                                
-->Write the code to the ArduinoIDE and upload to the Arduino board.                                                                                                                       
-->To run the connected circuit in proteus, copy the .hex file path in ArduinoIDE after compailing.                                                                                        
-->Paste the .hex file path in the board's program file box in the proteus software and run it.                                                                                            
-->Observe the energy and Cost data on the OLED display.                                                                                                                               
-->This program calculates energy consumption and displays it's Cost for a period of 15 days accurately.                                                                         
