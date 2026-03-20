---
title: "🎭 Libreto: Reparación de nevera en 6 Actos (Ópera Bufa)"
date: 2025-02-7 10:00:00
categories: [Proyectos, Reparaciones]
tags: [electronica, diy, potencia]
image:
  path: /assets/img/nevera-open.jpg
  alt: "Una historia Narrada en ópera bufa de la reparación de una nevera"
---

## Acto I: L'Obertura (La aparición del antiheroe)

No le preguntes a una mujer su edad, a un hombre su salario, a un estudiante de teleco cuántas matrículas de Física II lleva, ni a Fernando qué estuvo haciendo en febrero de 2025.
Bueno, pues sí, os lo voy a contar... y de la mejor de las maneras. Pero antes, tenemos que conocer la **Génesis de la Nevera**. Es una de las reparaciones con las que más he aprendido, pero que lamentablemente las fotos que tengo son de historias de instagram, pues poco después mi movil reventó y perdi todas las fotos originales, de todas formas creo que es bastante interesante, asique le voy a dar algo de rollo a la historia, al estilo opera:

El artefacto apareció un septiembre de 2024 por la Delegación de Alumnos de la Escuela Politécnica Superior. Unos cuentan que fue un botín traído desde la Delegación de Medicina; otros narran la aparición espontánea y mística de semejante aparato. Que cada cual escoja su propia versión de los hechos.
Lo que estaba claro es que no funcionaba. Y, en un alarde de optimismo ciego, decidieron que el mejor sitio para su reparación era la Politécnica. Craso error (lo veremos a lo largo de la obra).

Este dispositivo pasó varios meses bajo una mesa, escondido del resto del mundo, hasta que un caluroso día de febrero —estaba lloviendo, pero el drama requiere calor— el héroe de esta historia decidió aventurarse en el arduo camino de la reparación.
Y sí, como la historia la estoy contando yo, si quiero describirme como el **Héroe de las Eras**, lo voy a hacer. Lo que nuestro pequeño protagonista no sabía era el descenso a los infiernos por el que le iba a llevar el auténtico villano de esta historia: **La Nevera**.


## Acto II: Aria del Optimismo Ciego (La Nevera se veía bien fácil)

Así fue como nuestro héroe se encaminó hacia su absoluta y confiada reparación. Reunió a un pequeño ejército de armas tomar (mis colegas de la Dele) con el objetivo claro y sencillo de diagnosticar el entuerto.
La nevera, a ojos de un ingeniero en ciernes, era insultantemente simple: no tenía compresor ni sistemas termodinámicos complejos. Solo una gran célula Peltier, un par de ventiladores, un potenciómetro para el control de la potencia y una placa de regulación... una placa que, en este punto exacto de la obra, era una perfecta desconocida para nosotros.

El diagnóstico inicial fue de una sencillez casi ofensiva. Solo se apreciaban tres bajas en el frente: dos condensadores y un fusible.
Nuestro pequeño héroe, haciendo gala de su formación teórica, se puso a razonar: "Los condensadores electrolíticos son los componentes con menor vida útil, con diferencia. Ergo, con toda seguridad, uno ha fallado, arrastrando al segundo al abismo, provocando un corto y haciendo saltar el fusible por pura compasión. Solo necesitamos repuestos y la nevera estará enfriando antes del entreacto".

Y así, henchido de valor, procedió a la canibalización: desguazó varios circuitos olvidados en busca de los órganos necesarios. Los encontró. Con una precisión de cirujano de guerra y una profesionalidad radiante, sustituyó los componentes dañados por piezas en "perfecto" estado.

Con esta pre-hazaña consumada, la lógica dictaba que todo estaba solucionado. Solo quedaba probar la reparación... una prueba que, según todos los cálculos del optimismo, no podía ser otra cosa que un éxito rotundo.


![El error inocente](/assets/img/nevera-falla.jpg)


## Acto III: El Preludio del Error (El falso enemigo)

Todo apuntaba a un éxito inminente. El héroe, con cara triunfante y el ego en niveles críticos, enchufó el circuito "a estrenar". No pasaron ni 12 microsegundos cuando una exaltante luz iluminó los cielos de la EPS. Aquel brillante resplandor provenía del fusible... otra vez quemado.
(Saliéndome de la historia: pegó un petardazo increíble. Sobre todo porque, en nuestra infinita arrogancia, no nos lo esperábamos).

Volviendo a la narración: el lastimado héroe se dio cuenta, entre el humo y el pitido de oídos, del hábil engaño de su enemigo. Resulta que el fusible y los condensadores no eran las únicas víctimas; eran solo los rehenes de un villano mucho más profundo.
Ahora, con una atención nacida del miedo, reviso el circuito. Hay que recalcar que, mientras intentaba no morir electrocutado, estaba cursando **Electrónica de Potencia**, así que poco a poco mis ojos empezaron a descifrar aquel jeroglífico de silicio.

Se trataba de un circuito rectificador (paso de AC a DC) seguido de un **convertidor Flyback**. Este último alimentaba dos frentes a la vez: por un lado, una línea de 12V fijos para los ventiladores, una pequeña luz interna y el propio control del Flyback. Por otro lado, el circuito de potencia pura: el encargado de regular cuánto voltaje se suministraba a la Célula Peltier para decidir si enfriábamos una Coca-Cola o simplemente la manteníamos "menos caliente".
(Hacemos un breve paréntesis en la ópera para hablar de termodinámica básica:)

¿Qué es una célula Peltier? Muy sencillo: es una bomba de calor en estado sólido formada por láminas cerámicas. Aprovecha el **Efecto Peltier**, que consiste en que, si alimentas el dispositivo, este absorbe calor por un lado y lo expulsa por el otro. La magia de la nevera no es "crear frío" (que no existe), sino evacuar calor.
Lo curioso es que son dispositivos reversibles: si aprovechas el **Efecto Seebeck**, podrías generar electricidad aplicando una diferencia de temperatura. Pero volviendo a nuestro drama, el secreto aquí es la evacuación. En el lado caliente (fuera de la nevera) tenemos un radiador y un ventilador. Si no quitas el calor que ya has sacado, la bomba se colapsa. Et voilà, magia... o física, según a quién preguntes.
Seguimos con la obra:


## Acto IV: El Réquiem del Silicio (Descenso a los infiernos)

Nuestros protagonistas pronto comprendieron que el abismo era más profundo de lo esperado. El fusible había vuelto a rendirse (aunque, por fortuna, los condensadores esta vez decidieron no decorar el techo). Todas las sospechas apuntaban al **MOSFET del Flyback**. Efectivamente: muerto.

Pero la masacre no terminaba ahí. Al inspeccionar el puente rectificador, descubrimos que dos de los diodos habían reventado; el cortocircuito nos saludaba ya desde la misma entrada de 220V. Fue aquí cuando el narrador aplicó un viejo truco de guerra para no arruinarse en fusibles: conectar una bombilla incandescente de 60W en serie con el enchufe. Si la bombilla brilla como el sol, el corto sigue ahí; si apenas se ilumina, hay esperanza. Spoiler: aquello parecía un estadio de fútbol.

El análisis forense era desolador. Por alguna razón arcana, el MOSFET falló, quedando en un cortocircuito permanente que se llevó por delante a los condensadores. Con el secundario del Flyback sufriendo, el primario entró en barrena, fulminando los diodos del puente y, finalmente, sacrificando al fusible en un último y fútil acto de protección.

Hicimos acopio de suministros: MOSFET nuevo, diodos nuevos, condensadores nuevos. Todo era nuevo, salvo nuestra paciencia.
Empezó entonces una ruda campaña de pruebas, osciloscopio en mano y el corazón en un puño. Pero la lógica se rompió: las señales de PWM no tenían sentido. El circuito intentaba arrancar, subía agónicamente hasta los 7V y caía en picado. Tras descartar problemas de carga, la realidad nos golpeó en la cara: los 12V originales jamás volverían. Había un culpable en las sombras: **El Integrado de Control**.

Para que os hagáis una idea de la maldad del fabricante: el integrado era un componente custom. Sin número de serie, sin identificación, sin rastro en ningún datasheet del planeta. Un pequeño chip SMD camuflado entre el estaño, diseñado para no ser comprendido ni mucho menos reemplazado. Él era el cerebro de la trama, y su muerte sellaba la ruina de toda la placa original.

![Memorias de ese dia](/assets/img/nevera-captura.png)

*Captura recuperada de las fatidicas conversaciones de aquel día*

## Acto V: Quimera de Silicio (La magia prohibida)

Cuenta la leyenda que el enemigo de mi enemigo es mi amigo. Traducido al lenguaje de la desesperación, esto significa: "La etapa primaria de otro Flyback que no ha explotado es mi aliada". Porque, efectivamente, a problemas extraordinarios, soluciones que rozan la ilegalidad técnica.
Nuestro pequeño héroe pasó eones buscando el integrado fantasma por los rincones más oscuros de internet, pero no hubo rastro. Así que tomó una decisión drástica: un trasplante de órganos. Decidió amputar la etapa primaria entera, conservando solo el transformador original, e injertar el primario de otro circuito donante que sí funcionaba.

Con un poco de suerte —bueno, con una cantidad de suerte que desafía las leyes de la estadística— aquello iba a arrancar. El reto era que el control de salida, gobernado por el optoacoplador, hablara el mismo idioma que la nueva etapa injertada.
Las primeras pruebas arrojaron un resultado falsamente favorable. El circuito, como un zombi recién reanimado, era capaz de balbucear: arrancaba, subía, caía hasta los 6V y volvía a empezar. Un bucle infinito para nada ideal, pero mejor que el silencio absoluto de los 0V.

Sin embargo, la fase de agonía real llegó con la **prueba de carga**. En ese instante, todo atisbo de esperanza se evaporó. Ni 12V, ni 6V, ni 5V... aquel osciloscopio marcaba la nueva tasa de alcohol permitida para conducir: **0,0**.

Tras esta desesperación, en un intento irracional de "hacer algo por no quedarnos mirando", probamos a cambiar incluso el transformador. Obviamente, querido lector, no funcionó. En absoluto. No sé en qué momento me pareció una idea razonable montar un **Frankenstein de circuitos**, pero el agotamiento nubla el juicio. Revisé cada componente mil veces; ni siquiera el optoacoplador estaba fundido (aunque también lo cambié por vicio).

Finalmente, entre el olor a estaño quemado y el eco del fracaso, llegó la hora de la solución que nadie quiso utilizar como primera opción:

![El Frankenstein](/assets/img/nevera-franki.png)

*Este fue el frankenstein que surgió, archivos recuperados de las historias de aquel día*

## Acto VI: Il Finale (La Redención y el Triunfo residen en el cambio)

Tras eones de pruebas, chispazos y experimentos que me daría vergüenza admitir en un tribunal de ética ingenieril, nos detuvimos a reflexionar. El rendimiento de una célula Peltier no es precisamente el de un reactor de fusión; es un dispositivo humilde que, para hacer algo útil, suele trabajar siempre al límite. Es decir, a 12V constantes.
¿Y sabéis qué otra cosa entrega 12V con la fidelidad de un perro guía? Efectivamente: una fuente de alimentación de PC.

Asumiendo la derrota frente al circuito original (que descanse en paz, o en el cubo de basura electrónica), nuestro pequeño pelotón de protagonistas se embarcó en una misión ya no tan mística, pero sí muy necesaria: **El Gran Recableado**. Pusimos todo en paralelo —Peltier, ventiladores y el agónico LED interno— y buscamos una vieja fuente de ordenador que acumulaba polvo en un rincón.

Para no cometer el sacrilegio de cercenar los cables de la fuente (y evitar problemas con el inventario de la Delegación, que somos pobres pero ordenados), tomamos la decisión más elegante del siglo: usar un conector Molex de 4 pines. Aquel estándar de los tiempos de los discos duros IDE se convirtió en nuestro cordón umbilical con la vida.

El sistema arrancó a la perfección. Ni rastro de la "inteligencia" original, ni de aquella tecnología arcaica que tantos dolores de cabeza nos dio. Solo el rugido constante de los ventiladores y el flujo incesante de electrones directos a la placa cerámica.

La nevera funciona. No enfría como para conservar nitrógeno líquido, pero es que es una Peltier, no un compresor de turbina. Con este pequeño pero glorioso éxito, el viaje del héroe y su redención finalizan con estas sabias palabras:

**"Si camina como un pato, grazna como un pato y enfría a 12V... no le preguntes por su esquema eléctrico"**.


## Conclusiones: El Post-Opus

Acabada esta ópera de narrativa heroica, toca hacer el análisis de daños. Seamos sinceros: la fuente de alimentación externa fue una opción que estuvo sobre la mesa desde el primer minuto. Sin embargo, con el ansia de poner a prueba mis conocimientos de Electrónica de Potencia, decidí darle un asalto al circuito original. Me hacía una ilusión tremenda verlo funcionar... Lamentablemente, el silicio tenía otros planes.

Pero, como se suele decir en estos casos de fracaso técnico, el verdadero triunfo reside en "los amigos que hemos hecho por el camino". O, en mi caso, en los conocimientos que saqué a base de prueba y error: aprendí una cantidad ingente sobre rectificadores, topologías Flyback, técnicas de diagnóstico y me sumergí en foros recónditos donde otras personas del mundo de la electrónica intentaron, sin éxito, lo mismo que yo (y con el mismo circuito).

Si el problema real fue no encontrar el integrado que funcione. También os digo que mi presupuesto para este proyecto era 0 €, si no tenía un componente no lo iba a comprar, por lo que la opción de sustituir ese integrado por uno que sí sabíamos como funcionaba, pero a cambio de rehacer el circuito entero no me acababa de convencer. 
**Lección aprendida**: Los Flybacks son una obra de arte de la ingeniería, pero tienen una tendencia casi poética a fallar siempre por el mismo sitio.

**Nota del Autor**: La idea de estructurar esta historia como una “Ópera Bufa” me vino a la mente recordando un vídeo mítico sobre una discusión entre dos streamers contada con esta misma épica teatral. Os dejaré el link en la bibliografía por si queréis reíros un rato (si es que no habéis hecho ya).


## Bibliografía

Como este proyecto lo realicé hace más de un año, hay detalles específicos que se han desdibujado, pero gran parte del trabajo de investigación y las pruebas de diagnóstico se basaron en los siguientes recursos:
- [Foro Elektroda - HYS60-12-L](https://www.elektroda.com/rtvforum/topic3290360.html): Un hilo en un foro polaco donde se analiza a fondo la misma placa que aparece en este post. Fue clave para entender la topología del circuito.
- [Reparación de placa de vinoteca (Manitas Armada)](https://www.youtube.com/watch?v=IugRK69KaIk): Tutorial en español sobre una placa muy similar. Útil para identificar los componentes que suelen fallar por fatiga térmica (condensadores y transistores).
- [Inspiración narrativa: Discusión en 4 actos (Carola ft. Elisa Waves)](https://www.youtube.com/watch?v=vaV6oQuEQ00): El vídeo que inspiró la estructura de este post.

Además de estos enlaces, consulté diversas hojas de características (datasheets) de integrados PWM y MOSFETs de potencia similares, así como hilos técnicos en YoReparo que ayudaron a descartar soluciones inviables.




