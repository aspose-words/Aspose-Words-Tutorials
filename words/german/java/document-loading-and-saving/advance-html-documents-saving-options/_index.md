---
date: 2025-12-19
description: Erfahren Sie, wie Sie HTML mit Aspose.Words Java exportieren, einschließlich
  fortgeschrittener Optionen zum Speichern von Word als HTML und zum effizienten Konvertieren
  von Word in HTML.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Wie man HTML mit Aspose.Words Java exportiert: Erweiterte Optionen'
url: /de/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wie man HTML mit Aspose.Words Java exportiert: Erweiterte Optionen

In diesem Tutorial erfahren Sie **wie man HTML** aus Word‑Dokumenten mit Aspose.Words für Java exportiert. Ob Sie **Word als HTML speichern** möchten, um es im Web zu veröffentlichen, oder **Word in HTML konvertieren** für nachgelagerte Verarbeitung – die erweiterten Speicheroptionen geben Ihnen feinkörnige Kontrolle über das Ergebnis. Wir gehen jede Option Schritt für Schritt durch, erklären, wann sie zu verwenden ist, und zeigen Praxis‑Szenarien, in denen diese Einstellungen einen Unterschied machen.

## Schnellantworten
- **Welche Klasse ist die primäre für den HTML‑Export?** `HtmlSaveOptions`  
- **Können Schriftarten direkt im HTML eingebettet werden?** Ja, setzen Sie `exportFontsAsBase64` auf `true`.  
- **Wie behalte ich Word‑spezifische Round‑Trip‑Daten?** Aktivieren Sie `exportRoundtripInformation`.  
- **Welches Format ist am besten für Vektorgrafiken?** Verwenden Sie `convertMetafilesToSvg` für SVG‑Ausgabe.  
- **Ist es möglich, Kollisionen von CSS‑Klassenamen zu vermeiden?** Ja, nutzen Sie `addCssClassNamePrefix`.

## 1. Einführung
Aspose.Words für Java ist eine robuste API, die Entwicklern ermöglicht, Word‑Dokumente programmgesteuert zu manipulieren. Dieser Leitfaden konzentriert sich auf die erweiterten HTML‑Speicheroptionen, mit denen Sie den Konvertierungsprozess an spezifische Web‑ oder Integrationsanforderungen anpassen können.

## 2. Round‑Trip‑Informationen exportieren
Das Beibehalten von Round‑Trip‑Informationen ermöglicht es, das HTML wieder in ein Word‑Dokument zu konvertieren, ohne Layout‑ oder Formatierungsdetails zu verlieren.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### Wann zu verwenden
- Wenn Sie eine reversible Konvertierungspipeline benötigen (HTML → Word → HTML).  
- Ideal für kollaborative Bearbeitungsszenarien, bei denen die ursprüngliche Word‑Struktur erhalten bleiben muss.

## 3. Schriftarten als Base64 exportieren
Das direkte Einbetten von Schriftarten in das HTML eliminiert externe Schriftabhängigkeiten und sorgt für visuelle Treue über alle Browser hinweg.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Profi‑Tipp
Verwenden Sie diese Option, wenn die Zielumgebung nur eingeschränkten Zugriff auf externe Ressourcen hat (z. B. E‑Mail‑Newsletter).

## 4. Ressourcen exportieren
Steuern Sie, wie CSS‑ und Schriftressourcen ausgegeben werden, und geben Sie einen benutzerdefinierten Ordner oder URL‑Alias für diese Assets an.

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

### Warum es wichtig ist
Das Auslagern von CSS in eine externe Datei reduziert die HTML‑Größe und ermöglicht Caching für schnellere Seitenladezeiten.

## 5. Metadateien in EMF oder WMF konvertieren
Metadateien (z. B. EMF/WMF) werden in ein Format konvertiert, das Browser zuverlässig rendern können.

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

### Anwendungsfall
Wählen Sie EMF/WMF, wenn die Ziel‑Browser diese Vektorformate unterstützen und Sie eine verlustfreie Skalierung benötigen.

## 6. Metadateien in SVG konvertieren
SVG bietet die beste Skalierbarkeit und wird von modernen Browsern breit unterstützt.

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

### Nutzen
SVG‑Dateien sind leichtgewichtig und halten das Dokument auflösungsunabhängig – perfekt für responsives Webdesign.

## 7. CSS‑Klassenname‑Präfix hinzufügen
Verhindern Sie Stilkonflikte, indem Sie allen generierten CSS‑Klassenamen ein Präfix voranstellen.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Praktischer Hinweis
Verwenden Sie ein eindeutiges Präfix (z. B. Ihren Projektnamen), wenn Sie das HTML in bestehende Seiten einbetten, um CSS‑Konflikte zu vermeiden.

## 8. CID‑URLs für MHTML‑Ressourcen exportieren
Beim Speichern als MHTML können Sie Ressourcen über Content‑ID‑URLs exportieren, was die E‑Mail‑Kompatibilität verbessert.

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

### Wann zu verwenden
Ideal zur Erzeugung einer einzigen, eigenständigen HTML‑Datei, die an E‑Mails angehängt werden kann.

## 9. Schriftartnamen auflösen
Stellt sicher, dass das HTML die korrekten Schriftfamilien referenziert und verbessert die plattformübergreifende Konsistenz.

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

### Warum es hilft
Verwendet das Originaldokument Schriftarten, die nicht auf dem Client‑Rechner installiert sind, ersetzt diese Option sie durch web‑sichere Alternativen.

## 10. Text‑Eingabefeld als Text exportieren
Rendert Formularfelder als Klartext statt als interaktive HTML‑Eingabeelemente.

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

### Anwendungsfall
Wenn Sie eine schreibgeschützte Darstellung eines Formulars für Archivierungs‑ oder Druckzwecke benötigen.

## Häufige Fallstricke & Fehlerbehebung
| Problem | Typische Ursache | Lösung |
|---------|------------------|--------|
| Fehlende Schriftarten in der Ausgabe | `exportFontsAsBase64` nicht aktiviert | Setzen Sie `setExportFontsAsBase64(true)` |
| Defektes CSS nach dem Einbetten | Verwendung von `EXTERNAL` ohne Bereitstellung der CSS‑Datei | Stellen Sie sicher, dass die CSS‑Datei unter dem angegebenen `resourceFolderAlias` bereitgestellt wird |
| Große HTML‑Größe | Einbetten vieler Bilder als Base64 | Wechseln Sie zu externen Bildressourcen über `setExportFontResources(true)` und konfigurieren Sie `resourceFolder` |
| SVG wird in älteren Browsern nicht dargestellt | Browser unterstützt SVG nicht | Stellen Sie ein PNG‑Fallback bereit, indem Sie ebenfalls als EMF/WMF exportieren |

## Häufig gestellte Fragen

**F: Kann ich sowohl Schriftarten als Base64 einbetten als auch externes CSS beibehalten?**  
A: Ja. Setzen Sie `exportFontsAsBase64(true)`, während Sie `CssStyleSheetType.EXTERNAL` beibehalten, um Schriftartdaten von den Stilregeln zu trennen.

**F: Wie konvertiere ich ein vorhandenes HTML zurück in ein Word‑Dokument?**  
A: Laden Sie das HTML mit `Document doc = new Document("input.html");` und speichern Sie dann `doc.save("output.docx");`. Bewahren Sie Round‑Trip‑Daten mithilfe von `exportRoundtripInformation` während des ersten Exports.

**F: Gibt es einen Performance‑Einfluss bei der SVG‑Konvertierung?**  
A: Das Konvertieren großer Metadateien zu SVG kann die Verarbeitungszeit erhöhen, aber das resultierende HTML ist in der Regel kleiner und rendert schneller in Browsern.

**F: Funktionieren diese Optionen auch mit Aspose.Words für .NET?**  
A: Die gleichen Konzepte existieren in der .NET‑API, obwohl sich die Methodennamen leicht unterscheiden können (z. B. `HtmlSaveOptions` ist plattformübergreifend gleich).

**F: Welche Option sollte ich für e‑Mail‑freundliches HTML wählen?**  
A: Verwenden Sie `SaveFormat.MHTML` mit `exportCidUrlsForMhtmlResources`, um alle Ressourcen direkt in den E‑Mail‑Body einzubetten.

---

**Zuletzt aktualisiert:** 2025-12-19  
**Getestet mit:** Aspose.Words für Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}