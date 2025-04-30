---
"date": "2025-03-28"
"description": "Scopri come padroneggiare il rilevamento degli elenchi, la gestione del testo e altro ancora utilizzando Aspose.Words per Java. Questa guida illustra come rilevare elenchi separati da spazi, tagliare gli spazi, determinare la direzione del documento, disabilitare il rilevamento automatico della numerazione e gestire i collegamenti ipertestuali."
"title": "Rilevamento di elenchi master e gestione del testo in Java con Aspose.Words&#58; una guida completa"
"url": "/it/java/tables-lists/java-aspose-words-list-detection-text-handling/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Rilevamento di elenchi master e gestione del testo in Java con Aspose.Words: una guida completa

## Introduzione

Lavorare con documenti di testo normale presenta spesso difficoltà nell'identificazione di dati strutturati come gli elenchi a causa di delimitatori incoerenti e problemi di formattazione. La libreria Aspose.Words per Java offre funzionalità robuste per affrontare questi problemi, tra cui il rilevamento della numerazione con spazi vuoti, la riduzione degli spazi, la determinazione della direzione del documento, la disattivazione del rilevamento automatico della numerazione e la gestione dei collegamenti ipertestuali nei documenti di testo. Questo tutorial ti consente di manipolare efficacemente i dati testuali utilizzando Aspose.Words.

**Cosa imparerai:**
- Tecniche per rilevare elenchi separati da spazi
- Metodi per eliminare gli spazi indesiderati dal contenuto del documento
- Approcci per determinare la direzione di lettura di un file di testo
- Modi per disattivare il rilevamento automatico della numerazione
- Strategie per rilevare e gestire i collegamenti ipertestuali nei documenti in chiaro

Esaminiamo i prerequisiti necessari prima di implementare queste funzionalità.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

### Librerie richieste:
- **Aspose.Words per Java**: Versione 25.3 o successiva.

### Configurazione dell'ambiente:
- Assicurati che il tuo ambiente di sviluppo supporti Maven o Gradle, poiché sono necessari per gestire le dipendenze.

### Prerequisiti di conoscenza:
- Conoscenza di base della programmazione Java
- Familiarità con i sistemi di build Maven o Gradle

## Impostazione di Aspose.Words

Per iniziare a utilizzare Aspose.Words per Java nel tuo progetto, devi includere la dipendenza necessaria. Ecco come fare:

**Esperto:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Acquisizione della licenza

Per sfruttare appieno Aspose.Words, si consiglia di acquistare una licenza:
- **Prova gratuita**: Disponibile per testare le funzionalità.
- **Licenza temporanea**: A scopo di valutazione senza limitazioni.
- **Acquistare**: Licenza completa per uso continuativo.

Una volta ottenuta la licenza, inizializzala nella tua applicazione per sbloccare tutte le funzionalità della libreria.

## Guida all'implementazione

Analizziamo nel dettaglio ciascuna funzionalità e vediamo come implementarle utilizzando Aspose.Words per Java.

### Rileva la numerazione con spazi vuoti

**Panoramica:** Questa funzionalità consente di identificare gli elenchi all'interno di documenti di testo normale che utilizzano spazi vuoti come delimitatori.

#### Passaggio 1: caricare il documento
```java
import com.aspose.words.*;

final String TEXT_DOC = "Full stop delimiters:\n" +
    // ...
    "3 Fourth list item 3";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDetectNumberingWithWhitespaces(true);
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
```

#### Passaggio 2: convalidare il rilevamento dell'elenco
```java
List<Paragraph> paragraphList = Arrays.stream(doc.getFirstSection().getBody().getParagraphs().toArray())
        .filter(Paragraph.class::isInstance)
        .map(Paragraph.class::cast)
        .collect(Collectors.toList());

boolean detectNumberingWithWhitespaces = true;
if (detectNumberingWithWhitespaces) {
    assert doc.getLists().getCount() == 4 : "Expected four lists.";
    boolean foundFourthList = paragraphList.stream()
        .anyMatch(p -> p.getText().contains("Fourth list") && p.isListItem());
    assert foundFourthList : "Expected to find a fourth list item detected as numbered.";
}
```

*Parametri e metodi:*
- `setDetectNumberingWithWhitespaces(true)`: Configura il parser per riconoscere gli elenchi con delimitatori di spazi.
- `doc.getLists().getCount()`: Recupera il numero di elenchi rilevati nel documento.

### Rifinisci gli spazi iniziali e finali

**Panoramica:** Questa funzione elimina gli spazi non necessari all'inizio o alla fine delle righe nei documenti di testo normale, garantendo una formattazione pulita del testo.

#### Passaggio 1: configurare le opzioni di caricamento
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

String textDoc = "      Line 1 \n" +
    // ...
    " Line 3       ";

TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);

Document doc = new Document(new ByteArrayInputStream(textDoc.getBytes(StandardCharsets.US_ASCII)), loadOptions);
```

#### Passaggio 2: verifica del ritaglio
```java
ParagraphCollection paragraphs = doc.getFirstSection().getBody().getParagraphs();
for (int i = 0; i < paragraphs.getCount(); i++) {
    Paragraph paragraph = paragraphs.get(i);
    String text = paragraph.getText();
    assert !text.startsWith(" ") : "Expected no leading spaces.";
    assert !text.endsWith(" ") : "Expected no trailing spaces.";
}
```

*Configurazioni chiave:*
- `setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM)`: Taglia gli spazi dall'inizio delle righe.
- `setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM)`: Rimuove gli spazi a fine riga.

### Rileva la direzione del documento

**Panoramica:** Determina se un documento deve essere letto da destra a sinistra (RTL), ad esempio nel caso di testo ebraico o arabo.

#### Passaggio 1: imposta il rilevamento automatico
```java
TxtLoadOptions loadOptions = new TxtLoadOptions();
loadOptions.setDocumentDirection(DocumentDirection.AUTO);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Hebrew text.txt", loadOptions);

boolean isBidi = doc.getFirstSection().getBody().getFirstParagraph().getParagraphFormat().isBidi();
assert isBidi : "Expected Hebrew text to be right-to-left.";
```

### Disabilita il rilevamento automatico della numerazione

**Panoramica:** Impedisce alla libreria di rilevare e formattare automaticamente gli elementi dell'elenco.

#### Passaggio 1: configurare le opzioni di caricamento
```java
TxtLoadOptions options = new TxtLoadOptions();
options.setAutoNumberingDetection(false);
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Number detection.txt", options);

int listItemsCount = 0;
for (Paragraph paragraph : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true)) {
    if (paragraph.isListItem())
        listItemsCount++;
}
assert listItemsCount == 0 : "Expected no detected list items.";
```

### Rileva collegamenti ipertestuali nel testo

**Panoramica:** Identificare e gestire i collegamenti ipertestuali all'interno dei documenti di testo normale.

#### Passaggio 1: impostare le opzioni di rilevamento
```java
import java.nio.charset.StandardCharsets;
import java.io.ByteArrayInputStream;

final String INPUT_TEXT = "Some links in TXT:\n" +
    // ...
    "https://docs.aspose.com/words/net/";

try (ByteArrayInputStream stream = new ByteArrayInputStream(INPUT_TEXT.getBytes(StandardCharsets.US_ASCII))) {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    loadOptions.setDetectHyperlinks(true);
    Document doc = new Document(stream, loadOptions);

    String[] expectedLinks = {"https://www.aspose.com/", "https://docs.aspose.com/words/net/"};
    for (int i = 0; i < doc.getRange().getFields().getCount(); i++) {
        String result = doc.getRange().getFields().get(i).getResult().trim();
        assert result.equals(expectedLinks[i]) : "Expected hyperlink does not match.";
    }
}
```

## Applicazioni pratiche

1. **Sistemi di gestione dei contenuti (CMS):** Formatta automaticamente i contenuti generati dagli utenti in elenchi strutturati.
2. **Strumenti di estrazione dati:** Utilizzare il rilevamento degli elenchi per organizzare i dati non strutturati da analizzare.
3. **Pipeline di elaborazione del testo:** Migliora la pre-elaborazione dei documenti riducendo gli spazi e rilevando la direzione del testo.

## Considerazioni sulle prestazioni

Per ottimizzare le prestazioni:
- Carica i documenti con operazioni minime, concentrandoti sulle funzionalità necessarie.
- Se possibile, gestire l'utilizzo della memoria elaborando i documenti di grandi dimensioni in blocchi.

## Conclusione

Sfruttando Aspose.Words per Java, è possibile gestire in modo efficiente i dati testuali nei documenti in chiaro. Dal rilevamento di elenchi separati da spazi alla gestione dell'orientamento del testo e dei collegamenti ipertestuali, questi potenti strumenti consentono una manipolazione affidabile dei documenti. Per ulteriori approfondimenti, consultare [Documentazione di Aspose.Words](https://reference.aspose.com/words/java/) oppure prova la versione di prova gratuita.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}