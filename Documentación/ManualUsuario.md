# Manual de Usuario
## Visualizador de Algoritmos de Ordenamiento

**Curso:** Introducción a la Programación y Computación 1  
**Universidad:** San Carlos de Guatemala — Facultad de Ingeniería  
**Estudiante:** Yessenia Crystabel Mazariegos Carranza  
**Carnet:** 202503403  
**Práctica:** 2 — Visualizador de Algoritmos de Ordenamiento  
**Semestre:** 1S 2026  

---

## 1. Introducción

Algoritmos_Ordenamientos es una aplicación educativa que permite visualizar cómo funcionan los algoritmos de ordenamiento Bubble Sort, Shell Sort y Quick Sort. Podrás ver en tiempo real cómo los elementos de un arreglo se comparan e intercambian hasta quedar ordenados, con colores que indican el estado de cada barra en la gráfica.

---

## 2. Requisitos previos

- Tener instalado Java JDK 11 o superior
- Tener la librería JFreeChart en el proyecto
- Ejecutar desde NetBeans o como archivo `.jar`

---

## 3. Pantalla principal — Menú

Al iniciar la aplicación verás el menú principal con cuatro opciones:

| Botón | Acción |
|---|---|
| Algoritmos de ordenamiento | Abre el visualizador principal |
| Reportes | Abre el historial de ejecuciones |
| Ayuda | Muestra información y guía de uso |
| Salir | Cierra la aplicación |

Haz click en **Algoritmos de ordenamiento** para comenzar.

---

## 4. Panel de control

### 4.1 Cargar datos

Tienes dos formas de ingresar los números a ordenar:

**Opción A — Escribir manualmente:**
1. Escribe los números separados por comas en el campo de texto  
   Ejemplo: `33, 12, 54, 7, 89, 21`
2. Haz click en **Cargar**

**Opción B — Desde archivo .txt:**
1. Haz click en **Cargar**
2. Selecciona la opción "Cargar archivo .txt"
3. Busca y selecciona tu archivo (los números deben estar separados por comas o saltos de línea)

**Opción C — Aleatorio:**
1. Haz click en **Aleatorio** para generar automáticamente entre 5 y 30 números aleatorios

---

### 4.2 Seleccionar algoritmo

Usa el selector **Algoritmo** para elegir uno de los tres disponibles:

- **Bubble Sort** — compara elementos adyacentes y los intercambia si están fuera de lugar
- **Shell Sort** — ordena por grupos de elementos distantes entre sí
- **Quick Sort** — selecciona un pivote y divide el arreglo en dos partes

---

### 4.3 Seleccionar orden

Usa el selector **Orden** para elegir la dirección del ordenamiento:

- **ascendente** — de menor a mayor (ej: 1, 5, 12, 30)
- **descendente** — de mayor a menor (ej: 30, 12, 5, 1)

---

### 4.4 Seleccionar velocidad

Usa el selector **Velocidad** para controlar qué tan rápido se visualiza el proceso:

| Opción | Tiempo por paso |
|---|---|
| lento | 500 ms |
| medio | 100 ms |
| rápido | 20 ms |

---

### 4.5 Iniciar el ordenamiento

Una vez configurado todo, haz click en **Iniciar**. Verás cómo la gráfica se anima mostrando el proceso paso a paso.

Para reiniciar con los mismos datos haz click en **Recargar** (si lo tienes), o carga nuevos datos y presiona Iniciar nuevamente.

---

## 5. Visualización — Gráfica de barras

La gráfica muestra el estado actual del arreglo. Cada barra representa un elemento y su color indica lo que está ocurriendo:

| Color | Significado |
|---|---|
| 🔵 Azul | El elemento está en reposo (estado normal) |
| 🟡 Amarillo | El elemento está siendo comparado |
| 🔴 Rojo | El elemento está siendo intercambiado |
| 🟢 Verde | El elemento ya está en su posición final |

Los números sobre cada barra muestran el valor del elemento.

---

## 6. Estadísticas en tiempo real

Durante la ejecución, verás tres contadores que se actualizan automáticamente:

- **Comparaciones** — número de veces que se compararon dos elementos
- **Intercambios** — número de veces que dos elementos cambiaron de posición
- **Iteraciones** — número de pasadas o llamadas recursivas completadas

Estos contadores se reinician a cero cada vez que inicias una nueva ejecución.

---

## 7. Log de operaciones

El área de texto muestra cada paso del algoritmo en tiempo real, con el formato:

```
[Paso N] Comparando arr[i]=X con arr[j]=Y → intercambio realizado
[Paso N] Comparando arr[i]=X con arr[j]=Y
Ordenamiento completado en 1340 ms
```

Al finalizar aparece el tiempo total de ejecución en milisegundos.

---

## 8. Reportes

### 8.1 Reporte HTML automático

Al terminar cada ejecución, la aplicación genera automáticamente un archivo HTML en la carpeta del proyecto con el nombre:

```
reporte_Bubble_Sort_1743289234567.html
```

Este archivo contiene el resumen completo: algoritmo, orden, arreglos original y resultado, estadísticas y tiempo.

### 8.2 Historial de sesión

Haz click en **Reportes** desde el menú principal para ver la tabla con todas las ejecuciones realizadas durante la sesión actual. Las columnas son:

`#` · `Algoritmo` · `Orden` · `N` · `Comparaciones` · `Intercambios` · `Iteraciones` · `Tiempo`

Desde esta pantalla también puedes hacer click en **HTML** para abrir el último reporte generado en tu navegador.

> El historial se pierde al cerrar la aplicación.

---

## 9. Ayuda

Haz click en **Ayuda** desde el menú principal para ver una guía completa con la descripción de cada algoritmo, el significado de los colores y las instrucciones de uso.

---

## 10. Ejemplo de uso paso a paso

1. Abre la aplicación → aparece el menú principal
2. Click en **Algoritmos de ordenamiento**
3. Escribe `45, 12, 78, 3, 56` en el campo de texto
4. Click en **Cargar**
5. Selecciona **Bubble Sort**, orden **ascendente**, velocidad **lento**
6. Click en **Iniciar**
7. Observa cómo las barras cambian de color mientras se ordenan
8. Al terminar, revisa las estadísticas y el log
9. Abre la carpeta del proyecto y verás el archivo HTML generado

---

## 11. Solución de problemas comunes

| Problema | Solución |
|---|---|
| No carga datos | Verifica que los números estén separados por comas y sin letras |
| El archivo .txt no carga | Asegúrate que los números estén separados por comas o saltos de línea |
| La gráfica no aparece | Verifica que JFreeChart esté en las librerías del proyecto |
| La animación es muy lenta | Cambia la velocidad a "medio" o "rápido" |
| No se genera el HTML | Verifica que la aplicación tenga permisos de escritura en la carpeta del proyecto |
