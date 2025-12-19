---
date: 2025-12-19
description: Aprenda cómo exportar HTML con Aspose.Words Java, cubriendo opciones
  avanzadas para guardar Word como HTML y convertir Word a HTML de manera eficiente.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Cómo exportar HTML con Aspose.Words Java: opciones avanzadas'
url: /es/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cómo exportar HTML con Aspose.Words Java: Opciones avanzadas

En este tutorial descubrirá **cómo exportar HTML** desde documentos Word usando Aspose.Words para Java. Ya sea que necesite **guardar Word como HTML** para publicación web o **convertir Word a HTML** para procesamiento posterior, las opciones avanzadas de guardado le brindan un control granular sobre la salida. Recorreremos cada opción paso a paso, explicaremos cuándo usarla y mostraremos escenarios del mundo real donde estas configuraciones marcan la diferencia.

## Respuestas rápidas
- **¿Cuál es la clase principal para la exportación a HTML?** `HtmlSaveOptions`  
- **¿Se pueden incrustar fuentes directamente en el HTML?** Sí, establezca `exportFontsAsBase64` a `true`.  
- **¿Cómo mantengo los datos de ida y vuelta específicos de Word?** Active `exportRoundtripInformation`.  
- **¿Qué formato es mejor para gráficos vectoriales?** Use `convertMetafilesToSvg` para salida SVG.  
- **¿Es posible evitar colisiones de nombres de clases CSS?** Sí, use `addCssClassNamePrefix`.

## 1. Introducción
Aspose.Words para Java es una API robusta que permite a los desarrolladores manipular documentos Word de forma programática. Esta guía se centra en las opciones avanzadas de guardado de documentos HTML que le permiten adaptar el proceso de conversión para cumplir requisitos web o de integración específicos.

## 2. Exportar información de ida y vuelta
Preservar la información de ida y vuelta le permite convertir el HTML de nuevo a un documento Word sin perder detalles de diseño o formato.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### Cuándo usar
- Cuando necesita una canalización de conversión reversible (HTML → Word → HTML).  
- Ideal para escenarios de edición colaborativa donde se debe conservar la estructura original de Word.

## 3. Exportar fuentes como Base64
Incrustar fuentes directamente en el HTML elimina dependencias externas de fuentes y garantiza la fidelidad visual en todos los navegadores.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Consejo
Utilice esta opción cuando el entorno de destino tenga acceso limitado a recursos externos (p. ej., boletines de correo electrónico).

## 4. Exportar recursos
Controle cómo se emiten los recursos CSS y de fuentes, y especifique una carpeta o alias de URL personalizado para esos activos.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

### Por qué es importante
Separar CSS en un archivo externo reduce el tamaño del HTML y permite el almacenamiento en caché para cargas de página más rápidas.

## 5. Convertir Metafiles a EMF o WMF
Los metafiles (p. ej., EMF/WMF) se convierten a un formato que los navegadores pueden renderizar de forma fiable.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n                    vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

### Caso de uso
Elija EMF/WMF cuando los navegadores de destino admitan estos formatos vectoriales y necesite escalado sin pérdida.

## 6. Convertir Metafiles a SVG
SVG ofrece la mejor escalabilidad y es ampliamente compatible con los navegadores modernos.

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

### Beneficio
Los archivos SVG son ligeros y mantienen la independencia de resolución del documento, perfectos para diseño web responsivo.

## 7. Añadir prefijo a nombres de clases CSS
Prevenga colisiones de estilos añadiendo un prefijo a todos los nombres de clases CSS generados.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Consejo práctico
Utilice un prefijo único (p. ej., el nombre de su proyecto) al incrustar el HTML en páginas existentes para evitar conflictos de CSS.

## 8. Exportar URLs CID para recursos MHTML
Al guardar como MHTML, puede exportar recursos usando URLs Content‑ID para una mejor compatibilidad con correo electrónico.

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

### Cuándo usar
Ideal para generar un único archivo HTML autocontenido que pueda adjuntarse a correos electrónicos.

## 9. Resolver nombres de fuentes
Garantiza que el HTML haga referencia a las familias de fuentes correctas, mejorando la consistencia entre plataformas.

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

### Por qué ayuda
Si el documento original usa fuentes que no están instaladas en la máquina del cliente, esta opción las sustituye por alternativas web‑seguras.

## 10. Exportar campo de formulario de entrada de texto como texto
Renderiza los campos de formulario como texto plano en lugar de elementos interactivos de entrada HTML.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// The folder specified needs to exist and should be empty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Set an option to export form fields as plain text, not as HTML input elements.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

### Caso de uso
Cuando necesita una representación de solo lectura de un formulario para fines de archivo o impresión.

## Problemas comunes y solución de problemas
| Problema | Causa típica | Solución |
|----------|--------------|----------|
| Fuentes faltantes en la salida | `exportFontsAsBase64` no está habilitado | Establezca `setExportFontsAsBase64(true)` |
| CSS roto después de incrustar | Uso de `EXTERNAL` sin proporcionar el archivo CSS | Asegúrese de que el archivo CSS esté desplegado en el `resourceFolderAlias` especificado |
| Tamaño grande de HTML | Incrustar muchas imágenes como Base64 | Cambie a recursos de imagen externos mediante `setExportFontResources(true)` y configure `resourceFolder` |
| SVG no se renderiza en navegadores antiguos | El navegador no admite SVG | Proporcione PNG de respaldo exportando también como EMF/WMF |

## Preguntas frecuentes

**P: ¿Puedo incrustar fuentes como Base64 y mantener CSS externo?**  
R: Sí. Establezca `exportFontsAsBase64(true)` mientras mantiene `CssStyleSheetType.EXTERNAL` para separar los datos de fuentes de las reglas de estilo.

**P: ¿Cómo convierto un HTML existente de nuevo a un documento Word?**  
R: Cargue el HTML con `Document doc = new Document("input.html");` y luego `doc.save("output.docx");`. Preserve los datos de ida y vuelta usando `exportRoundtripInformation` durante la exportación inicial.

**P: ¿Hay impacto de rendimiento al usar la conversión a SVG?**  
R: Convertir metafiles grandes a SVG puede aumentar el tiempo de procesamiento, pero el HTML resultante suele ser más pequeño y se renderiza más rápido en los navegadores.

**P: ¿Estas opciones funcionan también con Aspose.Words para .NET?**  
R: Los mismos conceptos existen en la API .NET, aunque los nombres de los métodos pueden variar ligeramente (p. ej., `HtmlSaveOptions` se comparte entre plataformas).

**P: ¿Qué opción debo elegir para HTML apto para correo electrónico?**  
R: Use `SaveFormat.MHTML` con `exportCidUrlsForMhtmlResources` para incrustar todos los recursos directamente en el cuerpo del correo.

---

**Última actualización:** 2025-12-19  
**Probado con:** Aspose.Words para Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}