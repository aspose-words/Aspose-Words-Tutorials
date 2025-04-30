---
"description": "Aprende a guardar documentos en formato OOXML con Aspose.Words para Java. Protege, optimiza y personaliza tus archivos fácilmente."
"linktitle": "Guardar documentos en formato OOXML"
"second_title": "API de procesamiento de documentos Java de Aspose.Words"
"title": "Guardar documentos en formato OOXML en Aspose.Words para Java"
"url": "/es/java/document-loading-and-saving/saving-documents-as-ooxml-format/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Guardar documentos en formato OOXML en Aspose.Words para Java


## Introducción al guardado de documentos en formato OOXML en Aspose.Words para Java

En esta guía, exploraremos cómo guardar documentos en formato OOXML con Aspose.Words para Java. OOXML (Office Open XML) es un formato de archivo utilizado por Microsoft Word y otras aplicaciones ofimáticas. Analizaremos diversas opciones y configuraciones para guardar documentos en formato OOXML.

## Prerrequisitos

Antes de comenzar, asegúrese de tener la biblioteca Aspose.Words para Java configurada en su proyecto.

## Guardar un documento con cifrado de contraseña

Puedes cifrar tu documento con una contraseña al guardarlo en formato OOXML. Así es como puedes hacerlo:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Cargar el documento
Document doc = new Document("Document.docx");

// Cree OoxmlSaveOptions y configure la contraseña
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Guardar el documento con cifrado
doc.save("EncryptedDoc.docx", saveOptions);
```

## Configuración de la conformidad con OOXML

Puede especificar el nivel de conformidad con OOXML al guardar el documento. Por ejemplo, puede configurarlo como ISO 29500:2008 (Estricto). A continuación, le explicamos cómo:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Cargar el documento
Document doc = new Document("Document.docx");

// Optimizar para Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Cree OoxmlSaveOptions y establezca el nivel de cumplimiento
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Guardar el documento con la configuración de cumplimiento
doc.save("ComplianceDoc.docx", saveOptions);
```

## Actualización de la última propiedad guardada

Puede optar por actualizar la propiedad "Última fecha de guardado" del documento al guardarlo. A continuación, le explicamos cómo:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Cargar el documento
Document doc = new Document("Document.docx");

// Cree OoxmlSaveOptions y habilite la actualización de la propiedad Última hora guardada
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Guarde el documento con la propiedad actualizada
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Manteniendo los personajes de control heredados

Si su documento contiene caracteres de control antiguos, puede conservarlos al guardarlo. A continuación, le explicamos cómo:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Cargar un documento con caracteres de control heredados
Document doc = new Document("LegacyControlChars.doc");

// Cree OoxmlSaveOptions con el formato FLAT_OPC y habilite el mantenimiento de caracteres de control heredados
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Guardar el documento con caracteres de control heredados
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Configuración del nivel de compresión

Puedes ajustar el nivel de compresión al guardar el documento. Por ejemplo, puedes configurarlo en SUPER_FAST para una compresión mínima. Así es como se hace:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Cargar el documento
Document doc = new Document("Document.docx");

// Cree OoxmlSaveOptions y configure el nivel de compresión
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Guarde el documento con el nivel de compresión especificado
doc.save("FastCompressionDoc.docx", saveOptions);
```

Estas son algunas de las opciones y configuraciones clave que puedes usar al guardar documentos en formato OOXML con Aspose.Words para Java. Explora más opciones y personaliza el proceso de guardado de documentos según tus necesidades.

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

En esta guía completa, hemos explorado cómo guardar documentos en formato OOXML con Aspose.Words para Java. Ya sea que necesite cifrar sus documentos con contraseñas, garantizar el cumplimiento de estándares OOXML específicos, actualizar las propiedades del documento, conservar caracteres de control antiguos o ajustar los niveles de compresión, Aspose.Words ofrece un conjunto versátil de herramientas para satisfacer sus necesidades.

## Preguntas frecuentes

### ¿Cómo puedo eliminar la protección con contraseña de un documento protegido con contraseña?

Para desproteger un documento con contraseña, puede abrirlo con la contraseña correcta y guardarlo sin especificarla en las opciones de guardado. Esto guardará el documento sin contraseña.

### ¿Puedo establecer propiedades personalizadas al guardar un documento en formato OOXML?

Sí, puedes configurar propiedades personalizadas para un documento antes de guardarlo en formato OOXML. Usa el `BuiltInDocumentProperties` y `CustomDocumentProperties` clases para establecer varias propiedades como autor, título, palabras clave y propiedades personalizadas.

### ¿Cuál es el nivel de compresión predeterminado al guardar un documento en formato OOXML?

El nivel de compresión predeterminado al guardar un documento en formato OOXML usando Aspose.Words para Java es `NORMAL`Puede cambiar el nivel de compresión a `SUPER_FAST` o `MAXIMUM` según sea necesario.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}