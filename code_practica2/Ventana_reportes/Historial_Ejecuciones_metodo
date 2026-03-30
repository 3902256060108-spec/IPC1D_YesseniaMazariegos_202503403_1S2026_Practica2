package algoritmos_ordenamientos;

import java.util.ArrayList;

public class HistorialEjecuciones {
    
    // Lista estática para que sea compartida entre todas las ventanas
    public static ArrayList<String[]> historial = new ArrayList<>();
    
    public static void agregar(String algoritmo, String orden, int n,
                                int comparaciones, int intercambios,
                                int iteraciones, long tiempoMs) {
        String[] fila = {
            String.valueOf(historial.size() + 1), // #
            algoritmo,
            orden,
            String.valueOf(n),
            String.valueOf(comparaciones),
            String.valueOf(intercambios),
            String.valueOf(iteraciones),
            tiempoMs + " ms"
        };
        historial.add(fila);
    }
}
