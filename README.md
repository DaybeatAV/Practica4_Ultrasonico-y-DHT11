Practica4_Ultrasonico-y-DHT11
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



```

2. El segundo paso será instalar la libreria de DHT sensor library for ESPx:



3. El segundo paso será instalar va ser instalar la libreria de LiquidCrystal I2C:



4. Acontinuación realizaremos la conexion del componente ```HC-SR04 ULTRASONIC Distance sensor``` con la tarjeta ```ESP32```:



5. Procederemos a crear la conexion entre la pantalla ```LCD I2C``` con la tarjeta ```ESP32```:



6. Por último vamos a proceder a realizar la conexion entre el Sensor ```DHT11``` con la tarjeta ```ESP32```:



### Instrucciónes de operación
1. El primer paso será entrar al simulador [WOKWI](https://wokwi.com/).

2. El siguiente paso será visualizar los datos arrojados en la pantalla ```LCD 16x2 (I2C)```.

3. Procederemos a colocar la temperatura y humedad deseada dando doble click al Sensor ```DHT11```.

4. Por último vamos a agregar una distancia dando doble click al Sensor ```Ultrasonico```.

## Resultados

El resultado final cuando la simulación haya funcionado, se verán los valores dentro de la pantalla ```LCD 16x2 (I2C)```:



### Evidencias



# Créditos

Desarrollado por **JOSE DAVID AYALA VILLALBA**

-[GITHUB](https://github.com/DaybeatAV)
