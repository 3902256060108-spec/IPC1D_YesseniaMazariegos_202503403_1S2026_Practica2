#Ordenamientos
package algoritmos_ordenamientos;

import javax.swing.JLabel;
import javax.swing.JTextArea;
import javax.swing.SwingUtilities;

public class Ordenamientos {

##BUBBLESORT
    
    public static void bubbleSort(int[] arr, int[] estados, String orden, String velocidad,
        Runnable callback, JTextArea log, Estadisticas stats,
        JLabel lblComparaciones, JLabel lblIntercambios, JLabel lblIteraciones) {

        int n = arr.length;
        int paso = 1;
        int numPaso = 0;

        for (int i = 0; i < n - 1; i++) {
            log.append("--- Iteración " + paso + " ---\n");

            for (int j = 0; j < n - i - 1; j++) {

                estados[j] = 1;
                estados[j + 1] = 1;
                stats.comparaciones++;
                actualizarLabels(lblComparaciones, lblIntercambios, lblIteraciones, stats);

                numPaso++;
                boolean condicion = orden.equalsIgnoreCase("ascendente") ?
                        arr[j] > arr[j + 1] :
                        arr[j] < arr[j + 1];

                if (condicion) {
                    
                    int valA = arr[j];
                    int valB = arr[j + 1];

                    estados[j] = 2;
                    estados[j + 1] = 2;

                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;

                    stats.intercambios++;
                    actualizarLabels(lblComparaciones, lblIntercambios, lblIteraciones, stats);

                    
                    log.append("[Paso " + numPaso + "] Comparando arr[" + j + "]=" + valA +
                               " con arr[" + (j+1) + "]=" + valB + " → intercambio realizado\n");

                    callback.run();
                    dormir(velocidad);

                    estados[j] = 0;
                    estados[j + 1] = 0;
                } else {
                    
                    log.append("[Paso " + numPaso + "] Comparando arr[" + j + "]=" + arr[j] +
                               " con arr[" + (j+1) + "]=" + arr[j+1] + "\n");
                }

                estados[j] = 0;
                estados[j + 1] = 0;
                callback.run();
                dormir(velocidad);
            }

            estados[n - i - 1] = 3;
            stats.iteraciones++;
            actualizarLabels(lblComparaciones, lblIntercambios, lblIteraciones, stats);
            paso++;
        }

        for (int i = 0; i < arr.length; i++) {
            estados[i] = 3;
        }
        callback.run();
        log.append("\nOrdenamiento finalizado\n");
    }

##SHELLSORT
    public static void shellSort(int[] arr, int[] estados, String orden, String velocidad,
            Runnable callback, JTextArea log, Estadisticas stats,
            JLabel lblComparaciones, JLabel lblIntercambios, JLabel lblIteraciones) {

        int n = arr.length;
        int paso = 1;
        int numPaso = 0;

        for (int gap = n / 2; gap > 0; gap /= 2) {
            log.append("--- Iteración " + paso + " (gap=" + gap + ") ---\n");

            for (int i = gap; i < n; i++) {
                int temp = arr[i];
                int j = i;

                while (j >= gap) {
                    estados[j] = 1;
                    estados[j - gap] = 1;
                    callback.run();
                    dormir(velocidad);

                    stats.comparaciones++;
                    numPaso++;
                    actualizarLabels(lblComparaciones, lblIntercambios, lblIteraciones, stats);

                    boolean condicion = orden.equalsIgnoreCase("ascendente") ?
                            arr[j - gap] > temp :
                            arr[j - gap] < temp;

                    if (!condicion) {
                        log.append("[Paso " + numPaso + "] Comparando arr[" + (j-gap) + "]=" + arr[j-gap] +
                                   " con arr[" + j + "]=" + temp + "\n");
                        estados[j] = 0;
                        estados[j - gap] = 0;
                        break;
                    }

                    log.append("[Paso " + numPaso + "] Comparando arr[" + (j-gap) + "]=" + arr[j-gap] +
                               " con arr[" + j + "]=" + temp + " → moviendo\n");

                    estados[j] = 2;
                    estados[j - gap] = 2;
                    callback.run();
                    dormir(velocidad);

                    arr[j] = arr[j - gap];

                    estados[j] = 0;
                    estados[j - gap] = 0;

                    j -= gap;
                    stats.intercambios++;
                    actualizarLabels(lblComparaciones, lblIntercambios, lblIteraciones, stats);
                }

                arr[j] = temp;
                callback.run();
                dormir(velocidad);
            }

            stats.iteraciones++;
            actualizarLabels(lblComparaciones, lblIntercambios, lblIteraciones, stats);
            paso++;
        }

        for (int i = 0; i < arr.length; i++) {
            estados[i] = 3;
        }
        callback.run();
        log.append("\nOrdenamiento finalizado\n");
    }

##QUICKSORT
    public static void quickSort(int[] arr, int[] estados, int low, int high,
            String orden, String velocidad, Runnable callback,
            JTextArea log, Estadisticas stats,
            JLabel lblComparaciones, JLabel lblIntercambios, JLabel lblIteraciones) {

        if (low < high) {
            stats.iteraciones++;
            log.append("--- Partición [" + low + ", " + high + "] ---\n");

            int pi = partition(arr, estados, low, high, orden, velocidad,
                    callback, log, stats,
                    lblComparaciones, lblIntercambios, lblIteraciones);

            actualizarLabels(lblComparaciones, lblIntercambios, lblIteraciones, stats);

            quickSort(arr, estados, low, pi - 1, orden, velocidad,
                    callback, log, stats,
                    lblComparaciones, lblIntercambios, lblIteraciones);

            quickSort(arr, estados, pi + 1, high, orden, velocidad,
                    callback, log, stats,
                    lblComparaciones, lblIntercambios, lblIteraciones);
        }

        if (low == high) {
            estados[low] = 3;
            callback.run();
        }
    }

    private static int partition(int[] arr, int[] estados, int low, int high,
            String orden, String velocidad, Runnable callback,
            JTextArea log, Estadisticas stats,
            JLabel lblComparaciones, JLabel lblIntercambios, JLabel lblIteraciones) {

        int pivote = arr[high];
        int i = low - 1;
        int numPaso = stats.comparaciones;

        log.append("Pivote seleccionado: arr[" + high + "]=" + pivote + "\n");

        estados[high] = 1;
        callback.run();
        dormir(velocidad);

        for (int j = low; j < high; j++) {
            estados[j] = 1;
            callback.run();
            dormir(velocidad);

            stats.comparaciones++;
            numPaso++;
            actualizarLabels(lblComparaciones, lblIntercambios, lblIteraciones, stats);

            boolean condicion = orden.equalsIgnoreCase("ascendente") ?
                    arr[j] < pivote :
                    arr[j] > pivote;

            if (condicion) {
                i++;
                int valA = arr[i];
                int valB = arr[j];

                estados[j] = 2;
                estados[i] = 2;
                callback.run();
                dormir(velocidad);

                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;

                log.append("[Paso " + numPaso + "] Comparando arr[" + j + "]=" + valB +
                           " con pivote=" + pivote + " → intercambio realizado\n");

                stats.intercambios++;
                actualizarLabels(lblComparaciones, lblIntercambios, lblIteraciones, stats);
            } else {
                log.append("[Paso " + numPaso + "] Comparando arr[" + j + "]=" + arr[j] +
                           " con pivote=" + pivote + "\n");
            }

            if (estados[j] != 3) estados[j] = 0;
            if (i >= low && estados[i] != 3) estados[i] = 0;
        }

        log.append("Colocando pivote " + pivote + " en posición final [" + (i+1) + "]\n");

        estados[i + 1] = 2;
        estados[high] = 2;
        callback.run();
        dormir(velocidad);

        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;

        stats.intercambios++;
        estados[high] = 0;
        estados[i + 1] = 3;

        callback.run();
        dormir(velocidad);
        actualizarLabels(lblComparaciones, lblIntercambios, lblIteraciones, stats);

        return i + 1;
    }

    
    public static void dormir(String velocidad) {
        try {
            if (velocidad.equalsIgnoreCase("lento")) Thread.sleep(500);
            else if (velocidad.equalsIgnoreCase("medio")) Thread.sleep(100);
            else Thread.sleep(20);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }

    
    private static void actualizarLabels(JLabel lblComp, JLabel lblInt, JLabel lblIter, Estadisticas stats) {
        SwingUtilities.invokeLater(() -> {
            lblComp.setText("Comparaciones: " + stats.comparaciones);
            lblInt.setText("Intercambios: " + stats.intercambios);
            lblIter.setText("Iteraciones: " + stats.iteraciones);
        });
    }
}
