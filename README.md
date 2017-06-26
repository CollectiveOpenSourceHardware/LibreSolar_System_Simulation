# LibreSolar System Simulation

Modelling and simulation of LibreSolar components and needed external components like solarpanels and battery cells to analyse the behaviour of the system

## System overview
![Simulation_System Overview](00_Documentation_Pictures/LS_SystemOverview.png)

#### Environment Generator:
function: Generates system parameter which influence the LibreSolar Box Components out of given values from the location profile

input:  Location Profile (city/geo_position, season, daytime)

output: irradience [W/m^2], temperature [celsius]

Solar:

input:      irradience [W/m^2], temperature [celsius], type (type [mono/poly/...], surface [m^2], nominal_values (Wp, V, I))
            alternative: data_sheet parameter -> nominal_values 
output:     voltage[V]
In/Output:  current [I]

Battery:
input:         type (...), nominal_values (capacity [Ah], voltage [V]), security_values/MinMax Value (...)
output:       Box Temp., voltage[V], SOC, SOH
in/output:   temperature [celsius], current [I]

Loads:
input:   time_using [h], voltage [V], current [I] //open question: does the Load System effects with V or I the Libre Solar System

LibreSolar (electronics):
input:       solar_voltage [V], Box Temp. [celsius]
output:     voltage[V], current[I],
in/output: solar_current [I], ... , comm_data (modi (used panels+batteries, system parameter settings -> needed voltage, power, energy)))

## Control Model
![Simulation_Control_Model](00_Documentation_Pictures/LS_ControlModel.png)

Communication Interface/ Stack:
HW: circuit for signal voltage level to 
Communication Parameters from Higher Control Level
-> Server
(-> Selfmanaged)
-> mobile Application
-> Grid Application

Signal Generator:
- MPPT Charger algorithm
- BMS algorithm

Systemmodel/Power Circuit:
- Power component -> Interface between µC and Energy HW (Solar, Batteries) -> Output1
- measurement component (scaled U, I) -> Output2

Event Generator:
- system states and 

## Hardware Model
![Simulation_Hardware_Model](00_Documentation_Pictures/LS_HWModel.png)
