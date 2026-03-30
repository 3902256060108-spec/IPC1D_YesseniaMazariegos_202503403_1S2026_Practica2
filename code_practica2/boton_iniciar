
        if (arr == null) {
    JOptionPane.showMessageDialog(this, "Primero carga datos");
    return;
}

String algoritmo = comboAlgoritmo.getSelectedItem().toString();
String orden = comboOrden.getSelectedItem().toString();
String velocidad = comboVelocidad.getSelectedItem().toString();
txtMostrar.setText("");

// Guardar arreglo original antes de ordenar
int[] arrOriginal = arr.clone();

Estadisticas stats = new Estadisticas();
long inicio = System.currentTimeMillis();

new Thread(() -> {
    txtMostrar.append("Iniciando " + algoritmo + " (" + orden + ")\n\n");

    switch (algoritmo) {
        case "Bubble Sort":
            Ordenamientos.bubbleSort(arr, estados, orden, velocidad,
                () -> actualizarGrafica(), txtMostrar, stats,
                lblComparaciones, lblIntercambios, lblIteraciones);
            break;
        case "Shell Sort":
            Ordenamientos.shellSort(arr, estados, orden, velocidad,
                () -> actualizarGrafica(), txtMostrar, stats,
                lblComparaciones, lblIntercambios, lblIteraciones);
            break;
        case "Quick Sort":
            Ordenamientos.quickSort(arr, estados, 0, arr.length - 1,
                orden, velocidad, () -> actualizarGrafica(), txtMostrar, stats,
                lblComparaciones, lblIntercambios, lblIteraciones);
            break;
    }

    for (int i = 0; i < estados.length; i++) estados[i] = 3;
    actualizarGrafica();

    long fin = System.currentTimeMillis();
    long tiempoTotal = fin - inicio;

    // ✅ Log final con tiempo — formato del PDF
    txtMostrar.append("\nOrdenamiento completado en " + tiempoTotal + " ms\n");

    SwingUtilities.invokeLater(() -> {
        lblComparaciones.setText("Comparaciones: " + stats.comparaciones);
        lblIntercambios.setText("Intercambios: " + stats.intercambios);
        lblIteraciones.setText("Iteraciones: " + stats.iteraciones);
    });

    // ✅ Generar reporte HTML automáticamente
    generarReporteHTML(algoritmo, orden, velocidad, arrOriginal, arr,
                       stats, tiempoTotal);
    
    HistorialEjecuciones.agregar(algoritmo, orden, arrOriginal.length,
        stats.comparaciones, stats.intercambios,
        stats.iteraciones, tiempoTotal);

}).start();
