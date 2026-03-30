private void cargarTabla() {
    // Obtener el modelo de la tabla
    javax.swing.table.DefaultTableModel modelo = 
        (javax.swing.table.DefaultTableModel) tablao.getModel();
    
    // Limpiar filas actuales
    modelo.setRowCount(0);
    
    // Agregar cada ejecución del historial
    for (String[] fila : HistorialEjecuciones.historial) {
        modelo.addRow(fila);
    }
}
