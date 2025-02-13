# Diagrama de Casos de Uso - Cajero automático

>La actividad consiste en:
>
>Tras la reunión del analista, recibes una lista de Requisitos Funcionales para implementar el funcionamiento de un cajero de banco:
>
>R1. El cliente debe validarse en el sistema para poder realizar cualquier operación en el cajero automático.
>
>R2. Si el cliente intenta sacar una cantidad que supera el saldo de su cuenta, el cajero le avisará de que no es posible sacar esa cantidad
>
>R3. Si el cliente intenta sacar una cantidad que supera el límite diario, el cajero le avisará de que no es posible y volverá a solicitar una cantidad
>
>R4. El cliente podrá hacer una transferencia a otra cuenta
>
>R5. El cliente podrá realizar un ingreso a través del cajero automático
>
>Representa mediante una diagrama de casos de uso, los distintos escenarios, actores y relaciones.

<hr>
<br>

## 1. Crea el diagrama de uso haciendo uso de platuml, representado los actores y casos de uso que identifiques en los requisitos.

Acontinuación aparece el diagrama de casos de uso del enunciado del ejercicio, así como el código empleado.

![Diagrama de casos de uso](https://github.com/Lmrocio/PRACTICA_DIAGRAMA_CASOS_DE_USO/blob/main/Diagrama%20de%20casos%20de%20uso.png?raw=true)

<details> <summary>Código empleado</summary>

 ```
 @startuml

actor "Cliente" as Cliente

actor "Cajero" as Cajero

usecase "Validarse en el sistema" as UC1

usecase "Sacar dinero" as UC2

usecase "Realizar transferencia" as UC5

usecase "Realizar ingreso" as UC6

usecase "Avisar saldo insuficiente" as UC3

usecase "Avisar límite diario superado" as UC4


Cliente --> UC1

Cliente --> UC2

Cliente --> UC5

Cliente --> UC6

UC2 ..> UC1 : <include>

UC5 ..> UC1 : <include>

UC6 ..> UC1 : <include>

UC2 --> UC3 : Si saldo insuficiente

UC2 --> UC4 : Si supera límite diario

Cajero --> UC3 : Verifica saldo

Cajero --> UC4 : Verifica límite

Cajero --> UC5 : Procesa transferencia

Cajero --> UC6 : Procesa ingreso

@enduml
```

</details>

<hr>
<br>

## 2. Describe, haciendo uso de la plantilla, al menos el caso de uso "Sacar dinero", con las interacciones que tiene entre el actor y el caso de uso.

### a) Caso de uso: **Validarse en el sistema**.
- **Actor Principal**: Cliente
- **Descripción**: El cliente debe autenticarse en el sistema antes de realizar cualquier operación en el cajero automático. Para ello, debe insertar su tarjeta y luego ingresar el código PIN. Si la validación falla (por ejemplo, debido a un código incorrecto o tarjeta no válida), el sistema no permite al cliente continuar con ninguna otra operación.


### b) Caso de uso: **Sacar dinero**.
- **Actor Principal**: Cliente
- **Descripción**: El cliente puede retirar una cantidad de dinero del cajero automático. Primero, el cliente ingresa la cantidad que desea retirar, luego el cajero verifica si el saldo de la cuenta es suficiente y si la cantidad solicitada no supera el límite diario de retiro. Si alguna de estas condiciones no se cumple, el cajero informa al cliente con un mensaje adecuado (por ejemplo, "Saldo insuficiente" o "Límite diario superado"). Si ambas condiciones son satisfactorias, el cajero entrega el dinero y actualiza el saldo de la cuenta del cliente.


### c) Caso de uso: **Realizar transferencia**.
- **Actor Principal**: Cliente
- **Descripción**: Después de haberse validado correctamente, el cliente puede realizar una transferencia a otra cuenta. El cliente ingresa los datos necesarios (como el número de cuenta destino, la cantidad a transferir, etc.), y el cajero procesa la operación. El cajero verifica que el saldo sea suficiente y que la operación cumpla con los límites establecidos. Una vez que la operación es validada, el cajero realiza la transferencia y actualiza los saldos de ambas cuentas.


### d) Caso de uso: **Realizar ingreso**.
- **Actor Principal**: Cliente
- **Descripción**: El cliente puede realizar un ingreso de dinero en su cuenta mediante el cajero automático. El cliente introduce el dinero en el cajero, y este lo verifica. Si el dinero ingresado es correcto (por ejemplo, detectando que los billetes son legítimos), el cajero agrega la cantidad al saldo de la cuenta del cliente y confirma la operación con un mensaje de éxito.


### e) Caso de uso: **Avisar saldo insuficiente**.
- **Actor Principal**: Cajero
- **Descripción**: El cajero avisa al cliente cuando intenta retirar una cantidad superior al saldo disponible en su cuenta. El cajero muestra un mensaje indicando que no es posible realizar la operación debido a que el cliente no tiene suficiente saldo. El cliente puede optar por ingresar una cantidad menor o cancelar la operación.


### f) Caso de uso: **Avisar límite diario superado**.
- **Actor Principal**: Cajero
- **Descripción**: El sistema avisa al cliente cuando intenta retirar una cantidad que supera el límite de retiro diario permitido. Si el cliente ya ha alcanzado o excedido este límite, el cajero muestra un mensaje de advertencia indicando que no se puede continuar con la operación. El cliente puede optar por cancelar la transacción o realizar un retiro menor si está dentro del límite.


## Relación de los actores con los casos de uso:

### Cliente:
- **Interacciones**: 
  - **Validarse en el sistema**: El cliente se valida antes de realizar cualquier operación.
  - **Sacar dinero**: El cliente puede retirar dinero, siempre que se cumplan las condiciones de saldo y límite.
  - **Realizar transferencia**: El cliente puede transferir dinero a otra cuenta, una vez validado.
  - **Realizar ingreso**: El cliente puede ingresar dinero en su cuenta.
- **Recibe mensajes**:
  - **Avisar saldo insuficiente**: Recibe un mensaje si intenta retirar más dinero del disponible.
  - **Avisar límite diario superado**: Recibe un mensaje si intenta superar el límite de retiro diario.

### Cajero:
- **Responsabilidad**: 
  - Verifica el saldo y el límite de retiro en el caso de uso **"Sacar dinero"**.
  - Procesa y valida las operaciones de **"Realizar transferencia"** y **"Realizar ingreso"**, actualizando los saldos de las cuentas.
  - Muestra los mensajes de advertencia en los casos de uso **"Avisar saldo insuficiente"** y **"Avisar límite diario superado"**.
<hr>
<br>

## 3. ¿Para qué sirve tener/realizar un diagrama de casos de uso modelando el sistema que se representa? ¿Qué aporta?

El **diagrama de casos de uso** es una herramienta crucial en la fase de análisis y diseño de sistemas, ya que ayuda a representar las funcionalidades del sistema desde la perspectiva de los usuarios. En este caso, modela las interacciones entre los actores (Cliente y Cajero) y las funcionalidades del sistema del cajero automático. A continuación, se describen los beneficios y aportes de este diagrama:

### ¿Para qué sirve tener un diagrama de casos de uso?

- **Definir el alcance del sistema**: Muestra qué acciones o servicios ofrece el sistema a los actores involucrados, como el **Cliente** y el **Cajero**. Define claramente las interacciones del usuario con el sistema.

- **Comunicación clara**: Actúa como una herramienta de comunicación efectiva entre los desarrolladores y los stakeholders (cliente o usuarios finales), ya que ilustra las funcionalidades del sistema de manera visual y comprensible.

- **Documentación estructurada**: Proporciona una visión estructurada del comportamiento del sistema, lo que facilita la documentación para futuras referencias.

- **Análisis de requerimientos**: Permite entender de manera clara los requisitos funcionales del sistema y la lógica de interacción entre el usuario y el sistema, lo que facilita su implementación.

### ¿Qué aporta un diagrama de casos de uso?

- **Visión general del sistema**: El diagrama permite ver todas las operaciones principales que los usuarios pueden realizar en el sistema (en este caso, el cajero automático), facilitando la planificación de las funcionalidades.

- **Claridad en los procesos y flujos**: Ofrece una representación de los flujos de interacción entre los actores y el sistema, ayudando a comprender cómo deben desarrollarse las distintas funciones del sistema.

- **Base para la implementación del sistema**: Proporciona una base sólida para la fase de desarrollo del sistema, pues define claramente las tareas que deben ser cubiertas por el sistema.

- **Facilita la gestión de cambios**: Permite identificar rápidamente qué partes del sistema son modificadas al incluir nuevas funcionalidades o realizar ajustes, facilitando la gestión de cambios durante el desarrollo.

### En resumen

El diagrama de casos de uso es una herramienta esencial para definir, comunicar y documentar las funcionalidades del sistema, contribuyendo al desarrollo eficiente y organizado del software.

