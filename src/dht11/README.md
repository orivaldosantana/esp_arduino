# DHT11 - Sensor de temperatura

Este código é para realizer um teste básico de leitura de um sensor de temperatura ambiente, DHT11. Para mais detalhes ver o vídeo neste [link](https://youtu.be/XGheCgyzBLo). 

## Componentes 
* NodeMCU ESP32 
* Sensor, DHT11, de temperatura  

## Ligações 
Circuito básico: 

A tabela abaixo ilustra o uso dos jumpers para conectar o sensor à placa NodeMCU ESP32. 

| Sensor DS18B20 | ESP32 |
| --------------- | --------------- | 
| -  | GND  | 
|  + | 3.3v | 
| S  | 23 | 

## Código Básico 
Este código configura o pino GPIO23 como entrada do sinal lido do sensor dht11. 

```cpp
#include "DHT.h"
 
#define DHTPIN 23 
#define DHTTYPE DHT11 // DHT 11
 

DHT dht(DHTPIN, DHTTYPE);
 
void setup() 
{
  Serial.begin(9600);
  Serial.println("DHTxx test!");
  dht.begin();
}
 
void loop() 
{
 
  float h = dht.readHumidity();
  float t = dht.readTemperature();
  // testa se retorno é valido, caso contrário algo está errado.
  if (isnan(t) || isnan(h)) 
  {
    Serial.println("Falha na leitura do sensor DHT");
  } 
  else
  {
    Serial.print("Umidade: ");
    Serial.print(h);
    Serial.print("  ");
    Serial.print("Temperatura: ");
    Serial.print(t);
    Serial.println(" *C");
  }
  delay(1000);
}
```
 
## Referências 
 
* [ESP8266 DHT11/DHT22 Temperature and Humidity Web Server with Arduino IDE](https://randomnerdtutorials.com/esp8266-dht11dht22-temperature-and-humidity-web-server-with-arduino-ide/)
* [Monitorando Temperatura e Umidade com o sensor DHT11](https://www.makerhero.com/blog/monitorando-temperatura-e-umidade-com-o-sensor-dht11/)
* https://RandomNerdTutorials.com 
* [Vídeo testando o sensor de temperatura ambiente com Arduino IDE e ESP]( ) 
