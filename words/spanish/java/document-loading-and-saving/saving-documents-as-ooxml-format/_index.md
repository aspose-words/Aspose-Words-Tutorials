---
date: 2026-01-09
description: Aprenda cómo cifrar archivos docx con contraseña y cambiar el nivel de
  compresión al guardar documentos en formato OOXML usando Aspose.Words para Java.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Cifrar docx con contraseña – Guardar OOXML con Aspose.Words Java
url: /es/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cifrar docx con contraseña – Guardar OOXML con Aspose.Words Java

## Introducción a la guardado de documentos en formato OOXML en Aspose.Words para Java

En esta guía, aprenderá cómo **cifrar docx con contraseña** y guardar documentos en formato OOXML usando Aspose.Words para Java. OOXML (Office Open XML) es el formato de archivo moderno utilizado por Microsoft Word y muchas otras aplicaciones de oficina. Recorreremos las opciones más comunes—protección con contraseña, niveles de cumplimiento, actualización de propiedades, manejo de caracteres de control heredados y **cómo cambiar el nivel de compresión**—para que pueda adaptar la salida a sus necesidades exactas.

## Respuestas rápidas
- **¿Cómo puedo proteger un archivo de Word?** Use `OoxmlSaveOptions.setPassword("yourPassword")` antes de guardar.  
- **¿Qué nivel de cumplimiento OOXML debo elegir?** ISO 29500 2008 Strict para máxima compatibilidad con versiones modernas de Office.  
- **¿Puedo conservar los caracteres de control heredados?** Sí, habilite `setKeepLegacyControlChars(true)`.  
- **¿Cómo cambio el nivel de compresión?** Establezca `setCompressionLevel(CompressionLevel.SUPER_FAST)` o `MAXIMUM` según sea necesario.  
- **¿Estas opciones afectan el tamaño del archivo?** El nivel de compresión y el manejo de caracteres heredados pueden cambiar notablemente el tamaño final del .docx.

## ¿Qué significa “cifrar docx con contraseña”?
Cifrar un archivo DOCX significa que el documento se guarda con cifrado AES‑256, requiriendo una contraseña para abrirlo en Word o cualquier visor compatible. Esto es esencial para proteger información confidencial cuando los archivos se comparten por correo electrónico, almacenamiento en la nube o portales internos.

## ¿Por qué usar opciones de guardado OOXML?
- **Seguridad:** La protección con contraseña impide el acceso no autorizado.  
- **Compatibilidad:** Los ajustes de cumplimiento garantizan que el archivo funcione en diferentes versiones de Word.  
- **Rendimiento:** Ajustar la compresión puede acelerar el guardado o reducir el tamaño del archivo.  
- **Preservación:** Mantener los caracteres de control heredados conserva la fidelidad al convertir documentos antiguos.

## Requisitos previos
- Biblioteca Aspose.Words para Java añadida a su proyecto (Maven/Gradle o JAR manual).  
- Java 8 o superior.  
- Un documento fuente (`.docx` o `.doc`) que desee procesar.

## Guardar un documento con cifrado de contraseña

Puede cifrar su documento con una contraseña mientras lo guarda en formato OOXML. Así es como se hace:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

> **Consejo profesional:** Elija una contraseña robusta y guárdela de forma segura; la contraseña no se puede recuperar del archivo cifrado.

## Establecer cumplimiento OOXML

Puede especificar el nivel de cumplimiento OOXML al guardar el documento. Por ejemplo, puede establecerlo en ISO 29500:2008 (Strict). Así es como:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## Actualizar la propiedad “Last Saved Time”

Puede elegir actualizar la propiedad “Last Saved Time” del documento al guardarlo. Así es como:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Conservar caracteres de control heredados

Si su documento contiene caracteres de control heredados, puede optar por conservarlos al guardarlo. Así es como:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Cómo cambiar el nivel de compresión al guardar OOXML

Puede ajustar el nivel de compresión al guardar el documento. Por ejemplo, puede establecerlo en `SUPER_FAST` para compresión mínima o `MAXIMUM` para el archivo más pequeño. Así es como:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

Estas son algunas de las opciones y configuraciones clave que puede usar al guardar documentos en formato OOXML con Aspose.Words para Java. Siéntase libre de explorar más opciones y personalizar su proceso de guardado según sea necesario.

## Código fuente completo para guardar documentos en formato OOXML en Aspose.Words para Java

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## Conclusión

En esta guía completa, hemos explorado cómo **cifrar docx con contraseña** y guardar documentos en formato OOXML usando Aspose.Words para Java. Ya sea que necesite proteger sus archivos, garantizar un cumplimiento estricto de OOXML, actualizar propiedades del documento, preservar caracteres de control heredados o **cambiar el nivel de compresión**, Aspose.Words ofrece un conjunto versátil de herramientas para satisfacer sus requisitos.

## Preguntas frecuentes

**P: ¿Cómo elimino la protección con contraseña de un documento protegido?**  
R: Abra el documento con la contraseña correcta y luego guárdelo sin especificar una contraseña en `OoxmlSaveOptions`. Esto crea una copia sin protección.

**P: ¿Puedo establecer propiedades personalizadas al guardar un documento en formato OOXML?**  
R: Sí. Use `BuiltInDocumentProperties` y `CustomDocumentProperties` en el objeto `Document` antes de llamar a `save()`.

**P: ¿Cuál es el nivel de compresión predeterminado al guardar un documento en formato OOXML?**  
R: El predeterminado es `CompressionLevel.NORMAL`. Puede cambiar a `SUPER_FAST` para mayor velocidad o a `MAXIMUM` para el tamaño de archivo más pequeño.

**P: ¿Afectará la habilitación de `keepLegacyControlChars` la compatibilidad con versiones modernas de Word?**  
R: Word moderno puede abrir archivos con caracteres de control heredados, pero algunas funciones antiguas pueden mostrarse de forma diferente. Use esta opción solo cuando necesite preservar el contenido original exacto.

**P: ¿Es posible combinar múltiples opciones de guardado (p. ej., contraseña + compresión) en una sola llamada?**  
R: Absolutamente. Configure todas las propiedades deseadas en una única instancia de `OoxmlSaveOptions` antes de pasarla a `doc.save()`.

---

**Última actualización:** 2026-01-09  
**Probado con:** Aspose.Words para Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}