##### **\*\*\*\*\* Noise Margin \*\*\*\*\***



*.meas VOH MAX V(Vout)*

&#x20;

*.meas VOL MIN V(Vout)*

&#x20;

&#x20;

*.meas VIL FIND V(Vin) WHEN d(V(Vout))=-1 CROSS=1*

&#x20;

*.meas VIH FIND V(Vin) WHEN d(V(Vout))=-1 CROSS=2*

&#x20;

&#x20;

*.meas NML PARAM VIL - VOL*

&#x20;

*.meas NMH PARAM VOH - VIH*

