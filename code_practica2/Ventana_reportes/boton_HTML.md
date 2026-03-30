    
    try {
        // Busca el archivo HTML más reciente en la carpeta del proyecto
        java.io.File carpeta = new java.io.File(".");
        java.io.File[] archivos = carpeta.listFiles((dir, name) -> 
            name.startsWith("reporte_") && name.endsWith(".html"));
        
        if (archivos == null || archivos.length == 0) {
            JOptionPane.showMessageDialog(this, "No hay reportes generados aún.");
            return;
        }
        
        // Tomar el más reciente
        java.io.File masReciente = archivos[0];
        for (java.io.File f : archivos) {
            if (f.lastModified() > masReciente.lastModified()) {
                masReciente = f;
            }
        }
        
        // Abrirlo en el navegador
        java.awt.Desktop.getDesktop().browse(masReciente.toURI());
        
    } catch (Exception e) {
        JOptionPane.showMessageDialog(this, "Error al abrir el reporte: " + e.getMessage());
    }
