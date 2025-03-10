---
title: Utilizzo delle proprietà del documento in Aspose.Words per Java
linktitle: Utilizzo delle proprietà del documento
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Ottimizza la gestione dei documenti con Aspose.Words per Java. Impara a lavorare con le proprietà dei documenti, ad aggiungere metadati personalizzati e altro ancora in questo tutorial completo.
weight: 32
url: /it/java/document-manipulation/using-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo delle proprietà del documento in Aspose.Words per Java


## Introduzione alle proprietà del documento

Le proprietà del documento sono una parte essenziale di qualsiasi documento. Forniscono informazioni aggiuntive sul documento stesso, come il titolo, l'autore, l'oggetto, le parole chiave e altro. In Aspose.Words for Java, puoi manipolare sia le proprietà del documento integrate che quelle personalizzate.

## Enumerazione delle proprietà del documento

### Proprietà integrate

Per recuperare e utilizzare le proprietà integrate del documento, è possibile utilizzare il seguente frammento di codice:

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

Questo codice visualizzerà il nome del documento e le proprietà integrate, tra cui proprietà come "Titolo", "Autore" e "Parole chiave".

### Proprietà personalizzate

Per lavorare con le proprietà personalizzate del documento, puoi utilizzare il seguente frammento di codice:

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

Questo frammento di codice mostra come aggiungere proprietà personalizzate al documento, tra cui un valore booleano, una stringa, una data, un numero di revisione e un valore numerico.

## Rimozione delle proprietà del documento

Per rimuovere proprietà specifiche del documento, puoi utilizzare il seguente codice:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Questo codice rimuove la proprietà personalizzata "Data autorizzata" dal documento.

## Configurazione del collegamento al contenuto

In alcuni casi, potresti voler creare dei link all'interno del tuo documento. Ecco come puoi farlo:

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

    // Aggiungi collegato alla proprietà del contenuto.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Questo frammento di codice mostra come creare un segnalibro nel documento e aggiungere una proprietà personalizzata del documento che si collega a tale segnalibro.

## Conversione tra unità di misura

In Aspose.Words per Java, puoi convertire facilmente le unità di misura. Ecco un esempio di come farlo:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Imposta i margini in pollici.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Questo frammento di codice imposta vari margini e distanze in pollici convertendoli in punti.

## Utilizzo dei caratteri di controllo

I caratteri di controllo possono essere utili quando si ha a che fare con il testo. Ecco come sostituire un carattere di controllo nel testo:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Sostituisci il carattere di controllo "\r" con "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

In questo esempio, sostituiamo il ritorno a capo (`\r`) con un ritorno a capo seguito da un avanzamento di riga (`\r\n`).

## Conclusione

Le proprietà del documento svolgono un ruolo significativo nella gestione e nell'organizzazione efficace dei documenti in Aspose.Words per Java. Sia che si tratti di lavorare con proprietà integrate, proprietà personalizzate o di utilizzare caratteri di controllo, hai a disposizione una gamma di strumenti per migliorare le tue capacità di gestione dei documenti.

## Domande frequenti

### Come posso accedere alle proprietà integrate del documento?

 Per accedere alle proprietà del documento integrate in Aspose.Words per Java, è possibile utilizzare`getBuiltInDocumentProperties` metodo sul`Document` oggetto. Questo metodo restituisce una raccolta di proprietà integrate che puoi scorrere.

### Posso aggiungere proprietà personalizzate a un documento?

 Sì, puoi aggiungere proprietà personalizzate a un documento utilizzando`CustomDocumentProperties` raccolta. È possibile definire proprietà personalizzate con vari tipi di dati, tra cui stringhe, valori booleani, date e valori numerici.

### Come posso rimuovere una specifica proprietà personalizzata di un documento?

 Per rimuovere una proprietà specifica del documento personalizzato, è possibile utilizzare`remove` metodo sul`CustomDocumentProperties`raccolta, passando come parametro il nome della proprietà che si desidera rimuovere.

### Qual è lo scopo del collegamento al contenuto di un documento?

Il collegamento al contenuto all'interno di un documento consente di creare riferimenti dinamici a parti specifiche del documento. Ciò può essere utile per creare documenti interattivi o riferimenti incrociati tra sezioni.

### Come posso convertire diverse unità di misura in Aspose.Words per Java?

 È possibile convertire tra diverse unità di misura in Aspose.Words per Java utilizzando`ConvertUtil` classe. Fornisce metodi per convertire unità quali pollici in punti, punti in centimetri e altro ancora.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
