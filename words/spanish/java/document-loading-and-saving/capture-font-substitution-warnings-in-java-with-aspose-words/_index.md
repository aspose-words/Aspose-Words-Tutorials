---
category: general
date: 2026-01-11
description: Aprenda cómo capturar advertencias de sustitución de fuentes usando Aspose.Words
  para Java. Este tutorial paso a paso también cubre LoadOptions y devoluciones de
  llamada de advertencias.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: es
og_description: Captura las advertencias de sustitución de fuentes con Aspose.Words
  para Java. Sigue esta guía para configurar LoadOptions y una devolución de llamada
  de advertencias para una carga de documentos fiable.
og_title: Capturar advertencias de sustitución de fuentes en Java – Tutorial completo
tags:
- Aspose.Words
- Java
- Document Processing
title: Captura de advertencias de sustitución de fuentes en Java con Aspose.Words
  – Guía completa
url: /es/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturar advertencias de sustitución de fuentes – Tutorial completo de Java

¿Alguna vez necesitaste **capturar advertencias de sustitución de fuentes** al abrir un documento de Word con fuentes faltantes? Es un dolor de cabeza común, especialmente cuando generas PDFs o imprimes en un servidor que no tiene todas las tipografías instaladas. ¿La buena noticia? Aspose.Words for Java lo hace sin complicaciones: solo configura un objeto `LoadOptions` y conecta un callback de advertencia. En esta guía verás exactamente cómo hacerlo, por qué es importante y qué esperar cuando se dispara la advertencia.

También abordaremos temas relacionados como **Aspose.Words font substitution**, el uso de un **Java warning callback**, y las mejores prácticas para **LoadOptions usage**. Al final, tendrás un fragmento listo‑para‑ejecutar que registra cada evento de fuente faltante, de modo que tu procesamiento posterior nunca te sorprenda.

## Requisitos previos

Antes de sumergirnos, asegúrate de contar con:

- Java 17 (o cualquier JDK reciente) instalado y configurado.
- Aspose.Words for Java 23.10 (o más reciente) en tu classpath.
- Un documento de Word que haga referencia a una fuente que no tienes localmente (p. ej., `DocWithMissingFont.docx`).
- Familiaridad básica con bloques try/catch de Java—nada complejo.

Si alguno de estos te resulta desconocido, detente un momento e instala la biblioteca desde Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Ahora que la base está lista, pasemos al código.

## Paso 1: Configurar un callback de advertencia para **capturar advertencias de sustitución de fuentes**

Lo primero que necesitas es un callback que Aspose.Words invocará cada vez que encuentre una fuente faltante. Aquí es donde **capturamos advertencias de sustitución de fuentes**. El callback implementa la interfaz `IWarningCallback` y verifica el `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Por qué es importante:** Sin un callback, Aspose.Words sustituye silenciosamente la fuente faltante por una predeterminada, y nunca sabes que la salida visual ha cambiado. Al capturar la advertencia, puedes registrar, alertar o incluso abortar la carga si la fuente faltante es crítica.

## Paso 2: Configurar **LoadOptions** y registrar el callback

Ahora creamos una instancia de `LoadOptions` y adjuntamos nuestro `FontWarningCallback`. Este paso es esencial para **LoadOptions usage** y garantiza que cada carga de documento pase por el mismo filtro de advertencias.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Consejo:** Puedes reutilizar el mismo objeto `LoadOptions` para varios documentos, lo que ahorra algunas líneas de código repetitivo y garantiza un manejo consistente de **document loading warnings** en toda tu aplicación.

## Paso 3: Cargar el documento y observar la salida

Con el callback configurado, simplemente carga tu archivo de Word. Si el documento hace referencia a una fuente que no está instalada, el callback se disparará e imprimirá los detalles en la consola.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Salida esperada en la consola

Suponiendo que `DocWithMissingFont.docx` haga referencia a la fuente faltante *“Comic Sans MS”*, verás algo como:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Si el documento **no contiene fuentes faltantes**, la consola solo mostrará la línea final, confirmando que tu callback no produjo falsos positivos.

## Paso 4: Manejo de casos límite y errores comunes

### Múltiples fuentes faltantes

Si un documento usa varias fuentes no disponibles, el callback se ejecuta una vez por fuente. Obtendrás una serie de mensajes, cada uno con su propio `source` y `description`. No se requiere código adicional—solo asegúrate de que tu sistema de registro pueda manejar llamadas sucesivas rápidas.

### Suprimir advertencias

En casos raros podrías querer ignorar ciertas sustituciones (p. ej., sabes que una alternativa particular es aceptable). Amplía la lógica del callback:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Seguridad en hilos

`LoadOptions` de Aspose.Words no es seguro para hilos por defecto. Si estás cargando documentos en paralelo, crea una instancia separada de `LoadOptions` por hilo, o sincroniza el callback para evitar condiciones de carrera.

## Paso 5: Verificar la fuente sustituida en el documento resultante

Después de cargar, puede que quieras confirmar que la sustitución realmente ocurrió. La API te permite iterar sobre todos los runs y examinar el nombre de fuente efectivo:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Este fragmento imprime cada run de texto con su fuente final. Es una verificación práctica cuando construyes pipelines automatizados de conversión a PDF.

## Ejemplo completo y funcional

Juntando todo, aquí tienes el programa completo, listo‑para‑ejecutar:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Guarda esto como `FontSubstitutionInfo.java`, compílalo con `javac` y ejecútalo con `java FontSubstitutionInfo`. Deberías ver los mensajes de advertencia (si los hay) seguidos de la lista de runs y sus fuentes finales.

## Ayuda visual

![Captura de pantalla de la salida de consola mostrando advertencias de sustitución de fuentes](/images/font-substitution-warning.png "ejemplo de captura de advertencias de sustitución de fuentes")

*Texto alternativo:* **capturar advertencias de sustitución de fuentes** – salida de consola después de cargar un documento con fuentes faltantes.

## Conclusión

Ahora sabes cómo **capturar advertencias de sustitución de fuentes** usando Aspose.Words for Java. Configurando un objeto `LoadOptions` y proporcionando un `IWarningCallback` personalizado, obtienes total visibilidad de cualquier evento de fuente faltante que de otro modo podría afectar silenciosamente la apariencia de tu documento. Esta técnica se integra directamente con el manejo de **Aspose.Words font substitution**, garantiza advertencias fiables al **cargar documentos**, y te brinda la flexibilidad de registrar, alertar o abortar según tus reglas de negocio.

### ¿Qué sigue?

- Explora patrones de **Java warning callback** para otros tipos de advertencias (p. ej., `DEPRECATED_FEATURE`).
- Combina este enfoque con **PDF conversion** para garantizar que las fuentes sustituidas no rompan el diseño.
- Profundiza en **LoadOptions usage**—experimenta con `Password`, `Encoding` y `ResourceLoadingCallback` para escenarios más avanzados.

Siéntete libre de ajustar el callback, dirigir las advertencias a un framework de registro, o incluso lanzar una excepción personalizada si falta una fuente crítica. El cielo es el límite, y ahora tienes una base sólida sobre la que construir.

¡Feliz codificación, y que tus documentos siempre se rendericen tal como esperas!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}