---
category: general
date: 2026-05-04
description: Il tutorial sulla sostituzione dei font di Aspose mostra come gestire
  i font mancanti in Java usando callback di avviso e LoadOptions per un caricamento
  affidabile dei documenti.
draft: false
keywords:
- aspose font substitution tutorial
- handle missing fonts
- Aspose.Words font warning callback
- Java LoadOptions warning handling
- missing font detection Aspose
language: it
og_description: Il tutorial sulla sostituzione dei font di Aspose spiega come gestire
  i font mancanti in Java, catturare gli eventi di sostituzione e mantenere i documenti
  corretti.
og_title: Tutorial di sostituzione dei font Aspose – Gestire i font mancanti
tags:
- Aspose.Words
- Java
- Font Management
title: Tutorial sulla sostituzione dei font Aspose – Gestire i font mancanti
url: /it/java/document-loading-and-saving/aspose-font-substitution-tutorial-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutorial di Sostituzione Font Aspose – Gestire i Font Mancanti

Hai mai avuto bisogno di un **aspose font substitution tutorial** perché un DOCX che carichi appare improvvisamente sbagliato? Non sei solo—i font mancanti sono una fonte subdola di bug che può trasformare un report perfettamente formattato in un caos confuso. La buona notizia è che Aspose.Words ti offre un modo pulito per **gestire i font mancanti** prima che rompano il layout.

In questa guida percorreremo un esempio Java completo, pronto‑da‑eseguire, che cattura gli avvisi di sostituzione dei font, spiega perché ogni parte è importante e ti mostra come verificare il risultato. Alla fine saprai esattamente come mantenere i documenti nitidi anche quando i caratteri originali non sono presenti sulla macchina.

## Cosa Imparerai

- Come registrare un `IWarningCallback` personalizzato che ascolta gli eventi `FONT_SUBSTITUTION`.  
- Perché usare `LoadOptions` è l’approccio consigliato per una gestione affidabile dei font.  
- Modi per testare la soluzione con un documento deliberatamente danneggiato.  
- Trappole comuni (ad esempio, dimenticare di impostare il callback) e soluzioni rapide.  

**Prerequisiti**: Java 8+ installato, una licenza valida di Aspose.Words for Java (o la valutazione gratuita) e un IDE di base come IntelliJ o Eclipse. Non sono necessarie altre librerie esterne.

---

![Aspose font substitution tutorial diagram](https://example.com/images/font-substitution-diagram.png "Aspose font substitution tutorial diagram")

## Passo 1 – Definisci un Warning Callback per Catturare le Sostituzioni  

La prima cosa che fa Aspose.Words quando non riesce a trovare un font richiesto è generare un evento `WarningInfo`. Implementando `IWarningCallback` puoi registrare, visualizzare o persino abortire il caricamento se lo desideri.

```java
// Step 1: Create a callback that prints font‑substitution warnings
class FontWarningCollector implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
}
```

**Perché è importante** – Senza un callback non sapresti mai che Aspose ha sostituito *Arial* con *Liberation Sans* (o qualsiasi fallback scelto). Questa sostituzione silenziosa può causare spostamenti di layout, specialmente in tabelle o layout a più colonne.

---

## Passo 2 – Collega il Callback a `LoadOptions`

`LoadOptions` è il punto centrale per tutto ciò che influenza il modo in cui un documento viene letto. Collegando il callback qui garantisci che **qualsiasi** documento caricato con queste opzioni attivi la tua logica di avviso.

```java
// Step 2: Wire the callback into LoadOptions
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontWarningCollector());
```

**Suggerimento** – Se prevedi di caricare diversi documenti in batch, riutilizza la stessa istanza di `LoadOptions`. Riduce il sovraccarico di creazione degli oggetti e mantiene coerente il tuo logging.

---

## Passo 3 – Carica un Documento Che Potrebbe Richiedere la Sostituzione dei Font  

Ora leggiamo effettivamente un file di cui sappiamo che manca un font. Sostituisci `YOUR_DIRECTORY` con la cartella che contiene i tuoi file di test.

```java
// Step 3: Load a document that deliberately references a missing font
String inputPath = "YOUR_DIRECTORY/missing-font.docx";
Document doc = new Document(inputPath, loadOptions);
```

Quando il loader incontra un glifo che non può essere renderizzato, il callback del **Passo 1** stampa un messaggio amichevole sulla console. Per esempio:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

**Caso limite** – Se il documento contiene font *incorporati*, Aspose li utilizzerà prima e salterà l’avviso. È il comportamento previsto; gli avvisi compaiono solo per i font realmente mancanti.

---

## Passo 4 – Salva il Documento (Ora con i Font Sostituiti)

Dopo il caricamento, Aspose ha già sostituito internamente i font mancanti. Salvare il documento preserva la sostituzione, così l’output appare esattamente come quello mostrato sulla console.

```java
// Step 4: Persist the document – the fonts are already substituted if needed
String outputPath = "YOUR_DIRECTORY/loaded.docx";
doc.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Apri `loaded.docx` in Word o LibreOffice e vedrai il layout invariato, anche se il font originale non è installato sulla tua macchina.

---

## Passo 5 – Verifica il Risultato Programmaticamente (Opzionale)

Se vuoi essere ancora più sicuro che non siano sfuggite sostituzioni inattese, puoi interrogare la tabella dei font del documento dopo il caricamento.

```java
// Optional: List all fonts actually used in the saved document
for (FontInfo fontInfo : doc.getFontInfos()) {
    System.out.println("Used font: " + fontInfo.getFontName());
}
```

L’output dovrebbe contenere il font di fallback (ad es., *Arial*) al posto di quello mancante. È utile per pipeline automatizzate dove è necessario garantire che il PDF o DOCX finale rispetti i requisiti di branding.

---

## Pro Tips & Common Pitfalls

- **Pro tip:** Imposta `loadOptions.setFontSettings(new FontSettings())` se devi indicare ad Aspose una cartella di font personalizzata prima del caricamento. Questo riduce il numero di sostituzioni.  
- **Attenzione a:** Dimenticare di chiamare `setWarningCallback`. Il codice verrà comunque eseguito, ma perderai i messaggi diagnostici cruciali.  
- **Nota sulle prestazioni:** Caricare documenti di grandi dimensioni con molti font mancanti può generare numerosi avvisi. Considera di limitare l’output o scrivere su un file di log invece di `System.out`.  
- **E se vuoi abortire alla sostituzione?** Sostituisci la chiamata `System.out.println` con `throw new RuntimeException(info.getDescription())` all’interno del callback. Questo forza il fallimento del caricamento, utile in scenari di conformità rigorosa.

---

## Frequently Asked Questions

**D: Questo funziona con formati PDF o immagine?**  
R: Il callback di avviso è specifico alla fase di caricamento dei formati di elaborazione Word (`.docx`, `.doc`, `.rtf`, ecc.). Il rendering PDF utilizza una pipeline diversa, ma è comunque possibile catturare avvisi relativi ai font tramite `PdfLoadOptions`.

**D: Posso sostituire un font specifico con un altro a mia scelta?**  
R: Sì. Crea un oggetto `FontSettings`, chiama `fontSettings.getSubstitutionSettings().getTableSubstitutes().addSubstitutes("MissingFont", "MyPreferredFont")` e assegnalo a `loadOptions.setFontSettings(fontSettings)`.

**D: Il callback è thread‑safe?**  
R: L’implementazione predefinita non è sincronizzata. Se carichi documenti in parallelo, assicurati che la tua implementazione del callback gestisca l’accesso concorrente (ad es., usando `ConcurrentLinkedQueue` per il logging).

---

## Conclusione

Ora hai a disposizione un **aspose font substitution tutorial** completo che mostra come **gestire i font mancanti** in modo elegante in Java. Definendo un `IWarningCallback` personalizzato, collegandolo a `LoadOptions` e salvando il documento, mantieni l’output coerente indipendentemente dai font installati sulla macchina host.  

Da qui potresti esplorare:

- Tabelle di sostituzione dei font personalizzate per sostituzioni conformi al brand.  
- Integrazione del logger di avvisi con SLF4J o Log4j per diagnostica di livello produzione.  
- Estensione del callback per raccogliere statistiche su un batch di documenti.

Provalo, modifica i font di fallback e lascia che i tuoi documenti rimangano splendidi anche quando i caratteri originali scompaiono. Buon coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}