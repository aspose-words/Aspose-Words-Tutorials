---
date: 2026-01-11
description: Aprenda cómo mostrar y ocultar marcadores y crear marcadores en Java
  usando Aspose.Words for Java para una navegación y manipulación de documentos eficiente.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Mostrar y ocultar marcadores con Aspose.Words para Java
url: /es/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mostrar/Ocultar Marcadores con Aspose.Words para Java

## Introducción al uso de marcadores en Aspose.Words para Java

Los marcadores son una característica poderosa en Aspose.Words para Java que le permite **create bookmark java**, navegar a contenido específico e incluso **show hide bookmarks** cuando necesita generar diferentes versiones de documentos. En esta guía paso a paso recorreremos la creación, acceso, actualización, copia y conmutación de la visibilidad de los marcadores, dándole control total sobre la manipulación de documentos.

## Respuestas rápidas
- **¿Cuál es el propósito principal de los marcadores?** Para marcar y luego recuperar partes específicas de un documento.  
- **¿Puedo ocultar los marcadores en la salida final?** Sí—utilice la API show/hide para alternar su visibilidad.  
- **¿Cómo creo un marcador dentro de una celda de tabla?** Inicie y finalice el marcador con `DocumentBuilder` mientras el cursor está dentro de la celda.  
- **¿Es posible copiar texto marcado a otro documento?** Absolutamente—utilice `NodeImporter` para preservar el formato.  
- **¿Qué versión de Aspose.Words se requiere?** Cualquier versión reciente; el código funciona con la última compilación de 2026.

## ¿Qué es “show hide bookmarks”?

La función **show hide bookmarks** le permite mostrar u ocultar programáticamente los delimitadores de los marcadores en el documento guardado. Esto es útil cuando desea generar una salida limpia para los usuarios finales mientras conserva los datos de los marcadores para el procesamiento interno.

## ¿Por qué usar marcadores en la automatización de documentos Java?

- **Navegación eficiente** – Salte directamente a secciones sin escanear todo el archivo.  
- **Generación de contenido dinámico** – Inserte, reemplace o elimine texto vinculado a un marcador.  
- **Visibilidad condicional** – Muestre u oculte los marcadores según las preferencias del usuario o el formato de salida.  
- **Reutilización** – Copie fragmentos marcados entre documentos mientras preserva los estilos.

## Requisitos previos
- Java Development Kit (JDK) 8 o superior.  
- Biblioteca Aspose.Words para Java añadida a su proyecto (Maven/Gradle o JAR).  
- Familiaridad básica con las clases `Document` y `DocumentBuilder`.

## Guía paso a paso

### Paso 1: Crear un marcador (create bookmark java)

Para añadir un marcador, lo inicia, escribe el contenido y luego lo finaliza. Este ejemplo crea un marcador sencillo llamado **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Paso 2: Acceder a los marcadores (access bookmarks java)

Los marcadores pueden recuperarse tanto por su índice basado en cero como por nombre. El código a continuación muestra ambas aproximaciones.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Paso 3: Actualizar datos del marcador (update bookmark text)

Puede renombrar un marcador o reemplazar su contenido de texto. Esto es útil cuando el documento subyacente cambia.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Paso 4: Trabajar con texto marcado (copy bookmarked text)

Copiar un fragmento marcado a otro documento manteniendo el formato original es sencillo con `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Paso 5: Mostrar y ocultar marcadores (show hide bookmarks)

El siguiente fragmento muestra cómo ocultar los marcadores de un marcador en el archivo guardado. Pase `false` para ocultar, `true` para mostrar.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Paso 6: Desenredar marcadores de filas (bookmark table cell)

Cuando los marcadores abarcan filas de tabla, pueden enredarse. Los métodos utilitarios a continuación los desenredan y le permiten eliminar una fila específica mediante su marcador.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Problemas comunes y soluciones

| Problema | Solución |
|----------|----------|
| **Bookmark not found** | Verifique que el nombre del marcador coincida exactamente (sensible a mayúsculas/minúsculas) y que el documento se haya guardado después de su creación. |
| **Copied text loses formatting** | Use `ImportFormatMode.KEEP_SOURCE_FORMATTING` con `NodeImporter` como se muestra en el Paso 4. |
| **Show/hide does not affect output** | Asegúrese de llamar a `showHideBookmarkedContent` **antes** de guardar el documento. |
| **Bookmark inside a table cell is ignored** | Coloque las llamadas start/end mientras el cursor del builder está dentro de la celda objetivo. |

## Preguntas frecuentes

**Q:** ¿Cómo creo un marcador en una celda de tabla?  
**A:** Use `DocumentBuilder` para mover el cursor a la celda deseada, luego llame a `startBookmark` y `endBookmark` alrededor del contenido de la celda.

**Q:** ¿Puedo copiar un marcador a otro documento?  
**A:** Sí—use la clase `NodeImporter` (ver Paso 4) para importar el nodo marcado mientras preserva su formato original.

**Q:** ¿Cómo puedo eliminar una fila por su marcador?  
**A:** Primero localice la fila que contiene el marcador, luego llame a `remove` en el nodo de la fila (como se muestra en el Paso 6).

**Q:** ¿Cuáles son algunos casos de uso comunes para los marcadores?  
**A:** Generar una tabla de contenidos, extraer secciones específicas para informes y automatizar el ensamblaje de documentos basado en selecciones del usuario.

**Q:** ¿Dónde puedo encontrar más información sobre Aspose.Words para Java?  
**A:** Para documentación detallada y descargas, visite [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Última actualización:** 2026-01-11  
**Probado con:** Aspose.Words for Java 24.11 (2026)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}