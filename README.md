## Métodos de búsqueda
Los métodos de búsqueda nos servirán para encontrar un elemento en un array.

Puedes visualizarlos [aquí](https://www.cs.usfca.edu/~galles/visualization/Algorithms.html)

### Búsqueda secuencial
La búsqueda [secuencial o lineal](https://es.wikipedia.org/wiki/B%C3%BAsqueda_lineal) consiste en recorrer el vector hasta devolver el elemento buscado. Su eficiencia es de O(n). Es el método más sencillo de búsqueda, pero no es el más eficiente.
- https://www.youtube.com/watch?v=-PuqKbu9K3U

![imagen](https://jorgecontrerasp.files.wordpress.com/2012/06/d1.png)

```java
public class Main {
    public static int busquedaSecuencial(int[] array, int elemento) {
        for (int i = 0; i < array.length; i++) {
            if (array[i] == elemento) {
                return i;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        // Example usage
        int[] array = {1, 2, 3, 4, 5};
        int index = busquedaSecuencial(array, 3);
        System.out.println("Element found at index: " + index);
    }
}
```

### Búsqueda binaria
En la [búsqueda binaria](https://es.wikipedia.org/wiki/B%C3%BAsqueda_binaria) partimos de un array ordenado. Su eficiencia es de O(n log n).
Se compara el dato buscado con el elemento en el centro del vector:
1. Si coinciden, hemos encontrado el dato buscado.
2. Si el dato es mayor que el elemento central del vector, tenemos que buscar el dato en segunda mitad del vector (mejor recursivamente).
3. Si el dato es menor que el elemento central del vector, tenemos que buscar el dato en la primera mitad del vector (mejor recursivamente).
- https://www.youtube.com/watch?v=iP897Z5Nerk

![imagen](http://2.bp.blogspot.com/-t8Ra7s0Usvc/TthYTUMUbvI/AAAAAAAAAFA/Ztuh8WzYqaE/s1600/secuen.jpg)

```java
// Versión Iterativa
public class Main {
    public static int busquedaBinariaIterativa(int[] array, int elemento) {
        int centro;
        int inf = 0;
        int sup = array.length - 1;

        while (inf <= sup) {
            centro = (sup + inf) / 2;
            if (array[centro] == elemento) {
                return centro;
            } else if (elemento < array[centro]) {
                sup = centro - 1;
            } else {
                inf = centro + 1;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        // Example usage
        int[] array = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
        int index = busquedaBinariaIterativa(array, 5);
        System.out.println("Element found at index: " + index);
    }
}
// versión recursiva
public class Main {
    public static int busquedaBinariaRecursiva(int[] array, int elemento, int inf, int sup) {
        if (inf > sup) {
            return -1;
        }
        int centro = (sup + inf) / 2;
        if (array[centro] == elemento) {
            return centro;
        } else if (elemento < array[centro]) {
            return busquedaBinariaRecursiva(array, elemento, inf, centro - 1);
        } else {
            return busquedaBinariaRecursiva(array, elemento, centro + 1, sup);
        }
    }

    public static void main(String[] args) {
        // Example usage
        int[] array = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
        int index = busquedaBinariaRecursiva(array, 6, 0, array.length - 1);
        System.out.println("Element found at index: " + index);
    }
}
