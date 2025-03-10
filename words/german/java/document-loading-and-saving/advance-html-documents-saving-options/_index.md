---
title: Erweiterte Speicheroptionen für HTML-Dokumente mit Aspose.Words Java
linktitle: Speichern von HTML-Dokumenten mit
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: In diesem Tutorial haben wir verschiedene erweiterte Optionen zum Speichern von HTML-Dokumenten mit Aspose.Words für Java behandelt. Mit diesen Optionen können Sie hochwertige HTML-Dokumente erstellen
weight: 16
url: /de/java/document-loading-and-saving/advance-html-documents-saving-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erweiterte Speicheroptionen für HTML-Dokumente mit Aspose.Words Java


In diesem Tutorial erkunden wir die erweiterten Speicheroptionen für HTML-Dokumente, die Aspose.Words für Java bietet. Aspose.Words ist eine leistungsstarke Java-API für die Arbeit mit Word-Dokumenten und bietet eine breite Palette an Funktionen zur Dokumentbearbeitung und -konvertierung.

## 1. Einleitung
Mit Aspose.Words für Java können Sie programmgesteuert mit Word-Dokumenten arbeiten. In diesem Tutorial konzentrieren wir uns auf erweiterte Optionen zum Speichern von HTML-Dokumenten, mit denen Sie steuern können, wie Word-Dokumente in HTML konvertiert werden.

## 2. Roundtrip-Informationen exportieren
 Der`exportRoundtripInformation` Mit dieser Methode können Sie Word-Dokumente unter Beibehaltung der Roundtrip-Informationen in HTML exportieren. Diese Informationen können nützlich sein, wenn Sie HTML wieder in das Word-Format konvertieren möchten, ohne dokumentspezifische Details zu verlieren.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Schriftarten als Base64 exportieren
 Mit dem`exportFontsAsBase64` Mit dieser Methode können Sie die im Dokument verwendeten Schriftarten als Base64-codierte Daten in HTML exportieren. Dadurch wird sichergestellt, dass die HTML-Darstellung dieselben Schriftstile wie das ursprüngliche Word-Dokument beibehält.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Ressourcen exportieren
 Der`exportResources` Mit dieser Methode können Sie den Typ des CSS-Stylesheets angeben und Schriftressourcen exportieren. Sie können auch einen Ressourcenordner und einen Alias für Ressourcen im HTML festlegen.

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

## 5. Konvertieren Sie Metadateien in EMF oder WMF
 Der`convertMetafilesToEmfOrWmf`Mit dieser Methode können Sie Metadateien im Dokument entweder in das EMF- oder das WMF-Format konvertieren und so Kompatibilität und reibungslose Darstellung in HTML sicherstellen.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Metadateien in SVG konvertieren
 Verwenden Sie die`convertMetafilesToSvg` Methode zum Konvertieren von Metadateien in das SVG-Format. Dieses Format eignet sich ideal für die Anzeige von Vektorgrafiken in HTML-Dokumenten.

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

## 7. Fügen Sie ein CSS-Klassennamenpräfix hinzu
 Mit dem`addCssClassNamePrefix` können Sie den CSS-Klassennamen im exportierten HTML ein Präfix hinzufügen. Dadurch werden Konflikte mit vorhandenen Stilen vermieden.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. CID-URLs für MHTML-Ressourcen exportieren
 Der`exportCidUrlsForMhtmlResources` Die Methode wird beim Speichern von Dokumenten im MHTML-Format verwendet. Sie ermöglicht den Export von Content-ID-URLs für Ressourcen.

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

## 9. Schriftnamen auflösen
 Der`resolveFontNames` Die Methode hilft beim Auflösen von Schriftnamen beim Speichern von Dokumenten im HTML-Format und gewährleistet so eine konsistente Darstellung auf verschiedenen Plattformen.

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

## 10. Texteingabeformularfeld als Text exportieren
 Der`exportTextInputFormFieldAsText`Methode exportiert Formularfelder als einfachen Text in HTML, sodass sie leicht lesbar und bearbeitbar sind.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// Der angegebene Ordner muss vorhanden sein und sollte leer sein.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Legen Sie eine Option fest, um Formularfelder als einfachen Text und nicht als HTML-Eingabeelemente zu exportieren.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Abschluss
In diesem Tutorial haben wir die erweiterten Speicheroptionen für HTML-Dokumente untersucht, die Aspose.Words für Java bietet. Diese Optionen geben Ihnen eine detaillierte Kontrolle über den Konvertierungsprozess und ermöglichen Ihnen die Erstellung von HTML-Dokumenten, die den ursprünglichen Word-Dokumenten sehr ähnlich sind.

## Häufig gestellte Fragen
Hier sind einige häufig gestellte Fragen zur Arbeit mit Aspose.Words für Java- und HTML-Dokumentspeicheroptionen:

### F1: Wie kann ich HTML mit Aspose.Words für Java wieder in das Word-Format konvertieren?
 Um HTML wieder in das Word-Format zu konvertieren, können Sie die Aspose.Words API verwenden`load` Methode, um das HTML-Dokument zu laden und es dann im Word-Format zu speichern.

### F2: Kann ich die CSS-Stile beim Exportieren nach HTML anpassen?
Ja, Sie können CSS-Stile anpassen, indem Sie die im HTML verwendeten Stylesheets ändern oder indem Sie`addCssClassNamePrefix` Methode zum Hinzufügen eines Präfixes zu CSS-Klassennamen.

### F3: Gibt es eine Möglichkeit, die HTML-Ausgabe für die Anzeige im Web zu optimieren?
Ja, Sie können die HTML-Ausgabe für die Anzeige im Web optimieren, indem Sie Optionen wie das Exportieren von Schriftarten als Base64 und das Konvertieren von Metadateien in SVG konfigurieren.

### F4: Gibt es Einschränkungen bei der Konvertierung komplexer Word-Dokumente in HTML?
Während Aspose.Words für Java leistungsstarke Konvertierungsfunktionen bietet, erfordern komplexe Word-Dokumente mit komplizierten Layouts möglicherweise eine zusätzliche Nachbearbeitung, um die gewünschte HTML-Ausgabe zu erzielen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
