private void generarReporteHTML(String algoritmo, String orden, String velocidad,
        int[] arrOriginal, int[] arrResultado, Estadisticas stats, long tiempoMs) {

    StringBuilder sb = new StringBuilder();

    // Convertir arreglos a string
    StringBuilder orig = new StringBuilder("[");
    for (int i = 0; i < arrOriginal.length; i++) {
        orig.append(arrOriginal[i]);
        if (i < arrOriginal.length - 1) orig.append(", ");
    }
    orig.append("]");

    StringBuilder result = new StringBuilder("[");
    for (int i = 0; i < arrResultado.length; i++) {
        result.append(arrResultado[i]);
        if (i < arrResultado.length - 1) result.append(", ");
    }
    result.append("]");

    sb.append("<!DOCTYPE html><html lang='es'><head>")
      .append("<meta charset='UTF-8'>")
      .append("<title>Reporte de Ordenamiento</title>")
      .append("<style>")
      .append("body { font-family: Arial, sans-serif; background: #0a1428; color: #fff; padding: 30px; }")
      .append("h1 { color: #00aaff; } h2 { color: #00ccff; border-bottom: 1px solid #00aaff; padding-bottom: 5px; }")
      .append(".card { background: #1a2a4a; border-radius: 8px; padding: 20px; margin: 15px 0; }")
      .append(".stat { display: inline-block; background: #0a3060; border-radius: 6px; padding: 10px 20px; margin: 5px; text-align: center; }")
      .append(".stat span { display: block; font-size: 2em; color: #00ff88; font-weight: bold; }")
      .append(".arreglo { background: #0d1f3c; padding: 10px; border-radius: 5px; font-family: monospace; word-break: break-all; }")
      .append("</style></head><body>")
      .append("<h1>📊 Reporte de Ordenamiento</h1>")
      .append("<div class='card'>")
      .append("<h2>Configuración</h2>")
      .append("<p><b>Algoritmo:</b> ").append(algoritmo).append("</p>")
      .append("<p><b>Orden:</b> ").append(orden).append("</p>")
      .append("<p><b>Velocidad:</b> ").append(velocidad).append("</p>")
      .append("<p><b>Tamaño del arreglo:</b> ").append(arrOriginal.length).append(" elementos</p>")
      .append("</div>")
      .append("<div class='card'>")
      .append("<h2>Arreglos</h2>")
      .append("<p><b>Original:</b></p><div class='arreglo'>").append(orig).append("</div>")
      .append("<p><b>Resultado:</b></p><div class='arreglo'>").append(result).append("</div>")
      .append("</div>")
      .append("<div class='card'>")
      .append("<h2>Estadísticas</h2>")
      .append("<div class='stat'><span>").append(stats.comparaciones).append("</span>Comparaciones</div>")
      .append("<div class='stat'><span>").append(stats.intercambios).append("</span>Intercambios</div>")
      .append("<div class='stat'><span>").append(stats.iteraciones).append("</span>Iteraciones</div>")
      .append("<div class='stat'><span>").append(tiempoMs).append(" ms</span>Tiempo</div>")
      .append("</div>")
      .append("</body></html>");

    // Guardar archivo
    try {
        String nombreArchivo = "reporte_" + algoritmo.replace(" ", "_") + "_" +
                               System.currentTimeMillis() + ".html";
        java.io.FileWriter fw = new java.io.FileWriter(nombreArchivo);
        fw.write(sb.toString());
        fw.close();

        SwingUtilities.invokeLater(() -> {
            txtMostrar.append("📄 Reporte generado: " + nombreArchivo + "\n");
        });
    } catch (Exception e) {
        e.printStackTrace();
    }
}



private void cargarDesdeArchivo() {
    javax.swing.JFileChooser chooser = new javax.swing.JFileChooser();
    chooser.setDialogTitle("Seleccionar archivo .txt");
    chooser.setFileFilter(new javax.swing.filechooser.FileNameExtensionFilter(
            "Archivos de texto (*.txt)", "txt"));

    int resultado = chooser.showOpenDialog(this);
    if (resultado == javax.swing.JFileChooser.APPROVE_OPTION) {
        try {
            java.io.File archivo = chooser.getSelectedFile();
            String contenido = new String(java.nio.file.Files.readAllBytes(archivo.toPath()));

            // Soporta separación por coma O por salto de línea
            contenido = contenido.replace("\n", ",").replace("\r", "");
            String[] numeros = contenido.split(",");

            arr = new int[numeros.length];
            estados = new int[arr.length];

            for (int i = 0; i < numeros.length; i++) {
                arr[i] = Integer.parseInt(numeros[i].trim());
            }

            txtMostrar.append("✅ Archivo cargado: " + archivo.getName() +
                              " (" + arr.length + " elementos)\n");
            mostrarArreglo();
            mostrarGrafica();

        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this,
                "El archivo contiene valores no numéricos.", "Error", JOptionPane.ERROR_MESSAGE);
        } catch (Exception e) {
            JOptionPane.showMessageDialog(this,
                "Error al leer el archivo: " + e.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }
    }
}
    
    
