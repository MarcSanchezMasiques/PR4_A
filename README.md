# PR4A: Procedimiento
Iniciamos utilizando el xTaskCreate , donde tenemos que definir la función de la Task(tarea), el nombre, el tamaño del stack, el parámetro y su prioridad:
```
void setup()
{
Serial.begin(112500);
xTaskCreate(
anotherTask,
"another Task",
10000,
NULL,
1,
NULL);
}
```
Dentro del void loop() creamos una impresión infinita de lineas de codigo "this is ESP32 Task" con delay de 1segundo = delay(1000)
```
void loop()
{
Serial.println("this is ESP32 Task");
delay(1000);
}
```
Por ultimo llamamos a void anothertask( void * parameter) donde hacemos otro bucle infinito de la misma manera con una a condición de finalizado que borre la tarea (Task)
PISTA: Nunca sucedera por ser infinita la tarea =)
```
void anotherTask( void * parameter )
{
for(;;)
{
Serial.println("this is another Task");
delay(1000);
}
vTaskDelete( NULL );
}
```