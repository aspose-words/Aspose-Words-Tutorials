---
date: 2025-12-27
description: Scopri come impostare LoadOptions in Aspose.Words per Java, inclusa la
  specifica della cartella temporanea, l'impostazione della versione di Word, la conversione
  dei metafili in PNG e la conversione di forme in formule matematiche per una gestione
  flessibile dei documenti.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Come impostare LoadOptions in Aspose.Words per Java
url: /it/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Come impostare LoadOptions in Aspose.Words per Java

In questo tutorial vedremo **come impostare LoadOptions** per una varietà di scenari reali quando si lavora con Aspose.Words per Java. LoadOptions ti offrono un controllo dettagliato sul modo in cui un documento viene aperto — sia che tu debba aggiornare i campi sporchi, lavorare con file crittografati, convertire forme in Office Math o indicare alla libreria dove memorizzare i dati temporanei. Alla fine sarai in grado di personalizzare il comportamento di caricamento per soddisfare esattamente i requisiti della tua applicazione.

## Risposte rapide
- **Che cosa è LoadOptions?** Un oggetto di configurazione che influenza il modo in cui Aspose.Words carica un documento.  
- **Posso aggiornare i campi durante il caricamento?** Sì — imposta `setUpdateDirtyFields(true)`.  
- **Come apro un file protetto da password?** Passa la password al costruttore di `LoadOptions`.  
- **È possibile cambiare la cartella temporanea?** Usa `setTempFolder("path")`.  
- **Quale metodo converte le forme in Office Math?** `setConvertShapeToOfficeMath(true)`.

## Perché usare LoadOptions?
LoadOptions ti consentono di evitare passaggi di elaborazione post‑caricamento, ridurre l’utilizzo di memoria e garantire che il documento venga interpretato esattamente come desideri. Ad esempio, convertire i metafile in PNG durante il caricamento evita problemi di rasterizzazione successivi, e specificare la versione di MS Word aiuta a mantenere la fedeltà del layout quando si trattano file legacy.

## Prerequisiti
- Java 17 o versioni successive  
- Aspose.Words per Java (ultima versione)  
- Una licenza valida di Aspose per l’uso in produzione  

## Guida passo‑passo

### Aggiornare i campi sporchi

Quando un documento contiene campi modificati ma non aggiornati, puoi far sì che Aspose.Words li aggiorni automaticamente durante il caricamento.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*La chiamata `setUpdateDirtyFields(true)` assicura che tutti i campi sporchi vengano ricalcolati non appena il documento viene aperto.*

### Caricare un documento crittografato

Se il tuo file di origine è protetto da password, fornisci la password quando crei l’istanza di `LoadOptions`. Puoi anche impostare una nuova password quando salvi in un formato diverso.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Convertire forma in Office Math

Alcuni documenti legacy memorizzano le equazioni come forme disegnate. Abilitare questa opzione converte tali forme in oggetti Office Math nativi, più facili da modificare in seguito.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### Impostare la versione di MS Word

Specificare la versione di Word di destinazione aiuta la libreria a scegliere le regole di rendering corrette, soprattutto quando si trattano formati di file più vecchi.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Utilizzare una cartella temporanea

Documenti di grandi dimensioni possono generare file temporanei (ad esempio durante l’estrazione di immagini). Puoi indirizzare questi file verso una cartella a tua scelta, utile per ambienti sandbox.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Callback di avviso

Durante il caricamento, Aspose.Words può generare avvisi (ad es., funzionalità non supportate). Implementare un callback ti consente di registrare o reagire a questi eventi.

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

### Convertire metafile in PNG

Metafile come WMF possono essere rasterizzate in PNG durante il caricamento, garantendo una resa coerente su tutte le piattaforme.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Codice sorgente completo per lavorare con LoadOptions in Aspose.Words per Java

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

## Casi d'uso comuni e consigli

- **Pipeline di conversione batch** – Combina `setTempFolder` con un job pianificato per elaborare centinaia di file senza riempire la directory temporanea di sistema.  
- **Migrazione di documenti legacy** – Usa `setMswVersion` insieme a `setConvertShapeToOfficeMath` per portare vecchi documenti tecnici in un formato moderno preservando le equazioni.  
- **Gestione sicura dei documenti** – Accoppia `loadEncryptedDocument` con `OdtSaveOptions` per ricrittografare i file con una nuova password in un formato diverso.  

## Domande frequenti

**D: Come posso gestire gli avvisi durante il caricamento del documento?**  
R: Implementa un `IWarningCallback` personalizzato (come mostrato nell’esempio *Callback di avviso*) e registralo tramite `loadOptions.setWarningCallback(...)`. Questo ti permette di registrare, ignorare o interrompere l’operazione in base alla gravità dell’avviso.

**D: Posso convertire le forme in oggetti Office Math durante il caricamento di un documento?**  
R: Sì — chiama `loadOptions.setConvertShapeToOfficeMath(true)` prima di costruire il `Document`. La libreria sostituirà automaticamente le forme compatibili con oggetti Office Math nativi.

**D: Come specifico la versione di MS Word per il caricamento del documento?**  
R: Usa `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (o qualsiasi altro valore enum) per indicare a Aspose.Words quali regole di rendering di Word applicare.

**D: Qual è lo scopo del metodo `setTempFolder` in LoadOptions?**  
R: Dirige tutti i file temporanei generati durante il caricamento (come le immagini estratte) verso una cartella controllata da te, fondamentale per ambienti con directory temporanee di sistema limitate.

**D: È possibile convertire metafile come WMF in PNG durante il caricamento?**  
R: Assolutamente sì — abilitalo con `loadOptions.setConvertMetafilesToPng(true)`. Questo garantisce che le immagini raster siano salvate come PNG, migliorando la compatibilità con i visualizzatori moderni.

## Conclusione

Abbiamo coperto le tecniche essenziali per **come impostare LoadOptions** in Aspose.Words per Java, dall’aggiornamento dei campi sporchi alla gestione di file crittografati, dalla conversione delle forme alla specifica della versione di Word, dalla definizione della cartella temporanea e molto altro. Sfruttando queste opzioni potrai costruire pipeline di elaborazione documenti robuste e ad alte prestazioni, adattabili a una vasta gamma di scenari di input.

---

**Ultimo aggiornamento:** 2025-12-27  
**Testato con:** Aspose.Words per Java 24.11  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}