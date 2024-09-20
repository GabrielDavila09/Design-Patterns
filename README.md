# Elvirez Dávila Ulises Gabriel - 20211769
# Patrón SINGLETON
El patrón de diseño Singleton es uno de los patrones creacionales más conocidos en el desarrollo de software, cuya finalidad es asegurar que una clase tenga una única instancia y proporcionar un punto de acceso global a esa instancia.

# Ejemplo de su uso en el mundo real
Imagina que tienes una aplicación en tu teléfono que controla todos los dispositivos de tu casa inteligente. Si quisieras ajustar la temperatura del termostato, abrir la puerta principal o encender las luces, todas esas solicitudes deben pasar por un controlador central que asegura que no haya conflictos entre los comandos, que las instrucciones sean seguras y que los dispositivos respondan de forma coordinada.

## ¿Cómo aplica el Singleton aquí?
### • El controlador de acceso debe ser único en toda la casa para evitar que haya comandos contradictorios o múltiples sistemas controlando los mismos dispositivos al mismo tiempo.
### • Al usar el patrón Singleton, garantizas que solo haya un punto de acceso central a todos los dispositivos y que ese acceso sea uniforme.

## ¿Cómo soluciona el problema?
### Problema: 
En situaciones donde la creación de múltiples instancias de una clase puede ser costosa o generar inconsistencias, como en el caso de administrar conexiones a una base de datos, controladores de dispositivos, o gestionar configuraciones globales, crear más de una instancia puede causar sobrecarga de recursos, errores o conflictos.
### Solución en el código: 
Al tener un constructor privado y un método estático (Instance), el patrón asegura que no se pueda crear más de una instancia de la clase Singleton. El código se asegura de que siempre se devuelva la misma instancia al solicitarla, sin permitir que se creen objetos adicionales.

## Código ejemplo en C#
``` C#
using System;

public class SmartHomeController
{
    // 1. Instancia única de la clase (Singleton)
    private static SmartHomeController _instance;

    // 2. Constructor privado para evitar la creación directa de instancias
    private SmartHomeController() 
    {
        Console.WriteLine("Controlador central de la casa inteligente iniciado.");
    }

    // 3. Propiedad estática para obtener la única instancia de SmartHomeController
    public static SmartHomeController Instance
    {
        get
        {
            if (_instance == null)
            {
                _instance = new SmartHomeController();
            }
            return _instance;
        }
    }

    // Métodos simulados para controlar dispositivos de la casa inteligente
    public void ControlLights(string action)
    {
        if (action == "on")
        {
            Console.WriteLine("Luces encendidas.");
        }
        else if (action == "off")
        {
            Console.WriteLine("Luces apagadas.");
        }
        else
        {
            Console.WriteLine("Acción desconocida para las luces.");
        }
    }

    public void SetTemperature(int temperature)
    {
        Console.WriteLine($"La temperatura se ha ajustado a {temperature} grados.");
    }

    public void LockDoors()
    {
        Console.WriteLine("Las puertas están bloqueadas.");
    }

    public void UnlockDoors()
    {
        Console.WriteLine("Las puertas están desbloqueadas.");
    }
}

// Clase principal para simular la interacción con la casa inteligente
class Program
{
    static void Main(string[] args)
    {
        // Obtener la instancia del controlador de la casa inteligente
        SmartHomeController controller = SmartHomeController.Instance;

        // Controlar las luces
        controller.ControlLights("on");

        // Ajustar la temperatura
        controller.SetTemperature(22);

        // Bloquear las puertas
        controller.LockDoors();

        // Intentar obtener la instancia nuevamente y realizar más acciones
        SmartHomeController anotherController = SmartHomeController.Instance;

        // Comprobar que ambas referencias son a la misma instancia
        if (controller == anotherController)
        {
            Console.WriteLine("Ambos controladores son la misma instancia.");
        }

        // Apagar las luces
        anotherController.ControlLights("off");
    }
}

```
https://dotnetfiddle.net/c3Lmfa
