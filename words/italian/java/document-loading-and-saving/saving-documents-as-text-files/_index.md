---
title: Salvataggio di documenti come file di testo in Aspose.Words per Java
linktitle: Salvataggio dei documenti come file di testo
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Scopri come salvare i documenti come file di testo in Aspose.Words per Java. Segui la nostra guida passo passo con esempi di codice Java.
weight: 24
url: /it/java/document-loading-and-saving/saving-documents-as-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvataggio di documenti come file di testo in Aspose.Words per Java


## Introduzione al salvataggio di documenti come file di testo in Aspose.Words per Java

In questo tutorial, esploreremo come salvare i documenti come file di testo usando la libreria Aspose.Words per Java. Aspose.Words è una potente API Java per lavorare con i documenti Word e fornisce varie opzioni per salvare i documenti in diversi formati, incluso il testo normale. Tratteremo i passaggi per raggiungere questo obiettivo e forniremo un codice Java di esempio lungo il percorso.

## Prerequisiti

Prima di iniziare, assicurati di avere i seguenti prerequisiti:

- Java Development Kit (JDK) installato sul sistema.
-  Aspose.Words per la libreria Java integrata nel tuo progetto. Puoi scaricarla da[Qui](https://releases.aspose.com/words/java/).
- Conoscenza di base della programmazione Java.

## Passaggio 1: creare un documento

Per salvare un documento come file di testo, dobbiamo prima creare un documento usando Aspose.Words. Ecco un semplice frammento di codice Java per creare un documento con del contenuto:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

In questo codice creiamo un nuovo documento e vi aggiungiamo del testo, anche in diverse lingue.

## Passaggio 2: definire le opzioni di salvataggio del testo

Successivamente, dobbiamo definire le opzioni di salvataggio del testo che specificano come il documento deve essere salvato come file di testo. Possiamo configurare varie impostazioni come l'aggiunta di segni bidi, indentazione di elenco e altro. Diamo un'occhiata a due esempi:

### Esempio 1: aggiunta di segni Bidi

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

 In questo esempio, creiamo un`TxtSaveOptions` oggetto e imposta il`AddBidiMarks`proprietà a`true` per includere i segni bidi nel testo in uscita.

### Esempio 2: utilizzo del carattere di tabulazione per l'indentazione dell'elenco

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Qui configuriamo le opzioni di salvataggio per utilizzare un carattere di tabulazione per l'indentazione dell'elenco con un conteggio pari a 1.

## Passaggio 3: Salvare il documento come testo

Ora che abbiamo definito le opzioni di salvataggio del testo, possiamo salvare il documento come file di testo. Il seguente codice mostra come farlo:

```java
doc.save("output.txt", saveOptions);
```

 Sostituire`"output.txt"` con il percorso desiderato in cui si desidera salvare il file di testo.

## Codice sorgente completo per salvare documenti come file di testo in Aspose.Words per Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Crea un elenco con tre livelli di rientro.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Crea un elenco con tre livelli di rientro.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Conclusione

In questo tutorial, abbiamo imparato come salvare i documenti come file di testo in Aspose.Words per Java. Abbiamo trattato i passaggi per creare un documento, definire le opzioni di salvataggio del testo e salvare il documento in formato testo. Aspose.Words offre un'ampia flessibilità quando si tratta di salvare i documenti, consentendo di adattare l'output alle proprie esigenze specifiche.

## Domande frequenti

### Come posso aggiungere i contrassegni bidi al testo in uscita?

 Per aggiungere segni bidi al testo in uscita, impostare`AddBidiMarks` proprietà di`TxtSaveOptions` A`true`. Per esempio:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Posso personalizzare il carattere di rientro dell'elenco?

 Sì, puoi personalizzare il carattere di rientro dell'elenco configurando`ListIndentation` proprietà di`TxtSaveOptions`Ad esempio, per utilizzare un carattere di tabulazione per l'indentazione dell'elenco, puoi procedere come segue:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words per Java è adatto alla gestione di testo multilingue?

Sì, Aspose.Words per Java è adatto per gestire testo multilingue. Supporta varie lingue e codifiche di caratteri, rendendolo una scelta versatile per lavorare con documenti in diverse lingue.

### Come posso accedere ad altra documentazione e risorse per Aspose.Words per Java?

 È possibile trovare documentazione e risorse complete per Aspose.Words per Java sul sito web della documentazione di Aspose:[Documentazione di Aspose.Words per Java](https://reference.aspose.com/words/java/).

### Dove posso scaricare Aspose.Words per Java?

 È possibile scaricare la libreria Aspose.Words per Java dal sito web di Aspose:[Scarica Aspose.Words per Java](https://releases.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
