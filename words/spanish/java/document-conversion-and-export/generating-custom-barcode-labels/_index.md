---
date: 2025-12-10
description: Aprenda a generar etiquetas de códigos de barras personalizadas usando
  Aspose.Words para Java. Esta guía paso a paso le muestra cómo incrustar códigos
  de barras en documentos de Word.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Generar etiquetas de código de barras personalizadas en Aspose.Words para Java
url: /es/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generar etiquetas de código de barras personalizadas en Aspose.Words para Java

## Introducción a la generación de códigos de barras personalizados en Aspose.Words para Java

Los códigos de barras son esenciales en aplicaciones modernas—ya sea que estés gestionando inventario, imprimiendo boletos o creando tarjetas de identificación. En este tutorial **generarás etiquetas de código de barras personalizadas** e incrustarás la imagen directamente en un documento Word usando la interfaz `IBarcodeGenerator`. Recorreremos cada paso, desde la configuración del entorno hasta la inserción de la imagen del código de barras, para que puedas comenzar a usar códigos de barras en tus proyectos Java de inmediato.

## Respuestas rápidas
- **¿Qué enseña este tutorial?** Cómo generar etiquetas de código de barras personalizadas e incrustarlas en un archivo Word con Aspose.Words para Java.  
- **¿Qué tipo de de barras se usa en el ejemplo?** Código QR (puedes cambiarlo por cualquier tipo compatible).  
- **¿Necesito una licencia?** Se requiere una licencia temporal para acceso sin restricciones durante el desarrollo.  
- **¿Qué versión de Java se necesita?** JDK 8 o superior.  
- **¿Puedo cambiar el tamaño o los colores del código de barras?** Sí—modifica los ajustes de `BarcodeParameters` y `BarcodeGenerator`.

## Requisitos previos

Antes de comenzar a programar, asegúrate de contar con lo siguiente:

- Java Development Kit (JDK): Versión 8 o superior.  
- Biblioteca Aspose.Words para Java: [Download here](https://releases.aspose.com/words/java/).  
- Biblioteca Aspose.BarCode para Java: [Download here](https://releases.aspose.com/).  
- Entorno de desarrollo integrado (IDE): IntelliJ IDEA, Eclipse o cualquier IDE que prefieras.  
- Licencia temporal: Obtén una [temporary license](https://purchase.aspose.com/temporary-license/) para acceso sin restricciones.

## Importar paquetes

Usaremos las bibliotecas Aspose.Words y Aspose.BarCode. Importa los siguientes paquetes en tu proyecto:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Estas importaciones nos dan acceso a la API de generación de códigos de barras y a las clases de documentos Word que necesitaremos.

## Paso 1: Crear una clase de utilidad para operaciones de código de barras

Para mantener el código principal limpio, encapsularemos los ayudantes comunes—como **convertir twips a píxeles** y **conversión de color hexadecimal**—en una clase de utilidad.

### Código

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**Explicación**

- `twipsToPixels` – Word mide las dimensiones en **twips**; este método los convierte a píxeles de pantalla, lo cual es útil cuando necesitas dimensionar la imagen del código de barras con precisión.  
- `convertColor` – Convierte una cadena hexadecimal (p. ej., `"FF0000"` para rojo) en un objeto `java.awt.Color`, permitiéndote **how to insert barcode** con colores de primer plano y fondo personalizados.

## Paso 2: Implementar el generador de código de barras personalizado

Ahora implementaremos la interfaz `IBarcodeGenerator`. Esta clase será responsable de **generate qr code java**‑style images que Aspose.Words puede incrustar.

### Código

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**Explicación**

- `getBarcodeImage` crea una instancia de `BarcodeGenerator`, aplica los colores suministrados a través de `BarcodeParameters` y finalmente devuelve un `BufferedImage`.  
- El método también maneja errores devolviendo una imagen de marcador de posición, asegurando que la creación del documento Word nunca falle.

## Paso 3: Generar un código de barras y **embed barcode in Word**

Con el generador listo, ahora podemos producir una imagen de código de barras y **insertarla en un documento Word**.

### Código

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**Explicación**

1. **Inicialización del documento** – Crea un nuevo `Document` (o puedes cargar una plantilla existente).  
2. **Parámetros del código de barras** – Define el tipo de código de barras (`QR`), el valor a codificar y los colores de primer plano/fondo.  
3. **Inserción de la imagen** – `builder.insertImage` coloca el código de barras generado al tamaño deseado (200 × 200 píxeles). Este es el núcleo de **how to insert barcode** en un archivo Word.  
4. **Guardado** – El documento final, `CustomBarcodeLabels.docx`, contiene el código de barras incrustado listo para imprimir o distribuir.

## ¿Por qué generar etiquetas de código de barras personalizadas con Aspose.Words?

- **Control total** sobre la apariencia del código de barras (tipo, tamaño, colores).  
- **Integración fluida**—no se necesitan archivos de imagen intermedios; el código de barras se genera en memoria y se inserta directamente.  
- **Multiplataforma**—funciona en cualquier SO que soporte Java, lo que lo hace ideal para generación de documentos del lado del servidor.  
- **Escalable**—puedes iterar sobre una fuente de datos para crear cientos de etiquetas personalizadas en una sola ejecución.

## Problemas comunes y solución de errores

| Síntoma | Causa probable | Solución |
|---------|----------------|----------|
| El código de barras aparece en blanco | Los colores de `BarcodeParameters` son iguales (p. ej., negro sobre negro) | Verifica los valores de `foregroundColor` y `backgroundColor`. |
| La imagen está distorsionada | Se pasaron dimensiones de píxeles incorrectas a `insertImage` | Ajusta los argumentos de ancho/alto o usa la conversión `twipsToPixels` para un dimensionado preciso. |
| Error de tipo de código de barras no compatible | Se está usando un tipo no reconocido por `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Asegúrate de que la cadena del tipo de código de barras coincida con uno de los `EncodeTypes` soportados (p. ej., `"QR"`, `"CODE128"`). |

## Preguntas frecuentes

**P: ¿Puedo usar Aspose.Words para Java sin una licencia?**  
R: Sí, pero tendrá algunas limitaciones. Obtén una [temporary license](https://purchase.aspose.com/temporary-license/) para funcionalidad completa.

**P: ¿Qué tipos de códigos de barras puedo generar?**  
R: Aspose.BarCode soporta QR, Code 128, EAN‑13 y muchos otros formatos. Consulta la [documentation](https://reference.aspose.com/words/java/) para la lista completa.

**P: ¿Cómo puedo cambiar el tamaño del código de barras?**  
R: Ajusta los argumentos de ancho y alto en `builder.insertImage`, o usa `twipsToPixels` para convertir unidades de medida de Word a píxeles.

**P: ¿Es posible usar fuentes personalizadas para el texto del código de barras?**  
R: Sí, puedes personalizar la fuente del texto mediante la propiedad `CodeTextParameters` del `BarcodeGenerator`.

**P: ¿Dónde puedo obtener ayuda si tengo problemas?**  
R: Visita el [support forum](https://forum.aspose.com/c/words/8/) para recibir asistencia de la comunidad y los ingenieros de Aspose.

## Conclusión

Al seguir los pasos anteriores, ahora sabes cómo **generar imágenes de código de barras personalizadas** y **embed barcode in Word** documentos usando Aspose.Words para Java. Esta técnica es lo suficientemente flexible para etiquetas de inventario, boletos de eventos o cualquier escenario donde un código de barras deba formar parte de un documento generado. Experimenta con diferentes tipos de códigos de barras y opciones de estilo para adaptarlos a tus necesidades empresariales específicas.

---

**Última actualización:** 2025-12-10  
**Probado con:** Aspose.Words para Java 24.12, Aspose.BarCode para Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}