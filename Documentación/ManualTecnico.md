# Manual Técnico
## Visualizador de Algoritmos de Ordenamiento

**Curso:** Introducción a la Programación y Computación 1  
**Universidad:** San Carlos de Guatemala — Facultad de Ingeniería  
**Estudiante:** Yessenia Crystabel Mazariegos Carranza  
**Carnet:** 202503403  
**Práctica:** 2 — Visualizador de Algoritmos de Ordenamiento  
**Semestre:** 1S 2026  

---

## 1. Descripción general

Algoritmos_Ordenamientos es una aplicación de escritorio desarrollada en Java con interfaz gráfica Swing/AWT. Permite visualizar en tiempo real el funcionamiento de tres algoritmos de ordenamiento clásicos (Bubble Sort, Shell Sort y Quick Sort), mostrando mediante una gráfica de barras animada cómo los elementos del arreglo se comparan, intercambian y ordenan paso a paso.

---

## 2. Estructura del proyecto

```
algoritmos_ordenamientos/
│
├── MENU_PRINCIPAL.java       # Pantalla inicial de navegación
├── Algoritmos_ordenamientos.java  # Ventana principal del visualizador
├── reportes.java             # Pantalla de historial y reportes
├── Ayuda.java                # Pantalla de ayuda e información
│
├── Ordenamientos.java        # Lógica de los tres algoritmos de ordenamiento
├── Estadisticas.java         # Clase de datos para contadores
├── HistorialEjecuciones.java # Clase estática para historial de sesión
```

---

## 3. Clases y responsabilidades

### 3.1 `MENU_PRINCIPAL`
Pantalla inicial que se muestra al iniciar la aplicación. Contiene botones de navegación hacia el visualizador, la pantalla de reportes, la ayuda y la opción de salir.

### 3.2 `Algoritmos_ordenamientos` (ventana principal)
Contiene el panel de control, la visualización con JFreeChart, el log de operaciones y las estadísticas. Los métodos principales son:

| Método | Descripción |
|---|---|
| `mostrarGrafica()` | Genera y actualiza la gráfica de barras con JFreeChart |
| `actualizarGrafica()` | Llama a `mostrarGrafica()` desde el hilo de UI con `SwingUtilities.invokeLater` |
| `generarReporteHTML(...)` | Genera un archivo HTML con el resumen de la ejecución |
| `cargarDesdeArchivo()` | Permite cargar datos desde un archivo `.txt` usando `JFileChooser` |
| `mostrarArreglo()` | Muestra el arreglo actual en el log de operaciones |

### 3.3 `Ordenamientos`
Clase estática con los tres algoritmos de ordenamiento. Cada método recibe el arreglo, el arreglo de estados visuales, la dirección del orden, la velocidad y referencias a los componentes de la UI para actualizarlos en tiempo real.

| Método | Tipo | Descripción |
|---|---|---|
| `bubbleSort(...)` | Iterativo | Compara pares adyacentes y los intercambia si están fuera de orden |
| `shellSort(...)` | Iterativo | Ordena por gaps decrecientes |
| `quickSort(...)` | Recursivo | Divide el arreglo en particiones alrededor de un pivote |
| `partition(...)` | Auxiliar | Selecciona el pivote y reordena para Quick Sort |
| `dormir(String)` | Auxiliar | Controla la velocidad con `Thread.sleep()` |

### 3.4 `Estadisticas`
Clase simple con tres atributos públicos enteros: `comparaciones`, `intercambios` e `iteraciones`. Se instancia nueva en cada ejecución para reiniciar los contadores.

```java
public class Estadisticas {
    public int comparaciones;
    public int intercambios;
    public int iteraciones;
}
```

### 3.5 `HistorialEjecuciones`
Clase con una lista estática `ArrayList<String[]>` que persiste durante toda la sesión y acumula una fila por cada ejecución completada.

### 3.6 `reportes`
Muestra la tabla de historial de ejecuciones de la sesión y permite abrir el último reporte HTML generado en el navegador.

### 3.7 `Ayuda`
Muestra información sobre el uso de la aplicación, significado de los colores y descripción de cada algoritmo, usando un `JEditorPane` con contenido HTML.

---

## 4. Librerías utilizadas

| Librería | Versión | Uso |
|---|---|---|
| Java SE (JDK) | 11 o superior | Lenguaje base, Swing/AWT, hilos |
| JFreeChart | 1.5.x | Generación de gráfica de barras animada |

---

## 5. Concurrencia

Los algoritmos se ejecutan en un hilo separado (`new Thread(...).start()`) para no bloquear la interfaz gráfica. Todas las actualizaciones visuales (gráfica, labels, log) se realizan mediante `SwingUtilities.invokeLater()` para garantizar que ocurran en el Event Dispatch Thread (EDT).

```java
new Thread(() -> {
    // ejecución del algoritmo
    SwingUtilities.invokeLater(() -> {
        // actualización de la UI
    });
}).start();
```

---

## 6. Estados visuales de las barras

Los colores de las barras en la gráfica se controlan mediante el arreglo `estados[]` que se actualiza en cada paso del algoritmo:

| Valor | Color | Estado |
|---|---|---|
| 0 | Azul claro | Normal / reposo |
| 1 | Amarillo | Siendo comparado |
| 2 | Rojo | Siendo intercambiado |
| 3 | Verde | Ordenado en posición final |

---

## 7. Generación de reportes

Al finalizar cada ejecución se genera automáticamente un archivo `.html` en la carpeta raíz del proyecto con el nombre:

```
reporte_[Algoritmo]_[timestamp].html
```

El archivo incluye: algoritmo, orden, velocidad, arreglo original, arreglo resultado, estadísticas y tiempo de ejecución.

---

## 8. Requisitos del sistema

- Java JDK 11 o superior
- NetBeans IDE (recomendado) o IntelliJ IDEA
- Librería JFreeChart agregada al classpath del proyecto

---

## 9. Instrucciones de compilación

1. Abrir el proyecto en NetBeans
2. Verificar que JFreeChart esté en las librerías del proyecto (click derecho en proyecto → Properties → Libraries)
3. Ejecutar con `Run Project` (F6) o `Clean and Build` (Shift+F11) seguido de Run
