
For an mx5 nb 1.6l:
`chp ~ 0.8 * rwhp`

My target is 230 rwhp so my chp needs to be: ~ 290
My current is 110 rwhp so my chp is ~ 140

`290 - 140 = 150`

considering 1 psi =  9 rwhp; 1psi = ~ 11.5 chp

I'm aiming for:
**13 psi boost**

`Pressure ratio = P2c / P1c`

Where:
`P2c = Boost Gauge Pressure (PSIg) + Absolute Atmospheric Pressure (PSIa)`
and
`P1c = (PSIa)  Absolute Atmospheric Pressure (PSIa) – 1 System Depression`

`P2c = 13 + 14.7 = 27.7`
`P1c = 14.7 - 1 = 13.7`

There for my pressure ratio needs to be:
`27.7/13.7 ~ 2.02`

## Calculating Air Flow 
`( Wa = HP x A/F x BSFC/60 )`

Where:
```
Wa = Air Flow Actual (lb/min)  
HP = Horsepower Target (crank)  
A/F = Air/Fuel Ratio  
BSFC/60 = Brake Specific Fuel Consumption
```

Brake Specific Fuel Consumption: (BSFC):
![[How-to-turbo-charts-BSFC-300x199.jpg]]

Seeming as mx5 is petrol we can use the value `0.46`

Air/Fuel Ratio (AFR):
The AFR defines the ratio of the amount of air consumed by the engine compared to the amount of fuel.
![[How-to-turbo-2-AFR-Chart-300x186.jpg]]

As we're using petrol, our AFR is 11.5.

Therefore our required airflow is:
`Wa = 290 * 11.5 * (0.46 / 60) ~ 25.56`

## Calculating required manifold pressure

![[Manifold-Pressure-Calculation-300x67.jpg]]

Engine Volumetric Efficiency: VE is how efficient an engine is at moving air through its cylinders

![[How-to-turbo-2-VE-Chart-300x142.jpg]]

Considering ours is a 4 valve per cylinder our VE is 0.9.

Intake Manifold Temperature: Compressors with higher efficiency produce lower manifold temperatures

- MAPreq = Manifold Absolute Pressure (psia) required to meet the horsepower target
- Wa = Air flow actual(lb/min) **25.6**
- R = Gas Constant = **639.6**
- Tm = Intake Manifold Temperature (degrees F) **175**
- VE = Volumetric Efficiency (2 valve LS engine) VE **0.90**
- N = Engine speed (RPM) **Max RPM 6500**
- Vd = engine displacement in cubic inches (convert liters to CI by multiplying 61.02. example. 1.6 liters x 61.02 = **98 CI)**

Our manifold pressure:

```
MAPreq = (25.6 * 639.6 * (360 + 175)) / (0.9 * (6500/2) * 98) ~ 30.6
```

## Considering Pressure Loss

One thing to note is the numbers above do not take into account  how much pressure loss exists between the compressor and manifold

![[MAP-pressure-calculation-Ploss-300x98.jpg]]

Assuming our pressure loss is ~4psi

- P2c = Compressor Discharge Pressure (psia)
- MAP = Manifold Absolute Pressure **30.6**
- ΔPloss = Pressure Loss Between the Compressor and the Manifold (psi) **4**

P2c = 30.6 + 4 = 34.6

Our new Pressure ratio will be:
Pr = `34.6 / 13.7 = 2.5`

![[Pressure-calculation-peak-torque-300x65.jpg]]

- **Our Example:**
- Wa = Airflow actual (lb/min)
- MAP = Manifold Absolute Pressure (psia) **30.6**
- R = Gas Constant = **639.6**
- Tm = Intake Manifold Temperature (degrees F) =**175**
- VE = Volumetric Efficiency **0.90**
- N = Engine speed (RPM) = **4200 RPM**
- Vd = engine displacement in cubic inches **98**

`Wa at 4200rpm = (30.6 * 0.9 * (4200/2) * 98) / (639.6 * (460 + 175)) = 13.95`
`Wa at 6500rpm = 25.56`