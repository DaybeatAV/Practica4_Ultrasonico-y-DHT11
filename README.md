# Práctica 4 Ultrasónico y DHT22
En este repositorio se mostrará cómo programar un Sensor DHT, una pantalla LCD y un Ultrasónico.

## INTRODUCCION

### DESCRIPCION

Vamos a utilizar una tarjeta ```ESP32``` en un entorno de adquision de datos, por lo cual en esta práctica utilizaremos un Sensor ```DTH11``` para obtener temperatura y humedad del entorno, además tendremos que usar un Sensor ```Ultrasonico``` para medir distancia; como en las anteriores prácticas se va a volver a utilizar el simulador [WOKWI](https://wokwi.com/).
Además se añadirá una pantalla ```LCD I2C``` para monitorear dichos datos en cada cierto intervalo de tiempo.

## MATERIAL NECESARIO

Se necesitará de lo siguiente para poder realizar la práctica:

- Simulador [WOKWI](https://wokwi.com/)

- Una tarjeta ```ESP32```

- Un Sensor ```DHT11```

- Una pantalla ```LCD 16X2 (I2C)```

- Un componente ```HC-SR04 ULTRASONIC Distance sensor``` (Ultrasónico).

## INSTRUCCIONES

### Requisitos previos

Es necesario utilizar el simulador [WOKWI](https://wokwi.com/) para poder ejecutar este repositorio.

### Instrucciones de preparación de entorno

1. El primer paso será abrir la terminal de programación y colocar la siguente programación ya en dentro del simulador [WOKWI](https://wokwi.com/):

```

#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4
#include "DHTesp.h"
const int Trigger = 4;   //Pin digital 2 para el Trigger del sensor
const int Echo = 15;   //Pin digital 3 para el Echo del sensor
const int DHT_PIN = 16;
DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {
  Serial.begin(9600);//iniciailzamos la comunicación
  pinMode(Trigger, OUTPUT); //pin como salida
  pinMode(Echo, INPUT);  //pin como entrada
  digitalWrite(Trigger, LOW);//Inicializamos el pin con 0
  lcd.init();
  lcd.backlight();
   dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
}

void loop()
{
TempAndHumidity  data = dhtSensor.getTempAndHumidity();
 
  long t; //timepo que demora en llegar el eco
  long d; //distancia en centimetros

  digitalWrite(Trigger, HIGH);
  delayMicroseconds(10);          //Enviamos un pulso de 10us
  digitalWrite(Trigger, LOW);
  
  t = pulseIn(Echo, HIGH); //obtenemos el ancho del pulso
  d = t/59;             //escalamos el tiempo a una distancia en cm
  
  Serial.print("Distancia: ");
  Serial.print(d);      //Enviamos serialmente el valor de la distancia
  Serial.print("cm");
  Serial.println();
  delay(1000);          //Hacemos una pausa de 100ms

  lcd.setCursor(4, 0);
  lcd.print("DIPLOMADO");
  lcd.setCursor(2, 1); 
  lcd.print("AUTOMATIZACION");
   delay(2000);
  lcd.clear();

   lcd.setCursor(1, 0);
  lcd.print("JOSE DAVID A.V");
  lcd.setCursor(4, 1); 
  lcd.print("MECANICO");
   delay(2000);
  lcd.clear();
   lcd.setCursor(3, 0);
  lcd.print("07-06-2025");
  delay(2000);
  lcd.clear();
  
  
  lcd.setCursor(2, 0);
  lcd.print("DISTANCIA: " + String(d) + "cm");
  
  delay(2000);
  lcd.clear();
  
  lcd.setCursor(2, 0);
  lcd.print("Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(2, 1); 
  lcd.print("Humidity: " + String(data.humidity, 1) + "% ");
 
  delay(2000);
  lcd.clear();
}

```

2. El segundo paso será instalar la librería de DHT sensor library for ESPx:

![](https://github.com/DaybeatAV/Practica4_Ultrasonico-y-DHT11/blob/main/Pr%C3%A1ctica%204%20Librer%C3%ADa%20DHT%20Sensor.png)

3. El segundo paso será instalar va ser instalar la librería de LiquidCrystal I2C:

![](https://github.com/DaybeatAV/Practica4_Ultrasonico-y-DHT11/blob/main/Pr%C3%A1ctica%204%20Librer%C3%ADa%20LyquidCrystal%20I2C.png)

4. Acontinuación realizaremos la conexion del componente ```HC-SR04 ULTRASONIC Distance sensor``` con la tarjeta ```ESP32```:

![](https://github.com/DaybeatAV/Practica4_Ultrasonico-y-DHT11/blob/main/Pr%C3%A1ctica%204%20Conexi%C3%B3n%20Ultras%C3%B3nico.png)

5. Procederemos a crear la conexion entre la pantalla ```LCD I2C``` con la tarjeta ```ESP32```:

![](https://github.com/DaybeatAV/Practica4_Ultrasonico-y-DHT11/blob/main/Pr%C3%A1ctica%204%20Conexi%C3%B3n%20LCD%20(I2C).png)

6. Por último vamos a proceder a realizar la conexion entre el Sensor ```DHT22``` con la tarjeta ```ESP32```:

![](https://github.com/DaybeatAV/Practica4_Ultrasonico-y-DHT11/blob/main/Pr%C3%A1ctica%204%20Conexi%C3%B3n%20DHT%20Sensor.png)

### Instrucciónes de operación
1. El primer paso será entrar al simulador [WOKWI](https://wokwi.com/).

2. El siguiente paso será visualizar los datos arrojados en la pantalla ```LCD 16x2 (I2C)```.

3. Procederemos a colocar la temperatura y humedad deseada dando doble click al Sensor ```DHT11```.

4. Por último vamos a agregar una distancia dando doble click al Sensor ```Ultrasonico```.

## Resultados

El resultado final cuando la simulación haya funcionado, se verán los valores dentro de la pantalla ```LCD 16x2 (I2C)```:

![](https://github.com/DaybeatAV/Practica4_Ultrasonico-y-DHT11/blob/main/Pr%C3%A1ctica%204%20Resultado%20Final.png)

### Evidencias

![](https://github.com/DaybeatAV/Practica4_Ultrasonico-y-DHT11/blob/main/Pr%C3%A1ctica%204%20Evidencia%201.png)
![](https://github.com/DaybeatAV/Practica4_Ultrasonico-y-DHT11/blob/main/Pr%C3%A1ctica%204%20Evidencia%202.png)

# Créditos

Desarrollado por **JOSE DAVID AYALA VILLALBA**

-[GITHUB](https://github.com/DaybeatAV)
