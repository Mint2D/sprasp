# Sistemas Programables : Sensores

## Sensor UV Raspberry Pi utilizando la estación meteorológica VEML6075n.

Para hacer que todo este tutorial funcione, haremos uso de la librería VEML6075 de Adafruit. Esta librería se encarga de la mayor parte del trabajo haciendo todos los cálculos necesarios para calcular el índice UV y leer los valores UVA y UVB del sensor UV.El sensor UV VEML6075 es un sensor de doble banda que detecta las bandas de luz UVA (ultravioleta A/onda larga) y UVB (ultravioleta B/onda corta).
Una de las mejores cosas de este sensor es que proporciona sus datos a través del protocolo serie I2C, por lo que es muy sencillo interactuar con él.
Puedes combinar este sensor con muchos otros sensores que funcionan con la Raspberry Pi. Por ejemplo, usando una variedad de sensores, podrías construir tu propia estación meteorológica.

![VML.](https://pimylifeup.com/wp-content/uploads/2019/05/Raspberry-Pi-UV-Sensor-using-the-VEML6075-Thumbnail.jpg)

## Equipo
### A continuación encontrará una lista del equipo que puede necesitar para configurar el sensor UV VEML6075 con la Raspberry Pi.

* Raspberry Pi
* Tarjeta Micro SD (8GB+)
* Alambre para protoboard
* Sensor UV VEML6075
* Breadboard

## Conexiones

* Conecta el pin VIN del sensor UV VEML6075 al pin físico 1 (3v3) de la Raspberry Pi.
* Conecta el pin GND del sensor UV VEML6075 al pin físico 6 (GND) de la Raspberry Pi.
* Conecta el pin SDA del sensor UV VEML6075 al pin físico 3 (SDA) de la Raspberry Pi.
* Conecta el pin SCL del sensor UV VEML6075 al pin físico 5 (SCL) de la Raspberry Pi.

![Conexiones.](https://pimylifeup.com/wp-content/uploads/2019/05/Raspberry-Pi-VEML6075-UV-Sensor-Wiring-Schematic.png)

## Codigo
```
import time
import board
import busio
import adafruit_veml6075
i2c = busio.I2C(board.SCL, board.SDA)
veml = adafruit_veml6075.VEML6075(i2c, integration_time=100)
while True:
    print(veml.uv_index)
    time.sleep(1)
```
