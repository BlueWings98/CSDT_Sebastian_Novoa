# Registro de Code Smells y Deudas T�cnicas

Este documento sirve como un registro de los code smells (malos olores en el c�digo) y deudas t�cnicas identificados en el proyecto de C#. La finalidad es llevar un seguimiento de estos problemas para priorizar su refactoring (refactorizaci�n) o resoluci�n en futuras iteraciones.

## Plantilla para el Registro

Para a�adir un nuevo code smell o deuda t�cnica, copia y pega la siguiente plantilla en la secci�n correspondiente de este documento.

### 1: 
- **Tipo**: Deuda T�cnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: Todo
- **Descripci�n**: Clase di�s, es una clase que tiene 214 lineas de c�digo y se encarga en hacer la gran mayoria de l�gica del programa. Debe partirse en clases mas peque�as.
- **Impacto Potencial en el Proyecto**: Mediano
- **Sugerencia de Resoluci�n**: Crear sub-clases que se encarguen de los comportamientos del juego y dejar esta como solo la entidad con sus propiedades base.
### 2: 
- **Tipo**: Deuda T�cnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: Linea 19
- **Descripci�n**: Las preguntas de los diferentes temas (Pop, ciencia, etc) son su propio arreglo con nombre propio lo cual lo hace poco escalable de poner mas preguntas de temas.
- **Impacto Potencial en el Proyecto**: Alto, porque de poner temas nuevos hay que crear l�gica especializada para cada uno lo cual es innecesario.
- **Sugerencia de Resoluci�n**: Crear un arreglo de LinkedList de tipo string llamado Questions.
### 3: 
- **Tipo**: Deuda T�cnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: Linea 14, 15 y 17
- **Descripci�n**: Tanto places como purces y penaltybox debe ser su propia entidad y objeto, asi como se est� manejando las propiedades con arreglos int[6] es poco legible y escalable.
- **Impacto Potencial en el Proyecto**: Alto
- **Sugerencia de Resoluci�n**: Crear entidades con propiedades muy legibles en vez de arreglos y ponerlos en su propia carpeta.
### 4: 
- **Tipo**: Deuda T�cnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: Constructor, line 27.
- **Descripci�n**: Todo el constructor est� mal hecho. Est� quemada en la l�gica que va a recibir hasta 50 preguntas de cada categoria y estos datos se est�n cargando directamente en el constructor en vez de un metodo dedicado. 
- **Impacto Potencial en el Proyecto**: Medio
- **Sugerencia de Resoluci�n**: Reconstrucci�n completa del constructor donde pueda recibir parametros con los datos necesarios y delegar la carga de datos la cual no debe inluir codigo quemado y cargar cualquier categoria mediante referencia. Tambien se debe crear el objeto de categoria.
### 5: 
- **Tipo**: Code Smell
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: createRockQuestion(), hoyManyPlayers()
- **Descripci�n**: Este metodo no deberia existir y sobra.
- **Impacto Potencial en el Proyecto**: Poco
- **Sugerencia de Resoluci�n**:  Se deberia eliminar y su l�gica transferirse a un metodo de creacion gen�rico.
### 6: 
- **Tipo**: Code Smell
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: isPlayable
- **Descripci�n**: Metodo que no se referencia.
- **Impacto Potencial en el Proyecto**: Bajo
- **Sugerencia de Resoluci�n**: Eliminar el metodo.
### 7: 
- **Tipo**: Code Smell
- **Archivo(s) Afectado(s)**: Todo el proyecto
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: Todo el proyecto
- **Descripci�n**: Los IDE cuentan con herramientas de formateo de c�digo las cuales formatean y quitan importaciones no usadas para dejar el proyecto mucho mas limpio. Hay que usarlo pues el espaciado d� mucho donde mejorar.
- **Impacto Potencial en el Proyecto**: Medio
- **Sugerencia de Resoluci�n**: Correr las herramientas de limpieza de c�digo dentro del IDE (En este caso Visual Studio 2022).
### 8: 
- **Tipo**: Code Smell
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**:  add()
- **Descripci�n**: Dejaron en el c�digo logs de debugging, esos se deberian eliminar.
- **Impacto Potencial en el Proyecto**: Bajo
- **Sugerencia de Resoluci�n**: Eliminar todos los console.writeline pues solo se deber�an usar para debugging y nunca tocar la rama de master.
### 9: 
- **Tipo**: Code Smell
- **Archivo(s) Afectado(s)**: Todo el proyecto
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: Todos los metodos.
- **Descripci�n**: La nomenclatura recomendada recomienda que la primera letra de cada uno de los m�todos comenze con mayuscula y no use palabras reservadas como add. roll() -> Roll().
- **Impacto Potencial en el Proyecto**: Bajo
- **Sugerencia de Resoluci�n**: Usar la nomenclatura sugerida.
### 10: 
- **Tipo**: Deuda T�cnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: roll();
- **Descripci�n**: Usar un patr�n de administraci�n de estado del juego para remover la necesidad de informarle al jugador quel estado mediante console.writelines en la misma l�gica lo cual la infla y hace menos legible.
- **Impacto Potencial en el Proyecto**: Alto
- **Sugerencia de Resoluci�n**: Usar un patr�n que lleve el estado del juego mediante referencia y que sea esa clase dedicada la unica que informe al jugador del estado. 
### 11: 
- **Tipo**: Deuda T�cnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: askQUestion(); currentCategory();
- **Descripci�n**: Nunca se deberian usar IFs de manera simultanea para hacer comparaciones tan repetitivas.
- **Impacto Potencial en el Proyecto**: Medio
- **Sugerencia de Resoluci�n**: Usar el Switch Case o usar un m�todo que valore una categoria gen�rica.
### 12: 
- **Tipo**: Deuda T�cnica
- **Archivo(s) Afectado(s)**: Game.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: linea 179
- **Descripci�n**: Typo
- **Impacto Potencial en el Proyecto**: Bajo
- **Sugerencia de Resoluci�n**: Verificar y corregir los typos.
### 13: 
- **Tipo**: Deuda T�cnica
- **Archivo(s) Afectado(s)**: GameRunner.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: Todo el archivo
- **Descripci�n**: El m�todo Main encontrado en este archivo no deberia tener l�gica de negocio y mucho menos valores quemados.
- **Impacto Potencial en el Proyecto**: Alto
- **Sugerencia de Resoluci�n**: Usar un framework como .net que se encargue en administrar la aplicaci�n y especialmente el m�todo main. Despues de instalarlo hay que mover esa l�gica a otro lado.
### 14: 
- **Tipo**: Deuda T�cnica
- **Archivo(s) Afectado(s)**: OrderService.cs, UserService.cs, InvoiceService.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: Todo el archivo
- **Descripci�n**: Este archivo no es referenciado en ning�n otro m�todo y es basura o es failmente reemplazable.
- **Impacto Potencial en el Proyecto**: Bajo
- **Sugerencia de Resoluci�n**: Eliminar el archivo.
### 15: 
- **Tipo**: Deuda T�cnica
- **Archivo(s) Afectado(s)**: Database.cs
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: Todo el archivo
- **Descripci�n**: No hay ninguna implementaci�n de base de datos y los datos no se persisten.
- **Impacto Potencial en el Proyecto**: Alto.
- **Sugerencia de Resoluci�n**: Implementar una base de datos.
### 16: 
- **Tipo**: Deuda Tecnica
- **Archivo(s) Afectado(s)**: Todo el proyecto
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: Todo el proyecto 
- **Descripci�n**: No cuenta con ningun tipo de documentaci�n o comentarios o explicaciones.
- **Impacto Potencial en el Proyecto**: Alto
- **Sugerencia de Resoluci�n**: Crear documentaci�n.
### 17: 
- **Tipo**: Deuda Tecnica
- **Archivo(s) Afectado(s)**: Todo el proyecto
- **Ubicaci�n exacta (l�nea/clase/m�todo)**: Todo el proyecto.
- **Descripci�n**: No cuenta con ning�n tipo de arquitectura perceptible y es una gran bola de lodo.
- **Impacto Potencial en el Proyecto**: Alto
- **Sugerencia de Resoluci�n**: Refactorizar e implementar alguna arquitectura que tenga sentido para la aplicaci�n.
## Tecnicas de Refactoring recomendadas
Todas estas tecnicas de refactoring son sacadas de la p�gina https://refactoring.guru/es/refactoring/techniques
- Extraer M�todo: Se mueve la implementaci�n de cierta funcionalidad a otra funci�n que solo habr� que invocar
- Reemplazar el Arreglo por objeto: En vez de tener un arreglo que guarde informaci�n, se va a tener un objeto con propiedades nombradas que guarde esa informaci�n.
- Consolidar expresiones condicionales: Cuando hay muchas operaciones operaciones condicionales que hacen casi que lo mismo y no hay una buena razon para que est�n separadas (Muchos Ifs seguidos) se deben consolidar.
- Consolidar fragmentos de condiciones duplicados: Hay arboles de desici�n con codigo repetido que se pueden consolidar.
- Reemplazar Condiciones con Polimorfismo: Es mejor usar el polimorfismo cuando queremos que un objeto se comporte diferente dependiendo el caso para desacoplar el codigo.
- Extraer la Clase: Una clase solo deberia hacer exclusivamente el trabajo para el cual su nombre indica y usando la menor cantidad de lineas posibles. O si no se debe partir.