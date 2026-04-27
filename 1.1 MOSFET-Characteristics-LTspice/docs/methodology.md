.param W=360n

.param L=180n

.param Icon= 1u

.param Id\_target=Icon\*(W/L)

.meas DC Vth\_NMOS FIND V(N002) WHEN Id(M1)={Id\_target}

.meas DC Vgs\_at\_10u FIND V(N002) WHEN Id(M1)=10u



