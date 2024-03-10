# Registro de Code Smells y Deudas Técnicas

Este documento sirve como un registro de los code smells (malos olores en el código) y deudas técnicas identificados en el proyecto de C#. La finalidad es llevar un seguimiento de estos problemas para priorizar su refactoring (refactorización) o resolución en futuras iteraciones.

## Plantilla para el Registro

Para añadir un nuevo code smell o deuda técnica, copia y pega la siguiente plantilla en la sección correspondiente de este documento.

### 1: 
- **Tipo**: Deuda Técnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicación exacta (línea/clase/método)**: Todo
- **Descripción**: Clase diós, es una clase que tiene 214 lineas de código y se encarga en hacer la gran mayoria de lógica del programa. Debe partirse en clases mas pequeñas.
- **Impacto Potencial en el Proyecto**: Mediano
- **Sugerencia de Resolución**: Crear sub-clases que se encarguen de los comportamientos del juego y dejar esta como solo la entidad con sus propiedades base.
### 2: 
- **Tipo**: Deuda Técnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicación exacta (línea/clase/método)**: Linea 19
- **Descripción**: Las preguntas de los diferentes temas (Pop, ciencia, etc) son su propio arreglo con nombre propio lo cual lo hace poco escalable de poner mas preguntas de temas.
- **Impacto Potencial en el Proyecto**: Alto, porque de poner temas nuevos hay que crear lógica especializada para cada uno lo cual es innecesario.
- **Sugerencia de Resolución**: Crear un arreglo de LinkedList de tipo string llamado Questions.
### 3: 
- **Tipo**: Deuda Técnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicación exacta (línea/clase/método)**: Linea 14, 15 y 17
- **Descripción**: Tanto places como purces y penaltybox debe ser su propia entidad y objeto, asi como se está manejando las propiedades con arreglos int[6] es poco legible y escalable.
- **Impacto Potencial en el Proyecto**: Alto
- **Sugerencia de Resolución**: Crear entidades con propiedades muy legibles en vez de arreglos y ponerlos en su propia carpeta.
### 4: 
- **Tipo**: Deuda Técnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicación exacta (línea/clase/método)**: Constructor, line 27.
- **Descripción**: Todo el constructor está mal hecho. Está quemada en la lógica que va a recibir hasta 50 preguntas de cada categoria y estos datos se están cargando directamente en el constructor en vez de un metodo dedicado. 
- **Impacto Potencial en el Proyecto**: Medio
- **Sugerencia de Resolución**: Reconstrucción completa del constructor donde pueda recibir parametros con los datos necesarios y delegar la carga de datos la cual no debe inluir codigo quemado y cargar cualquier categoria mediante referencia. Tambien se debe crear el objeto de categoria.
### 5: 
- **Tipo**: Code Smell
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicación exacta (línea/clase/método)**: createRockQuestion(), hoyManyPlayers()
- **Descripción**: Este metodo no deberia existir y sobra.
- **Impacto Potencial en el Proyecto**: Poco
- **Sugerencia de Resolución**:  Se deberia eliminar y su lógica transferirse a un metodo de creacion genérico.
### 6: 
- **Tipo**: Code Smell
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicación exacta (línea/clase/método)**: isPlayable
- **Descripción**: Metodo que no se referencia.
- **Impacto Potencial en el Proyecto**: Bajo
- **Sugerencia de Resolución**: Eliminar el metodo.
### 7: 
- **Tipo**: Code Smell
- **Archivo(s) Afectado(s)**: Todo el proyecto
- **Ubicación exacta (línea/clase/método)**: Todo el proyecto
- **Descripción**: Los IDE cuentan con herramientas de formateo de código las cuales formatean y quitan importaciones no usadas para dejar el proyecto mucho mas limpio. Hay que usarlo pues el espaciado dá mucho donde mejorar.
- **Impacto Potencial en el Proyecto**: Medio
- **Sugerencia de Resolución**: Correr las herramientas de limpieza de código dentro del IDE (En este caso Visual Studio 2022).
### 8: 
- **Tipo**: Code Smell
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicación exacta (línea/clase/método)**:  add()
- **Descripción**: Dejaron en el código logs de debugging, esos se deberian eliminar.
- **Impacto Potencial en el Proyecto**: Bajo
- **Sugerencia de Resolución**: Eliminar todos los console.writeline pues solo se deberían usar para debugging y nunca tocar la rama de master.
### 9: 
- **Tipo**: Code Smell
- **Archivo(s) Afectado(s)**: Todo el proyecto
- **Ubicación exacta (línea/clase/método)**: Todos los metodos.
- **Descripción**: La nomenclatura recomendada recomienda que la primera letra de cada uno de los métodos comenze con mayuscula y no use palabras reservadas como add. roll() -> Roll().
- **Impacto Potencial en el Proyecto**: Bajo
- **Sugerencia de Resolución**: Usar la nomenclatura sugerida.
### 10: 
- **Tipo**: Deuda Técnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicación exacta (línea/clase/método)**: roll();
- **Descripción**: Usar un patrón de administración de estado del juego para remover la necesidad de informarle al jugador quel estado mediante console.writelines en la misma lógica lo cual la infla y hace menos legible.
- **Impacto Potencial en el Proyecto**: Alto
- **Sugerencia de Resolución**: Usar un patrón que lleve el estado del juego mediante referencia y que sea esa clase dedicada la unica que informe al jugador del estado. 
### 11: 
- **Tipo**: Deuda Técnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicación exacta (línea/clase/método)**: askQUestion(); currentCategory();
- **Descripción**: Nunca se deberian usar IFs de manera simultanea para hacer comparaciones tan repetitivas.
- **Impacto Potencial en el Proyecto**: Medio
- **Sugerencia de Resolución**: Usar el Switch Case o usar un método que valore una categoria genérica.
### 12: 
- **Tipo**: Deuda Técnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicación exacta (línea/clase/método)**: linea 179
- **Descripción**: Typo
- **Impacto Potencial en el Proyecto**: Bajo
- **Sugerencia de Resolución**: Verificar y corregir los typos.
### 13: 
- **Tipo**: Deuda Técnica
- **Archivo(s) Afectado(s)**: GameRunner.cs
- **Ubicación exacta (línea/clase/método)**: Todo el archivo
- **Descripción**: El método Main encontrado en este archivo no deberia tener lógica de negocio y mucho menos valores quemados.
- **Impacto Potencial en el Proyecto**: Alto
- **Sugerencia de Resolución**: Usar un framework como .net que se encargue en administrar la aplicación y especialmente el método main. Despues de instalarlo hay que mover esa lógica a otro lado.
### 14: 
- **Tipo**: Deuda Técnica
- **Archivo(s) Afectado(s)**: OrderService.cs, UserService.cs, InvoiceService.cs
- **Ubicación exacta (línea/clase/método)**: Todo el archivo
- **Descripción**: Este archivo no es referenciado en ningún otro método y es basura o es failmente reemplazable.
- **Impacto Potencial en el Proyecto**: Bajo
- **Sugerencia de Resolución**: Eliminar el archivo.
### 15: 
- **Tipo**: Deuda Técnica
- **Archivo(s) Afectado(s)**: Database.cs
- **Ubicación exacta (línea/clase/método)**: Todo el archivo
- **Descripción**: No hay ninguna implementación de base de datos y los datos no se persisten.
- **Impacto Potencial en el Proyecto**: Alto.
- **Sugerencia de Resolución**: Implementar una base de datos.
### 16: 
- **Tipo**: Deuda Tecnica
- **Archivo(s) Afectado(s)**: Todo el proyecto
- **Ubicación exacta (línea/clase/método)**: Todo el proyecto 
- **Descripción**: No cuenta con ningun tipo de documentación o comentarios o explicaciones.
- **Impacto Potencial en el Proyecto**: Alto
- **Sugerencia de Resolución**: Crear documentación.
### 17: 
- **Tipo**: Deuda Tecnica
- **Archivo(s) Afectado(s)**: Todo el proyecto
- **Ubicación exacta (línea/clase/método)**: Todo el proyecto.
- **Descripción**: No cuenta con ningún tipo de arquitectura perceptible y es una gran bola de lodo.
- **Impacto Potencial en el Proyecto**: Alto
- **Sugerencia de Resolución**: Refactorizar e implementar alguna arquitectura que tenga sentido para la aplicación.
## Tecnicas de Refactoring recomendadas
Todas estas tecnicas de refactoring son sacadas de la página https://refactoring.guru/es/refactoring/techniques
- Extraer Método: Se mueve la implementación de cierta funcionalidad a otra función que solo habrá que invocar
- Reemplazar el Arreglo por objeto: En vez de tener un arreglo que guarde información, se va a tener un objeto con propiedades nombradas que guarde esa información.
- Consolidar expresiones condicionales: Cuando hay muchas operaciones operaciones condicionales que hacen casi que lo mismo y no hay una buena razon para que estén separadas (Muchos Ifs seguidos) se deben consolidar.
- Consolidar fragmentos de condiciones duplicados: Hay arboles de desición con codigo repetido que se pueden consolidar.
- Reemplazar Condiciones con Polimorfismo: Es mejor usar el polimorfismo cuando queremos que un objeto se comporte diferente dependiendo el caso para desacoplar el codigo.
- Extraer la Clase: Una clase solo deberia hacer exclusivamente el trabajo para el cual su nombre indica y usando la menor cantidad de lineas posibles. O si no se debe partir.