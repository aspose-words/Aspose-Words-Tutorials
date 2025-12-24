---
date: 2025-12-24
description: Aprenda a crear archivos de texto plano a partir de documentos Word usando
  Aspose.Words para Java. Esta guía muestra cómo convertir Word a txt, usar sangría
  con tabulaciones y guardar Word como txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Cómo crear un archivo de texto plano con Aspose.Words para Java
url: /es/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un archivo de texto plano con Aspose.Words para Java

## Introducción a la guardado de documentos como archivos de texto en Aspose.Words para Java

En este tutorial, aprenderás **cómo crear un archivo de texto plano** a partir de un documento Word usando la biblioteca Aspose.Words para Java. Ya sea que necesites **convertir word a txt**, automatizar la generación de informes, o simplemente extraer texto sin formato para su posterior procesamiento, esta guía te acompañará en todo el flujo de trabajo—desde la creación del documento hasta el ajuste fino de las opciones de guardado como **usar sangría con tabulaciones** o añadir marcas bidi. ¡Comencemos!

## Respuestas rápidas
- **¿Cuál es la clase principal para crear un documento?** `Document` de Aspose.Words.  
- **¿Qué opción añade marcas bidi para idiomas de derecha a izquierda?** `TxtSaveOptions.setAddBidiMarks(true)`.  
- **¿Cómo puedo sangrar los elementos de lista con tabulaciones?** Establece `ListIndentation.Character` a `'\t'`.  
- **¿Necesito una licencia para desarrollo?** Una prueba gratuita funciona para pruebas; se requiere una licencia para producción.  
- **¿Puedo guardar el archivo con un nombre y ruta personalizados?** Sí—pasa la ruta completa a `doc.save()`.

## Requisitos previos

Antes de comenzar, asegúrate de contar con los siguientes requisitos:

- Java Development Kit (JDK) instalado en tu sistema.  
- Biblioteca Aspose.Words para Java integrada en tu proyecto. Puedes descargarla desde [aquí](https://releases.aspose.com/words/java/).  
- Conocimientos básicos de programación en Java.

## Paso 1: Crear un documento

Para **guardar word como txt**, primero necesitamos una instancia de `Document`. A continuación se muestra un fragmento simple de Java que crea un documento y escribe algunas líneas de texto multilingüe:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

En este código creamos un nuevo documento, añadimos texto en inglés, hebreo y árabe, y habilitamos el formato de derecha a izquierda para el párrafo en hebreo.

## Paso 2: Definir opciones de guardado de texto

A continuación, configuramos cómo se guardará el documento como un archivo de texto plano. Aspose.Words proporciona la clase `TxtSaveOptions`, que permite controlar todo, desde marcas bidi hasta la sangría de listas.

### Ejemplo 1: Añadir marcas bidi (cómo guardar txt con soporte RTL adecuado)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Establecer `AddBidiMarks` en `true` garantiza que los caracteres de derecha a izquierda se representen correctamente en el **archivo de texto plano** resultante.

### Ejemplo 2: Usar carácter de tabulación para la sangría de listas (usar sangría con tabulaciones)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Aquí indicamos a Aspose.Words que anteponga un carácter de tabulación (`'\t'`) antes de cada nivel de lista, facilitando la lectura del texto de salida.

## Paso 3: Guardar el documento como texto

Ahora que las opciones de guardado están listas, puedes persistir el documento como un **archivo de texto plano**:

```java
doc.save("output.txt", saveOptions);
```

Reemplaza `"output.txt"` con la ruta completa donde deseas que se almacene el archivo.

## Código fuente completo para guardar documentos como archivos de texto en Aspose.Words para Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Problemas comunes y soluciones

| Problema | Solución |
|----------|----------|
| **Los caracteres bidi aparecen como texto corrupto** | Asegúrate de que `setAddBidiMarks(true)` esté habilitado y que el archivo de salida se abra con codificación UTF‑8. |
| **La sangría de la lista se ve incorrecta** | Verifica que `ListIndentation.Count` y `Character` estén configurados con los valores deseados (tab `'\t'` o espacio `' '` ). |
| **El archivo no se crea** | Comprueba que la ruta del directorio exista y que la aplicación tenga permisos de escritura. |

## Preguntas frecuentes

### ¿Cómo añado marcas bidi a la salida de texto?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### ¿Puedo personalizar el carácter de sangría de la lista?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### ¿Es Aspose.Words para Java adecuado para manejar texto multilingüe?

Sí, Aspose.Words para Java admite una amplia gama de idiomas y codificaciones de caracteres, lo que lo hace ideal para extraer y guardar contenido multilingüe como texto plano.

### ¿Cómo puedo acceder a más documentación y recursos para Aspose.Words para Java?

Puedes encontrar documentación completa y recursos en la página de documentación de Aspose.Words para Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### ¿Dónde puedo descargar Aspose.Words para Java?

Puedes descargar la biblioteca desde el sitio oficial: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### ¿Qué pasa si necesito **convertir word a txt** en un proceso por lotes?

Envuelve el código mostrado arriba en un bucle que cargue cada archivo `.docx`, aplique las mismas `TxtSaveOptions` y guarde cada uno como `.txt`. Asegúrate de gestionar los recursos disponiendo de los objetos `Document` después de cada iteración.

### ¿La API admite guardar directamente en un flujo en lugar de un archivo?

Sí, puedes pasar un `OutputStream` a `doc.save(outputStream, saveOptions)` para procesamiento en memoria o al integrarlo con servicios web.

---

**Última actualización:** 2025-12-24  
**Probado con:** Aspose.Words para Java 24.12 (última)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}