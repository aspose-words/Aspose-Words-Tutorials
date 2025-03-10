---
title: Caricamento di file di testo con Aspose.Words per Java
linktitle: Caricamento di file di testo con
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Sblocca la potenza di Aspose.Words per Java. Impara a caricare documenti di testo, gestire elenchi, gestire spazi e controllare la direzione del testo.
weight: 13
url: /it/java/document-loading-and-saving/loading-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Caricamento di file di testo con Aspose.Words per Java


## Introduzione al caricamento di file di testo con Aspose.Words per Java

In questa guida, esploreremo come caricare file di testo usando Aspose.Words per Java e manipolarli come documenti Word. Tratteremo vari aspetti come il rilevamento di elenchi, la gestione degli spazi e il controllo della direzione del testo.

## Fase 1: Rilevamento degli elenchi

Per caricare un documento di testo e rilevare gli elenchi, puoi seguire questi passaggi:

```java
// Creare un documento di testo normale sotto forma di stringa con parti che possono essere interpretate come elenchi.
// Durante il caricamento, i primi tre elenchi verranno sempre rilevati da Aspose.Words,
// e gli oggetti Elenco verranno creati per loro dopo il caricamento.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
//Il quarto elenco, con spazi vuoti tra il numero dell'elenco e il contenuto dell'elemento dell'elenco,
// verrà rilevato come un elenco solo se "DetectNumberingWithWhitespaces" in un oggetto LoadOptions è impostato su true,
// per evitare che i paragrafi che iniziano con dei numeri vengano erroneamente interpretati come elenchi.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Caricare il documento applicando LoadOptions come parametro e verificare il risultato.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

 Questo codice mostra come caricare un documento di testo con vari formati di elenco e utilizzare`DetectNumberingWithWhitespaces` opzione per rilevare correttamente gli elenchi.

## Fase 2: Gestione delle opzioni degli spazi

Per controllare gli spazi iniziali e finali durante il caricamento di un documento di testo, è possibile utilizzare il seguente codice:

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

 In questo esempio, carichiamo un documento di testo e tagliamo gli spazi iniziali e finali utilizzando`TxtLeadingSpacesOptions.TRIM` E`TxtTrailingSpacesOptions.TRIM`.

## Passaggio 3: controllo della direzione del testo

Per specificare la direzione del testo durante il caricamento di un documento di testo, è possibile utilizzare il seguente codice:

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

Questo codice imposta la direzione del documento su rilevamento automatico (`DocumentDirection.AUTO`e carica un documento di testo con testo ebraico. Puoi regolare la direzione del documento come necessario.

## Codice sorgente completo per caricare file di testo con Aspose.Words per Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Creare un documento di testo normale sotto forma di stringa con parti che possono essere interpretate come elenchi.
	// Durante il caricamento, i primi tre elenchi verranno sempre rilevati da Aspose.Words,
	// e gli oggetti Elenco verranno creati per loro dopo il caricamento.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// Il quarto elenco, con spazi vuoti tra il numero dell'elenco e il contenuto dell'elemento dell'elenco,
	// verrà rilevato come un elenco solo se "DetectNumberingWithWhitespaces" in un oggetto LoadOptions è impostato su true,
	// per evitare che i paragrafi che iniziano con dei numeri vengano erroneamente interpretati come elenchi.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Caricare il documento applicando LoadOptions come parametro e verificare il risultato.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Conclusione

In questa guida, abbiamo esplorato come caricare file di testo usando Aspose.Words per Java, rilevare elenchi, gestire spazi e controllare la direzione del testo. Queste tecniche consentono di manipolare efficacemente i documenti di testo nelle applicazioni Java.

## Domande frequenti

### Che cos'è Aspose.Words per Java?

Aspose.Words per Java è una potente libreria di elaborazione documenti che consente agli sviluppatori di creare, manipolare e convertire documenti Word a livello di programmazione in applicazioni Java. Fornisce un'ampia gamma di funzionalità per lavorare con testo, tabelle, immagini e altri elementi di documenti.

### Come posso iniziare a usare Aspose.Words per Java?

Per iniziare a usare Aspose.Words per Java, segui questi passaggi:
1. Scarica e installa la libreria Aspose.Words per Java.
2.  Fare riferimento alla documentazione a[Riferimento API Aspose.Words per Java](https://reference.aspose.com/words/java/) per informazioni dettagliate ed esempi.
3. Esplora il codice di esempio e i tutorial per imparare a utilizzare la libreria in modo efficace.

### Come carico un documento di testo utilizzando Aspose.Words per Java?

 Per caricare un documento di testo utilizzando Aspose.Words per Java, è possibile utilizzare`TxtLoadOptions` classe e la`Document` classe. Assicurati di specificare le opzioni appropriate per la gestione degli spazi e della direzione del testo, come necessario. Fai riferimento alla guida passo passo in questo articolo per un esempio dettagliato.

### Posso convertire un documento di testo caricato in altri formati?

 Sì, Aspose.Words per Java consente di convertire un documento di testo caricato in vari formati, tra cui DOCX, PDF e altro. È possibile utilizzare`Document` classe per eseguire conversioni. Controlla la documentazione per esempi di conversione specifici.

### Come gestisco gli spazi nei documenti di testo caricati?

 È possibile controllare come vengono gestiti gli spazi iniziali e finali nei documenti di testo caricati utilizzando`TxtLoadOptions` Opzioni come`TxtLeadingSpacesOptions` E`TxtTrailingSpacesOptions`consentono di tagliare o conservare gli spazi a seconda delle necessità. Per un esempio, fare riferimento alla sezione "Opzioni di gestione degli spazi" in questa guida.

### Qual è il significato della direzione del testo in Aspose.Words per Java?

La direzione del testo è essenziale per i documenti che contengono alfabeti o lingue miste, come l'ebraico o l'arabo. Aspose.Words per Java fornisce opzioni per specificare la direzione del testo, assicurando il rendering e la formattazione corretti del testo in queste lingue. La sezione "Controllo della direzione del testo" in questa guida illustra come impostare la direzione del testo.

### Dove posso trovare ulteriori risorse e supporto per Aspose.Words per Java?

 Per ulteriori risorse, documentazione e supporto, visitare il[Documentazione di Aspose.Words per Java](https://reference.aspose.com/words/java/)Puoi anche partecipare ai forum della community di Aspose.Words o contattare il supporto di Aspose per ricevere assistenza su problemi o richieste specifiche.

### Aspose.Words per Java è adatto a progetti commerciali?

Sì, Aspose.Words per Java è adatto sia per progetti personali che commerciali. Offre opzioni di licenza per adattarsi a vari scenari di utilizzo. Assicurati di rivedere i termini di licenza e i prezzi sul sito Web di Aspose per scegliere la licenza appropriata per il tuo progetto.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
