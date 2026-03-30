#cargar datos
        try {
        String texto = txtDatos.getText(); 
        String[] numeros = texto.split(",");
        


        arr = new int[numeros.length];
        estados = new int[arr.length];

        for (int i = 0; i < numeros.length; i++) {
            arr[i] = Integer.parseInt(numeros[i].trim());
        }

        txtMostrar.append("Arreglo cargado correctamente\n");
        mostrarArreglo();
        mostrarGrafica();

    } catch (Exception e) {
        JOptionPane.showMessageDialog(this, "Error al cargar datos");
    }
    }                                        

    private void jButton2ActionPerformed(java.awt.event.ActionEvent evt) {                                         
        Random r = new Random();
    int n = r.nextInt(26) + 5; // entre 5 y 30

    arr = new int[n];
    estados = new int[arr.length];

    for (int i = 0; i < n; i++) {
        arr[i] = r.nextInt(100); // números de 0 a 99
    }

     txtMostrar.append("Arreglo aleatorio generado\n");
    mostrarArreglo();
    mostrarGrafica();

    
    #Aleatorio
      Random r = new Random();
    int n = r.nextInt(26) + 5; // entre 5 y 30

    arr = new int[n];
    estados = new int[arr.length];

    for (int i = 0; i < n; i++) {
        arr[i] = r.nextInt(100); // números de 0 a 99
    }

     txtMostrar.append("Arreglo aleatorio generado\n");
    mostrarArreglo();
    mostrarGrafica();
