# TC2008B Reto: Simluación de Movilidad Urbana con Multiagentes

## Integrandes del equipo

* Luis Ángel Guzmán Iribe - A01741757 - Programador
* Cesar Galvez - A01252177 - Diseñador y Documentación
* Antonio López Chávez - A01741741 - Unity y Programador 
* Sebastián Gálvez Trujillo - A01251884 - Unity y Documentación

## Link al Zip del proyecto de Unity
https://drive.google.com/file/d/1WHZgc7Xvp1VoIP8SzvHPYkZgy_mNBW5e/view?usp=sharing

## Instalaciones requeridas

1. Python
El programa se desarrolló en ```Python 3.10.0```. Se recomienda realizar esta instalación de la [página oficial de python](https://www.python.org/downloads/)

2. Librerías
Librerías de Python necesarias para la ejecución del código. Para corroborar que la instalación de Python fue exitosa puede escribir:
```
python --version
``` 
Una vez que corrobora que la instalación fue exitosa, proceda a instalar las librerías enlistadas mediante pip install en la consola de comandos con:

* mesa
```
pip install mesa
``` 
* matplotlib
```
pip install matplotlib
``` 
* pandas
```
pip install pandas
``` 

3. Visual Studio Code
Este paso es opcional, pero recomendamos correr el código con la extensión ```Jupyter``` para la ejecución de la notebook con el código. Puede encontrar la guía de instalación en la [página oficial de Visual Studio Code](https://code.visualstudio.com/download).

## Problematica
El reto consiste en proponer una solución para un problema de movilidad en México, en este caso, el control del flujo vehicular en una intersección. Nuestro sistema deberá ser capaz de simular y controlar el movimiento de los vehiculos que crucen por una intersección de manera que reduzca el tiempo que tardarían en ciruclar los autos con un semaforo tradicional con temporizador.

## Propuesta de solución
La coordinación del tráfico está bajo el control de los semáforos. Los semáforos detectan cuando un vehiculo está a punto de entrar al cruce para detener o permitir su movimiento si ya hay otro carro en el cruce.

Los 4 semaforos de la intersección estarían interconectados para coordinarse de manera eficiente y así permitir a los autos pasar sin riesgo de chocar con otro auto que viene en otro carril.

Este modelo consta de una intersección de dos calles de doble sentido representada como una cuadricula discreta donde los carros deben esperar a la luz indicada del semaforo para poder avanzar. A su vez, lo carros tienen una probabilidad predeterminada (en este caso de 5%) de dar una vuelta a la derecha o izquierda dependiendo del sentido del carril en en el que se encuentren actualmente.

### Agentes

### Carros

Principal agente del modelo, sus acciones y estado están determinadas por los agentes a su alrededor.

#### Reglas de estado:
* Su orientación (dx, dy y vertical) se define en el momento que se crea la instancia del agente, pero puede cambiar mediante el método change_direction().
* Cuando se encuentra en medio de la intersección (sin vecinos de tipo terreno o semaforo) puede cambiar su orientación (a la del carril en el que se encuentra) con una probabilidad predeterminada, en este caso de 10%
<center>
<img src="./Diagrama Carro - Reto multiagentes.png" width=auto height=600 />
</center>

#### Reglas de acción:
* Si la casilla de adelante (dependiendo de la orientación del agente) está vacía, y no hay ninguún semaforo en su vecindad con la misma orientación: **avanza**.
* Si la casilla de adelante está vacía, y hay un semaforo en su vecindad con la misma orientación y estado en color verde: **avanza**.
* Si la casilla de adelante está vacía, y hay un semaforo en su vecindad con la misma orientación y estado en color rojo: **no avanza**.
* Si la casilla de adelante está obstruida por cualquier agente: **no avanza**.

### Semaforo

Agente sin acciones cuyo estado determina las acciones de los carros.

#### Reglas de estado:
* Si no hay ningún carro con la misma orientación (vertical u horizontal) en la vecindad inmediata del semaforo, su color cambia a **amarillo**
* Si hay un carro en con la misma orientación en la vecindad inmediata del semáforo, y ninguno de los semáforos en una vecindad de un radio de 3 casillas con la misma orientación es verde, su color cambia a **Verde**
* Si hay un carro en con la misma orientación en la vecindad inmediata del semáforo, y al menos uno de los semáforos en una vecindad de un radio de 3 casillas con la misma orientación es verde, su color cambia a **Rojo**
<center>
<img src="./Diagrama Semáforo - Reto multiagentes.png" width=auto height=600 />
</center>

### Terreno

Agente sin estado ni acciones que sirve para delimitar la calle. Representa el pasto y demás estructuras que rodean la intersección

### Créditos para autores de assets usados en el proyecto
* Low Poly Tree Pack [Árboles]: Broken Vector (support@brokenvector.com)
* Low Poly Park [Assets para parque]: Broken Vector (support@brokenvector.com)
* Low Poly Road Pack [Assets para calles]: Broken Vector (support@brokenvector.com)
* Low Poly Brick House [Assets de casas]: Broken Vector (support@brokenvector.com)
* Free Stylized Skybox [Cielos]: Yuki2022 (gamemakeryuki@outlook.com)
* Tarbo - City 'Traffic Lights' Pack [Semáforos]: Tarbo studio (tarbostudio@gmail.com)
* JSON .NET For Unity [Funciones para 'parsear' JSONs]: parentElement, LLC (nebraskadev@gmail.com)
* Simple Cars Pack [Assets de autos]: MyxerMan (m-anton-a@mail.ru)
