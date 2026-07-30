---
date: 2025-12-24
description: Scopri come creare file di testo semplice da documenti Word utilizzando
  Aspose.Words per Java. Questa guida mostra come convertire Word in txt, utilizzare
  l'indentazione con tabulazioni e salvare Word come txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Come creare un file di testo semplice con Aspose.Words per Java
url: /it/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un file di testo semplice con Aspose.Words per Java

## Introduzione al salvataggio dei documenti come file di testo in Aspose.Words per Java

In questo tutorial imparerai **come creare un file di testo semplice** da un documento Word utilizzando la libreria Aspose.Words per Java. Che tu debba **convertire word in txt**, automatizzare la generazione di report o semplicemente estrarre testo grezzo per ulteriori elaborazioni, questa guida ti accompagna passo passo attraverso l’intero flusso di lavoro—dalla creazione del documento alla messa a punto delle opzioni di salvataggio come **uso dell’indentazione a tabulazione** o aggiunta di segni bidi. Iniziamo!

## Risposte rapide
- **Qual è la classe principale per creare un documento?** `Document` di Aspose.Words.  
- **Quale opzione aggiunge i segni bidi per le lingue da destra a sinistra?** `TxtSaveOptions.setAddBidiMarks(true)`.  
- **Come posso indentare gli elementi di elenco con tabulazioni?** Imposta `ListIndentation.Character` a `'\t'`.  
- **È necessaria una licenza per lo sviluppo?** Una versione di prova gratuita è sufficiente per i test; è richiesta una licenza per la produzione.  
- **Posso salvare il file con un nome e percorso personalizzati?** Sì—passa il percorso completo a `doc.save()`.

## Prerequisiti

Prima di iniziare, assicurati di avere i seguenti prerequisiti:

- Java Development Kit (JDK) installato sul tuo sistema.  
- Libreria Aspose.Words per Java integrata nel tuo progetto. Puoi scaricarla da [qui](https://releases.aspose.com/words/java/).  
- Conoscenze di base della programmazione Java.

## Passo 1: Creare un documento

Per **salvare word come txt**, dobbiamo prima ottenere un'istanza di `Document`. Di seguito trovi un semplice snippet Java che crea un documento e scrive alcune righe di testo multilingue:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

In questo codice creiamo un nuovo documento, aggiungiamo testo in inglese, ebraico e arabo, e abilitiamo la formattazione da destra a sinistra per il paragrafo ebraico.

## Passo 2: Definire le opzioni di salvataggio del testo

Successivamente configuriamo come il documento verrà salvato come file di testo semplice. Aspose.Words fornisce la classe `TxtSaveOptions`, che consente di controllare tutto, dai segni bidi all’indentazione degli elenchi.

### Esempio 1: Aggiunta di segni bidi (come salvare txt con corretto supporto RTL)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Impostare `AddBidiMarks` su `true` garantisce che i caratteri da destra a sinistra siano rappresentati correttamente nel **file di testo semplice** risultante.

### Esempio 2: Utilizzo del carattere di tabulazione per l’indentazione degli elenchi (uso dell’indentazione a tabulazione)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Qui diciamo ad Aspose.Words di anteporre un carattere di tabulazione (`'\t'`) prima di ogni livello di elenco, rendendo l’output di testo più leggibile.

## Passo 3: Salvare il documento come testo

Ora che le opzioni di salvataggio sono pronte, puoi persistere il documento come **file di testo semplice**:

```java
doc.save("output.txt", saveOptions);
```

Sostituisci `"output.txt"` con il percorso completo dove desideri che il file venga salvato.

## Codice completo per salvare documenti come file di testo in Aspose.Words per Java

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
        // Create a list with three levels of indentation.
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
        // Create a list with three levels of indentation.
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

## Problemi comuni e soluzioni

| Problema | Soluzione |
|----------|-----------|
| **I caratteri bidi appaiono come testo illeggibile** | Assicurati che `setAddBidiMarks(true)` sia abilitato e che il file di output sia aperto con codifica UTF‑8. |
| **L’indentazione dell’elenco è errata** | Verifica che `ListIndentation.Count` e `Character` siano impostati ai valori desiderati (tab `'\t'` o spazio `' '` ). |
| **Il file non viene creato** | Controlla che il percorso della directory esista e che l’applicazione abbia i permessi di scrittura. |

## Domande frequenti

### Come aggiungo i segni bidi all’output di testo?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Posso personalizzare il carattere di indentazione dell’elenco?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words per Java è adatto alla gestione di testo multilingue?

Sì, Aspose.Words per Java supporta un’ampia gamma di lingue e codifiche di caratteri, rendendolo ideale per estrarre e salvare contenuti multilingue come testo semplice.

### Come posso accedere a ulteriore documentazione e risorse per Aspose.Words per Java?

Puoi trovare documentazione completa e risorse nella pagina della Documentazione di Aspose.Words per Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Dove posso scaricare Aspose.Words per Java?

Puoi scaricare la libreria dal sito ufficiale: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### Cosa fare se devo **convertire word in txt** in un processo batch?

Avvolgi il codice mostrato sopra in un ciclo che carica ogni file `.docx`, applica le stesse `TxtSaveOptions` e salva ciascuno come `.txt`. Assicurati di gestire le risorse disponendo gli oggetti `Document` dopo ogni iterazione.

### L’API supporta il salvataggio diretto su stream invece che su file?

Sì, è possibile passare un `OutputStream` a `doc.save(outputStream, saveOptions)` per l’elaborazione in memoria o quando si integra con servizi web.

---

**Ultimo aggiornamento:** 2025-12-24  
**Testato con:** Aspose.Words per Java 24.12 (ultima versione)  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}