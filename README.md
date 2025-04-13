# Temporizadores
 
 - Faciles de usar
 - Internamente esa funcion se ejecuta en un ciclo for
 - Modulos para contar tiempo y poder ejecutarlo con todas las tareas

## 1. Modulo temporizador
 
 - Conteo de eventos internos y externos
 - **Modulo Timer**

### 1.1 APLICACIONES

 - **TEMPORIZADOR**
   
   - Cuenta los ciclos de **Reloj**
   
 - **CONTADOR**
   
   - Hace un conteo consecutivo de diferentes eventos y se carga a un registro, el registro tiene limite y si se llena se resetea

## 2. Modulo Contador 

  - Se puede usar ascendente y descendente
  - Maximo conteo 255
  - Se puede hacer una interrupción al llenar el registro

### 2.1 Tamaño Bus vs Resolución Timer

 - Se puede usar 2 resoluciones **8 Bits** y **16 Bits**
 - Para el uso de **16 Bits** se tiene que usar 2 registros
 - Los fabricantes plantean estrategias para no perder información

## 3. Sistema de Reloj

  - Señales externas : Flancos o cambios de estado
  - Señales o eventos internos

### 3.1 Sistema de Reloj Interno

  - Flancos de señal del reloj, conteos precisos
  - Tiempo no lo toma directamente del oscilador, cuenta con un circuito interno que produce esta señal

## 4. PreScaler

 - Es un contador de longitud variable (8bit a 10bit), al hacer el conteo dividir la frecuencia
 - Aumentar el tamaño del tiempo que podemos contar antes de que se llene el registro

## 4. Granularidad

  - La cual es la mínima fracción de tiempo que puede contar
  - La mínima granularidad es 1 us para esa configuración
  - Llegar a conteos mas grandes

## 5. Fuente Conteo 

### 5.1 Señal Externa

 - Señales externas son los que nos permiten realizar conteo
 - Flanco puede provenir de cualquier objeto debe tener flanco para hacer conteo
 - No puede contar muy rapido, no puede ser mayor al ciclo del reloj
   
### 5.2 Cristal 

 - Cristales o osciladores externos o osciladores internos

 **TIMER DISPONIBLES**
 
   - **TIMER 0**
       - Hasta 16 Bits, temporizador o contador

   - **TIMER 1**
       - Hasta 16 Bits, temporizador o contador
            
   - **TIMER 2**
       - Limitado a 8 Bits, temporizador
            
   - **TIMER 3**
       - Hasta 16 Bits, temporizador o contador

#### 5.2.1 TIMER 0

 - Administrar pines para que no haya problemas
 - Puede sacar información en cualquier momento del programa
 - Si se activa por desborde, se debe borrar la bandera

#### 5.2.2 Información del TIMER

- Es el registro donde se lleva a cabo la cuenta. Es de 16 bits
- Resolución de conteo
- Frecuencia del cristal o oscilador
- Máximo tiempo timer=tiempo de instrucción*Prescaler
- Tiempo de desbordamiento= (conteo-TMRX)* Máximo tiempo timer
- TMRX=conteo-(Tiempo de desbordamiento/máximo tiempo timer )

**FOSC** = **4MHz**
**t conteo** = **3 Seg** 
**Resolución** = **16 bits**

### 5.3 Máximo conteo timer
   
  - Utilizando resolución de 16 bits
    
    <img src="https://github.com/HeisenDiaz/Temporizadores/blob/main/Screenshot%202025-04-12%20214436.png" width="50%">

### 5.4 Precarga registro TMRX

  - Desea precargar el registro para que realice un conteo de 5ms

<img src="https://github.com/HeisenDiaz/Temporizadores/blob/main/Screenshot%202025-04-12%20215122.png" width="50%">
    
## 6. Conclusiones
- Los temporizadores y contadores son herramientas esenciales en microcontroladores, ya que permiten gestionar el tiempo y contar eventos internos o externos con alta precisión y eficiencia
- La resolución del temporizador (8 o 16 bits) define su capacidad de conteo, y al utilizar 16 bits se pueden alcanzar tiempos más largos antes de un desbordamiento, aunque se requieren dos registros para el manejo del dato
- El prescaler amplía el rango de conteo del temporizador, al dividir la frecuencia de entrada, permitiendo así medir intervalos de tiempo más largos sin modificar la resolución
- Los temporizadores del PIC18F4550 como TIMER0, TIMER1 y TIMER3 ofrecen hasta 16 bits de resolución, lo que permite su uso tanto como temporizadores como contadores, dependiendo de la configuración de sus registros y pines asociados
- El manejo correcto de las interrupciones por desbordamiento y el uso de banderas es vital para asegurar que el sistema responda correctamente al fin de un periodo temporizado

## 7. Autores

  ### Luis Fernando Pulido Salazar - 76257
  ### Heisen Jawer Diaz Ascencio - 137604
