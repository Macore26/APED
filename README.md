# APED
Aulas_Praticas

// Nome: Santos Alfredo Macore
// ficha 1 numero 6.

public class MedianaArray {

    public static int mediana(int[] array) {
        if (array == null || array.length == 0) {
            throw new IllegalArgumentException("Array vazio ou nulo.");
        }

        int meio = array.length / 2;
        return medianaRecursiva(array, 0, array.length - 1, meio);
    }

    private static int medianaRecursiva(int[] array, int inicio, int fim, int k) {
        int indicePivo = particionar(array, inicio, fim);

        if (indicePivo == k) {
            return array[indicePivo];
        } else if (indicePivo < k) {
            return medianaRecursiva(array, indicePivo + 1, fim, k);
        } else {
            return medianaRecursiva(array, inicio, indicePivo - 1, k);
        }
    }

    private static int particionar(int[] array, int inicio, int fim) {
        int pivo = array[fim];
        int i = inicio - 1;

        for (int j = inicio; j < fim; j++) {
            if (array[j] <= pivo) {
                i++;
                trocar(array, i, j);
            }
        }

        trocar(array, i + 1, fim);
        return i + 1;
    }

    private static void trocar(int[] array, int i, int j) {
        int temp = array[i];
        array[i] = array[j];
        array[j] = temp;
    }

    public static void main(String[] args) {
        int[] array = {5, 2, 9, 1, 7, 6, 3};
        int mediana = mediana(array);
        System.out.println("A mediana do array é: " + mediana);
    }
}

