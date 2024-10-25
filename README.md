<p style="text-align: center; color: lightgray; font-size: 12px;">
    <strong>Programación Orientada a Objetos II</strong>
</p>

___

<h1 style="text-align: center;color:blue"><u>Trabajo Práctico 3</u></h1>
<h3 style="text-align: center;">Patrones de Diseño</h3>

###### Alumnos:
>Gigena, Maximo
>Eitner, Bianca Michelle
>Fernandez, Lautaro
>Lovera, Hernan

### Consignas
###### Objetivo: 
El objetivo de este trabajo es que apliquen los patrones de diseño Adapter, Composite y Template Method en situaciones de desarrollo de software. Deberán diseñar y programar soluciones que implementen estos patrones.
###### Instrucciones:
  1. El trabajo se realizará en grupo.
  2. Cada grupo debe desarrollar los tres ejercicios utilizando el lenguaje de programación Java.
  3. Cada ejercicio debe estar acompañado de un diagrama de clases y una breve explicación del por qué eligieron esa solución.
  4. Los programas deben ejecutarse correctamente y cumplir con las funcionalidades solicitadas.
  5. Se debe realizar la documentación de lo codificado.
  6. Se debe crear un repositorio, subir la resolución del tp al mismo y compartir el link en la tarea.

#### Ejercicio 1: Patrón Adapter
**Enunciado:**
Tienes una aplicación que permite a los usuarios gestionar sus listas de reproducción de
música. Actualmente, la aplicación utiliza una interfaz MusicPlayer para reproducir canciones,
pero ahora te piden integrar un servicio externo llamado ThirdPartyAudioPlayer que tiene una
interfaz diferente para reproducir pistas de audio.
**Tareas:**
  1. Implementa un adaptador que permita que ThirdPartyAudioPlayer funcione con la interfaz MusicPlayer existente.
  2. Crea una clase MusicApp que utilice tu adaptador para reproducir canciones desde ambos reproductores.

**Requisitos:**
  - La interfaz MusicPlayer debe tener un método playSong(String fileName).
  - La clase ThirdPartyAudioPlayer tiene un método startAudio(String file).
  - Usa el patrón Adapter para integrar ambos sistemas sin modificar la clase ThirdPartyAudioPlayer.

**Puntos clave a evaluar:**
  - Aplicación correcta del patrón Adapter.
  - Correcta implementación del adaptador para traducir las interfaces.
  - Diagrama de clases bien estructurado.

#### Ejercicio 2: Patrón Composite
**Enunciado:**
Tienes que diseñar un sistema de gestión de archivos y directorios, donde tanto los archivos como los directorios deben ser tratados de manera uniforme. Los directorios pueden contener tanto archivos como otros directorios.

**Tareas:**
  1. Crea una clase base abstracta FileSystemComponent con un método showDetails().
  2. Crea las clases File y Directory que hereden de FileSystemComponent. Los objetos de la clase Directory pueden contener tanto archivos como otros directorios.
  3. Implementa una función en la clase Directory para agregar y eliminar componentes (archivos o directorios).
  4. Implementa un cliente que permita crear una estructura jerárquica de directorios y archivos, y que muestre los detalles de esta estructura.

**Requisitos:**
-  La clase File debe tener un nombre y su tamaño en bytes.
- La clase Directory debe poder contener una lista de objetos FileSystemComponent.
- El método showDetails() debe imprimir el nombre del archivo o directorio, y en el caso de los directorios, debe listar su contenido de manera recursiva.

**Puntos clave a evaluar:**
- Correcta aplicación del patrón Composite.
- Implementación de la recursividad para mostrar los detalles de los directorios y sus
contenidos.
- Diagrama de clases que refleje la jerarquía de objetos compuestos.

#### Ejercicio 3: Patrón Template Method
**Enunciado:**
Debes desarrollar un sistema que gestione el proceso de fabricación de diferentes tipos de pasteles. El proceso general para hacer un pastel incluye: preparar los ingredientes, hornear, decorar y empaquetar. Sin embargo, los detalles de cada paso varían según el tipo de pastel (por ejemplo, pastel de chocolate, pastel de vainilla).

**Tareas:**
1. Crea una clase abstracta Cake que defina el método makeCake(), que incluye los pasos generales para hacer un pastel.
2. Define métodos abstractos para los pasos que varían entre los diferentes tipos de pasteles (por ejemplo, prepareIngredients(), decorateCake()).
3. Crea subclases como ChocolateCake y VanillaCake que implementen los detalles específicos de estos pasos.
4. Implementa un cliente que cree diferentes tipos de pasteles y los fabrique usando el método makeCake().

**Requisitos:**
- La clase Cake debe tener el método makeCake(), que no debe ser modificado por las subclases.
- Los pasos como prepareIngredients() y decorateCake() deben ser implementados en las subclases.
- El cliente debe ser capaz de crear tanto un pastel de chocolate como un pastel de vainilla y procesarlos utilizando el mismo flujo de fabricación.

**Puntos clave a evaluar:**
- Correcta aplicación del patrón Template Method.
- Implementación clara de las variaciones en los pasos del algoritmo entre los diferentes tipos de pasteles.
- Diagrama de clases que ilustre la estructura jerárquica y los métodos.

<h3 style="text-align: center;">Desarrollo</h3>

#### Ejercicio 1: Patrón Adapter
###### Diagrama de clases sistema de gestion de archivos y directorios
![DiagramaDeClases_Musica](https://i.imgur.com/htKIfaG.jpeg)


#### Ejercicio 2: Patrón Composite
###### Diagrama de clases sistema de gestion de archivos y directorios
![DiagramaDeClases_GestionArchivos](https://i.imgur.com/Fe4TNSG.png)

El patrón Composite permite que los objetos simples(en este escenario son los archivos) y los objetos compuestos(directorios que contienen otros archivos y directorios) se manejen de manera uniforme. En este caso, FileSystemComponent es una clase abstracta que define una interfaz para ambos, ya que archivos y directorios son componentes del sistema de gestión y es abstracta porque nunca se creará una instancia directa de FileSystemComponent solo de las subclases File y Directory.
La clase _*File*_ representa un archivo dentro del sistema de archivos. Un archivo es una "hoja" del patrón Composite porque no puede contener otros componentes (es un elemento simple); implementa el método showDetails(), que simplemente imprime el nombre y el tamaño del archivo, ya que no contiene otros componentes.

La clase _*Directory*_ representa un directorio dentro del sistema de archivos. Los directorios son componentes compuestos en el patrón Composite porque pueden contener otros componentes, ya sean archivos o directorios; implementa los métodos agregarComponent() y eliminarComponent(), que permiten agregar o eliminar archivos y directorios en la lista componentes. El método showDetails() en Directory muestra el nombre del directorio y luego recursivamente muestra los detalles de todos los componentes que contiene. Esta recursividad es clave para permitir que un directorio contenga otros directorios, que a su vez pueden contener otros archivos y directorios.
La clase Directory además contiene una lista de objetos de tipo FileSystemComponent, esta relación es de composición, lo que significa que un directorio está compuesto por múltiples archivos y otros directorios. La composición se utiliza porque un directorio puede tener un ciclo de vida independiente de los archivos y directorios que contiene, Si se destruyese un directorio, también deberían destruirse los archivos y directorios que contiene.

Tanto File como Directory heredan de FileSystemComponent, lo que refleja la naturaleza del patrón Composite, donde ambos (archivos y directorios) deben ser tratados de forma uniforme. Mediante la herencia, compartimos los atributos y el comportamiento común de ambos (el nombre y el método showDetails()).


### Ejercicio 3: Patrón Template Method
##### Diagrama de clases sistema de gestion de fabricacion de pasteles
![Sistema de preparación de Pasteles (DDC) vpd](https://github.com/user-attachments/assets/47c38e63-a147-49ee-a5a7-70e62ed32b50)

El patrón de diseño "Template Method" sirve para estructurar los procesos que se realizarán en el código de manera eficiente y reutilizable. En este ejemplo, la clase abstracta "Cake" define el flujo general a través del método "makeCake()", que organiza los pasos esenciales (preparar ingredientes, hornear, decorar y empaquetar). Las subclases "VanillaCake" y "ChocolateCake" heredan de "Cake" y proporcionan sus propias implementaciones para estos pasos específicos, garantizando que cada tipo de pastel siga el mismo proceso básico, pero con detalles personalizados. Este enfoque permite una alta reutilización de código, ya que el flujo general está centralizado en la clase Cake, y las subclases solo necesitan definir las particularidades de su tipo de pastel.
