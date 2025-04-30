---
"description": "Scopri passo dopo passo come utilizzare intestazioni e piè di pagina in Aspose.Words per Java. Crea documenti professionali senza sforzo."
"linktitle": "Utilizzo di intestazioni e piè di pagina"
"second_title": "API di elaborazione dei documenti Java Aspose.Words"
"title": "Utilizzo di intestazioni e piè di pagina in Aspose.Words per Java"
"url": "/it/java/using-document-elements/using-headers-and-footers/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo di intestazioni e piè di pagina in Aspose.Words per Java


In questa guida completa, ti guideremo attraverso il processo di utilizzo di intestazioni e piè di pagina in Aspose.Words per Java. Intestazioni e piè di pagina sono elementi essenziali nella formattazione dei documenti e Aspose.Words offre potenti strumenti per crearli e personalizzarli in base alle tue esigenze.

Ora analizziamo nel dettaglio ciascuno di questi passaggi.

## 1. Introduzione ad Aspose.Words

Aspose.Words è una potente API Java che consente di creare, manipolare e visualizzare documenti Word a livello di codice. Offre ampie funzionalità per la formattazione dei documenti, inclusi intestazioni e piè di pagina.

## 2. Configurazione dell'ambiente Java

Prima di iniziare a utilizzare Aspose.Words, assicurati di aver configurato correttamente il tuo ambiente di sviluppo Java. Puoi trovare le istruzioni di configurazione necessarie nella pagina della documentazione di Aspose.Words: [Documentazione Java di Aspose.Words](https://reference.aspose.com/words/java/).

## 3. Creazione di un nuovo documento

Per lavorare con intestazioni e piè di pagina, è necessario creare un nuovo documento utilizzando Aspose.Words. Il codice seguente illustra come farlo:

```java
// Codice Java per la creazione di un nuovo documento
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Comprensione dell'impostazione della pagina

L'impostazione della pagina è fondamentale per controllare il layout del documento. È possibile specificare varie proprietà relative a intestazioni e piè di pagina utilizzando `PageSetup` classe. Per esempio:

```java
// Impostazione delle proprietà della pagina
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Intestazione/piè di pagina della prima pagina diversi

Aspose.Words ti consente di avere intestazioni e piè di pagina diversi per la prima pagina del tuo documento. Usa `pageSetup.setDifferentFirstPageHeaderFooter(true);` per abilitare questa funzione.

## 6. Lavorare con le intestazioni

### 6.1. Aggiunta di testo alle intestazioni

È possibile aggiungere testo alle intestazioni utilizzando `DocumentBuilder`Ecco un esempio:

```java
// Aggiungere testo all'intestazione della prima pagina
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. Inserimento di immagini nelle intestazioni

Per inserire immagini nelle intestazioni, puoi utilizzare `insertImage` metodo. Ecco un esempio:

```java
// Inserimento di un'immagine nell'intestazione
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Personalizzazione degli stili di intestazione

È possibile personalizzare gli stili delle intestazioni impostando varie proprietà, ad esempio il carattere, l'allineamento e altro ancora, come mostrato negli esempi sopra.

## 7. Lavorare con i piè di pagina

### 7.1. Aggiungere testo ai piè di pagina

Similmente alle intestazioni, puoi aggiungere testo ai piè di pagina utilizzando `DocumentBuilder`Ecco un esempio:

```java
// Aggiungere testo al piè di pagina principale
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Inserisci testo e campi secondo necessità
```

### 7.2. Inserimento di immagini nei piè di pagina

Per inserire immagini nei piè di pagina, utilizzare `insertImage` metodo, proprio come nelle intestazioni.

### 7.3. Personalizzazione degli stili del piè di pagina

Personalizza gli stili del piè di pagina utilizzando `DocumentBuilder`, simile alla personalizzazione delle intestazioni.

## 8. Numerazione delle pagine

Puoi includere i numeri di pagina nelle intestazioni e nei piè di pagina utilizzando campi come `PAGE` E `NUMPAGES`Questi campi vengono aggiornati automaticamente quando aggiungi o rimuovi pagine.

## 9. Informazioni sul copyright nei piè di pagina

Per aggiungere informazioni sul copyright al piè di pagina del documento, puoi utilizzare una tabella con due celle, allineandone una a sinistra e l'altra a destra, come mostrato nel frammento di codice.

## 10. Lavorare con più sezioni

Aspose.Words consente di lavorare con più sezioni all'interno di un documento. È possibile impostare diverse impostazioni di pagina e intestazioni/piè di pagina per ogni sezione.

## 11. Orientamento orizzontale

Se necessario, è possibile modificare l'orientamento di sezioni specifiche in modalità orizzontale.

## 12. Copia di intestazioni/piè di pagina dalle sezioni precedenti

Copiare intestazioni e piè di pagina dalle sezioni precedenti può far risparmiare tempo durante la creazione di documenti complessi.

## 13. Salvataggio del documento

Dopo aver creato e personalizzato il documento, non dimenticare di salvarlo utilizzando `doc.save()` metodo.

## Codice sorgente completo
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Specificare se si desidera che le intestazioni e i piè di pagina della prima pagina siano diversi da quelli delle altre pagine.
        // È anche possibile utilizzare la proprietà PageSetup.OddAndEvenPagesHeaderFooter per specificare
        // intestazioni/piè di pagina diversi per le pagine pari e dispari.
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // Inserire un'immagine posizionata nell'angolo superiore/sinistro dell'intestazione.
        // La distanza dai bordi superiore/sinistro della pagina è impostata su 10 punti.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Utilizziamo una tabella con due celle per creare una parte del testo sulla riga (con numerazione delle pagine).
        // Da allineare a sinistra, e l'altra parte del testo (con copyright) da allineare a destra.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // Utilizza i campi PAGE e NUMPAGES per calcolare automaticamente il numero di pagina corrente e di molte pagine.
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // Crea un'interruzione di pagina per creare una seconda pagina in cui verranno visualizzate le intestazioni e i piè di pagina principali.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // Questa sezione non necessita di un'intestazione/piè di pagina diverso per la prima pagina, abbiamo bisogno solo di una pagina del titolo nel documento,
        // e l'intestazione/piè di pagina per questa pagina sono già stati definiti nella sezione precedente.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // Questa sezione mostra le intestazioni/piè di pagina della sezione precedente
        // per impostazione predefinita chiama currentSection.HeadersFooters.LinkToPrevious(false) per annullare questa larghezza di pagina
        // è diverso per la nuova sezione e quindi dobbiamo impostare larghezze di cella diverse per una tabella di piè di pagina.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Se vogliamo utilizzare il set di intestazioni/piè di pagina già esistente per questa sezione.
        // Ma con alcune piccole modifiche, potrebbe essere opportuno copiare intestazioni/piè di pagina
        // dalla sezione precedente e applichiamo le modifiche necessarie dove vogliamo.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
Codice sorgente del metodo copyHeadersFootersFromPreviousSection
```java
    /// <sommario>
    //Clona e copia le intestazioni/i piè di pagina della sezione precedente nella sezione specificata.
    /// </sommario>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## Conclusione

In questo tutorial abbiamo trattato le basi dell'utilizzo di intestazioni e piè di pagina in Aspose.Words per Java. Hai imparato a creare, personalizzare e formattare intestazioni e piè di pagina, oltre ad altre tecniche essenziali di formattazione dei documenti.

Per ulteriori dettagli e funzionalità avanzate, fare riferimento a [Documentazione Java di Aspose.Words](https://reference.aspose.com/words/java/).

## Domande frequenti

### 1. Come posso aggiungere i numeri di pagina al piè di pagina del mio documento?
È possibile aggiungere i numeri di pagina inserendo il `PAGE` campo nel piè di pagina utilizzando Aspose.Words.

### 2. Aspose.Words è compatibile con gli ambienti di sviluppo Java?
Sì, Aspose.Words fornisce supporto per lo sviluppo Java. Assicurati di avere la configurazione necessaria.

### 3. Posso personalizzare il carattere e lo stile delle intestazioni e dei piè di pagina?
Certamente, puoi personalizzare i caratteri, l'allineamento e altri stili per rendere le tue intestazioni e i tuoi piè di pagina visivamente accattivanti.

### 4. È possibile avere intestazioni diverse per le pagine pari e dispari?
Sì, puoi usare `PageSetup.OddAndEvenPagesHeaderFooter` per specificare intestazioni diverse per le pagine pari e dispari.

### 5. Come posso iniziare a usare Aspose.Words per Java?
Per iniziare, visita il [Documentazione Java di Aspose.Words](https://reference.aspose.com/words/java/) per una guida completa sull'utilizzo dell'API.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}