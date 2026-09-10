---
date: 2025-12-27
description: Aprende a establecer la dirección, cargar archivos txt, recortar espacios
  y convertir txt a docx usando Aspose.Words para Java.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Cómo establecer la dirección y cargar archivos de texto con Aspose.Words para
  Java
url: /es/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer la dirección y cargar archivos de texto con Aspose.Words para Java

## Introducción a la carga de archivos de texto con Aspose.Words para Java

En esta guía, descubrirás **cómo establecer la dirección** al cargar documentos de texto plano y verás formas prácticas de **cargar txt**, **eliminar espacios** y **convertir txt a docx** usando Aspose.Words para Java. Ya sea que estés construyendo un servicio de conversión de documentos o necesites un control fino sobre la detección de listas, este tutorial te lleva paso a paso con explicaciones claras y código listo para ejecutar.

## Respuestas rápidas
- **¿Cómo establezco la dirección del texto para un archivo TXT cargado?** Usa `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` o especifica `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **¿Puede Aspose.Words detectar listas numeradas en texto plano?** Sí – habilita `DetectNumberingWithWhitespaces` en `TxtLoadOptions`.
- **¿Cómo puedo eliminar los espacios iniciales y finales?** Configura `TxtLeadingSpacesOptions.TRIM` y `TxtTrailingSpacesOptions.TRIM`.
- **¿Es posible convertir un archivo TXT a DOCX en una sola línea?** Carga el TXT con `TxtLoadOptions` y llama a `Document.save("output.docx")`.
- **¿Qué versión de Java se requiere?** Java 8+ es suficiente para Aspose.Words 24.x.

## ¿Qué significa “cómo establecer la dirección” en Aspose.Words?
Cuando un archivo de texto contiene scripts de derecha a izquierda (p. ej., hebreo o árabe), la biblioteca debe conocer el orden de lectura. El enumerado `DocumentDirection` te permite **establecer la dirección** manualmente o dejar que Aspose la detecte automáticamente, garantizando un diseño correcto y formato bidi.

## ¿Por qué usar Aspose.Words para cargar archivos TXT?
- **Detección precisa de listas** – maneja listas numeradas, con viñetas y listas delimitadas por espacios.
- **Manejo fino de espacios** – elimina o conserva los espacios iniciales/finales.
- **Detección automática de dirección de texto** – ideal para documentos multilingües.
- **Conversión en un solo paso** – carga un `.txt` y guárdalo como `.docx`, `.pdf` o cualquier formato compatible.

## Requisitos previos
- Java 8 o superior.
- Biblioteca Aspose.Words para Java (agrega la dependencia Maven/Gradle o el JAR a tu proyecto).
- Conocimientos básicos de flujos de I/O en Java.

## Guía paso a paso

### Paso 1: Detección de listas (cómo cargar txt)
Para cargar un documento de texto y detectar listas automáticamente, crea una instancia de `TxtLoadOptions` y habilita la detección de listas. El código a continuación muestra varios estilos de lista y habilita la numeración sensible a espacios en blanco.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Consejo profesional:** Si solo necesitas detección básica de listas, puedes omitir la opción de espacios en blanco – Aspose seguirá reconociendo los patrones estándar `1.` y `1)`.

### Paso 2: Opciones de manejo de espacios (cómo eliminar espacios)
Los espacios iniciales y finales a menudo provocan fallos de formato. Usa `TxtLeadingSpacesOptions` y `TxtTrailingSpacesOptions` para controlar este comportamiento.

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

> **Por qué es importante:** Eliminar espacios evita indentaciones no deseadas en el DOCX resultante, haciendo que el documento se vea limpio sin procesamiento manual posterior.

### Paso 3: Control de la dirección del texto (cómo establecer la dirección)
Para lenguajes de derecha a izquierda, establece la dirección del documento antes de cargarlo. El ejemplo a continuación carga un archivo de texto en hebreo y muestra la bandera bidi para confirmar la dirección.

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

> **Error común:** Olvidar establecer `DocumentDirection` puede generar texto árabe/hebreo desordenado donde los caracteres aparecen en el orden incorrecto.

### Código fuente completo para cargar archivos de texto con Aspose.Words para Java
A continuación se muestra el código completo, listo para ejecutar, que combina detección de listas, manejo de espacios y control de dirección. Puedes copiar‑pegarlo en una única clase y ejecutar los tres métodos de prueba individualmente.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Problemas comunes y soluciones
| Problema | Causa | Solución |
|----------|-------|----------|
| Las listas no se detectan | `DetectNumberingWithWhitespaces` quedó en `false` para listas delimitadas por espacios | Habilita `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Indentación extra después de cargar | Los espacios iniciales se conservaron | Configura `TxtLeadingSpacesOptions.TRIM` |
| El texto en hebreo aparece invertido | No se estableció la dirección del documento o se estableció `LEFT_TO_RIGHT` | Usa `DocumentDirection.AUTO` o `RIGHT_TO_LEFT` |
| El DOCX de salida está vacío | El flujo de entrada no se reinició antes de la segunda carga | Vuelve a crear `ByteArrayInputStream` para cada llamada de carga |

## Preguntas frecuentes

### P: ¿Qué es Aspose.Words para Java?
R: Aspose.Words para Java es una potente biblioteca de procesamiento de documentos que permite a los desarrolladores crear, manipular y convertir documentos Word programáticamente en aplicaciones Java. Soporta una amplia gama de funciones, desde la carga simple de texto hasta el formato complejo y la conversión.

### P: ¿Cómo puedo comenzar con Aspose.Words para Java?
R: 1. Descarga e instala la biblioteca Aspose.Words para Java. 2. Consulta la documentación en [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) para obtener información detallada y ejemplos. 3. Explora el código de muestra y los tutoriales para aprender a usar la biblioteca de manera eficaz.

### P: ¿Cómo cargo un documento de texto usando Aspose.Words para Java?
R: Utiliza la clase `TxtLoadOptions` junto con el constructor de `Document`. Especifica opciones como detección de listas, manejo de espacios o dirección del texto como se muestra en las secciones paso a paso anteriores.

### P: ¿Puedo convertir un documento de texto cargado a otros formatos?
R: Sí. Después de cargar el archivo TXT en un objeto `Document`, llama a `doc.save("output.pdf")`, `doc.save("output.docx")` o cualquier otro formato compatible.

### P: ¿Cómo manejo los espacios en documentos de texto cargados?
R: Controla los espacios iniciales y finales con `TxtLeadingSpacesOptions` y `TxtTrailingSpacesOptions`. Configúralos en `TRIM` para eliminar espacios no deseados, o en `PRESERVE` si necesitas mantener el espaciado original.

### P: ¿Cuál es la importancia de la dirección del texto en Aspose.Words para Java?
R: La dirección del texto garantiza la representación correcta de scripts de derecha a izquierda (hebreo, árabe, etc.). Al establecer `DocumentDirection`, aseguras que el texto bidi se muestre adecuadamente en el documento resultante.

### P: ¿Dónde puedo encontrar más recursos y soporte para Aspose.Words para Java?
R: Visita la [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) para referencias de API, ejemplos de código y guías detalladas. También puedes unirte a los foros de la comunidad Aspose o contactar al soporte de Aspose para preguntas específicas.

### P: ¿Aspose.Words para Java es adecuado para proyectos comerciales?
R: Sí. Ofrece opciones de licencia tanto para uso personal como comercial. Revisa los términos de licencia en el sitio web de Aspose para elegir el plan adecuado para tu proyecto.

## Conclusión
Ahora dispones de un conjunto completo de herramientas para **cargar archivos txt**, **detectar listas**, **eliminar espacios** y **establecer la dirección** al convertir texto plano en documentos Word enriquecidos con Aspose.Words para Java. Aplica estos patrones para automatizar flujos de trabajo de documentos, mejorar el soporte multilingüe y garantizar una salida limpia y profesional en cada ocasión.

---

**Última actualización:** 2025-12-27  
**Probado con:** Aspose.Words para Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}