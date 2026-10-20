---
date: 2025-12-27
description: Aprenda cómo establecer LoadOptions en Aspose.Words para Java, incluyendo
  cómo especificar la carpeta temporal, establecer la versión de Word, convertir metarchivos
  a PNG y convertir formas a ecuaciones para un procesamiento flexible de documentos.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Cómo establecer LoadOptions en Aspose.Words para Java
url: /es/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer LoadOptions en Aspose.Words para Java

En este tutorial recorreremos **cómo establecer LoadOptions** para una variedad de escenarios del mundo real al trabajar con Aspose.Words para Java. LoadOptions le brinda un control granular sobre la forma en que se abre un documento: ya sea que necesite actualizar campos sucios, trabajar con archivos cifrados, convertir formas a Office Math o indicar a la biblioteca dónde almacenar datos temporales. Al final podrá personalizar el comportamiento de carga para que coincida exactamente con los requisitos de su aplicación.

## Respuestas rápidas
- **¿Qué es LoadOptions?** Un objeto de configuración que influye en cómo Aspose.Words carga un documento.  
- **¿Puedo actualizar campos durante la carga?** Sí—establezca `setUpdateDirtyFields(true)`.  
- **¿Cómo abro un archivo protegido con contraseña?** Pase la contraseña al constructor de `LoadOptions`.  
- **¿Es posible cambiar la carpeta temporal?** Use `setTempFolder("path")`.  
- **¿Qué método convierte formas a Office Math?** `setConvertShapeToOfficeMath(true)`.

## ¿Por qué usar LoadOptions?
LoadOptions le permite evitar pasos de procesamiento posteriores a la carga, reducir el uso de memoria y garantizar que el documento se interprete exactamente como lo necesita. Por ejemplo, convertir metafiles a PNG durante la carga evita problemas de rasterización posteriores, y especificar la versión de MS Word ayuda a mantener la fidelidad del diseño al trabajar con archivos heredados.

## Requisitos previos
- Java 17 o posterior  
- Aspose.Words para Java (última versión)  
- Una licencia válida de Aspose para uso en producción  

## Guía paso a paso

### Actualizar campos sucios

Cuando un documento contiene campos que se han editado pero no se han actualizado, puede indicar a Aspose.Words que los actualice automáticamente durante la carga.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*La llamada `setUpdateDirtyFields(true)` garantiza que cualquier campo sucio se recalcula en cuanto se abre el documento.*

### Cargar documento cifrado

Si su archivo de origen está protegido con contraseña, proporcione la contraseña al crear la instancia de `LoadOptions`. También puede establecer una nueva contraseña al guardar en un formato diferente.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Convertir forma a Office Math

Algunos documentos heredados almacenan ecuaciones como formas de dibujo. Habilitar esta opción convierte esas formas en objetos nativos de Office Math, que son más fáciles de editar posteriormente.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### Establecer versión de MS Word

Especificar la versión de Word objetivo ayuda a la biblioteca a elegir las reglas de renderizado correctas, especialmente al trabajar con formatos de archivo más antiguos.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Usar carpeta temporal

Los documentos grandes pueden generar archivos temporales (p. ej., al extraer imágenes). Puede dirigir esos archivos a una carpeta de su elección, lo que resulta útil en entornos aislados.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Callback de advertencias

Durante la carga, Aspose.Words puede generar advertencias (p. ej., características no compatibles). Implementar un callback le permite registrar o reaccionar a estos eventos.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Convertir metafiles a PNG

Metafiles como WMF pueden rasterizarse a PNG durante la carga, garantizando una renderización coherente en todas las plataformas.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Código fuente completo para trabajar con Load Options en Aspose.Words para Java

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
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
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
		// Prints warnings and their details as they arise during document loading.
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

## Casos de uso comunes y consejos

- **Pipelines de conversión por lotes** – Combine `setTempFolder` con un trabajo programado para procesar cientos de archivos sin llenar el directorio temporal del sistema.  
- **Migración de documentos heredados** – Use `setMswVersion` junto con `setConvertShapeToOfficeMath` para llevar documentos de ingeniería antiguos a un formato moderno manteniendo las ecuaciones.  
- **Manejo seguro de documentos** – Combine `loadEncryptedDocument` con `OdtSaveOptions` para volver a cifrar archivos con una nueva contraseña en un formato diferente.  

## Preguntas frecuentes

**P: ¿Cómo puedo manejar advertencias durante la carga del documento?**  
R: Implemente un `IWarningCallback` personalizado (como se muestra en el ejemplo de *Callback de advertencias*) y regístrelo mediante `loadOptions.setWarningCallback(...)`. Esto le permite registrar, ignorar o abortar según la gravedad de la advertencia.

**P: ¿Puedo convertir formas a objetos Office Math al cargar un documento?**  
R: Sí—llame a `loadOptions.setConvertShapeToOfficeMath(true)` antes de crear el `Document`. La biblioteca reemplazará automáticamente las formas compatibles por objetos nativos de Office Math.

**P: ¿Cómo especifico la versión de MS Word para la carga del documento?**  
R: Use `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (u otro valor del enum) para indicar a Aspose.Words qué reglas de renderizado de Word aplicar.

**P: ¿Cuál es el propósito del método `setTempFolder` en LoadOptions?**  
R: Dirige todos los archivos temporales generados durante la carga (como imágenes extraídas) a una carpeta que usted controla, lo cual es esencial en entornos con directorios temporales restringidos.

**P: ¿Es posible convertir metafiles como WMF a PNG durante la carga?**  
R: Absolutamente—actívelo con `loadOptions.setConvertMetafilesToPng(true)`. Esto asegura que las imágenes rasterizadas se almacenen como PNG, mejorando la compatibilidad con visores modernos.

## Conclusión

Hemos cubierto las técnicas esenciales para **cómo establecer LoadOptions** en Aspose.Words para Java, desde actualizar campos sucios hasta manejar archivos cifrados, convertir formas, especificar la versión de Word, dirigir el almacenamiento temporal y más. Al aprovechar estas opciones, puede crear pipelines de procesamiento de documentos robustos y de alto rendimiento que se adapten a una amplia gama de escenarios de entrada.

---

**Última actualización:** 2025-12-27  
**Probado con:** Aspose.Words para Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}