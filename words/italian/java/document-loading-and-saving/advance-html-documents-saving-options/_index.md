---
title: Opzioni avanzate di salvataggio dei documenti HTML con Aspose.Words Java
linktitle: Salvataggio di documenti HTML con
second_title: API di elaborazione dei documenti Java Aspose.Words
description: In questo tutorial, abbiamo trattato varie opzioni avanzate di salvataggio di documenti HTML con Aspose.Words per Java. Queste opzioni ti consentono di creare documenti HTML di alta qualità
weight: 16
url: /it/java/document-loading-and-saving/advance-html-documents-saving-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Opzioni avanzate di salvataggio dei documenti HTML con Aspose.Words Java


In questo tutorial, esploreremo le opzioni avanzate di salvataggio dei documenti HTML fornite da Aspose.Words per Java. Aspose.Words è una potente API Java per lavorare con i documenti Word e offre un'ampia gamma di funzionalità per la manipolazione e la conversione dei documenti.

## 1. Introduzione
Aspose.Words per Java consente di lavorare con i documenti Word a livello di programmazione. In questo tutorial, ci concentreremo sulle opzioni avanzate di salvataggio dei documenti HTML, che consentono di controllare il modo in cui i documenti Word vengono convertiti in HTML.

## 2. Esportazione delle informazioni di andata e ritorno
 IL`exportRoundtripInformation` metodo consente di esportare documenti Word in HTML preservando le informazioni di andata e ritorno. Queste informazioni possono essere utili quando si desidera riconvertire HTML in formato Word senza perdere alcun dettaglio specifico del documento.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Esporta i font come Base64
 Con il`exportFontsAsBase64` metodo, puoi esportare i font utilizzati nel documento come dati codificati in Base64 nell'HTML. Ciò assicura che la rappresentazione HTML mantenga gli stessi stili di font del documento Word originale.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Esportazione delle risorse
 IL`exportResources` metodo consente di specificare il tipo di foglio di stile CSS ed esportare risorse font. È anche possibile impostare una cartella di risorse e un alias per le risorse nell'HTML.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://esempio.com/risorse");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

## 5. Convertire i metafile in EMF o WMF
 IL`convertMetafilesToEmfOrWmf`Il metodo consente di convertire i metafile presenti nel documento nel formato EMF o WMF, garantendo compatibilità e un rendering fluido in HTML.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Punto rosso\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Convertire i metafile in SVG
 Utilizzare il`convertMetafilesToSvg` metodo per convertire i metafile in formato SVG. Questo formato è ideale per visualizzare la grafica vettoriale nei documenti HTML.

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

## 7. Aggiungi il prefisso del nome della classe CSS
 Con il`addCssClassNamePrefix` metodo, puoi aggiungere un prefisso ai nomi delle classi CSS nell'HTML esportato. Questo aiuta a prevenire conflitti con gli stili esistenti.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Esportare URL CID per risorse MHTML
 IL`exportCidUrlsForMhtmlResources` metodo viene utilizzato quando si salvano documenti in formato MHTML. Consente di esportare URL Content-ID per le risorse.

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

## 9. Risolvi i nomi dei font
 IL`resolveFontNames` Il metodo aiuta a risolvere i nomi dei font quando si salvano documenti in formato HTML, garantendo un rendering coerente su diverse piattaforme.

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

## 10. Esporta il campo del modulo di immissione testo come testo
 IL`exportTextInputFormFieldAsText`Il metodo esporta i campi del modulo come testo normale in HTML, rendendoli facilmente leggibili e modificabili.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// La cartella specificata deve esistere e deve essere vuota.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Imposta un'opzione per esportare i campi del modulo come testo normale, non come elementi di input HTML.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Conclusione
In questo tutorial, abbiamo esplorato le opzioni avanzate di salvataggio dei documenti HTML fornite da Aspose.Words per Java. Queste opzioni ti offrono un controllo dettagliato sul processo di conversione, consentendoti di creare documenti HTML che assomigliano molto ai documenti Word originali.

## Domande frequenti
Ecco alcune domande frequenti sull'utilizzo di Aspose.Words per Java e sulle opzioni di salvataggio dei documenti HTML:

### D1: Come posso riconvertire l'HTML nel formato Word utilizzando Aspose.Words per Java?
 Per convertire nuovamente l'HTML nel formato Word, puoi utilizzare le API di Aspose.Words`load` Metodo per caricare il documento HTML e poi salvarlo in formato Word.

### D2: Posso personalizzare gli stili CSS durante l'esportazione in HTML?
Sì, puoi personalizzare gli stili CSS modificando i fogli di stile utilizzati nell'HTML o utilizzando`addCssClassNamePrefix` Metodo per aggiungere un prefisso ai nomi delle classi CSS.

### D3: Esiste un modo per ottimizzare l'output HTML per la visualizzazione sul Web?
Sì, puoi ottimizzare l'output HTML per la visualizzazione sul Web configurando opzioni come l'esportazione dei font come Base64 e la conversione dei metafile in SVG.

### D4: Ci sono delle limitazioni quando si convertono documenti Word complessi in HTML?
Sebbene Aspose.Words per Java offra potenti capacità di conversione, i documenti Word complessi con layout intricati potrebbero richiedere un'ulteriore post-elaborazione per ottenere l'output HTML desiderato.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
