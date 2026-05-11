---
title: Secadora de Filamento para impresion 3D
date: 2026-04-20 10:00:00
categories: [Proyectos, Impresion3D]
tags: [c++, 3dprint, lasercut, diy, ]
image:
  path: /assets/img/secadora-open.jpg
  alt: Secadora de filamento
---

## Introducción: Los dramas le dan emoción a la historia
La impresión 3D es algo maravilloso. De hecho, de las mejores sensaciones que puedes tener en la vida es llegar a casa después de un largo día de la uni y encontrarte con que esa impresión de 23 horas ha fallado justo en el momento en el que cruzaste la puerta por la mañana.
Lo mejor de todo es que la mayoría de los errores que sufro siempre son por culpa del filamento; mis impresoras son demasiado "poco premium" como para tener sensores de flujo, pero bueno, ¡así tiene más emoción!
El caso es que, después de acumular varios rollos abiertos que tienen más parecido con un paquete de espaguetis caducados que con material de impresión, decidí que era el momento de construir mi propia secadora de filamento. Viendo lo que cuestan las comerciales, casi me sale más rentable ahorrar para una Bambu Lab X1 Carbon... (Bueno, no, pero es la excusa).

## Principios físicos: Mi colega Arquímedes y su primo Willis

Antes de ponerse a cortar madera y llorar con la electrónica ardiendo, primero hay que analizar cómo va a funcionar la máquina. Nuestro problema real es la humedad: cuando un filamento la absorbe del ambiente, se cristalizan sus microestructuras y se vuelve más quebradizo, arruinando nuestra impresión. Nuestro objetivo es eliminar esa humedad, y aquí entran mis amigos:
Hace un par de mundiales (más o menos), Arquímedes descubrió el concepto de densidad mientras veía un partido del Betis (o eso afirma mi profesor de fluidos). También descubrió que las sustancias más densas tienden a bajar, dejando por encima a las menos densas. Por esa razón, el aire frío tiende a bajar y el caliente a subir, ya que este tiene menor densidad debido a la velocidad de sus partículas.
Por la otra parte de nuestra historia entra Willis Carrier, quien se puso a investigar y descubrió que el aire caliente es capaz de saturarse con mucha más humedad que el aire frío. Esto que os cuento es la razón de que en verano el aire acondicionado gotee agua: el aire caliente se enfría de golpe, se satura rápido y el agua precipita, dejando un aire de salida mucho más seco.
Si juntamos estas dos ideas, obtenemos el corazón de nuestro proyecto. El funcionamiento de la secadora consistirá en calentar un flujo de aire que subirá un poco por densidad y otro poco forzado por un ventilador (lo veremos más adelante). En su camino, este aire se 
encontrará con la bobina de filamento, a la que le irá "robando" la humedad hasta salir de la caja.
Lo que pase después... ya no es problema mío. Lo que sí es un problema es el hardware que vamos a usar:


## Hardware a utilizar (Perdón David, la Anet A8 ya es historia)

Curioso título, ¿eh? Pues efectivamente, el promotor de esta idea es un colega que me prestó los restos de su Anet A8; prefería donarla a la “ciencia” que dejar que ardiera su casa (las Anet A8 tienen fama de salir ardiendo solas).
Después de este gancho narrativo, os explico la idea principal: una caja fabricada en DM de 3 mm. Me interesa que el material no sea muy grueso, pero que a la vez sea un buen aislante térmico para evitar pérdidas considerables. El elemento calefactor será la propia cama de la impresora, ya que es una resistencia excelente con su termistor correspondiente. Lo único que tenemos que averiguar es cómo hacer que esta electrónica no arda (ya lo resolveremos).
Cuando diseñe la caja, buscaba un estilo poligonal. Como la caja es cuadrada, opté por unos agujeros de entrada de flujo hexagonales siguiendo un patrón en dos filas. Casi no se ven de lo pequeños que son, pero me mola la estética.
Por otra parte, al diseñar las entradas de aire hay que tener en cuenta que no nos podemos volver locos: el área de entrada debe ser la misma que el área de salida. Así favorecemos una mejor conducción del flujo y no la liamos por el camino.
Pero, un detalle importante: ¿cómo vamos a abrir la caja? Pues muy sencillo, con unas bisagras impresas en 3D. Así nos ahorramos el mal rato de diseñarlas en madera (que la verdad es un tostón) y nos queda una caja bastante bien cerrada. Le añadimos un asa chula al estilo Josef Prusa, y ya está. Tenemos la parte física planteada. Ahora, el problema va a ser montarla...

## Montaje: DM, humedad, poliuretano y manos negras

Con el diseño hecho, nos vamos a mi querida K40 a cortar el DM. Como es de 3 mm se lo "papea" sin problemas; el único inconveniente fue el área de trabajo: tanto la base como la tapa son demasiado grandes para cortarlas en una sola pieza, así que me tocó dividirlas en dos y pegarlas luego. El resto de la caja tiene unos dientes para facilitar el montaje (spoiler: no lo fue, aunque funcionaron bien).
Aquí llegó el primer golpe de realidad: el DM es caro para lo que es. Como tenía una gran cantidad de carteles antiguos, decidí tirar de existencias, pero resulta que con la humedad (sí, todos los problemas actuales son por el agua) se habían cuarteado y doblado. Cortarlos fue complicado por el tema del foco del láser, pero montarlos iba a ser totalmente imposible.
Así que decidí aplicar psicología inversa: si se doblan por absorber humedad por un lado... pues toma dos tazas. Los mojé por el otro lado y les puse peso durante varios días. Contra todo pronóstico, este método precario y de dudosa calidad funcionó relativamente bien, y con el DM más recto que antes, me propuse pegar la caja.
La duda principal era el tipo de pegamento. Por un lado, la silicona caliente era mala idea porque la caja alcanza la temperatura. Por otro lado, la cola blanca se vuelve elástica con el calor y no quería que la caja pareciera una colchoneta de feria. ¿Resina epoxi? No me quedaba suficiente. Así que acabé, casi sin saberlo, en la mejor de las opciones: Poliuretano.
El poliuretano es ideal porque buscamos un fijador que se quede más duro que la calva de Pitbull. Además, al expandirse, es capaz de rellenar los huecos entre las piezas y tolera altas temperaturas sin despeinarse.

![Estrutcura de madera](/assets/img/secadora-madera.jpg)

Postdata: El bote amarillo de poliuretano trae unos guantes pegados por algo. Este pegamento reacciona con la humedad para curar, el problema es que en tejidos biológicos se mete por los poros y te deja las manos negras. No me los puse y pasó lo que pasó. Conclusión: Safety first.
Para terminar esta fase, solo quedaba imprimir las bisagras. Podría haberlas diseñado yo, pero mi colega [FM](https://www.printables.com/model/307580-parametric-hinge) (bueno, no le conozco jajaja) ya lo había hecho por mí. Las parametrizar para que se ajustaran a mis dimensiones, imprimí el [asa](https://www.printables.com/model/423500-hex-pattern-handle-collection) al estilo hexagonal de Prusa.

Todo va atornillado con tornillos de métrica 3, salvo por la cama, que usa métrica 4. Además tiene una separación con respecto a la base de la caja de unos 2 cm hecha con unos tubos de teflón, porque como he dicho varias veces, no me apetece que salga ardiendo.
Como la caja se va a calentar, la he forrado con capas de aluminio y cinta de aluminio para que se pierda la menor energía posible (vamos, que no se escape el calorcito).
El Jueves pasado tuve una barbacoa, y me sentí inspirado al ver la parrilla, por lo que se me ocurrió que la bobina de filamento, en lugar de ir apoyada directamente sobre la cama caliente, fuera un poco por encima, sobre una estructura metálica con cierto parecido a una barbacoa. Y con eso, a tirar con el siguiente campo.

![Estrutcura de madera](/assets/img/secadora-barbacoa.jpg)


## Electrónica: Matando moscas a cañonazos

Para la electrónica estaba claro que iba a usar la cama de la Anet A8 como elemento calefactor. Lo que no tenía tan claro era si montar un circuito específico para controlar el PID y la lectura del termistor o aprovechar lo que ya tenía. Como problemas ya tenía "para parar un tren", decidí utilizar la placa completa de la Anet: una PCB capaz de controlar cuatro motores paso a paso y tres salidas PWM de potencia... todo eso para usar un solo sensor y un ventilador. Pero bueno, ya que estábamos tirando recursos en cosas inútiles, le puse hasta la pantalla. Puestos a exagerar, lo hacemos con todo.
Y con "ponerse a tope" me refiero a controlarlo todo. Como periféricos reales tenemos la cama, el termistor, la pantalla y el ventilador. Este último lo rescaté de un cajón; funciona a 12V pero su lógica PWM va a 5V. Me tocó jugar a los cirujanos buscando la pista correspondiente al PWM del microcontrolador antes de que pasara por el MOSFET de potencia. Así conseguí un control total y perfecto sobre las revoluciones.
Llegamos al punto crítico: evitar que la casa salga ardiendo. Como ya he repetido varias veces, la Anet A8 tiene fama de incendiaria específicamente por sus conectores. Si eliminamos cualquier conector que lleve algo de potencia, evitamos el desastre. Para la alimentación de la placa, opté por rascar un poco la máscara de soldadura y soldar directamente a la pista; hice exactamente lo mismo con el conector de la cama.
Lo más complicado fue el lado de la cama caliente. Al soldar directamente sobre una placa diseñada precisamente para evacuar calor, el estaño se enfría al instante y cuesta horrores. ¿La solución? Soldador a máxima temperatura, mucha paciencia, mucho flux y precalentar la placa con una pistola de aire caliente "por si acaso". El resultado: las soldaduras más feas que he hecho en mi vida. Podría enseñaros una foto, pero prefiero que os quedéis con el hecho de que, normalmente, sueldo bonito.
Lo que sí me quedó estético (totalmente verídico) fue el conector para la fuente de alimentación: un Molex de 4 pines donde los dos centrales son el negativo y los dos extremos son 12V. Es un estándar que uso en mis proyectos para compartir las fuentes, que no me sobran.
Con todos los elementos colocados, la cama atornillada y la electrónica fijada con un chorro de silicona caliente (en las zonas que no se calientan, obviamente), llegó el momento de pelearse con la programación. Porque, spoiler: la placa de la A8 no lo puso nada fácil.



## Peleando con el código (vamos perdiendo)

Pues si fuese por la placa, no la programo, eh, resulta que esta placa viene de serie con marlin, y claro, los ingenieros que la diseñaron no pensaban en que iba a haber un chaval que se iba a plantear convertirla en una cajita feliz (y caliente), por lo que no trae bootloader (porque no está pensado reprogramarlo).
Nos hace falta quemar un bootloader, y tenemos varias opciones, esperas a que se haga solo (Pista, no hacer nada no funciona) o usar un arduino uno que tengo por ahí tirado para que funcione como programador, básicamente desde la interfaz de arduino es una opción que da, porque es un procedimiento normal y común, se conectan los cables correspondientes al puerto ISP y ale, a correr.

![quemando el bootloader](/assets/img/secadora-flashplaca.jpg)


Con el bootloader quemado, probamos con un “hello word”, y cuando ya tenemos claro que la conexión funciona y es perfectamente programable, saltamos a pegarnos con el código.
En resumidas cuentas, tiene que tener una monitorización de tiempo, velocidad del ventilador, el PID para la resistencia de la cama y el control de la pantalla.
Sin dudas, la parte que mas guerra me dio fue los botones de la pantalla, porque los queridos ingenieros de Anet, en lugar de meter varios canales, prefirieron jugar con valores analogicos para diferenciar cual de los botones se ha pulsado, en mi opinión una idea brillante, pero que falla a veces si no existe un buen contacto al pulsar el botón, y si pulsas varios, nada, hasta luego (lo poco que costaba poner un encoder con pulsador)
Una vez conseguido esto, y después de varias horas de programación ya lo tendriamos funcionando.
He decidido que como tenemos que controlar varios parámetros, lo mejor es un menú, donde con los botones arriba y abajo me muevo entre tiempo, temperatura y velocidad del ventilador, y con los laterales voy cambiando el parámetro. El botón central va a ser de start/stop.

![quemando el bootloader](/assets/img/secadora-completoab.jpg)

## Conclusiones

Pues la verdad es que ha quedado bastante mejor de lo que esperaba; una cosa es el diseño y el ensamblaje que hago previo al montaje y otra muy distinta es el resultado final. Hay que tener en cuenta que cuando diseñó para previsualizar, la mayoría de las veces no incluyo todas las piezas, como la electrónica, los cables o las propias bisagras, pero una vez montado, queda espectacular.
No os voy a engañar: la primera vez que lo enchufé, no me di cuenta de que quedaban unos pocos residuos de flux sobre la cama (cerca de las soldaduras). Como son resinas, cuando se calentaron empezaron a echar humo y dije: "pues va a salir ardiendo, destino inevitable". Pero después de desmontar y revisar cada soldadura, me di cuenta de que solo me faltó un poquito de limpieza.
La secadora funciona bien. En las pruebas el calor se distribuye uniformemente por todo el área. Con muy poca velocidad en el ventilador (un 10 o 20%), mueve el aire caliente mientras el interior se mantiene a temperatura constante. Eso sí, hablando de ventiladores: como está puesto en la tapa y apuntando hacia abajo, el eje tenía un pequeño gap y rozaba con la superficie del DM, pero nada que un poco de impresión 3D no pudiera arreglar con un separador y una junta de goma.

¡Ale, pues ya está! Me queda todavía probarlo a fondo, pero buena pinta tiene para rato.

Hay que decir que si he hecho pruebas, no han sido una locura vista a simple vista, ya que las piezas de antes y de después de secarlo han salido tremendamente parecidas (que quereis que haga, compró filamento de calidad, a ver si me patrocina winkle algún día) por lo que en la comparativa de la imagen que os pongo a continuación no se nota, pero si se nota en la impresión, el filamento lo burbujea al imprimir y lo más importante, no se rompe. Ya os contaré que tal las pruebas con el filamento de 2,85, porque ese tiene menos flexibilidad que una persona con el síndrome del azulejo:

![quemando el bootloader](/assets/img/secadora-conclusiones.jpg)

Fun fact: Todo este proyecto ha salido porque el horno de mi casa no es capaz de mantener una temperatura constante de 50 °C sin meter picos de 90 °C. Si no, ni me complicaba la vida. En fin, hay que ser realistas.

## Recursos del proyecto

A ver, dudo que vayáis a construir una máquina igual que esta, porque es bastante específica y está adaptada a los materiales que tenía por casa. Pero ya que el trabajo está hecho, os dejo por aquí un link al repositorio: [Insertar aquí el link, que todavia no he acabado de redactar el repo](https://github.com/FernanFPV).
De nada por tanto y gracias por tan poco.

## Bibliografía y Referencias Técnicas

Para la realización de este proyecto me he basado en documentación técnica y estándares de la comunidad maker, combinando principios de termodinámica con ingeniería de hardware, he revisado tantas cosas que si os pongo links concretos no acabo nunca, pero básicamente los principales campos han sido estos:


    * 1. Termodinámica y Psicrometría:
        - Principios de Willis Carrier: Fundamentos sobre el control de humedad y temperatura del aire. 	
        - Convección Natural: Conceptos de densidad y flujo de aire e intercambio termico
    * 2. Hardware y Electrónica (Hackeo de la Anet A8):
        - RepRap Wiki - Anet A8: Documentación completa sobre 	los esquemas y riesgos de la placa base Anet.
        - Pinout ATmega1284P: Esquema del microcontrolador para 	localizar el pin PWM del ventilador. 
        - Especificación de Ventiladores 4-Wire: Estándar de 	Intel para el control PWM a 5V de ventiladores.
        - Estándar Molex 4-pin: Especificaciones de corriente y 	voltaje para conectores de periféricos.
    * 3. Software y Firmware:
        - Arduino como ISP: Guía oficial para usar un Arduino 	Uno como programador de bootloaders.
        - Control PID: Teoría sobre el algoritmo 	Proporcional-Integral-Derivativo para estabilidad térmica.
    
    * 4. Materiales y Construcción:
        - Adhesivos de Poliuretano: Propiedades de expansión y 	resistencia térmica en maderas (DM).









