private void cargarContenido() {
    String html = "<html><body style='font-family: Arial; padding: 15px; background:#fff;'>"

        + "<h1 style='color:#0066cc;'>📖 Ayuda - Visualizador de Algoritmos</h1>"

        + "<hr>"

        + "<h2 style='color:#0099aa;'>🎨 Colores de la visualización</h2>"
        + "<table border='1' cellpadding='6' cellspacing='0' width='100%'>"
        + "<tr style='background:#ddeeff;'><th>Color</th><th>Estado</th><th>Descripción</th></tr>"
        + "<tr><td style='background:#00aaff; color:white; text-align:center;'>Azul</td>"
        + "<td><b>Normal</b></td><td>El elemento está en reposo</td></tr>"
        + "<tr><td style='background:#ffdd00; text-align:center;'>Amarillo</td>"
        + "<td><b>Comparando</b></td><td>Par de elementos siendo evaluados</td></tr>"
        + "<tr><td style='background:#ff4444; color:white; text-align:center;'>Rojo</td>"
        + "<td><b>Intercambiando</b></td><td>Elementos siendo permutados</td></tr>"
        + "<tr><td style='background:#00cc66; color:white; text-align:center;'>Verde</td>"
        + "<td><b>Ordenado</b></td><td>Elemento en su posición final</td></tr>"
        + "</table>"

        + "<h2 style='color:#0099aa;'>⚙️ Cómo usar la aplicación</h2>"
        + "<ol>"
        + "<li><b>Cargar datos:</b> Escribe números separados por comas en el campo de texto "
        + "y presiona <b>Cargar</b>, o presiona <b>Aleatorio</b> para generar datos automáticamente. "
        + "También puedes cargar desde un archivo <b>.txt</b>.</li>"
        + "<li><b>Seleccionar algoritmo:</b> Elige entre Bubble Sort, Shell Sort o Quick Sort.</li>"
        + "<li><b>Seleccionar orden:</b> Ascendente (menor a mayor) o Descendente (mayor a menor).</li>"
        + "<li><b>Seleccionar velocidad:</b> Lento (500ms), Medio (100ms) o Rápido (20ms).</li>"
        + "<li><b>Iniciar:</b> Presiona el botón Iniciar para comenzar la visualización.</li>"
        + "<li><b>Reportes:</b> Al finalizar cada ejecución se genera automáticamente un archivo HTML "
        + "con el resumen. También puedes ver el historial de ejecuciones en la sección Reportes.</li>"
        + "</ol>"

        + "<h2 style='color:#0099aa;'>🔵 Bubble Sort</h2>"
        + "<p>Algoritmo iterativo que compara elementos adyacentes y los intercambia si están "
        + "en el orden incorrecto. Realiza múltiples pasadas reduciendo el rango en cada iteración "
        + "hasta que el arreglo queda ordenado.</p>"
        + "<p><b>Complejidad:</b> O(n²) en el peor caso.</p>"

        + "<h2 style='color:#0099aa;'>🟡 Shell Sort</h2>"
        + "<p>Mejora del Bubble Sort que compara elementos distantes entre sí usando un valor "
        + "llamado <b>gap</b>. El gap se va reduciendo hasta llegar a 1, momento en que el "
        + "arreglo queda ordenado.</p>"
        + "<p><b>Complejidad:</b> Depende de la secuencia de gaps, generalmente O(n log n).</p>"

        + "<h2 style='color:#0099aa;'>🔴 Quick Sort</h2>"
        + "<p>Algoritmo recursivo que selecciona un <b>pivote</b> (último elemento) y divide "
        + "el arreglo en dos particiones: elementos menores al pivote y elementos mayores. "
        + "Se llama a sí mismo sobre cada partición hasta ordenar todo el arreglo.</p>"
        + "<p><b>Complejidad:</b> O(n log n) promedio, O(n²) peor caso.</p>"

        + "<hr>"
        + "<p style='color:#888; font-size:11px; text-align:center;'>"
        + "Visualizador de Algoritmos de Ordenamiento — IPC1 — USAC 2026</p>"

        + "</body></html>";

    txtAyuda.setContentType("text/html");
    txtAyuda.setText(html);
    txtAyuda.setEditable(false);
    txtAyuda.setCaretPosition(0); // para que inicie arriba
}
