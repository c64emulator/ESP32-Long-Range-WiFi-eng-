# ESP32-Long-Range-WiFi

Estos son las primeras pruebas con el protocolo propietario **802.11 LR (Long Range)** de espressif de las ESP32.
Los dispositivos utilizados son dos  [Wemos lolin32](https://wiki.wemos.cc/products:lolin32:lolin32), de las antiguas.
![](https://wiki.wemos.cc/_media/products:lolin32:lolon32_v1.0.0_1_16x9.jpg)

The scenario is the following:

* One of the lolin32 is configured as master in STA and AP mode. First it connects to the traditional router and obtains an IP from it. Then create an access point in 802.11 Long Range mode, with an ssid called "kkkkk". This access point is not visible by normal devices, since I don't think they can detect the protocol. The IP in mode is 192.168.4.1.

The master cyclically sends the 'b' command via UDP, to the broadcast address 192.168.4.255.

* The other lolin32 is configured as slave, in STA mode. It connects to the ssid "kkkkk" and obtains its IP, probably 192.168.4.2.
Every time the 'b' command arrives, the LED connected to GPIO5 changes state. If there is no reception there is no change.

To achieve a good range the two units must be in line of sight. The lolin32 antennas are of the [MIFA](https://en.wikipedia.org/wiki/Inverted-F_antenna) type and their maximum radiation is in this direction:

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRC79ql3CHAhfLjbrxUMksoLZ9WpQKKgsQRn848KdDWiLN4QdE_5A)

En una primera prueba, seguramente mejorable, he conseguido **294 m** de alcance. Espero superar esta distancia en algunos metros. 

Actualización **346 m**.
![](https://pbs.twimg.com/media/DiDnwA8X4AAGyLf.jpg)

Es de esperar que con antenas externas o direccionales se pudiera alcanzar el 1 kilómetro indicado por espressif. 

Se aceptan consejos y propuestas.
