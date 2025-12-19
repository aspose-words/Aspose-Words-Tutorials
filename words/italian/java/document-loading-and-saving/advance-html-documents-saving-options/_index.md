---
date: 2025-12-19
description: Scopri come esportare HTML con Aspose.Words Java, coprendo le opzioni
  avanzate per salvare Word come HTML e convertire Word in HTML in modo efficiente.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Come esportare HTML con Aspose.Words Java: opzioni avanzate'
url: /it/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Come esportare HTML con Aspose.Words Java: Opzioni avanzate

In questo tutorial scoprirai **come esportare HTML** da documenti Word usando Aspose.Words per Java. Che tu debba **salvare Word come HTML** per la pubblicazione web o **convertire Word in HTML** per elaborazioni successive, le opzioni di salvataggio avanzate ti offrono un controllo dettagliato sull'output. Percorreremo ogni opzione passo‑per‑passo, spiegheremo quando usarla e mostreremo scenari reali in cui queste impostazioni fanno la differenza.

## Risposte rapide
- **Qual è la classe principale per l'esportazione HTML?** `HtmlSaveOptions`  
- **È possibile incorporare i font direttamente nell'HTML?** Sì, impostare `exportFontsAsBase64` su `true`.  
- **Come mantenere i dati round‑trip specifici di Word?** Abilitare `exportRoundtripInformation`.  
- **Quale formato è migliore per la grafica vettoriale?** Usare `convertMetafilesToSvg` per l'output SVG.  
- **È possibile evitare collisioni di nomi di classi CSS?** Sì, usare `addCssClassNamePrefix`.

## 1. Introduzione
Aspose.Words per Java è un'API robusta che consente agli sviluppatori di manipolare i documenti Word programmaticamente. Questa guida si concentra sulle opzioni avanzate di salvataggio dei documenti HTML che ti permettono di personalizzare il processo di conversione per soddisfare requisiti web o di integrazione specifici.

## 2. Esporta informazioni round‑trip
Preservare le informazioni round‑trip consente di convertire l'HTML nuovamente in un documento Word senza perdere dettagli di layout o formattazione.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### Quando usarlo
- Quando è necessario un flusso di conversione reversibile (HTML → Word → HTML).  
- Ideale per scenari di editing collaborativo in cui la struttura originale di Word deve essere conservata.

## 3. Esporta font come Base64
Incorporare i font direttamente nell'HTML elimina le dipendenze da font esterni e garantisce la fedeltà visiva su tutti i browser.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Consiglio professionale
Usa questa opzione quando l'ambiente di destinazione ha accesso limitato a risorse esterne (ad es., newsletter email).

## 4. Esporta risorse
Controlla come vengono emessi i CSS e le risorse dei font, e specifica una cartella o un alias URL personalizzato per tali asset.

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

### Perché è importante
Separare il CSS in un file esterno riduce la dimensione dell'HTML e consente il caching per caricamenti di pagina più rapidi.

## 5. Converti metafile in EMF o WMF
I metafile (ad es., EMF/WMF) vengono convertiti in un formato che i browser possono renderizzare in modo affidabile.

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

### Caso d'uso
Scegli EMF/WMF quando i browser di destinazione supportano questi formati vettoriali e hai bisogno di una scalatura senza perdita.

## 6. Converti metafile in SVG
SVG offre la migliore scalabilità ed è ampiamente supportato dai browser moderni.

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

### Vantaggio
I file SVG sono leggeri e mantengono il documento indipendente dalla risoluzione, perfetti per il design web responsivo.

## 7. Aggiungi prefisso al nome della classe CSS
Previeni i conflitti di stile aggiungendo un prefisso a tutti i nomi di classe CSS generati.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Suggerimento pratico
Usa un prefisso unico (ad es., il nome del tuo progetto) quando incorpori l'HTML in pagine esistenti per evitare conflitti CSS.

## 8. Esporta URL CID per risorse MHTML
Quando si salva come MHTML, è possibile esportare le risorse usando URL Content‑ID per una migliore compatibilità con le email.

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

### Quando usarlo
Ideale per generare un unico file HTML autonomo che può essere allegato alle email.

## 9. Risolvi i nomi dei font
Assicura che l'HTML faccia riferimento alle famiglie di font corrette, migliorando la coerenza tra piattaforme.

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

### Perché è utile
Se il documento originale utilizza font non installati sul client, questa opzione li sostituisce con alternative web‑safe.

## 10. Esporta campo di input del modulo come testo
Rendi i campi del modulo come testo semplice invece di elementi di input HTML interattivi.

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

### Caso d'uso
Quando è necessaria una rappresentazione di sola lettura di un modulo per scopi di archiviazione o stampa.

## Problemi comuni e risoluzione
| Problema | Causa tipica | Soluzione |
|----------|--------------|-----------|
| Font mancanti nell'output | `exportFontsAsBase64` non abilitato | Impostare `setExportFontsAsBase64(true)` |
| CSS interrotto dopo l'incorporamento | Uso di `EXTERNAL` senza fornire il file CSS | Assicurarsi che il file CSS sia distribuito nella `resourceFolderAlias` specificata |
| Dimensione HTML grande | Incorporamento di molte immagini come Base64 | Passare a risorse immagine esterne tramite `setExportFontResources(true)` e configurare `resourceFolder` |
| SVG non renderizzato nei browser più vecchi | Il browser non supporta SVG | Fornire un PNG di fallback esportando anche come EMF/WMF |

## Domande frequenti

**Q: Posso sia incorporare i font come Base64 sia mantenere il CSS esterno?**  
A: Sì. Impostare `exportFontsAsBase64(true)` mantenendo `CssStyleSheetType.EXTERNAL` per separare i dati dei font dalle regole di stile.

**Q: Come converto un HTML esistente nuovamente in un documento Word?**  
A: Caricare l'HTML con `Document doc = new Document("input.html");` e poi `doc.save("output.docx");`. Conservare i dati round‑trip usando `exportRoundtripInformation` durante l'esportazione iniziale.

**Q: C'è un impatto sulle prestazioni quando si usa la conversione SVG?**  
A: Convertire metafile di grandi dimensioni in SVG può aumentare il tempo di elaborazione, ma l'HTML risultante è tipicamente più piccolo e si rende più velocemente nei browser.

**Q: Queste opzioni funzionano anche con Aspose.Words per .NET?**  
A: Gli stessi concetti esistono nell'API .NET, sebbene i nomi dei metodi possano differire leggermente (ad es., `HtmlSaveOptions` è condiviso tra le piattaforme).

**Q: Quale opzione dovrei scegliere per un HTML adatto alle email?**  
A: Usare `SaveFormat.MHTML` con `exportCidUrlsForMhtmlResources` per incorporare tutte le risorse direttamente nel corpo dell'email.

**Last Updated:** 2025-12-19  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}