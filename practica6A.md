# Pràctica 6

## Practica 6A: Lectura de SD

### Objectiu
Comprendre el funcionament del bus spi

### Codi

```cpp
#include <SPI.h> 
#include <SD.h> 
File myFile; 
void setup() 
{ 
Serial.begin(9600); 
Serial.print("Iniciando SD ..."); 
if (!SD.begin(4)) { 
Serial.println("No se pudo inicializar"); 
return; 
} 
Serial.println("inicializacion exitosa");   
myFile = SD.open("archivo.txt");//abrimos  el archivo  
  if (myFile) { 
    Serial.println("archivo.txt:"); 
    while (myFile.available()) { 
     Serial.write(myFile.read()); 
    } 
    myFile.close(); //cerramos el archivo 
  } else { 
    Serial.println("Error al abrir el archivo"); 
  } 
} 
 
void loop() 
{ 
   
} 
```

### Sortida pel port sèrie

La sortida pel port sèrie contindrà informació sobre l'estat d'inicialització de la targeta SD i el contingut del fitxer si l'inicialització i l'obertura del fitxer són exitoses.

Exemple de Sortida pel Port Sèrie:

Iniciando SD ...
inicializacion exitosa
archivo.txt:
Hola, aquest és el contingut del fitxer.

### Funcionament del programa

El programa descriu un sistema que llegeix el contingut d'un fitxer anomenat "archivo.txt" des d'una targeta SD i mostra el contingut pel port sèrie. 