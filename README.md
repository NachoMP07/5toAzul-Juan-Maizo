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
