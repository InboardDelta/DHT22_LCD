# PRACTICA ESP32 CON DHT22 Y LCD
Este repositorio muestra como podemos programar una ESP32 con el sensor DHT22 y un LCD el cual programaremos con los valores pedidos por el docente.
## MATERIAL NECESARIO

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor DHT22
- Pantalla LCD (```16x2 I2C```)
## INTRODUCCION
### DESCRIPCION
La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```DTH22```) para adquirir temperatura y humedad del entorno; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/). 
### INSTRUCCIONES
1. Abrir la terminal de programación y colocar la siguente programación:

```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");

  delay(1000);
}
```
2.- Se buscaran las herramientas necesarias en el programa como : **DTH22** y **LCD 16x2 (I2C)** como se muestra en la imagen.
![](https://github.com/InboardDelta/DHT22_LCD/blob/main/COMPONENTES.png?raw=true)

3.- Realizaremos las conexiones de el sensor **DTH22** y la pantalla **LCD 16x2 (I2C)** como se muestra en la imagen.
![](https://github.com/InboardDelta/DHT22_LCD/blob/main/CONEXIONES.png?raw=true)
4. Instalaremos las librerias de **DHT sensor library for ESPx** y **LiquidCrystal I2C** como se muestra en la siguente imagen.
![](https://github.com/InboardDelta/DHT22_LCD/blob/main/LIBRERIAS.png?raw=true)

## RESULTADOS
Cuando haya funcionado, verás los valores dentro del monitor serial considerando que tendremos los valores de temperatura y adicionalmente una segunda valor el cual se agrego a consideración del alumno como se muestra en las siguentes imagenes.
![](https://github.com/InboardDelta/DHT22_LCD/blob/main/TEMP.png?raw=true)
![](https://github.com/InboardDelta/DHT22_LCD/blob/main/NAME.png?raw=true)
# Comentarios del alumno
Esta practica nos mostro la programación, conexión y funcionamiento de un sensor en conjunto con una pantalla LCD para obtener un valor del sensor y mostrarlo en la pantalla e igualmente poder imprimir en la pantalla un texto predeterminado por el alumno.

# Créditos

Desarrollado por RODRIGO VEGA
- [GitHub](https://github.com/InboardDelta)