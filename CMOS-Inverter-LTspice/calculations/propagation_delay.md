###### **\*\*\*\*\*\*\* Propagation Delay \*\*\*\*\*\*\***





*.meas time1 FIND time WHEN V(Vin) = 50% of Vdd  RISE=1*

*.meas time2 FIND time WHEN V(Vout) = 50% of Vdd FALL=1*

*.meas tPHL param time2-time1*

&#x20;

*.meas time3 FIND time WHEN V(Vin) = 50% of Vdd FALL=1*

*.meas time4 FIND time WHEN V(Vout) = 50% of Vdd RISE=1*

*.meas tPLH param time4-time3*

&#x20;

*.meas delay param (tPHL+tPLH)/2*



###### **\*\*\*\*\*\*\* Rise and Fall Time \*\*\*\*\*\*\***



*.meas timea FIND time WHEN V(Vout) = 0.9  FALL=1*

*.meas timeb FIND time WHEN V(Vout) = 0.1 FALL=1*

*.meas fall\_time param timeb-timea*

&#x20;

*.meas timec FIND time WHEN V(Vout) = 0.1 RISE=1*

*.meas timed FIND time WHEN V(Vout) = 0.9 RISE=1*

*.meas rise\_time param timed-timec*

