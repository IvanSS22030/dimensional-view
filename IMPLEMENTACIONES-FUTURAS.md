# Implementaciones futuras

Ranking de mejoras para **Dimensional View**, ordenado por cuánto aporta cada una
al objetivo de la página: que alguien que no sabe nada de dimensiones termine
entendiéndolas.

El orden es un juicio de diseño, no un cálculo. Cada punto lleva su razón.

---

## Principio rector: no agregar más texto

La página **cuenta** mucho y **demuestra** poco. Ya hay 33 fichas bien escritas;
el cuello de botella no es información, es demostración. Ninguna mejora de esta
lista consiste en escribir más: una ficha número 34 competiría con las 33 que
nadie alcanza a leer.

Toda mejora de aquí en adelante tiene que **mostrar** algo que hoy solo se afirma.

---

## 1. La pelota y la barrera que sube de nivel

**Estado:** ✅ implementado — modo *El escape*
**Valor:** muy alto · **Esfuerzo:** alto

La mejor adición posible para el objetivo fijado. Razón: hoy el panel derecho
afirma *"ninguna habitación lo encierra"* mientras la figura solo gira. Esta demo
ataca exactamente ese hueco, es interactiva y enseña el concepto raíz.

Que la barra siga avanzando mientras la pelota **se niega a moverse** es la
lección entera: esa resistencia física enseña más que las 33 fichas juntas.

La clave del diseño: **no cambia el objeto, cambia la barrera.**

| Dimensión | La barrera | El desenlace |
|---|---|---|
| **0D** | ninguna | no hay movimiento posible, ni «un poco» |
| **1D** | otra pelota en la recta | imposible pasar: solo atravesándola |
| **2D** | la misma pelota | la rodea… pero un círculo cerrado la atrapa |
| **3D** | el círculo cerrado | salta por encima… pero una caja cerrada la atrapa |
| **4D** | la caja cerrada | sale sin tocar las paredes |
| **5D** | nada de 3D | harían falta paredes de cuatro dimensiones |

La pelota es la misma siempre. Lo que sube de nivel es la cárcel.

### El riesgo, y es serio

En 4D, *"la pelota sale de la caja cerrada"* se va a ver como si atravesara la
pared — es decir, como un **bug**, no como una revelación. La única forma de que
funcione es hacer **visible el eje oculto**: un marcador de la coordenada W, o
que la pelota se apague y se vuelva fantasma conforme se aleja de tu rebanada de
espacio. Si el espectador no ve el movimiento por *ana*, cree que hiciste trampa.

Esa es la diferencia entre que la demo enseñe o que desprestigie a la página.

**Cómo se resolvió:** las tres cosas a la vez — medidor del eje oculto con la
coordenada numérica, la pelota se vuelve fantasma al salir del espacio, y el
estado dice *FUERA DE TU ESPACIO* en el momento exacto. Además las colisiones
son reales: la caja bloquea solo mientras `|w| < radio`, así que el escape no
está guionizado, ocurre porque el eje extra existe.

---

## 2. Aislar los planos de rotación

**Estado:** pendiente
**Valor:** alto · **Esfuerzo:** bajo — la mejor relación de la lista

Ahora mismo el teseracto gira en 6 planos a la vez y el penteracto en 10. No es
incorrecto, pero es **ilegible**: nadie puede seguir nada y se vuelve un adorno
bonito.

Un control para girar en *un solo* plano (XY, XW, ZW…) convierte el 4D de
"hipnótico" a "ah, ya vi lo que hace".

La maquinaria por plano ya existe en el código (`planes[]`, con su velocidad por
plano); solo falta exponerla en la interfaz.

**Bonus:** el propio panel dice que un ser 4D *"gira en dos planos a la vez"*
mientras la pantalla muestra seis.

---

## 3. Un mando continuo entre dimensiones

**Estado:** pendiente
**Valor:** alto · **Esfuerzo:** bajo

El morph ya es continuo por dentro — las extensiones de los ejes (`ext[]`) son
números decimales. Hoy se desperdicia: el paso de 2D a 3D dura 600 ms y no puedes
detenerlo.

Con una barra arrastrable podrías **quedarte en 2.4D** y ver el cuadrado siendo
arrastrado por el eje nuevo, con un rastro de dónde empezó.

Eso hace visible la regla de construcción — *cada dimensión es la anterior
barrida por un eje perpendicular* — que hoy solo está escrita.

---

## 4. La escalera de sombras

**Estado:** pendiente
**Valor:** alto · **Esfuerzo:** medio

Mostrar un cubo 3D proyectando su sombra de cuadrado-dentro-de-cuadrado, al lado
del teseracto haciendo exactamente lo mismo un piso más arriba.

Mata el malentendido número uno (*"el cubo interior es más pequeño"*) dejándote
ver el mismo truco en una dimensión que ya dominas. La página ya lo advierte con
texto; esto lo probaría.

---

## 5. El corte transversal (rebanadas)

**Estado:** pendiente
**Valor:** muy alto · **Esfuerzo:** alto — el techo más alto de la lista

La esfera de Planilandia, bien hecha: un objeto 4D atravesando tu espacio aparece
de la nada, cambia de forma (cubo → triángulo → hexágono → …) y se esfuma.

Es la otra manera canónica de "ver" el 4D, complementaria a la proyección que ya
usa la página. Requiere calcular la intersección de un hiperplano con el
politopo, que es el trabajo más grande de toda la lista.

---

## 6. Modo guiado

**Estado:** pendiente
**Valor:** medio · **Esfuerzo:** bajo

Un recorrido que se reproduce solo de 0D a 5D, con los ejemplos cronometrados.

El menor valor conceptual de la lista, pero el mayor alcance: la mayoría de quien
abra la página no va a tocar ningún botón.
