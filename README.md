# Diagrama de Casos de Uso


1. Crea el diagrama de uso haciendo uso de platuml, representado los actores y casos de uso que identifiques en los requisitos.

![Diagrama de casos de uso](https://github.com/Lmrocio/PRACTICA_DIAGRAMA_CASOS_DE_USO/blob/main/Diagrama%20de%20casos%20de%20uso.png?raw=true)

<details> <summary>Código empleado</summary>
@startuml

actor "Cliente" as Cliente

actor "Sistema" as Sistema

usecase "Validarse en el sistema" as UC1

usecase "Sacar dinero" as UC2

usecase "Avisar saldo insuficiente" as UC3

usecase "Avisar límite diario superado" as UC4

usecase "Realizar transferencia" as UC5

usecase "Realizar ingreso" as UC6

Cliente -- UC1

Cliente -- UC2

Cliente -- UC5

Cliente -- UC6

UC2 ..> UC1 : <<include>>

UC5 ..> UC1 : <<include>>

UC6 ..> UC1 : <<include>>

UC2 --> UC3 : Si saldo insuficiente

UC2 --> UC4 : Si supera límite diario

Sistema --> UC3 : Verifica saldo

Sistema --> UC4 : Verifica límite

Sistema --> UC5 : Procesa transferencia

Sistema --> UC6 : Procesa ingreso

@enduml
</details>
<hr>

2. Describe, haciendo uso de la plantilla, al menos el caso de uso "Sacar dinero", con las interacciones que tiene entre el actor y el caso de uso.
 
a) Caso de uso: Validarse en el sistema.
- Actor Principal: Cliente

- Descripción: El cliente debe autenticarse en el sistema antes de realizar cualquier otra operación en el cajero automático. El sistema solicita al
cliente ingresar su tarjeta y código PIN. Si la validación falla, el sistema no permite continuar con ninguna operación.

b) Caso de uso: Sacar dinero.
- Actor Principal: Cliente

- Descripción: El cliente puede retirar una cantidad de dinero en el cajero automático. El cliente ingresa la cantidad de dinero que desea retirar y el
sistema verifica si el cliente tiene suficiente saldo en su cuenta y si no supera el límite diario permitido. Si alguna
de estas condiciones no se cumple, el sistema informa al cliente con un mensaje. Si todo está correcto, el sistema entrega el dinero y actualiza el saldo del cliente.

c) Caso de uso: Realizar transferencia.
- Actor Principal: Cliente

- Descripción: El cliente, después de validarse correctamente, puede realizar una transferencia a otra cuenta. El cliente ingresa los datos necesarios
(número de cuenta destino, monto, etc.), y el sistema procesa la operación. El sistema verifica si el saldo es suficiente y si la operación cumple con
los límites establecidos. Una vez validada la operación, el sistema transfiere el dinero y actualiza los saldos de ambas cuentas.

d) Caso de uso: Realizar ingreso.
- Actor Principal: Cliente

- Descripción: El cliente también puede realizar un ingreso de dinero en su cuenta mediante el cajero automático. El cliente introduce el dinero que desea ingresar y el sistema lo verifica. Si el proceso es correcto, el sistema agrega el monto ingresado al saldo de la cuenta del cliente y confirma la operación.

e) Caso de uso: Avisar saldo insuficiente.
- Actor Principal: Sistema

- Descripción: El sistema avisa al cliente cuando intenta retirar una cantidad superior al saldo disponible en su cuenta. El mensaje que muestra el sistema
indica que no es posible realizar la operación debido a que el cliente no tiene suficiente dinero en su cuenta. El cliente puede optar por intentar con
una cantidad menor o cancelar la operación.

f) Caso de uso: Avisar límite diario superado.
- Actor Principal: Sistema

- Descripción: El sistema avisa al cliente cuando intenta retirar una cantidad que supera el límite de retiro diario permitido. Si el cliente ya ha
alcanzado o excedido este límite, el sistema muestra un mensaje de advertencia y le informa que no puede continuar con la operación. El cliente
puede optar por cancelar la transacción o realizar una cantidad menor si está dentro del límite.



Relación de los actores con los casos de uso:
Cliente:

Interactúa con los casos de uso "Validarse en el sistema", "Sacar dinero", "Realizar transferencia" y "Realizar ingreso".
Recibe los mensajes del sistema a través de los casos de uso "Avisar saldo insuficiente" y "Avisar límite diario superado".
Sistema:

El sistema es responsable de verificar el saldo y el límite de retiro en los casos de uso "Sacar dinero", "Avisar saldo insuficiente", y "Avisar límite diario superado".
El sistema procesa las operaciones de "Realizar transferencia" y "Realizar ingreso" y actualiza los saldos correspondientes.

<hr>

3. Responde a las siguiente pregunta:
   - ¿Para qué me sirve tener/realizar un diagrama de casos de uso modelando el sistema que se representa? ¿Qué aporta?

<hr>
