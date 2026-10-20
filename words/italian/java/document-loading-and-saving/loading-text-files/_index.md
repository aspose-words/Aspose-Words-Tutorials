---
date: 2025-12-27
description: Scopri come impostare la direzione, caricare file txt, rimuovere gli
  spazi e convertire i file txt in docx usando Aspose.Words per Java.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Come impostare la direzione e caricare file di testo con Aspose.Words per Java
url: /it/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Come impostare la direzione e caricare file di testo con Aspose.Words per Java

## Introduzione al caricamento di file di testo con Aspose.Words per Java

In questa guida scoprirai **come impostare la direzione** durante il caricamento di documenti di testo semplice e vedrai modi pratici per **caricare txt**, **rimuovere spazi**, e **convertire txt in docx** usando Aspose.Words per Java. Che tu stia costruendo un servizio di conversione documenti o abbia bisogno di un controllo fine sulla rilevazione delle liste, questo tutorial ti accompagna passo passo con spiegazioni chiare e codice pronto all'uso.

## Risposte rapide
- **Come imposto la direzione del testo per un file TXT caricato?** Usa `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` o specifica `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **Aspose.Words può rilevare le liste numerate in testo semplice?** Sì – abilita `DetectNumberingWithWhitespaces` in `TxtLoadOptions`.
- **Come posso rimuovere gli spazi iniziali e finali?** Imposta `TxtLeadingSpacesOptions.TRIM` e `TxtTrailingSpacesOptions.TRIM`.
- **È possibile convertire un file TXT in DOCX in una sola riga?** Carica il TXT con `TxtLoadOptions` e chiama `Document.save("output.docx")`.
- **Quale versione di Java è necessaria?** Java 8+ è sufficiente per Aspose.Words 24.x.

## Cos'è “impostare la direzione” in Aspose.Words?
Quando un file di testo contiene script da destra a sinistra (ad es. ebraico o arabo), la libreria deve conoscere l'ordine di lettura. L'enum `DocumentDirection` ti consente di **impostare la direzione** manualmente o di lasciare che Aspose la rilevi automaticamente, garantendo un layout corretto e una formattazione bidi adeguata.

## Perché usare Aspose.Words per caricare file TXT?
- **Rilevamento accurato delle liste** – gestisce liste numerate, puntate e delimitate da spazi.
- **Gestione fine degli spazi** – rimuove o preserva spazi iniziali/finali.
- **Rilevamento automatico della direzione del testo** – ideale per documenti multilingue.
- **Conversione in un solo passaggio** – carica un `.txt` e salva come `.docx`, `.pdf` o qualsiasi formato supportato.

## Prerequisiti
- Java 8 o superiore.
- Libreria Aspose.Words per Java (aggiungi la dipendenza Maven/Gradle o il JAR al tuo progetto).
- Conoscenza di base degli stream I/O di Java.

## Guida passo‑passo

### Passo 1: Rilevamento delle liste (come caricare txt)
Per caricare un documento di testo e rilevare automaticamente le liste, crea un'istanza di `TxtLoadOptions` e abilita il rilevamento delle liste. Il codice qui sotto mostra diversi stili di lista e abilita la numerazione sensibile agli spazi.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Consiglio professionale:** Se ti serve solo il rilevamento di base delle liste, puoi omettere l'opzione sugli spazi – Aspose riconoscerà comunque i pattern standard `1.` e `1)`.

### Passo 2: Gestione delle opzioni degli spazi (come rimuovere gli spazi)
Gli spazi iniziali e finali spesso causano anomalie di formattazione. Usa `TxtLeadingSpacesOptions` e `TxtTrailingSpacesOptions` per controllare questo comportamento.

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

> **Perché è importante:** Rimuovere gli spazi evita indentazioni indesiderate nel DOCX risultante, rendendo il documento pulito senza post‑processing manuale.

### Passo 3: Controllo della direzione del testo (come impostare la direzione)
Per le lingue da destra a sinistra, imposta la direzione del documento prima del caricamento. L'esempio qui sotto carica un file di testo ebraico e stampa il flag bidi per confermare la direzione.

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

> **Errore comune:** Dimenticare di impostare `DocumentDirection` può provocare testo arabo/ebraico illeggibile, con caratteri nell'ordine sbagliato.

### Codice sorgente completo per il caricamento di file di testo con Aspose.Words per Java
Di seguito trovi il codice completo, pronto all'uso, che combina rilevamento delle liste, gestione degli spazi e controllo della direzione. Puoi copiarlo in una singola classe e eseguire i tre metodi di test singolarmente.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## Problemi comuni e soluzioni
| Problema | Causa | Soluzione |
|----------|-------|-----------|
| Liste non rilevate | `DetectNumberingWithWhitespaces` lasciato false per le liste delimitate da spazi | Abilitare `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Indentazione extra dopo il caricamento | Gli spazi iniziali sono stati preservati | Impostare `TxtLeadingSpacesOptions.TRIM` |
| Il testo ebraico appare invertito | Direzione del documento non impostata o impostata su `LEFT_TO_RIGHT` | Usare `DocumentDirection.AUTO` o `RIGHT_TO_LEFT` |
| Il DOCX di output è vuoto | Lo stream di input non è stato ripristinato prima del secondo caricamento | Ricreare `ByteArrayInputStream` per ogni chiamata di caricamento |

## Domande frequenti

### Q: Che cos'è Aspose.Words per Java?
A: Aspose.Words per Java è una potente libreria di elaborazione documenti che consente agli sviluppatori di creare, manipolare e convertire documenti Word programmaticamente in applicazioni Java. Supporta una vasta gamma di funzionalità, dal semplice caricamento di testo alla formattazione complessa e alla conversione.

### Q: Come posso iniziare con Aspose.Words per Java?
A: 1. Scarica e installa la libreria Aspose.Words per Java. 2. Consulta la documentazione su [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) per informazioni dettagliate ed esempi. 3. Esplora il codice di esempio e i tutorial per imparare a utilizzare la libreria in modo efficace.

### Q: Come carico un documento di testo usando Aspose.Words per Java?
A: Usa la classe `TxtLoadOptions` insieme al costruttore `Document`. Specifica opzioni come il rilevamento delle liste, la gestione degli spazi o la direzione del testo come mostrato nelle sezioni passo‑passo sopra.

### Q: Posso convertire un documento di testo caricato in altri formati?
A: Sì. Dopo aver caricato il file TXT in un oggetto `Document`, chiama `doc.save("output.pdf")`, `doc.save("output.docx")` o qualsiasi altro formato supportato.

### Q: Come gestisco gli spazi nei documenti di testo caricati?
A: Controlla gli spazi iniziali e finali con `TxtLeadingSpacesOptions` e `TxtTrailingSpacesOptions`. Impostali su `TRIM` per rimuovere gli spazi indesiderati, o su `PRESERVE` se devi mantenere la spaziatura originale.

### Q: Qual è l'importanza della direzione del testo in Aspose.Words per Java?
A: La direzione del testo garantisce la corretta visualizzazione degli script da destra a sinistra (ebraico, arabo, ecc.). Impostando `DocumentDirection`, assicuri che il testo bidi venga visualizzato correttamente nel documento risultante.

### Q: Dove posso trovare ulteriori risorse e supporto per Aspose.Words per Java?
A: Visita la [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) per riferimenti API, esempi di codice e guide dettagliate. Puoi anche partecipare ai forum della community Aspose o contattare il supporto Aspose per domande specifiche.

### Q: Aspose.Words per Java è adatto a progetti commerciali?
A: Sì. Offre opzioni di licenza sia per uso personale che commerciale. Consulta i termini di licenza sul sito Aspose per scegliere il piano più adatto al tuo progetto.

## Conclusione
Ora disponi di un toolkit completo per **caricare file txt**, **rilevare le liste**, **rimuovere gli spazi** e **impostare la direzione** quando converti testo semplice in documenti Word ricchi con Aspose.Words per Java. Applica questi pattern per automatizzare i flussi di lavoro documentali, migliorare il supporto multilingue e garantire output puliti e professionali ogni volta.

---

**Ultimo aggiornamento:** 2025-12-27  
**Testato con:** Aspose.Words per Java 24.12  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}