---
category: general
date: 2026-10-04
description: Aprende cómo ocultar una forma en Word con Java. Esta guía paso a paso
  te muestra cómo ocultar una forma en Word, hacer que una forma sea invisible en
  Word y ocultar una forma en Microsoft Word de forma programática.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- make shape invisible word
- hide shape microsoft word
language: es
lastmod: 2026-10-04
og_description: Cómo ocultar una forma en Word con Java. Sigue esta guía para ocultar
  una forma en Word, hacer invisible una forma en Word y ocultar una forma en Microsoft
  Word en unas pocas líneas de código.
og_image_alt: Screenshot showing a Word document with a hidden shape after applying
  the how to hide shape code
og_title: Cómo ocultar una forma en un documento de Word usando Java – guía completa
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to hide shape in Word with Java. This step‑by‑step guide
    shows you how to hide shape in Word, make shape invisible Word, and hide shape
    Microsoft Word programmatically.
  headline: How to hide shape in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Microsoft Word
- Document Automation
title: Cómo ocultar una forma en un documento de Word usando Java
url: /es/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo ocultar una forma en un documento Word usando Java

Si necesitas ocultar una forma en un archivo Word, esta guía te muestra exactamente **cómo ocultar una forma** de forma programática. Ya sea que estés generando informes, limpiando plantillas o preparando documentos para cumplimiento, puedes hacer que una forma sea invisible sin eliminarla de la estructura del archivo.

En las secciones siguientes aprenderás cómo ocultar una forma en Word, hacer una forma invisible en Word y ocultar una forma en Microsoft Word usando la biblioteca Aspose.Words para Java. El tutorial asume que tienes conocimientos básicos de Java y un entorno de desarrollo Java funcional.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java Development Kit (JDK) 8 o superior  
* Maven o Gradle para la gestión de dependencias  
* Aspose.Words para Java (versión 23.9 o posterior) – agrega la coordenada Maven `com.aspose:aspose-words:23.9`  
* Un documento Word (`input.docx`) que contenga al menos una forma (p. ej., una imagen, un cuadro de texto o SmartArt)

## Paso 1: Configurar el proyecto e importar Aspose.Words

Crea un nuevo proyecto Maven o agrega la dependencia Aspose.Words a uno existente.

```xml
<!-- pom.xml snippet -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier> <!-- adjust classifier for your JDK -->
</dependency>
```

La biblioteca proporciona las clases `Document`, `NodeType` y `Shape` que se usan en los pasos siguientes. Importa estas clases al inicio de tu archivo fuente Java:

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;
```

## Paso 2: Cargar el documento Word

Cargar el documento es el primer paso en cualquier flujo de trabajo de procesamiento de Word. El constructor `Document` lee el archivo en memoria, preservando todos los nodos, incluidas las formas ocultas.

```java
// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Por qué es importante*: Cargar el archivo crea un DOM (Document Object Model) que te permite navegar, consultar y modificar nodos individuales como formas, párrafos o tablas.

## Paso 3: Recuperar la forma objetivo

Si el documento contiene varias formas, puedes localizar una específica por índice, nombre u otro criterio. Para una demostración rápida, el ejemplo obtiene la primera forma en la jerarquía del documento, incluidas las formas anidadas dentro de tablas o grupos.

```java
// Retrieve the first shape (including descendants)
Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*Por qué es importante*: El método `getChild` con `true` para la bandera `isDeep` recorre todo el árbol de nodos, asegurando que captures formas que no son hijos directos del cuerpo del documento.

## Paso 4: Ocultar la forma

Establecer la propiedad `Hidden` a `true` indica a Microsoft Word que excluya la forma del renderizado del diseño mientras la mantiene en la estructura del documento. La forma no será visible cuando el archivo se abra en Word, pero seguirá accesible para procesamiento posterior.

```java
// Hide the shape so it does not appear in the layout
shape.setHidden(true);
```

*Por qué es importante*: Ocultar una forma es útil cuando necesitas preservar la forma para una activación posterior (p. ej., contenido condicional, versionado) sin mostrarla al usuario final.

## Paso 5: Guardar el documento modificado

Después de cambiar la visibilidad de la forma, escribe el documento de nuevo en disco. Puedes sobrescribir el archivo original o crear uno nuevo; el ejemplo escribe en `HiddenShape.docx`.

```java
// Save the document with the hidden shape
doc.save("YOUR_DIRECTORY/HiddenShape.docx");
```

Al abrir `HiddenShape.docx` en Microsoft Word, la forma será invisible, aunque el diseño del documento reflejará su estado oculto (sin espacio en blanco adicional).

## Ejemplo completo ejecutable

Unir todos los pasos produce un programa autónomo que puedes compilar y ejecutar directamente.

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

/**
 * Demonstrates how to hide shape in a Word document using Aspose.Words for Java.
 */
public class HideShapeExample {
    public static void main(String[] args) {
        // Verify that the input path is provided
        if (args.length != 1) {
            System.out.println("Usage: java HideShapeExample <input-docx-path>");
            return;
        }

        String inputPath = args[0];
        String outputPath = "HiddenShape.docx";

        try {
            // Step 1: Load the Word document
            Document doc = new Document(inputPath);

            // Step 2: Retrieve the first shape (including descendants)
            Shape shape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
            if (shape == null) {
                System.out.println("No shape found in the document.");
                return;
            }

            // Step 3: Hide the shape
            shape.setHidden(true);

            // Step 4: Save the modified document
            doc.save(outputPath);
            System.out.println("Shape hidden successfully. Output saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error processing document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Resultado esperado**  
Ejecutar el programa genera `HiddenShape.docx`. Al abrir ese archivo en Microsoft Word se muestra el contenido original, pero la forma que estaba presente en `input.docx` ya no es visible. La estructura del documento sigue conteniendo el nodo de la forma, que puede volver a mostrarse más tarde mediante `shape.setHidden(false)`.

## ¿Por qué ocultar una forma en lugar de eliminarla?

* **Preservar metadatos** – Las formas suelen contener texto alternativo, hipervínculos o datos personalizados que podrías necesitar más adelante.  
* **Visualización condicional** – En escenarios de combinación de correspondencia o generación de informes puedes mostrar la forma solo para destinatarios específicos.  
* **Control de versiones** – Mantener la forma oculta te permite conservar una única plantilla mientras alternas la visibilidad programáticamente.

## Variaciones comunes y casos límite

| Situación | Ajuste recomendado |
|-----------|--------------------|
| Múltiples formas, se necesita una específica | Usa `doc.getChild(NodeType.SHAPE, index, true)` con el índice apropiado, o recorre `doc.getChildNodes(NodeType.SHAPE, true)` y compara `shape.getName()` o `shape.getAlternativeText()`. |
| La forma está dentro de un GroupShape | La búsqueda profunda (`true`) ya llega dentro de los grupos, pero puede que necesites hacer cast a `GroupShape` primero si planeas ocultar solo un miembro del grupo. |
| Quieres ocultar todas las formas | Recorre todos los nodos de forma y llama a `setHidden(true)` dentro del bucle. |
| Compatibilidad con versiones antiguas de Word | La bandera `Hidden` es compatible desde Word 2000. Los formatos antiguos (`.doc`) también la respetan, pero prueba en la versión objetivo si encuentras cambios inesperados en el diseño. |

**Consejo profesional:** Después de ocultar una forma, puedes llamar a `doc.updatePageLayout()` si necesitas que el diseño de página se recalcule antes de guardar. Esto rara vez es necesario porque Word vuelve a ajustar el contenido al abrir, pero puede ser útil para la generación de vistas previas del lado del servidor.

## Probar el resultado programáticamente

Si deseas confirmar que la forma está oculta sin abrir Word, puedes consultar la propiedad después de guardar:

```java
Document checkDoc = new Document(outputPath);
Shape hiddenShape = (Shape) checkDoc.getChild(NodeType.SHAPE, 0, true);
System.out.println("Shape hidden flag: " + hiddenShape.isHidden()); // prints true
```

## Próximos pasos

Ahora que sabes cómo ocultar una forma en Word, considera estos temas relacionados:

* **Ocultar forma en Word según condiciones personalizadas** – Combina la bandera `Hidden` con campos de combinación de correspondencia para alternar la visibilidad por destinatario.  
* **Hacer una forma invisible en Word usando VBA** – Para automatización en el dispositivo, la misma propiedad puede establecerse vía VBA (`Shape.Visible = msoFalse`).  
* **Ocultar forma en Microsoft Word en bloque** – Procesa una carpeta de documentos con un bucle que aplique el mismo código a cada archivo.  

Explorar estas extensiones profundizará tu control sobre la automatización de documentos Word y mantendrá tus archivos generados limpios y profesionales.

--- 

*Este tutorial sigue la Guía de Estilo de Documentación para Desarrolladores de Google, usa voz activa, perspectiva en segunda persona y proporciona una solución completa y citables para motores de búsqueda y asistentes de IA.*

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Add shadow to shape in Word – Complete Aspose.Words Guide](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}