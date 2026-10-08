# 5toAzul-Juan-Maizo
Pensamiento computacional 
clase del 24/09 creación del github 
1. Patrón : por cada arepa adicional, el precio total decrece en 2 Bs. (pasa de aumentar 8, luego 6, luego 4, luego 2 Bs).
2. Fórmula matemática Como el aumento disminuye de manera constante, la relación es de tipo cuadrática: (n es la cantidad de arepas y P el precio total). P(n) = n(11 - n) 
3. Fórmula aplicada P(10) = 1(10) - 10^2 = 110 - 100 = 10 \BsSiguiendo este patrón matemático el precio marginal seguirá bajando y se hará negativo en cierto punto lo demuestra un límite práctico del modelo.
4. Fórmula generalizada Si a = precio, diferencia= (a - 2) y disminuye de 2 en 2. P(n) = (a + 1)n - n^2 

Reflexión:
 ¿Por qué el precio no aumenta siempre lo mismo? Porque se está aplicando un descuento por volumen. Mientras más arepas compra el cliente, menor es el precio por unidad adicional para incentivar ventas al mayor.  
 ¿Qué pasaría si el patrón cambiara? Si el aumento fuera constante (ej. +10 Bs por arepa), el modelo sería lineal (\bm{P = 10n}). Si el patrón no sigue una regla lógica, la automatización del software no podría predecir los precios correctamente y habría pérdidas para el negocio o cobros incorrectos al cliente.
<img width="1080" height="810" alt="IMG_3103" src="https://github.com/user-attachments/assets/d2a8e1a5-680d-447e-a370-f7cf3e7c6054" />
https://www.tinkercad.com/things/bYdopru1TDf-smashing-kieran-lappi/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard&sharecode=XyGdzn8THbD7LNEAyrgzodyV8tWQpSlWypxGIDkduU4
// ----- Parte 1: 6 LEDs con pulsador -----
const int boton = 11;
const int leds[] = {2, 3, 4, 5, 6, 9};
const int numLeds = 6;
const unsigned long intervaloLeds = 8000; // 8 segundos

bool activado = false;
bool estadoLeds = LOW;
unsigned long ultimoCambioLeds = 0;

// ----- Parte 2: 2 LEDs con interruptor -----
const int interruptor = 12;
const int ledAzul = 10;
const int ledVerde = 13;
const unsigned long tiempoAlternar = 500; // medio segundo

bool turnoAzul = false;
unsigned long ultimoCambioAlternar = 0;

void setup() {
  pinMode(boton, INPUT_PULLUP);
  pinMode(interruptor, INPUT_PULLUP);
  for (int i = 0; i < numLeds; i++) {
    pinMode(leds[i], OUTPUT);
    digitalWrite(leds[i], LOW);
  }
  pinMode(ledAzul, OUTPUT);
  pinMode(ledVerde, OUTPUT);
}

void ponerLeds(bool estado) {
  for (int i = 0; i < numLeds; i++) {
    digitalWrite(leds[i], estado);
  }
}

void loop() {
  unsigned long ahora = millis();

  // ----- Parte 1 -----
  if (!activado) {
    if (digitalRead(boton) == LOW) {
      activado = true;
      estadoLeds = HIGH;
      ponerLeds(estadoLeds);
      ultimoCambioLeds = ahora;
    }
  } else if (ahora - ultimoCambioLeds >= intervaloLeds) {
    estadoLeds = !estadoLeds;
    ponerLeds(estadoLeds);
    ultimoCambioLeds = ahora;
  }

  // ----- Parte 2 -----
  if (digitalRead(interruptor) == LOW) {
    if (ahora - ultimoCambioAlternar >= tiempoAlternar) {
      turnoAzul = !turnoAzul;
      digitalWrite(ledAzul, turnoAzul);
      digitalWrite(ledVerde, !turnoAzul);
      ultimoCambioAlternar = ahora;
    }
  } else {
    digitalWrite(ledAzul, LOW);
    digitalWrite(ledVerde, LOW);
  }
}

