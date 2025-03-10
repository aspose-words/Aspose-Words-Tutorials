---
title: Utilizzo delle opzioni di caricamento in Aspose.Words per Java
linktitle: Utilizzo delle opzioni di caricamento
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Padroneggiare le opzioni di caricamento in Aspose.Words per Java. Personalizza il caricamento dei documenti, gestisci la crittografia, converti le forme, imposta le versioni di Word e altro ancora per un'elaborazione efficiente dei documenti Java.
weight: 11
url: /it/java/document-loading-and-saving/using-load-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo delle opzioni di caricamento in Aspose.Words per Java


## Introduzione all'utilizzo delle opzioni di caricamento in Aspose.Words per Java

In questo tutorial, esploreremo come lavorare con Load Options in Aspose.Words per Java. Load Options consente di personalizzare il modo in cui i documenti vengono caricati ed elaborati. Tratteremo vari scenari, tra cui l'aggiornamento di dirty fields, il caricamento di documenti crittografati, la conversione di forme in Office Math, l'impostazione della versione di MS Word, la specifica di una cartella temporanea, la gestione degli avvisi e la conversione di metafile in PNG. Immergiamoci passo dopo passo.

## Aggiorna campi sporchi

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

 Questo frammento di codice mostra come aggiornare i campi sporchi in un documento.`setUpdateDirtyFields(true)` Il metodo viene utilizzato per garantire che i campi sporchi vengano aggiornati durante il caricamento del documento.

## Carica documento crittografato

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

 Qui carichiamo un documento criptato usando una password.`LoadOptions` il costruttore accetta la password del documento, ed è anche possibile specificare una nuova password quando si salva il documento utilizzando`OdtSaveOptions`.

## Convertire la forma in Office Math

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

 Questo codice dimostra come convertire le forme in oggetti Office Math durante il caricamento del documento.`setConvertShapeToOfficeMath(true)`Il metodo abilita questa conversione.

## Imposta la versione di MS Word

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

 È possibile specificare la versione di MS Word per il caricamento del documento. In questo esempio, impostiamo la versione su Microsoft Word 2010 utilizzando`setMswVersion`.

## Usa cartella temporanea

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

 Impostando la cartella temporanea utilizzando`setTempFolder`è possibile controllare dove vengono archiviati i file temporanei durante l'elaborazione dei documenti.

## Avviso di richiamo

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Gestire gli avvisi man mano che si presentano durante il caricamento del documento.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Questo codice dimostra come impostare un callback di avviso per gestire gli avvisi durante il caricamento del documento. Puoi personalizzare il comportamento della tua applicazione quando si verificano gli avvisi.

## Convertire i metafile in PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

 Per convertire i metafile (ad esempio, WMF) in immagini PNG durante il caricamento del documento, è possibile utilizzare`setConvertMetafilesToPng(true)` metodo.

## Codice sorgente completo per lavorare con le opzioni di caricamento in Aspose.Words per Java

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
	// Crea un nuovo oggetto LoadOptions, che caricherà i documenti in base alle specifiche di MS Word 2019 per impostazione predefinita
	// e modificare la versione di caricamento in Microsoft Word 2010.
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
		//Stampa gli avvisi e i relativi dettagli man mano che si presentano durante il caricamento del documento.
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

## Conclusione

In questo tutorial, abbiamo approfondito vari aspetti del lavoro con Load Options in Aspose.Words per Java. Load Options svolge un ruolo cruciale nella personalizzazione del modo in cui i documenti vengono caricati ed elaborati, consentendoti di adattare l'elaborazione dei documenti alle tue esigenze specifiche. Riassumiamo i punti chiave trattati in questa guida:

## Domande frequenti

### Come posso gestire gli avvisi durante il caricamento dei documenti?

 È possibile impostare un callback di avviso come mostrato in`warningCallback()` metodo sopra. Personalizza il`DocumentLoadingWarningCallback` classe per gestire gli avvisi in base ai requisiti della tua applicazione.

### Posso convertire le forme in oggetti di Office Math quando carico un documento?

 Sì, puoi convertire le forme in oggetti di Office Math utilizzando`loadOptions.setConvertShapeToOfficeMath(true)`.

### Come faccio a specificare la versione di MS Word per il caricamento del documento?

 Utilizzo`loadOptions.setMswVersion(MsWordVersion.WORD_2010)` per specificare la versione di MS Word per il caricamento del documento.

###  Qual è lo scopo del`setTempFolder` method in Load Options?

 IL`setTempFolder`metodo consente di specificare la cartella in cui vengono archiviati i file temporanei durante l'elaborazione del documento.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
