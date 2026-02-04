---
title: Recicladora de PET para impresión 3D
date: 2026-01-25 10:00:00
categories: [Proyectos, Impresion3D]
tags: [c++, 3dprint, lasercut, diy, ]
image:
  path: /assets/img/petedora-open.jpg
  alt: Recicladora de PET
---

## Introducción
Hace tiempo comencé un proyecto con un objetivo claro: convertir residuos plásticos (botellas PET) en material útil para impresión 3D. La primera versión funcionaba, pero sabía que el concepto tenía mucho más potencial. Recientemente, aprovechando un tiempo libre, decidí desempolvar el proyecto y rediseñar toda la electrónica y el control desde cero, buscando no solo que 'funcionara', sino que fuera preciso y robusto(y algo mas bonito).

![Funcionamiento de la boquilla](/assets/img/petedora-boquilla.jpg)

## PET y PETG
Bueno, antes de empezar a rediseñar la recicladora vamos a hablar de el material a reciclar. La mayoria de botellas de plástico estan hechas de PET (Tereftalato de polietileno)
Y aquí es donde surge la primera confusión habitual: No, esto no es lo mismo que el PETG que compramos en bobinas. La "G" extra en el filamento comercial significa Glicol, un aditivo que modifica la estructura química del plástico para hacerlo "amorfo". Esto hace que el PETG sea fácil de imprimir, fluya bien y no se deforme.

El PET de las botellas, en cambio, es semicristalino. Esto, que a priori parece una desventaja porque lo hace más difícil de trabajar (tiende a cristalizar y sufrir warping si se enfría mal), es en realidad es una ventaja en el resultado final. Al no tener glicol, el PET reciclado mantiene unas propiedades mecánicas brutales:

    * Mayor resistencia térmica: Aguanta temperaturas de 75-80°C sin deformarse, mientras que el PETG se ablanda a los 65°C.

    *  Mayor rigidez y resistencia a la tracción: Es un material de ingeniería superior para piezas funcionales.

    * Coste e Impacto: Materia prima infinita y gratuita, cerrando el ciclo de consumo localmente.

Sin embargo, domar el PET tiene un precio: exige precisión. Necesita una temperatura de extrusión muy estable en el rango de los 260°C. Una variación de pocos grados puede hacer que el plástico no funda bien o, por el contrario, se degrade y cristalice dentro del extrusor (o se quede pegado al teflon del extrusor y lo fastidie).

## Funcionamiento:
El funcionamiento de la máquina se basa en una bobina que tracciona una tira fina de PET, cortada a una medida específica, a través de un extrusor modificado. Este extrusor cuenta con un orificio de salida por el que pasa la tira de botella, doblándose debido a la geometría cónica hasta convertirse en un pequeño 'tubo' hueco.

Este hueco interior presenta un desafío técnico: al no ser un sólido completo, es crucial calcular el factor de flujo correcto para obtener impresiones perfectas. Una vez formado el filamento, este se va enrollando en el carrete, el cual, mediante una reductora y un motor paso a paso, ejerce el par (torque) necesario para mantener la tracción. El concepto teórico es así de simple, aunque el montaje real conlleva mayor complejidad.

![Funcionamiento](/assets/img/petedora-funcionamiento.jpg)

## Base Mecánica
Teniendo claro que el PET requiere precisión y una tracción constante, para la mecánica decidí no reinventar la rueda, sino optimizar una de las mejores bases Open Source que existen: [Petalot](https://www.printables.com/model/768657-petalot-pet-filament-machine).


Este diseño opera mediante tracción (pultrusión): a diferencia de los sistemas convencionales que empujan el material, esta máquina tira de la tira de botella a través del bloque calentador. Sin embargo, este principio genera una tensión mecánica considerable. La fuerza de arrastre es tan alta que las piezas originales sufrían fatiga estructural, especialmente en los alojamientos de los rodamientos.

Sin el refuerzo adecuado, los rodamientos tienden a ceder ante la carga, llegando literalmente a arrancarse de la estructura principal y fracturando la unión entre la bobina y la reductora. Por ello, fue necesario rediseñar y reforzar estas zonas críticas.

Para el ensamblaje base, seguí las directrices del proyecto Petalot, aprovechando su ingeniería mecánica pero descartando los módulos que no se ajustaban a mis necesidades, como el alojamiento de la electrónica. En su lugar, opté por diseñar y fabricar una carcasa personalizada ('custom') que se integrara mejor con mi nuevo hardware.

![Base mecanica](/assets/img/petedora-mecanica.jpg)

Esta carcasa, fabricada mediante corte láser en mdf de 3mm, aparte de estéticamente elegante. Fue diseñada específicamente para alojar el ESP32, el driver del motor y el resto de electronica necesaria, manteniendo el sistema compacto y portátil. Todo el cableado queda oculto, dejando expuesta solo la interfaz de usuario (LCD y Encoder) para un control limpio y accesible.


## ESP32, STEPPER + TERMISTOR + EXTRUSOR
Teniendo la mecácina, la electronica va a ser la siguiente:
    * ESP32, es mas potente que un arduino y tiene mejores caracteristicas
    * Motor paso a paso
    * Extrusor adaptado
    * Termistor
    * Encoder
    * Pantalla LCD
    * Mosfet para alimentar la resistencia del extrusor
    * Driver A4988 para controlar el motor paso a paso
    * Convertidor DC-DC Buck (para bajar de 12v a 5v)

Una vez tenemos los componentes, los vamos a montar siguiendo el siguiente circuito:

![Electronica](/assets/img/petedora_bb.png)

Una aclaracion importante es que el extrusor es reciclado de otro proyecto, y que para conseguir el grosor de filamento necesario, aparte de la velocidad de tracción y  la temperatura, es muy importante conseguir un agujero en la boquilla de lo mas cercano posible al valor de 1,7 mm de diámetro. 

El esquema de la electrónica es el siguiente:

![Esquema](/assets/img/petedora_esquema.png)

## Programación del ESP32
A nivel de firmware, la plataforma ESP32 facilita enormemente la programación, ya que permite configurar interrupciones en casi todos sus pines, algo vital para la gestión del encoder y el motor.

Sin embargo, el mayor desafío técnico reside en la lectura del termistor. Al prescindir de un módulo ADC externo, dependemos del convertidor analógico-digital integrado en el microcontrolador. Dado que el ESP32 trabaja con una lógica de 0 a 3.3V (un rango dinámico menor que los 5V de un Arduino UNO) y su ADC no es perfectamente lineal, la resolución a bajas temperaturas se ve comprometida.

Esto significa que por debajo de 150 ºC perdemos precisión en la medida. No obstante, mediante el uso de una resistencia pull-up de 1kΩ (en lugar de la estándar de 4.7kΩ), desplazamos la zona de mayor sensibilidad hacia el rango alto. Con esta modificación, conseguimos una lectura precisa y estable en la zona crítica de operación (260 ºC), que es donde realmente necesitamos control.

![Funcionamiento](/assets/img/petedora-conclusion.jpg)

## Conclusiones y usos
Llegados a este punto, es necesario evaluar la máquina y sus aplicaciones reales. El objetivo principal siempre fue conseguir un material más resistente que el PLA, evitando comprar PETG. El problema es que este material exige impresoras con un rango de temperatura alto, en torno a los 260 ºC.

De momento, solo he realizado pruebas con la Ender-3 V3 SE. Dado que su temperatura máxima es exactamente 260 ºC, trabajar justo en ese umbral ha impedido conseguir buenos resultados. Por ello, en el futuro planeo utilizar una Prusa MK1 modificada con un extrusor de 1.75mm, diseñada específicamente para alcanzar esas temperaturas sin forzar la mecánica.

Además, como ya he mencionado, el material es complejo: produce un warping tremendo y el flujo varía porque realmente estamos imprimiendo con un 'tubo' y no con un cilindro sólido. Sin embargo, como prueba de concepto lo considero un éxito total. Haber logrado obtener filamento a partir de botellas de PET es increíble por sí mismo, y creo firmemente que, con los ajustes de hardware necesarios, seré capaz de imprimir sin problemas.

## Recursos del Proyecto
Todo el código fuente, los archivos CAD y la lista de materiales (BOM) están disponibles en mi repositorio:

👉 **[Ver Repositorio Completo en GitHub](https://github.com/FernanFPV/Petedora)**

## Bibliografía
Algunos sitios web de donde he sacado la información:
[Petalot](https://www.printables.com/model/768657-petalot-pet-filament-machine), 
[pet2print](https://the-diy-life.com/pet-bottle-recycler-part-1-using-an-arduino-uno-r4-to-control-a-3d-printers-hotend/) ,
[Ctrl3d](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://www.youtube.com/watch%3Fv%3Dm1Yb0tGEswY&ved=2ahUKEwi5jdLAw8CSAxVhhv0HHeBBKjIQwqsBegQIDBAB&usg=AOvVaw1zkkMqhI524CAwaKrYZZ8P) ,
[CaracolMaker](https://www.printables.com/model/88300-extrusora-de-filamento-pet-v3-diy-filament-machine) ,
[Recreator3D](https://www.recreator3d.com/)

