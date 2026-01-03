---
title: Diseño y Construcción de Antena Slim Jim para meshtastic
date: 2025-10-02 10:00:00 +0100
categories: [Proyectos, Radiofrecuencia]
tags: [antenas, meshtastic, nanovna, diy]
image:
  path: /assets/img/slimjim-open.jpg
  alt: Antena Slim Jim construida
---

## 📡 Introducción
Para crear un nodo meshtastic hay varias cosas necesarias, una de ellas es una antena medianamente decente. El problema de esta tecnología es que al emitir con una potencia tan baja (27dbm) no nos interesa que se desperdicie. He optado por una antena Slim Jim, ya que tiene mas ganancia que una antena J-pole, aunque sean ligeramente parecidas. La diferencia es que concentra la potencia de la polarización vertical en el horizonte, ya que nos interesa "llegar lejos" en el mismo plano horizontal.
## 📐 Cálculos y Teoría
La Slim Jim se basa en un dipolo plegado, alimentado por el extremo. Utiliza como plano de tierra la varilla inferior(en forma de J, por eso se parece a la J-pole). 
Para la banda de 868 mHz(34cm).
Para las dimensiones de cada elemento, vamos a utilizar una calculadora online creada por M0UKD(https://m0ukd.com/calculators/slim-jim-and-j-pole-calculator), con un factor de velocidad de 0,96 (aproximado por ser un conductor de cobre)
![Detalle del esquema](/assets/img/slimjim-esquema.png)


Obtenemos unas dimensiones de:
A = 252 mm
B =166 mm
C = 83 mm
D = 8 mm
E = 3 mm
F = 8 mm
Para conseguir una adaptación de impedancias lo mas perfecta posible, hay que tener cuidado con la distancia D, ya que es realmente la que adapta la linea de transmisión a los 50 ohmios.

## 🛠️ Construcción
Materiales utilizados:
* Cable unifilar de cobre de 4 mm
* Cable coaxial RG-58 para la bajada(de muy bajas pérdidas).
* Conector IPX para nodo meshtastic (evitamos perdidas en los distintos conectores)
* Tubo de PVC para la carcasa y separadores impresos en 3d

Para la construcción, imprimí una plantilla para doblar el cable de cobre con la forma necesaria(respetando las medidas y los radios de giro mínimos). Una vez doblado el cable, tocaba soldar la linea de transmisión(coaxial). Este es el punto critico de todo el montaje, ya que para que la adaptación de impedancias fuera perfecta fue necesario soldar y resoldar a diferentes distancias hasta que conseguí una impedancia lo mas cercana posible a los 50 ohmios. Una vez soldado, tocaba construir la carcasa. Use tubos de PVC de diferentes tamaños(para colocar las bridas de cara al montaje fijo) y pegamento de PVC. Para que el elemento radiante no tocara la carcasa, use unos separadores impresos en 3d. Finalmente pinte la antena de blanco para minimizar el desgaste por el sol y las condiciones climáticas.

![Montaje](/assets/img/slimjim-montaje.jpg)


## 📊 Ajuste y Mediciones (NanoVNA)
Una vez construida, la antena requiere ajuste fino. Utilicé un analizador vectorial de redes (**NanoVNA**) para ajustar el punto de alimentación.

El ajuste se realiza moviendo el punto de soldadura milimétricamente hacia arriba o abajo hasta obtener la mínima **Relación de Ondas Estacionarias (ROE/SWR)** en la frecuencia central de diseño.

**Resultados obtenidos:**
* **Frecuencia central:** 868.000 MHz
* **ROE:** 1.13
* **Impedancia:** 48,7 ohm

![Gráfica del NanoVNA](/assets/img/slimjim-vna.png)
*(Gráfica de Smith o SWR mostrando el "dip" en la frecuencia correcta)*

