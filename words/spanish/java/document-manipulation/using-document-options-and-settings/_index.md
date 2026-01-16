---
date: 2026-01-16
description: Aprende a resaltar errores ortográficos en Word usando Aspose.Words para
  Java, y descubre cómo establecer caracteres por línea, personalizar opciones de
  vista y limpiar estilos.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Resaltar errores ortográficos en Word con Aspose.Words Java
url: /es/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Uso de Opciones y Configuraciones de Documento en Aspose.Words para Java

## Introducción al Uso de Opciones y Configuraciones de Documento en Aspose.Words para Java

En esta guía completa, aprenderás **cómo resaltar errores ortográficos en Word** usando Aspose.Words para Java mientras dominas configuraciones relacionadas como opciones de visualización, diseño de página y limpieza de estilos. Ya seas un desarrollador experimentado o estés comenzando, los ejemplos a continuación te ayudarán a crear documentos robustos y conscientes de errores que funcionen en todas las versiones de Word.

## Respuestas Rápidas
- **¿Cómo puedo resaltar errores ortográficos en Word?** Use `setShowSpellingErrors(true)` on the `Document` object.  
- **¿Puedo también mostrar errores gramaticales?** Sí—llama a `setShowGrammaticalErrors(true)`.  
- **¿Qué método establece los caracteres por línea?** `getPageSetup().setCharactersPerLine(int)`.  
- **¿Qué API optimiza para una versión específica de Word?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **¿Hay una forma de limpiar estilos no utilizados?** Use `CleanupOptions` con `setUnusedStyles(true)` y llame a `doc.cleanup(options)`.

## Cómo resaltar errores ortográficos en Word?

Aspose.Words facilita activar el resaltado de errores ortográficos. Cuando el documento se abre en Microsoft Word, las palabras mal escritas aparecen con la conocida subrayado rojo, ayudando a los usuarios finales a detectar problemas al instante.

## Cómo establecer caracteres por línea

Controlar la cantidad de caracteres por línea es esencial para diseños de ancho fijo (p. ej., listados de código o formularios heredados). La clase `PageSetup` proporciona `setCharactersPerLine(int)` que te permite definir este valor con precisión.

## Cómo mostrar errores gramaticales

Más allá de la ortografía, también puedes habilitar la visualización de errores gramaticales. Esto es útil para redactar contenido que debe cumplir con guías de estilo o para crear herramientas de corrección.

## Optimización de Documentos para Compatibilidad

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

Un aspecto clave de la gestión de documentos es garantizar la compatibilidad con diferentes versiones de Microsoft Word. Aspose.Words para Java ofrece una forma sencilla de optimizar documentos para versiones específicas de Word. En el ejemplo anterior, optimizamos un documento para Word 2016, asegurando una compatibilidad sin problemas.

## Identificación de Errores Gramaticales y Ortográficos

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

La precisión es fundamental al trabajar con documentos. Aspose.Words para Java te permite resaltar errores gramaticales y ortográficos dentro de tus documentos, haciendo la corrección y edición más eficientes.

## Limpieza de Estilos y Listas No Utilizados

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

Gestionar eficientemente los estilos y listas de un documento es esencial para mantener la consistencia del mismo. Aspose.Words para Java te permite limpiar estilos y listas no utilizados, garantizando una estructura de documento simplificada y organizada.

## Eliminación de Estilos Duplicados

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

Los estilos duplicados pueden generar confusión e inconsistencia en tus documentos. Con Aspose.Words para Java, puedes eliminar fácilmente los estilos duplicados, manteniendo la claridad y coherencia del documento.

## Personalización de Opciones de Visualización del Documento

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

Personalizar la experiencia de visualización de tus documentos es crucial. Aspose.Words para Java te permite establecer diversas opciones de visualización, como el diseño de página y el porcentaje de zoom, para mejorar la legibilidad del documento.

## Configuración del Diseño de Página del Documento

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

Una configuración precisa de la página es crucial para el formato del documento. Aspose.Words para Java te permite establecer modos de diseño, **caracteres por línea** y líneas por página, asegurando que tus documentos sean visualmente atractivos.

## Configuración de Idiomas de Edición

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

Los idiomas de edición juegan un papel vital en el procesamiento de documentos. Con Aspose.Words para Java, puedes establecer y personalizar los idiomas de edición para adaptarlos a las necesidades lingüísticas de tu documento.

## Conclusión

En esta guía, hemos profundizado en las diversas opciones y configuraciones de documento disponibles en Aspose.Words para Java. Desde la optimización y la visualización de errores hasta la limpieza de estilos y las opciones de visualización, esta poderosa biblioteca ofrece amplias capacidades para gestionar y personalizar tus documentos.

## Preguntas Frecuentes

### ¿Cómo optimizo un documento para una versión específica de Word?

Para optimizar un documento para una versión específica de Word, usa el método `optimizeFor` y especifica la versión deseada. Por ejemplo, para optimizar para Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### ¿Cómo puedo resaltar errores gramaticales y ortográficos en un documento?

Puedes habilitar la visualización de errores gramaticales y ortográficos en un documento usando el siguiente código:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### ¿Cuál es el propósito de limpiar estilos y listas no utilizados?

Limpiar estilos y listas no utilizados ayuda a mantener una estructura de documento limpia y organizada. Elimina el desorden innecesario, mejorando la legibilidad y consistencia del documento.

### ¿Cómo puedo eliminar estilos duplicados de un documento?

Para eliminar estilos duplicados de un documento, utiliza el método `cleanup` con la opción `duplicateStyle` establecida en `true`. Aquí tienes un ejemplo:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### ¿Cómo personalizo las opciones de visualización de un documento?

Puedes personalizar las opciones de visualización del documento usando la clase `ViewOptions`. Por ejemplo, para establecer el tipo de vista a diseño de página y el zoom al 50%:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Consejos Adicionales y Errores Comunes

- **Activa tanto la revisión ortográfica como la gramatical** cuando necesites una corrección exhaustiva. Olvidar una de las banderas (`setShowGrammaticalErrors` o `setShowSpellingErrors`) puede dejar errores sin detectar.
- **Al establecer caracteres por línea**, recuerda que el valor interactúa con la fuente seleccionada y los márgenes de página. Prueba con el diseño real del documento para evitar saltos de línea inesperados.
- **Las operaciones de limpieza son irreversibles** en el archivo original. Siempre trabaja sobre una copia o usa control de versiones para preservar el estilo original.
- **Las preferencias de idioma de edición** afectan el comportamiento del corrector ortográfico. Si trabajas con documentos multilingües, agrega todos los idiomas relevantes a `LanguagePreferences`.

---

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}