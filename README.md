## lab2-solid-principles

### Task 1 
Se marcan todas las violacionas a los principios SOLID
<img width="586" alt="image" src="https://github.com/IvanG-G/lab2-solid-principles/assets/138608967/3e04141f-04fa-4ea6-a1cd-657f86afc413">
<img width="648" alt="image" src="https://github.com/IvanG-G/lab2-solid-principles/assets/138608967/be78390c-018c-4459-98b8-3b5dac38c5e5">

### Task 2 & 3

### Refactorización en la clase Order
Se crea una interface para Order y se hacen implementaciones para ExpressOrder y StandardOrder, cada uno con su processPayment correspondiente, debido a que el código original ambos devolvían un true, simplemente devuelve un true, pero añadí como comentario que ahí debería de haber cierta lógica distinta para cada processPayment en cada Order.
Se aplican los siguientes principios SOLID:
- LSP: Al colocar una interface el método processOrder puede procesar todo tipo de Orders.
- OCP: Se pueden añadir más orders, pero los orders que ya existen no se modifican en caso de que se añadan más.
- DIP: El método processOrder utiliza la interace Order y una específica.
- ISP: Al dividir en dos clases StandardOrder y ExpressOrder no obligamos a la otra clase a implementar otro tipo de procesamiento de pago.
<img width="459" alt="image" src="https://github.com/IvanG-G/lab2-solid-principles/assets/138608967/6cafffc9-9ef0-4ee3-b3f3-37de3fadf0ad">


### Refactorización en el método verifyInventory
Para esta refactorización se crea una interface llamada VerifierInvetory con su implementación VerifierInventoryAdapter
Dentro de él se coloca el método verifyInventory.
<img width="455" alt="image" src="https://github.com/IvanG-G/lab2-solid-principles/assets/138608967/03e81380-f85d-4f2e-9e69-39615a2e97fa">

De igual manera se mandó a llamar la interface desde la clase principal.
<img width="455" alt="image" src="https://github.com/IvanG-G/lab2-solid-principles/assets/138608967/11b6dc75-aa3f-4e1b-94f5-59b154762921">

Se aplicaron los siguientes principios SOLID:
- DIP: Se manda a llamar desde SystemManager la interface y no su implementación.
- SRP: Debido a que la clase SystemManager se encargaba de todo, se creó esta clase llamada VerifierInvetory para delegar esta resonsabilidad de verificar existencia en inventario
- OCP: En caso de que requiera más validaciones se pueden agregar como otras implementaciones.


### Refactorización en el método updateOrderStatus
Se creó una interface Repository y su adaptador(el cuál es su implementación) para quitarle responsabilidad a la clase principal.
<img width="398" alt="image" src="https://github.com/IvanG-G/lab2-solid-principles/assets/138608967/d65cad22-a63a-49fa-a880-fd31f6d09bee">

Mismo caso que en el anterior, manda a llamar desde la interface en la clase principal.
<img width="455" alt="image" src="https://github.com/IvanG-G/lab2-solid-principles/assets/138608967/11b6dc75-aa3f-4e1b-94f5-59b154762921">

Se aplicaron los siguientes principios SOLID:
- DIP: Se manda a llamar desde SystemManager la interface y no su implementación.
- SRP: Delegación de responsabilidad del SM al repositorio


### Refactorización al método notifyCustomer

Se crea la interface NotificationManager y su implementación, la cuál es llamada EmailNotificationManager
<img width="643" alt="image" src="https://github.com/IvanG-G/lab2-solid-principles/assets/138608967/970e5fbf-1955-4265-8eea-4915c08a5e54">

Se aplicaron los siguientes principios SOLID:
- OCP: se pueden añadir más formas de notificación implementando la misma interface
- DIP: Desde el método principal se llama la interface.
- SRP: Se delegó esta tarea a la interface de notificaciones.
- LSP: en caso de que se requieran otros métodos de notificación, es fácil realizar la substitucion de ésta.
- ISP: No estás forzando a los otros métodos de notificacion a compartir la misma implementación.
