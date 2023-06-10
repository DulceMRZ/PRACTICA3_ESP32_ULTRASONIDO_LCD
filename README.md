# Practica 3_ ESP32 con DTH22 con Ultrasonido + LCD


En esta práctica podemos programar una ESP32 con un ultrasonido, con visualización en datos en LCD.

## Contenido 

- Introducción 
- Objetivo
- Material Requerido
- Procedimiento 
- Instrucciones de operación 
- Resultados 



## 1. Introducción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un ultrasonido (```HC-SR04 Ultrasonic distance sensor```).
### 1.1 Descripción
  
 
 ### 1.2 Especificación 
 Es importante considerar que esta practica se estara realiando en un simulador llamado [WOKWI](https://https://wokwi.com/).

## 2. Objetivo 

Poder diseñar un diagrama con HC-SR04 Ultrasonic distance sesor, mediante la utilización de una ESP32.


## 3. Material Requerido

Tomar en cuenta el material necesario para realizar esta práctica:

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor de ultrasonido de distancia 
  (HC-SR04 Ultrasonic distance sensor)
- LCD 16x2 (I2C)



## 4. Procedimiento a realizar 

 - Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


## Paso 1 

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

lcd.setCursor(0, 0);
  lcd.print("Practica2 DTH22_LCD      " );
  lcd.setCursor(0, 1);
  lcd.print(" Dulce M                      " );

  delay(1000);

}
```


## Paso 2 

2. Instalar la libreria de **DHT sensor library for ESPx** como se muestra en la siguente imagen.

![](https://github.com/DulceMRZ/PRACTICA3_ESP32_ULTRASONIDO_LCD/blob/main/PRACTICA%203%20ESP32%20ULTRASONIDO%20+%20LCD%20-%20Wokwi%20ESP32,%20STM32,%20Arduino%20Simulator%20-%20Google%20Chrome%2010_06_2023%2009_05_53%20a.%20m..png?raw=true)

## Paso 3

3. Hacer la conexion de **DHT22** con la **ESP32** como se muestra en la siguentes imagenes:

3.1 Es importante considerar que para **ESP32** se maneja un ```Voltaje de trabajo 3.3 VDC```. 

a) Observar conexión de  **ESP32**. 

![](https://github.com/DiegoJm10/PracticaESP32conULTRASONICO/blob/main/ESP32%20ULTRASONICO%20-%20Wokwi%20ESP32,%20STM32,%20Arduino%20Simulator%20-%20Google%20Chrome%2009_06_2023%2008_32_06%20a.%20m..png?raw=true)

b) Conexión de pin 2 (GND) 


![](e)

c) Conexión pin 3 (pin 15) 


![]()

d) Conexión de LCD 


![](https://github.com/DulceMRZ/PRACTICA_2_DHT22_CON_LCD/blob/main/Captura3.PNG?raw=truee)



e) Conexión de LCD más ESP32 y SENSOR

![](https://github.com/DulceMRZ/PRACTICA3_ESP32_ULTRASONIDO_LCD/blob/main/Captura1.PNG?raw=true)



### 5. Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la temperatura y humedad dando *doble click* al sensor **** 

## 6. Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en la siguente imagen.

![]()

![](https://github.com/DulceMRZ/PRACTICA3_ESP32_ULTRASONIDO_LCD/blob/main/Captura2.PNG?raw=true)
 
 **Comenatrio adicional**: Puedes programar la información de la siguiente manera: 
 
![](https://github.com/DulceMRZ/PRACTICA_2_DHT22_CON_LCD/blob/main/Captura6.PNG?raw=true)


![](https://github.com/DulceMRZ/PRACTICA_2_DHT22_CON_LCD/blob/main/Captura4.PNG?raw=true)

#### Nota: Tu puedes cambiar la información a imprimir


# Créditos

Desarrollado por Dulce M Rodriguez Zarate 

- [GitHub](https://github.com/DulceMRZ)