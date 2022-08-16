# TC2008B Reto: Simluación de Movilidad Urbana con Multiagentes

## Integrandes del equipo

* Luis Ángel Guzmán Iribe - A01741757
* Cesar Galvez - A01252177
* Antonio López Chávez - A01741741
* Sebastián Gálvez Trujillo - A01251884

## Descripción del reto a desarrollar.
El reto consiste en la simulación de un evento de tráfico, donde automóviles circularán según las reglas de tránsito establecidas, con espacio entre carros, respeto a los semáforos, velocidad adecuada y sobre todo, no tener colisiones entre vehículos. Durante dicha simulación, se espera que se resuelva alguno de los siguientes puntos:
* Controlar los espacios disponibles de un estacionamiento de forma inteligente, para evitar tener carros manejando en vueltas buscando uno.
* Fomentar el carpooling, para reducir el número de carros en las calles.
* Estrategia eficiente para tomar rutas menos congestionadas, reduciendo tráfico al tener más movimiento.
* Desarrollar un sistema de coordinación entre los semáforos, para reducir embotellamientos. Puede ser también el cálculo inteligente de movimiento de los carros cruzando para saber cuando cambiar de color el semáforo.

## Identificación de los agentes involucrados. 
* **Carros**: El carro será el agente principal en nuestra simulación, y el que más interés genera al momento de estudiar su comportamiento. El vehículo tendrá que atenerse a reglas de tránsito básicas y ser capaz de circular por las calles, de las que se hablará más adelante. También deberá ser capaz de atenerse a semáforos y tomar en cuenta la presencia de otros carros. Será el agente con más reglas propias por obedecer.
* **Semáforos**: Los semáforos interactúan principalmente con los carros, deteniendo o permitiendo su movimiento dependiendo de su estado (luz roja, amarilla o verde).
* **Calles / Escenario**: Las calles servirán como medio para delimitar las casillas de la grid a la que se puede mover el vehículo, no tendrán ninguna acción en particular, solamente estados que representen el sentido de la calle para que el carro pueda avanzar hacia las casillas correspondientes.

## Elementos de interfaz en el proyecto  en Unity.
La función de **Unity** es ofrecer una representación gráfica mucho más elaborada de lo que se podría hacer en Python con la librería de **MatPlotLib**, con *“sprites”* y otros assets que procesen la información generada durante la simulación del modelo y generen objetos que sigan los movimientos de los agentes. 
