---
title: Nodo UltraSlim para Meshtastic (bonito y todo)
date: 2026-07-11 10:00:00
categories: [Proyectos, Radiofrecuencia]
tags: [meshtastic, diy, redes, faketec, 3dprint, nanovna, antenas]
image:
  path: /assets/img/faketecnfy-open.jpg
  alt: Nodo-UltraSlim-para-Meshtastic
---





## Introducción

Hay decisiones de las que nos arrepentimos toda la vida. Dicen que la peor decisión es la que no se toma, pero no estoy muy a favor de esa afirmación; personalmente, de las peores decisiones que tomé hace un par de semanas fue ponerme a montar otro nodo de Meshtastic.

Para quien no lo sepa, ya tengo otra entrada montando un nodo Meshtastic, pero ese fue de los primeros que hice y el planteamiento era completamente distinto: una antena seria con la idea de dejarlo como nodo fijo. Este, en cambio, tenía otro objetivo: hacer un nodo móvil, de viaje, que se pueda llevar a todas partes pero con una antena lo suficientemente buena para llegar a la esquina y no morir en el intento.

El problema es que me empezó a molar el concepto de los nodos *ultraslim* a raíz de ver [este proyecto en Printables](https://www.printables.com/model/1067553-meshtastic-fakecap-ultra-slim-nrf52-gps-node).

Está guapo, ¿eh? Pues lo mismo pensé yo. La verdad es que un nodo que cabe en un bolsillo (algo grande) es un sueño bastante chulo, así que me puse manos a la obra ignorando todas las señales que me enviaba el universo... básicamente porque 8 mm de grosor molaban demasiado. 

Lo que iba a ser un proyecto de un par de días se acabó convirtiendo en un calvario de un par de semanas. Y por eso estoy redactando esto: porque ha tenido los suficientes giros de guión como para ganarse su propia entrada en este, mi portfolio. 

*(Nota: Espero que en algún momento alguien lea esto. Ahora mismo estoy en la recepción de un hotel algo chungo escribiendo todo mientras la gente me mira raro).*

## Fase I: Todo es maravilloso y huele a coche nuevo

Pues nada, con la idea en la cabeza empiezo a reunir materiales. El planteamiento es una carcasa impresa en 3D y, para los distintos componentes, opté por conseguirlos de sitios variados:

* **La batería y el motor de vibración:** Los saqué de un móvil que ya no usaba y que murió en cierto momento (de los mejores modelos en mi opinión, si me preguntas: un Samsung A8 de 2018).
* **La placa (una FakeTec), el interruptor y la pantalla:** Componentes pedidos directamente a AliExpress, del primer pedido que hice para toda esta movida, igual que el pigtail para la antena.
* **Los pulsadores:** De un Kindle que me regalaron en algun momento porque la pantalla decidió suicidarse.
* **Los cables:** No me preguntéis de dónde los saqué porque no lo sé.

![Componentes](/assets/img/faketecnfy-componentes.jpg)

Con la lista hecha y los materiales sobre la mesa, me puse a diseñar. Recordad que estamos en la primera fase y que, de momento, los problemas del mundo real todavía no me habían llegado. 

Tras varias horas conseguí lo que era la primera versión del prototipo: supercompacto, con las tolerancias de una CNC de 10.000 euros... pero oye, que era feliz. Seguro que mi Ender 3 V3 SE lo conseguía.

Estéticamente la primera versión era muy chula. Sus dimensiones eran de $70 \times 90 \times 8\text{ mm}$, lo cual es una burrada (es algo más que la mitad de un móvil normalillo).

![Diseño primera versión](/assets/img/faketecnfy-fasei.png)

Como me dijo un tío muy sabio: *"se mide dos veces y se corta una"*. Así que, para no liarla, volví a tomar las medidas de todo para asegurarme de que entraba con margen y me puse a imprimir la primera versión.

Ay, qué emoción... la mitad del proyecto ya está hecha, ¿no? 

...¿no?

## Fase II: Un fallito lo tiene cualquiera

Con el primer prototipo me di cuenta de varios problemas. El primero fue el de las tolerancias y las capas de impresión. Pero vamos a ver, Fernan, no podemos pretender que una pared de 0.4 mm vaya a soportar la rigidez estructural de un ladrillo. Si literalmente con una boquilla de 0.4 es una sola pasada, se traduce en que las separaciones interiores no iban a aguantar. Pero bueno, no pasa nada, son cosas que pasan.

Otro de los problemas fue que el orificio para los pulsadores (tremendamente estéticos, si me preguntas) era demasiado "perfecto" como para que entraran y funcionaran. Tanto es así que por la ranura de 0.5 mm no entraban. Además, no me podía permitir el lujo de hacer soportes, porque no los iba a sacar ni el mismísimo Josef Prusa.

Por lo demás, el diseño guapo, guapo. Hice varias piezas para comprobar cuál funcionaba mejor con los pulsadores, elegí el que mejor se adaptaba y listo: ¡a por la versión 3! *(La versión 2 también salió chunga por problemas menores, pero de ella no hablamos).*

Mientras se imprimía (tranquilamente se tomaba sus 3 horitas), empecé a montar la plaquita FakeTec. Como me salieron tan baratas las PCB hace un tiempo, tenía 28 de ellas guardadas. 

Este paso fue complicado: la placa nRF52 trae unas raspas (*pin headers*) para soldarla a la PCB, pero claro, en un diseño de 8 mm de ancho nos sobran, no las podemos usar. Midiendo otros nodos que sí monté con estas raspas, se quedaban en 16 mm de grosor (el doble de lo que me podía permitir). Así que con mucha paciencia, cinta Kapton y cuidado, lo conseguí: un nodo que en su parte más ancha mide 6 mm. 

*(No os hagáis los sorprendidos: tenía que medir 6 mm sí o sí, porque los otros 2 mm son la tapa de arriba y de abajo del nodo).*

![Microcontrolador fino fino](/assets/img/faketecnfy-faseii.jpg)

Flashearla me costó la vida. Por alguna extraña razón no conseguía conectarme a la placa y, después de un par de horas jugando con varias versiones del programa (estable e inestable), apagados repentinos y reinicios de mierda, lo conseguí. 

Por cierto: los apagados repentinos eran porque la estaba alimentando desde un puerto USB del portátil, y la placa para arrancar pide chicha. Me di cuenta bastante tarde, claro.
Pero eh, que la versión 3 ya ha acabado de imprimirse, vamos a ver que tal, seguro que encaja todo a la perfección, cierro y a correr … .. .

## Fase III: Creo que esto empieza a ser un chiste

Bueno, bueno... las piezas encajan perfectamente, así que cometo uno de los mayores errores de todo el proyecto: me pongo a montar el hardware directamente. Total, está programado, malo tiene que ser que falle algo, ¿no? 

*(Posdata: soy subnormal).*

Pues nada, me pongo a montar y soldar todo en su sitio. La lié un poco con el interruptor porque lo pegué con cianocrilato a la base que hasta ese momento pensaba que iba a ser la definitiva *(spoiler: no)* y me tocó rascar y pillar otro interruptor porque el primero me lo cargué.

Por otra parte, como la batería era de un móvil, tuve que cortarle con mucho cuidado el flex, rascar y soldarle dos cables. El conector chiquito que traía para engancharlo al móvil no me venía nada bien y además la faja era bastante rígida. Pero oye, milagrosamente esa parte salió bien.

Con la batería lista, presento las piezas y, en un momento de emoción pura, me pongo a soldarlo todo en un par de horas. Quedó espectacular. 

Así que no se me ocurrió otra cosa que, justo en este momento —con todo soldado, la pantalla en su sitio y el chasis cerrado—, conectarle una antena que tenía por casa de esa frecuencia *(no queremos freír módulos LoRa, que son realmente caros para lo que hacen)*. Y ocurre el desastre: el nodo tarda media hora en iniciarse (seguimos con los reinicios) y, cuando al fin arranca, intento conectarme por Bluetooth. Imposible.

Me da por girar el módulo para ver si pone algo en la pantalla y, efectivamente: **“Critical Fault 3”**. 

Me voy a la documentación de Meshtastic y se confirma lo peor que podía pasar: el módulo LoRa está frito.

Hay que tener en cuenta que a este nodo **solo le quedaba ponerle la antena y cerrarlo**. Así que mi desesperación en este punto no es poca: llevo ya dos días más con el proyecto de lo que me gustaría. 

Revisando el inventario veo que me quedan un porrón de PCB, 3 módulos LoRa y 3 microcontroladores. Así que tomo la decisión drástica de montar un FakeTec totalmente nuevo. No quiero perder más tiempo comprobando qué es lo que realmente falla en la placa frita, ya lo miraré en el futuro.

![el nodo si inicia](/assets/img/faketecnfy-faseiii.jpg)

Venga, ahora lo monto todo rápido y tirando para adelante. ¿Qué podría salir mal en la Fase IV?


## Fase IV: ¿Dónde está la cámara oculta?

**LA ANTENA. ESO ES LO QUE PODÍA SALIR MAL.**

Mira, no os voy a engañar: no empecé este proyecto dos meses antes justo por este dilema: qué antena poner. La mayoría de diseños que hay por internet se limitan a meter una espiral que venden en AliExpress por 4 o 5 euros (normalmente con los módulos Heltec). Pero claro, es que la mayoría no son telecos, así que se limitan a pillar cosas que *se supone* que funcionan. *(Pista: no lo hacen).*

En un primer momento pensé en comprar una comercial, pero luego le di mil vueltas. Pensé en demasiados tipos de antenas que podía construir y al final llegué al diseño del monopolo: una antena simple pero efectiva. La parte del vivo va conectada al monopolo, mientras que la malla hace el otro lado mediante la masa común del resto de componentes. Hay que tener en cuenta que tengo una batería enorme funcionando como plano de tierra, a la que se le suma gran parte de la superficie del microcontrolador y algo de la pantalla. Con este planteamiento me lancé casi sin pensar al diseño: únicamente dejé un hueco para meter el brazo del monopolo y me despreocupé, que si no, no iba a empezar en la vida.

Pues siguiendo con nuestra interesante narrativa: cambié la FakeTec y todo tenía una pinta espectacular. Con una antena grande externa funcionaba que te cagas, ya no había *"Critical Fault 3"* y todo parecía solucionado. Únicamente faltaba fabricar e integrar la antena casera, así que me puse con ella. 

![nodo casi acabado](/assets/img/faketecnfy-faseiv.jpg)

Como iba a estar superencapsulada, la resonancia dentro de la carcasa iba a producir un efecto por el cual la onda iba a ser un poco más corta (y por lo tanto, el elemento radiante también). La explicación rápida es que el PLA es un material de mierda para radomos. 

Ea, pues nada: pillo un pigtail, sueldo en el vivo un par de cables de $1.5\text{ mm}^2$ soldados juntos para aumentar el ancho de banda *(que para el ajuste me iba a hacer falta)* y hago un puente con la malla al resto del circuito. Saco el NanoVNA, calibro, conecto y... *pum*, me encuentro con la siguiente sorpresa:

No es solo que el monopolo esté algo desintonizado, es que no está cerca de parecer una antena ni nada. Si hubiera conectado una piedra hubiese funcionado mejor. En el primer intento, la ROE no bajaba de **18** y la reflexión era un chiste. Por curiosidad miro las impedancias y no se acercaba a los $50\ \Omega$ ni de broma. 

Antes de ponerme a llorar, intenté varias medidas a la desesperada para conseguir algo medianamente funcional: acabo soldando otro hilo a la malla para montar un dipolo doblado (teniendo en cuenta que la impedancia iba a seguir estando lejos de los $50\ \Omega$, pero por lo menos para ver si la ROE bajaba y conseguía un elemento algo radiante). Y vaya si lo conseguí: ROE de **2.05** y $37\ \Omega$ de impedancia. *(De la reflexión mejor no vamos a hablar).*

Pero bueno, hablando mal: esto es una mierda. Y pensándolo bien, con un monopolo tan cerca del plano de masa principal el alcance iba a ser una basura. Así que tomo la decisión más realista de todo el proceso en cuanto a la antena: **rediseñar el chasis y meter una antena de verdad.**


## Fase V: Primero haz que exista, luego ya lo mejoras

En efecto: el nodo ya existía, así que solo quedaba mejorarlo. Y vamos a ser claros: tocaba reformular las dimensiones. Pero eh, los 8 mm de grosor **se quedan como están**. Solo le he dado un poco de pinta de walkie-talkie en lugar del bloque puramente rectangular del principio. Es verdad que le rompe un poco la estética, pero bueno: ahora tiene una antena de verdad.

![nuevo diseño (la version 5 para no engañarnos)](/assets/img/faketecnfy-fasevdiseno.png)

Y con "antena de verdad" me refiero al todopoderoso **dipolo**. Una antena genial: fácil de construir, fácil de ajustar y muy agradecida para transmitir, con un patrón de radiación lo suficientemente bueno como para no complicarte la vida. Es verdad que del diseño le sale un palo hacia arriba, pero no pasa nada: tiene su encanto. 

Esta antena fue bastante más fácil de ajustar. Se quedó un poco más corta que la medida teórica en aire, pero eso ya lo sabía y contaba con ello, por lo que el diseño en 3D estaba justo calculado para eso. También separé un poco la rama de la malla del resto de la electrónica, lo cual mejora el rendimiento general.

Siendo realistas, el único "problema" que tiene este dipolo es que, dependiendo de cómo agarres el nodo con la mano, **tú pasas a ser parte del plano de masa** y las propiedades cambian un poco. Pero estuve haciendo pruebas y el comportamiento es más que aceptable. 

Con todo listo, lo vuelvo a soldar todo y se viene la campaña de pruebas. Con el NanoVNA consigo esta preciosidad:

![captura-nanoVNA del dipolo](/assets/img/faketecnfy-fasevnanovna.jpg)

Y nada: el módulo funciona, la antena funciona y, tras varios días de pruebas intensivas, quito la cinta de carrocero con la que lo había pegado provisionalmente y me dispongo a cerrarlo definitivamente. 

Hay que tener en cuenta que al principio pensaba pegarlo con adhesivo B-7000, pero el PLA no se lleva especialmente bien con él, así que se me ocurrió una solución más drástica: **calor**. Está literalmente soldado por termofusión. Si el día de mañana quiero abrirlo, me va a tocar cortar plástico con la cuchilla. Algunos pensaréis que es una chapuza, pero la verdad es que no tengo previsto abrirlo cada dos semanas, así que por eso le hice antes todas las pruebas que se me ocurrieron.

![Nodo acabado](/assets/img/faketecnfy-fasevfin.jpg)

Y *voilà*: ahí está, listo, cerrado y tan tranquilo el pobre... con la guerra que ha dado.


## Conclusiones

Bueno, hacía mucho tiempo que quería tener un nodo de estos. Al principio pensé en construirme el diseño más famoso que había por internet, pero necesitaba que tuviese un toque personal. Lo bueno de diseñarlo e imprimirlo yo mismo es que me lo he personalizado a mi gusto: tiene una estética inspirada en *Cómo entrenar a tu dragón* que me encanta. Por lo menos que me guste el resultado, ¿sabes?

La mayoría de problemas que he tenido se podrían haber evitado si hubiese pensado un poquito más. Pero me lancé a construirlo directamente... total, el PLA es bastante más barato que el acero, así que no pasa nada si gasto un par de prototipos más. Además, es una forma bastante divertida de fabricar cosas.

Podría haberme tirado tres semanas delante de Onshape y haberlo dejado fino, fino, pero así ha sido mucho más movido. Lo de que el módulo LoRa estuviese fundido tampoco me lo esperaba. Lo de la antena en el fondo sí, pero preferí ser feliz hasta que llegó el momento del NanoVNA. 

**Resumen:** Ha quedado chulo, me ha gustado el proceso y he aprendido un montón por si en un futuro quiero seguir con esto de los nodos *ultraslim*. Han pasado más cosas y he tenido algún marrón más por el camino, pero he preferido contar las partes más interesantes.

---

## Bibliografía

Todo proyecto debería tener su bibliografía. La mayoría de referencias e información las he sacado de los siguientes sitios:

* **[meshtastic.es](https://meshtastic.es):** Donde está toda la información sobre nodos en español y guías de inicio muy buenas.
* **[meshtastic.org](https://meshtastic.org):** Imprescindible para *debuggear* y buscar códigos de fallo (aquí encontré la explicación del *Critical Fault 3*). Mención honorífica a su Web Flasher y al Web Client, todo integrado en el mismo sitio.
* **[FakeCAP Ultra Slim en Printables](https://www.printables.com/model/1067553-meshtastic-fakecap-ultra-slim-nrf52-gps-node):** Mi fuente de inspiración principal. Me moló el concepto original y quise replicarlo a mi manera.

## Diseños y recursos para el montaje

A ver, esto no es un tutorial paso a paso, pero ha quedado tan decente que he decidido subir los STL de la carcasa y la lista con los componentes principales a mi perfil de Printables:

👉 **[Enlace a mi perfil / proyecto en Printables](https://www.printables.com/model/1807433-ultraslim-node-meshtastic)**

No creo que nadie vaya a montar exactamente el mismo *Frankenstein* (de hecho, os recomendaría encarecidamente haceros el vuestro propio customizado), pero oye: ahí tenéis un buen punto de inicio.

Si has llegado leyendo hasta aquí, de corazón: **gracias por leer**. La verdad es que me lo paso igual de bien diseñando, soldando y peleándome con la RF que escribiendo todo el proceso... a pesar de ser consciente de que esto es un portfolio y que probablemente poca gente se lo vaya a leer entero.

Ea, pues lo dicho: ¡muchas gracias! :)

