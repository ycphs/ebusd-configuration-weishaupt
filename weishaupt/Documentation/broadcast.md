# type (r[1-9];w;u),class,name,comment,QQ,ZZ,PBSB,ID,field,part (m/s),type / templates,divider / values,unit,comment,field,part (m/s),type / templates,divider / values,unit,comment,field,part (m/s),type / templates,divider / values,unit,comment,field,part (m/s),type / templates,divider / values,unit,comment
*b,broadcast,,,,FE,,,,,,,,,,,,,,,,,,,,,,,,,,

#
# 500A - Prozesswerte des Heizungsreglers/Feuerungsautomaten
# Dieses Telegramm wird vom Heizungsregler/Feuerungsautomaten per Broadcast gesendet.
#
# M1  QQ   F1h Quelladresse
# M2  ZZ = FEh Zieladresse -> Broadcast
# M3  PB = 50h
# M4  SB = 0Ah
# M5  NN = 0Dh Datenlänge -> 14                                                  Aus 00_WTCX5.pm
# M6       0Dh Status0                                                           10: 
# M7       06h Betriebsphase (->I10)        betriebsphase (-> _templates.csv)    12: TStatus
# M8       7Fh Status2                                                           14: TStatusA
# M9       42h Status3                                                           16: TStatusB - TStatusWW+TStatusSommerWinter (0=Sommer,2=Winter)
# M10      20h Laststellung (->I11)         uch                                  18: T_P
# M11      6ah Wassertemp                   data1c (0..100 / 0.5) -> 53°C        20: Vorlauf
# M12      ffh ECS (Exhaust Control System) data1C (0..100 / 0.5) -> --          22:
# M13      68h                                                                   24: TWWasser
# M14      00h                                                                   26:
# M15      0bh Ext Temp                     data1b (-127..127 / 1)-> 11          28: TAussen
# M16      e1h Lsb Simulated Floating Point Ext measure data2b   -> Trend
# M17      0ah Msb Simulated Floating Point Ext measure data2b   -> Trend
# M18      36h
b,,IstWerte,Broadcast mit Istwerten,,,500a,,Status0,,UCH,,,Status ,Betriebsphase,,operatingphase,,,Status ,Status2,,UCH,,,Status ,Status3,,UCH,,,Status ,Laststellung,,UCH,,,Laststellung ,T_Water,,temp1,,,Wassertemperatur ,T_ECS,,temp1,,,ECS-Temperatur ,T_Temp1,,temp1,,,Temp ,T_Temp2,,temp1,,,Temp ,T_Out,,ctemp1,,,Außentemperatur ,T_Trend,,temp2,,,Trend ,T_Temp3,,temp0,,,Temp