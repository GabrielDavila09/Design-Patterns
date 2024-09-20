# Elvirez Dávila Ulises Gabriel - 20211769
# Patrón SINGLETON
El patrón de diseño Singleton es uno de los patrones creacionales más conocidos en el desarrollo de software, cuya finalidad es asegurar que una clase tenga una única instancia y proporcionar un punto de acceso global a esa instancia.

# Ejemplo de su uso en el mundo real
Imagina que tienes una aplicación en tu teléfono que controla todos los dispositivos de tu casa inteligente. Si quisieras ajustar la temperatura del termostato, abrir la puerta principal o encender las luces, todas esas solicitudes deben pasar por un controlador central que asegura que no haya conflictos entre los comandos, que las instrucciones sean seguras y que los dispositivos respondan de forma coordinada.

## ¿Cómo aplica el Singleton aquí?
• El controlador de acceso debe ser único en toda la casa para evitar que haya comandos contradictorios o múltiples sistemas controlando los mismos dispositivos al mismo tiempo.
• Al usar el patrón Singleton, garantizas que solo haya un punto de acceso central a todos los dispositivos y que ese acceso sea uniforme.

## Código ejemplo en C#
``` C#
using System;

public class Singleton
{
    // 1. Instancia privada y estática que almacenará la única instancia de la clase
    private static Singleton _instance;

    // 2. Constructor privado: impide que se cree una instancia fuera de la clase
    private Singleton()
    {
        Console.WriteLine("Instancia del Singleton creada.");
    }

    // 3. Método estático que proporciona el acceso global a la instancia
    public static Singleton Instance
    {
        get
        {
            // 4. Si la instancia aún no ha sido creada, la creamos
            if (_instance == null)
            {
                _instance = new Singleton();
            }
            // 5. Devolvemos la instancia única
            return _instance;
        }
    }

    // Ejemplo de método dentro de la clase Singleton
    public void DoSomething()
    {
        Console.WriteLine("Método ejecutado desde la instancia Singleton.");
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Intentamos obtener la instancia de la clase Singleton
        Singleton instance1 = Singleton.Instance;

        // Llamamos a un método de la clase Singleton
        instance1.DoSomething();

        // Intentamos obtener la instancia de nuevo
        Singleton instance2 = Singleton.Instance;

        // Comprobamos si ambas instancias son iguales
        if (instance1 == instance2)
        {
            Console.WriteLine("Ambas instancias son la misma.");
        }
    }
}
```
https://dotnetfiddle.net/c3Lmfa
