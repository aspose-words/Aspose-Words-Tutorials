---
date: 2026-01-16
description: Scopri come evidenziare gli errori ortografici in Word usando Aspose.Words
  per Java e impara a impostare i caratteri per riga, personalizzare le opzioni di
  visualizzazione e pulire gli stili.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Evidenzia gli errori ortografici in Word con Aspose.Words Java
url: /it/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo delle Opzioni e delle Impostazioni del Documento in Aspose.Words per Java

## Introduzione all'Utilizzo delle Opzioni e delle Impostazioni del Documento in Aspose.Words per Java

In questa guida completa, imparerai **come evidenziare gli errori ortografici in Word** usando Aspose.Words per Java, oltre a padroneggiare impostazioni correlate come le opzioni di visualizzazione, il layout di pagina e la pulizia degli stili. Che tu sia uno sviluppatore esperto o alle prime armi, gli esempi seguenti ti aiuteranno a creare documenti robusti e consapevoli degli errori, compatibili con le diverse versioni di Word.

## Risposte Rapide
- **Come posso evidenziare gli errori ortografici in Word?** Usa `setShowSpellingErrors(true)` sull'oggetto `Document`.  
- **Posso anche mostrare gli errori grammaticali?** Sì—chiama `setShowGrammaticalErrors(true)`.  
- **Quale metodo imposta i caratteri per riga?** `getPageSetup().setCharactersPerLine(int)`.  
- **Quale API ottimizza per una versione specifica di Word?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Esiste un modo per pulire gli stili non utilizzati?** Usa `CleanupOptions` con `setUnusedStyles(true)` e chiama `doc.cleanup(options)`.

## Come evidenziare gli errori ortografici in Word?

Aspose.Words rende semplice attivare l'evidenziazione degli errori ortografici. Quando il documento viene aperto in Microsoft Word, le parole errate appaiono con la classica sottolineatura rossa, aiutando gli utenti a individuare i problemi immediatamente.

## Come impostare i caratteri per riga

Controllare il numero di caratteri per riga è essenziale per layout a larghezza fissa (ad es. elenchi di codice o moduli legacy). La classe `PageSetup` fornisce `setCharactersPerLine(int)` che consente di definire questo valore con precisione.

## Come mostrare gli errori grammaticali

Oltre all'ortografia, è possibile abilitare la visualizzazione degli errori grammaticali. Questo è utile per redigere contenuti che devono rispettare guide di stile o per creare strumenti di correzione bozze.

## Ottimizzazione dei Documenti per la Compatibilità

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

Un aspetto chiave della gestione dei documenti è garantire la compatibilità con le diverse versioni di Microsoft Word. Aspose.Words per Java offre un modo semplice per ottimizzare i documenti per versioni specifiche di Word. Nell'esempio sopra, ottimizziamo un documento per Word 2016, assicurando una compatibilità senza problemi.

## Identificazione di Errori Grammaticali e Ortografici

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

L'accuratezza è fondamentale quando si lavora con i documenti. Aspose.Words per Java consente di evidenziare errori grammaticali e ortografici all'interno dei documenti, rendendo la correzione e la modifica più efficienti.

## Pulizia di Stili e Elenchi Non Utilizzati

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

Gestire in modo efficiente gli stili e gli elenchi dei documenti è essenziale per mantenere la coerenza. Aspose.Words per Java permette di pulire gli stili e gli elenchi non utilizzati, garantendo una struttura del documento snella e organizzata.

## Rimozione di Stili Duplicati

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

Gli stili duplicati possono causare confusione e incoerenza nei documenti. Con Aspose.Words per Java, è possibile rimuovere facilmente gli stili duplicati, mantenendo chiarezza e coerenza.

## Personalizzazione delle Opzioni di Visualizzazione del Documento

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

Personalizzare l'esperienza di visualizzazione dei documenti è cruciale. Aspose.Words per Java consente di impostare varie opzioni di visualizzazione, come il layout di pagina e la percentuale di zoom, per migliorare la leggibilità del documento.

## Configurazione del Layout di Pagina del Documento

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

Una configurazione precisa della pagina è fondamentale per la formattazione del documento. Aspose.Words per Java ti permette di impostare modalità di layout, **caratteri per riga** e linee per pagina, assicurando che i documenti siano esteticamente gradevoli.

## Impostazione delle Lingue di Modifica

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

Le lingue di modifica svolgono un ruolo fondamentale nell'elaborazione dei documenti. Con Aspose.Words per Java, puoi impostare e personalizzare le lingue di modifica per soddisfare le esigenze linguistiche del tuo documento.

## Conclusione

In questa guida abbiamo approfondito le varie opzioni e impostazioni del documento disponibili in Aspose.Words per Java. Dall'ottimizzazione e visualizzazione degli errori alla pulizia degli stili e alle opzioni di visualizzazione, questa potente libreria offre capacità estese per gestire e personalizzare i tuoi documenti.

## FAQ's

### Come ottimizzo un documento per una versione specifica di Word?

Per ottimizzare un documento per una versione specifica di Word, utilizza il metodo `optimizeFor` e specifica la versione desiderata. Ad esempio, per ottimizzare per Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### Come posso evidenziare gli errori grammaticali e ortografici in un documento?

Puoi abilitare la visualizzazione degli errori grammaticali e ortografici in un documento usando il seguente codice:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### Qual è lo scopo della pulizia di stili e elenchi non utilizzati?

La pulizia di stili e elenchi non utilizzati aiuta a mantenere una struttura del documento pulita e organizzata. Rimuove elementi superflui, migliorando la leggibilità e la coerenza del documento.

### Come posso rimuovere gli stili duplicati da un documento?

Per rimuovere gli stili duplicati da un documento, utilizza il metodo `cleanup` con l'opzione `duplicateStyle` impostata su `true`. Ecco un esempio:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### Come personalizzo le opzioni di visualizzazione per un documento?

Puoi personalizzare le opzioni di visualizzazione del documento usando la classe `ViewOptions`. Ad esempio, per impostare il tipo di visualizzazione su layout di pagina e lo zoom al 50%:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Suggerimenti Aggiuntivi & Trappole Comuni

- **Abilita sia il controllo ortografico che grammaticale** quando hai bisogno di una correzione completa. Dimenticare uno dei flag (`setShowGrammaticalErrors` o `setShowSpellingErrors`) può far passare inosservati degli errori.  
- **Quando imposti i caratteri per riga**, ricorda che il valore interagisce con il font selezionato e i margini della pagina. Testa con il layout reale del documento per evitare interruzioni di riga inattese.  
- **Le operazioni di pulizia sono irreversibili** sul file originale. Lavora sempre su una copia o utilizza il controllo di versione per preservare lo stile originale.  
- **Le preferenze della lingua di modifica** influenzano il comportamento del correttore ortografico. Se lavori con documenti multilingue, aggiungi tutte le lingue rilevanti a `LanguagePreferences`.

---

**Ultimo Aggiornamento:** 2026-01-16  
**Testato Con:** Aspose.Words per Java 24.12  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}