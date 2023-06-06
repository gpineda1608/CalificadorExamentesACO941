//Gabriela Maria Pineda Gonzales PG120866
#include <LiquidCrystal.h>
#include <Servo.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2); // Conexiones de la pantalla LCD
Servo cambioexamen; //Declaracion Servo Movimiento Del Examen
Servo cambiopregunta; //Declaracion Servo Movimiento De Pregunta
int preguntas = 10; // Cantidad de preguntas en el examen
int respuestas_correctas = 0; 
int examen =1; //Identificacion Examen 1
int nota2 = 0;// Contador de respuestas correctas examen 2
int nota1 = 0;// Contador de respuestas correctas examen 1
int examen2=0; //Identificacion Examen 2

void setup() {
  lcd.begin(16, 2); // Inicialización de la pantalla LCD
  lcd.print("Examen"); // Mensaje de inicio
  delay(2000);
  lcd.clear();
  pinMode(1, OUTPUT); // Configurar el pin 1 como salida de foco
  pinMode(6, INPUT); // Configurar el pin 6 como entrada letra A
  pinMode(7, INPUT); // Configurar el pin 7 como entrada letra B
  pinMode(8, INPUT); // Configurar el pin 8 como entrada letra C
  pinMode(13, INPUT); // Configurar el pin 13 como entrada letra D
  Serial.begin(9600); // Habilitar la comunicación serial
  cambioexamen.attach(10,500,2500); //Habilitar pin 9 para cambioexamen (pin, rango minimo, rango maximo)
  cambiopregunta.attach(9,500,2500); //Habilitar pin 10 para cambiopregunta (pin, rango minimo, rango maximo)
}

void loop() {
  digitalWrite(1 , HIGH);//Enciende el FOCO
  char respuestas[preguntas]; // Array para almacenar las respuestas ingresadas por el usuario
  char respuestas_correctas[preguntas]; // Array para almacenar las respuestas correctas
  // Ingresar las respuestas correctas en el array
  respuestas_correctas[0] = 'a';
  respuestas_correctas[1] = 'b';
  respuestas_correctas[2] = 'b';
  respuestas_correctas[3] = 'c';
  respuestas_correctas[4] = 'c';
  respuestas_correctas[5] = 'c';
  respuestas_correctas[6] = 'd';
  respuestas_correctas[7] = 'd';
  respuestas_correctas[8] = 'd';
  respuestas_correctas[9] = 'd';
  // Son 1:A, 2:B, 3C, y 4D.

  // Realizar el proceso de evaluación del examen 
  for (int i = 0; i < preguntas; i++) {
    lcd.clear();
    lcd.print("Pregunta ");
    lcd.print(i + 1);
    lcd.setCursor(0, 1);
    lcd.print("Respuesta: ");
    cambiopregunta.write(89);
    delay(2000);
    cambiopregunta.write(90);
    delay(2000);
    
    // Esperar a que el usuario ingrese la respuesta
respuestas[i] = leerRespuesta();
    // Leer la respuesta ingresada por el usuario desde los pines de entrada
    // Comparar la respuesta ingresada con la respuesta correcta
   
    if (respuestas[i] == respuestas_correctas[i]) {
      lcd.clear();
      lcd.print("Pregunta ");
      lcd.print(i + 1);
      lcd.setCursor(0, 1);
      lcd.print("Correcta");
      respuestas_correctas+1;
      
  if(examen==1){ //sumador de nota para examen 1
  nota1=nota1+1;
  }
  else if(examen2==1){ //sumador de nota para examen 2
  nota2=nota2+1;
  }
    // Incrementar el contador de respuestas correctas
    } else {
      lcd.clear();
      lcd.print("Pregunta ");
      lcd.print(i + 1);
      lcd.setCursor(0, 1);
      lcd.print("Incorrecta"); 
      delay(1500);
    }

  delay(1000); // Esperar 2 segundos antes de pasar a la siguiente pregunta
  }

  // Mostrar la nota total
 if(examen2==1){
  digitalWrite(1,LOW);
  lcd.clear();
  lcd.print("Nota 1: ");
  lcd.print((nota1)); // Calcular la nota como un porcentaje
  lcd.setCursor(0, 2);
  lcd.print("Nota 2: ");
  lcd.print((nota2));
  lcd.print(" ");
  while (true) {
  // Mantener la pantalla mostrando la nota total
  }
 }
  if(examen==1){
  lcd.clear();
  lcd.print("Nota Uno: ");
  lcd.print(" ");
  lcd.print((nota1)); // Calcular la nota como un porcentaje
    cambioexamen.write(89); //Movimiento de servomotor de cambio de pregunta
    delay(5000);
    cambioexamen.write(90); //Detiene el movimiento de cambio de pregunta
    delay(2000);  
 examen2=1;
 examen=0;
  return setup();
  }
}

// Función para leer la respuesta ingresada desde los pines de entrada
char leerRespuesta() {
  if (digitalRead(6) == HIGH) {
    return 'a'; //Lectura de sensor para repuesta A.
  } else if (digitalRead(7) == HIGH) {
    return 'b'; //Lectura de sensor para repuesta B.
  } else if (digitalRead(8) == HIGH) {
    return 'c'; //Lectura de sensor para repuesta C.
  } else if (digitalRead(13) == HIGH) {
    return 'd'; //Lectura de sensor para repuesta D.
  } 
}
