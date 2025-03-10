---
title: Uso de opciones de carga en Aspose.Words para Java
linktitle: Uso de las opciones de carga
second_title: API de procesamiento de documentos Java Aspose.Words
description: Domine las opciones de carga en Aspose.Words para Java. Personalice la carga de documentos, administre el cifrado, convierta formas, establezca versiones de Word y más para un procesamiento eficiente de documentos Java.
weight: 11
url: /es/java/document-loading-and-saving/using-load-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uso de opciones de carga en Aspose.Words para Java


## Introducción al trabajo con opciones de carga en Aspose.Words para Java

En este tutorial, exploraremos cómo trabajar con las opciones de carga en Aspose.Words para Java. Las opciones de carga le permiten personalizar cómo se cargan y procesan los documentos. Cubriremos varios escenarios, incluida la actualización de campos sucios, la carga de documentos cifrados, la conversión de formas a Office Math, la configuración de la versión de MS Word, la especificación de una carpeta temporal, el manejo de advertencias y la conversión de metarchivos a PNG. Profundicemos paso a paso.

## Actualizar campos sucios

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

 Este fragmento de código demuestra cómo actualizar campos sucios en un documento.`setUpdateDirtyFields(true)` Se utiliza este método para garantizar que los campos sucios se actualicen durante la carga del documento.

## Cargar documento cifrado

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

 Aquí cargamos un documento cifrado mediante una contraseña.`LoadOptions` El constructor acepta la contraseña del documento y también puede especificar una nueva contraseña al guardar el documento usando`OdtSaveOptions`.

## Convertir forma a matemáticas de oficina

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

 Este código demuestra cómo convertir formas en objetos de Office Math durante la carga del documento.`setConvertShapeToOfficeMath(true)`El método permite esta conversión.

## Establecer la versión de MS Word

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

 Puede especificar la versión de MS Word para cargar el documento. En este ejemplo, configuramos la versión en Microsoft Word 2010 utilizando`setMswVersion`.

## Usar carpeta temporal

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

 Configurando la carpeta temporal usando`setTempFolder`Puede controlar dónde se almacenan los archivos temporales durante el procesamiento del documento.

## Advertencia de devolución de llamada

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Manejar las advertencias a medida que surgen durante la carga del documento.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Este código demuestra cómo configurar una devolución de llamada de advertencia para manejar las advertencias durante la carga del documento. Puede personalizar el comportamiento de su aplicación cuando se producen advertencias.

## Convertir metarchivos a PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

 Para convertir metarchivos (por ejemplo, WMF) a imágenes PNG durante la carga del documento, puede utilizar el`setConvertMetafilesToPng(true)` método.

## Código fuente completo para trabajar con opciones de carga en Aspose.Words para Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Cree un nuevo objeto LoadOptions, que cargará documentos de acuerdo con la especificación de MS Word 2019 de forma predeterminada
	// y cambiar la versión de carga a Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		//Imprime advertencias y sus detalles a medida que surgen durante la carga del documento.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Conclusión

En este tutorial, hemos profundizado en varios aspectos del trabajo con las opciones de carga en Aspose.Words para Java. Las opciones de carga desempeñan un papel fundamental a la hora de personalizar la forma en que se cargan y procesan los documentos, lo que le permite adaptar el procesamiento de los mismos a sus necesidades específicas. Recapitulemos los puntos clave tratados en esta guía:

## Preguntas frecuentes

### ¿Cómo puedo gestionar las advertencias durante la carga de documentos?

 Puede configurar una devolución de llamada de advertencia como se muestra en la`warningCallback()` Método anterior. Personaliza el`DocumentLoadingWarningCallback` clase para manejar advertencias según los requisitos de su aplicación.

### ¿Puedo convertir formas en objetos de Office Math al cargar un documento?

 Sí, puedes convertir formas en objetos de Office Math usando`loadOptions.setConvertShapeToOfficeMath(true)`.

### ¿Cómo especifico la versión de MS Word para cargar documentos?

 Usar`loadOptions.setMswVersion(MsWordVersion.WORD_2010)` para especificar la versión de MS Word para la carga de documentos.

###  ¿Cuál es el propósito de la`setTempFolder` method in Load Options?

 El`setTempFolder`El método le permite especificar la carpeta donde se almacenan los archivos temporales durante el procesamiento del documento.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
