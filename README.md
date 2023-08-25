# HA-Inepro-PRO380-Mod
Enables reading out the MODBUS port on your Inepro PRO380-Mod via an ESPHome master. 

Add the sensorcode to your alraedy set up ESPHome ESP32 + RS485 and enjoy.

# Communication
Taken from the PRO380-Mod manual:
The PRO380-Mod can be connected for Modbus communication. The Modbus implementation used is Modbus basic
(standard). This means the following:
-Baud rate 9600
-8 data bits
-Even parity
-1 stop bit


![image](https://github.com/firefox159/HA-Inepro-PRO380-Mod-EN/assets/1909681/f381d220-45e3-4943-8905-0875409a08ef)

Following data is available in the meter:

Live values

| Reg. address | Content               | Function code | Register length | Unit | Data type | Format |
|--------------|-----------------------|---------------|-----------------|------|-----------|--------|
| 5000         | Voltage*              | 03            | 2               | V    | Float     | ABCD   |
| 5002         | L1 Voltage            | 03            | 2               | V    | Float     | ABCD   |
| 5004         | L2 Voltage            | 03            | 2               | V    | Float     | ABCD   |
| 5006         | L3 Voltage            | 03            | 2               | V    | Float     | ABCD   |
| 5008         | Grid frequency        | 03            | 2               | Hz   | Float     | ABCD   |
| 500A         | Current*              | 03            | 2               | A    | Float     | ABCD   |
| 500C         | L1 Current            | 03            | 2               | A    | Float     | ABCD   |
| 500E         | L2 Current            | 03            | 2               | A    | Float     | ABCD   |
| 5010         | L3 Current            | 03            | 2               | A    | Float     | ABCD   |
| 5012         | Total active power    | 03            | 2               | kW   | Float     | ABCD   |
| 5014         | L1 Active power       | 03            | 2               | kW   | Float     | ABCD   |
| 5016         | L2 Active power       | 03            | 2               | kW   | Float     | ABCD   |
| 5018         | L3 Active power       | 03            | 2               | kW   | Float     | ABCD   |
| 501A         | Total reactive power  | 03            | 2               | kvar | Float     | ABCD   |
| 501C         | L1 Reactive power     | 03            | 2               | kvar | Float     | ABCD   |
| 501E         | L2 Reactive power     | 03            | 2               | kvar | Float     | ABCD   |
| 5020         | L3 Reactive power     | 03            | 2               | kvar | Float     | ABCD   |
| 5022         | Total apparent power  | 03            | 2               | kVA  | Float     | ABCD   |
| 5024         | L1 Apparent power     | 03            | 2               | kVA  | Float     | ABCD   |
| 5026         | L2 Apparent Power     | 03            | 2               | kVA  | Float     | ABCD   |
| 5028         | L3 Apparent Power     | 03            | 2               | kVA  | Float     | ABCD   |
| 502A         | Power factor          | 03            | 2               | -    | Float     | ABCD   |
| 502C         | L1 Power factor       | 03            | 2               | -    | Float     | ABCD   |
| 502E         | L2 Power factor       | 03            | 2               | -    | Float     | ABCD   |
| 5030         | L3 Power factor       | 03            | 2               | -    | Float     | ABCD   |

Values that 'add up'

| Reg. address | Content                    | Function code | Register length | Unit  | Data type | Format |
|--------------|----------------------------|---------------|-----------------|-------|-----------|--------|
| 6000         | Total active energy        | 03            | 2               | kWh   | Float     | ABCD   |
| 6002         | T1 Total active energy     | 03            | 2               | kWh   | Float     | ABCD   |
| 6004         | T2 Total active energy     | 03            | 2               | kWh   | Float     | ABCD   |
| 6006         | L1 Total active energy     | 03            | 2               | kWh   | Float     | ABCD   |
| 6008         | L2 Total active energy     | 03            | 2               | kWh   | Float     | ABCD   |
| 600A         | L3 Total active energy     | 03            | 2               | kWh   | Float     | ABCD   |
| 600C         | Forward active energy      | 03            | 2               | kWh   | Float     | ABCD   |
| 600E         | T1 Forward active energy   | 03            | 2               | kWh   | Float     | ABCD   |
| 6010         | T2 Forward active energy   | 03            | 2               | kWh   | Float     | ABCD   |
| 6012         | L1 Forward active energy   | 03            | 2               | kWh   | Float     | ABCD   |
| 6014         | L2 Forward active energy   | 03            | 2               | kWh   | Float     | ABCD   |
| 6016         | L3 Forward active energy   | 03            | 2               | kWh   | Float     | ABCD   |
| 6018         | Reverse active energy      | 03            | 2               | kWh   | Float     | ABCD   |
| 601A         | T1 Reverse active energy   | 03            | 2               | kWh   | Float     | ABCD   |
| 601C         | T2 Reverse Active Energy   | 03            | 2               | kWh   | Float     | ABCD   |
| 601E         | L1 Reverse active energy   | 03            | 2               | kWh   | Float     | ABCD   |
| 6020         | L2 Reverse active energy   | 03            | 2               | kWh   | Float     | ABCD   |
| 6022         | L3 Reverse active energy   | 03            | 2               | kWh   | Float     | ABCD   |
| 6024         | Total reactive energy      | 03            | 2               | kvarh | Float     | ABCD   |
| 6026         | T1 Total reactive energy   | 03            | 2               | kvarh | Float     | ABCD   |
| 6028         | T2 Total reactive energy   | 03            | 2               | kvarh | Float     | ABCD   |
| 602A         | L1 Total reactive energy   | 03            | 2               | kvarh | Float     | ABCD   |
| 602C         | L2 Total reactive energy   | 03            | 2               | kvarh | Float     | ABCD   |
| 602E         | L3 Total reactive energy   | 03            | 2               | kvarh | Float     | ABCD   |
| 6030         | Forward reactive energy    | 03            | 2               | kvarh | Float     | ABCD   |
| 6032         | T1 Forward reactive energy | 03            | 2               | kvarh | Float     | ABCD   |
| 6034         | T2 Forward reactive energy | 03            | 2               | kvarh | Float     | ABCD   |
| 6036         | L1 Forward reactive energy | 03            | 2               | kvarh | Float     | ABCD   |
| 6038         | L2 Forward reactive energy | 03            | 2               | kvarh | Float     | ABCD   |
| 603A         | L3 Forward reactive energy | 03            | 2               | kvarh | Float     | ABCD   |
| 603C         | Reverse reactive energy    | 03            | 2               | kvarh | Float     | ABCD   |
| 603E         | T1 Reverse reactive energy | 03            | 2               | kvarh | Float     | ABCD   |
| 6040         | T2 Reverse reactive energy | 03            | 2               | kvarh | Float     | ABCD   |
| 6042         | L1 Reverse reactive energy | 03            | 2               | kvarh | Float     | ABCD   |
| 6044         | L2 Reverse reactive energy | 03            | 2               | kvarh | Float     | ABCD   |
| 6046         | L3 Reverse reactive energy | 03            | 2               | kvarh | Float     | ABCD   |
| 6048         | Tariff                     | 03            | 1               | -     | Signed    | -      |
| 6049         | Resettable day counter     | 03            | 2               | kWh   | Float     | ABCD   |
