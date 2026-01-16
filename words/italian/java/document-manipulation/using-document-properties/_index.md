---
date: 2026-01-16
description: Scopri come convertire i pollici in punti, leggere i metadati del documento
  in Java, aggiungere proprietà personalizzate in Java e impostare i margini della
  pagina in Java con Aspose.Words per Java.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Convertire i pollici in punti – Utilizzando le proprietà del documento in Aspose.Words
  per Java
url: /it/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Convertire Pollici in Punti – Utilizzando le Proprietà del Documento in Aspose.Words per Java

In questo tutorial scoprirai come **convertire pollici in punti** quando imposti i margini della pagina, leggere i metadati del documento Java, aggiungere proprietà personalizzate Java e lavorare con le proprietà di documento integrate utilizzando Aspose.Words per Java. Che tu stia generando report, fatture o documenti legali, padroneggiare queste tecniche ti offre un controllo preciso sull'aspetto e sui metadati dei tuoi file Word.

## Risposte Rapide
- **Come converto i pollici in punti?** Usa `ConvertUtil.inchToPoint(value)` di Aspose.Words.
- **Posso leggere i metadati del documento in Java?** Sì – chiama `doc.getBuiltInDocumentProperties()` o `doc.getCustomDocumentProperties()`.
- **Come aggiungo una proprietà personalizzata in Java?** Usa `doc.getCustomDocumentProperties().add(name, value)`.
- **Quale metodo imposta i margini della pagina in punti?** `PageSetup.setTopMargin`, `setBottomMargin`, ecc., accettano valori in punti.
- **È supportato il collegamento a un segnalibro?** Sì – usa `addLinkToContent` sulla collezione delle proprietà personalizzate.

## Introduzione alle Proprietà del Documento

Le proprietà del documento sono una parte fondamentale di qualsiasi file Word. Conservano informazioni come titolo, autore, soggetto, parole‑chiave e qualsiasi metadato personalizzato necessario per l'elaborazione successiva. In Aspose.Words per Java puoi manipolare sia le proprietà integrate sia quelle personalizzate, e puoi anche controllare dettagli di layout come i margini convertendo le unità di misura (ad es., **convertire pollici in punti**).

## Che cosa significa “convertire pollici in punti”?

In Word, le misure di layout sono espresse in punti (1 punto = 1/72 di pollice). Convertire i pollici in punti ti consente di definire margini, rientri e spaziature usando le unità imperiali familiari, mentre l'API lavora internamente con i punti.

## Perché gestire i metadati del documento in Java?

Incorporare i metadati facilita la ricerca, la categorizzazione e l'automazione dei flussi di lavoro. Ad esempio, potresti etichettare un contratto con una bandiera “Authorized” o memorizzare un numero di revisione per le tracce di audit. Leggere e scrivere queste informazioni programmaticamente garantisce coerenza su grandi lotti di documenti.

## Prerequisiti
- Java 17+ (o JDK compatibile)
- Libreria Aspose.Words per Java aggiunta al progetto (Maven/Gradle)
- Un file `.docx` di esempio (ad es., `Properties.docx`) posizionato in una directory accessibile

## Guida Passo‑Passo

### Enumerare le Proprietà di Documento Integrate
Di seguito è riportato un semplice test che apre un documento e stampa tutte le proprietà integrate come Titolo, Autore e Parole‑chiave.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Suggerimento professionale:** Usa questo snippet per verificare che i tuoi metadati siano stati scritti correttamente nei passaggi precedenti.

### Aggiungere Proprietà di Documento Personalizzate (add custom properties java)
Le proprietà personalizzate ti consentono di memorizzare qualsiasi tipo di dato necessario—booleano, stringa, data, numero, ecc.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Perché è importante:** Aggiungere una bandiera come **Authorized** può guidare i flussi di lavoro di approvazione successivi senza modificare il contenuto del documento.

### Rimuovere una Proprietà Personalizzata
Se una proprietà non è più necessaria, puoi eliminarla in modo pulito.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Configurare un Collegamento a Contenuto (collegamento a segnalibro)
Puoi creare un segnalibro e poi aggiungere una proprietà personalizzata che punta a quel segnalibro, abilitando riferimenti incrociati dinamici.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Convertire tra Unità di Misura (set page margins java)
Ecco dove brilla la parola chiave principale. Impostiamo i margini in pollici, poi **convertiamo i pollici in punti** usando `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Nota:** `ConvertUtil` fornisce anche `pointToInch`, `mmToPoint`, ecc., per una gestione flessibile del layout.

### Utilizzare Caratteri di Controllo (read document metadata java)
I caratteri di controllo ti aiutano a pulire i flussi di testo. Questo esempio sostituisce un ritorno a capo (`\r`) con la sequenza di interruzione di riga di Windows (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Problemi Comuni & Soluzioni
| Problema | Causa | Soluzione |
|----------|-------|-----------|
| I margini appaiono errati dopo la conversione | Uso di unità sbagliata (es. cm invece di pollici) | Verifica di chiamare `ConvertUtil.inchToPoint` per valori in pollici |
| La proprietà personalizzata non compare | Proprietà aggiunta dopo il salvataggio del documento | Chiama `doc.save(...)` dopo aver aggiunto le proprietà |
| Il collegamento al segnalibro è interrotto | Errore di battitura nel nome del segnalibro | Assicurati che il nome del segnalibro corrisponda esattamente in `addLinkToContent` |

## FAQ

### Come accedo alle proprietà di documento integrate?

Per accedere alle proprietà di documento integrate in Aspose.Words per Java, puoi usare il metodo `getBuiltInDocumentProperties` sull'oggetto `Document`. Questo metodo restituisce una collezione di proprietà integrate che puoi iterare.

### Posso aggiungere proprietà di documento personalizzate a un documento?

Sì, puoi aggiungere proprietà di documento personalizzate a un documento utilizzando la collezione `CustomDocumentProperties`. Puoi definire proprietà personalizzate con vari tipi di dato, incluse stringhe, booleani, date e valori numerici.

### Come posso rimuovere una specifica proprietà di documento personalizzata?

Per rimuovere una specifica proprietà di documento personalizzata, puoi usare il metodo `remove` sulla collezione `CustomDocumentProperties`, passando il nome della proprietà da rimuovere come parametro.

### Qual è lo scopo del collegamento a contenuto all'interno di un documento?

Il collegamento a contenuto all'interno di un documento consente di creare riferimenti dinamici a parti specifiche del documento. Questo può essere utile per creare documenti interattivi o riferimenti incrociati tra sezioni.

### Come posso convertire tra diverse unità di misura in Aspose.Words per Java?

Puoi convertire tra diverse unità di misura in Aspose.Words per Java utilizzando la classe `ConvertUtil`. Essa fornisce metodi per convertire unità come pollici in punti, punti in centimetri e altro ancora.

## Domande Frequenti

**D: Come leggo i metadati del documento Java senza caricare l'intero file?**  
R: Usa `DocumentInfo` per recuperare le proprietà di base senza caricare completamente il contenuto del documento.

**D: Posso impostare programmaticamente i margini della pagina Java per documenti esistenti?**  
R: Sì—apri il documento, modifica i margini di `PageSetup` (converti i pollici in punti se necessario) e salva.

**D: È possibile esportare le proprietà personalizzate nei metadati PDF?**  
R: Quando salvi in PDF, Aspose.Words mappa automaticamente le proprietà di documento personalizzate nei metadati PDF personalizzati.

**D: I caratteri di controllo influenzano la conversione in PDF?**  
R: Vengono preservati durante la conversione; tuttavia, potresti voler normalizzare le terminazioni di riga per coerenza.

**D: Quale versione di Aspose.Words è necessaria per `ConvertUtil`?**  
R: `ConvertUtil` è disponibile da Aspose.Words 16.5; qualsiasi versione recente lo supporta.

## Conclusione

Padroneggiando **convertire pollici in punti**, leggendo i metadati del documento Java e aggiungendo proprietà personalizzate Java, ottieni il pieno controllo sia sul layout visivo sia sui dati nascosti dei tuoi file Word. Queste capacità ti consentono di costruire pipeline documentali automatizzate, garantire la conformità e creare report riccamente formattati—tutto con Aspose.Words per Java.

---

**Ultimo aggiornamento:** 2026-01-16  
**Testato con:** Aspose.Words per Java 24.11  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}