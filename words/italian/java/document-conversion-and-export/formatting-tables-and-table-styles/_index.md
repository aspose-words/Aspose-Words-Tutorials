---
date: 2025-11-28
description: Scopri come modificare i bordi delle celle e formattare le tabelle con
  Aspose.Words per Java. Questa guida passo passo copre l'impostazione dei bordi,
  l'applicazione dello stile prima colonna, l'adattamento automatico del contenuto
  della tabella e l'applicazione degli stili di tabella.
language: it
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: Come modificare i bordi delle celle nelle tabelle – Aspose.Words per Java
url: /java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Come modificare i bordi delle celle nelle tabelle – Aspose.Words per Java

## Introduzione

Quando si tratta di formattare i documenti, le tabelle svolgono un ruolo cruciale, e **sapere come modificare i bordi delle celle** è essenziale per creare layout chiari e professionali. Se sviluppi in Java con Aspose.Words, hai già a disposizione un potente toolkit. In questo tutorial percorreremo l’intero processo di formattazione delle tabelle, modifica dei bordi delle celle, applicazione dello *stile prima colonna* e utilizzo dell’*auto‑fit dei contenuti della tabella* per rendere i tuoi documenti impeccabili.

## Risposte rapide
- **Qual è la classe principale per creare tabelle?** `DocumentBuilder` crea tabelle e celle programmaticamente.  
- **Come cambio lo spessore del bordo di una singola cella?** Usa `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Posso applicare uno stile di tabella predefinito?** Sì – chiama `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **Quale metodo adatta automaticamente una tabella al suo contenuto?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **È necessaria una licenza per la produzione?** È richiesta una licenza valida di Aspose.Words per l’uso non‑trial.

## Cos’è “come modificare i bordi delle celle” in Aspose.Words?

Modificare i bordi delle celle significa personalizzare le linee visive che separano le celle—colore, larghezza e stile della linea. Aspose.Words espone un’API ricca che consente di regolare queste proprietà a livello di tabella, riga o singola cella, offrendo un controllo granulare sull’aspetto dei documenti.

## Perché usare Aspose.Words per Java per lo styling delle tabelle?

- **Aspetto coerente su tutte le piattaforme** – lo stesso codice di styling funziona su Windows, Linux e macOS.  
- **Nessuna dipendenza da Microsoft Word** – genera o modifica documenti lato server.  
- **Libreria di stili ricca** – stili di tabella integrati (ad es. *stile prima colonna*) e capacità complete di auto‑fit.  

## Prerequisiti

1. **Java Development Kit (JDK) 8+** – assicurati che `java` sia nel tuo PATH.  
2. **IDE** – IntelliJ IDEA, Eclipse o qualsiasi editor tu preferisca.  
3. **Aspose.Words per Java** – scarica l’ultimo JAR dal [sito ufficiale](https://releases.aspose.com/words/java/).  
4. **Conoscenza di base di Java** – dovresti sentirti a tuo agio a creare un progetto Maven/Gradle e aggiungere JAR esterni.

## Importare i pacchetti

Per iniziare a lavorare con le tabelle è necessario le classi core di Aspose.Words:

```java
import com.aspose.words.*;
```

Questa singola importazione ti dà accesso a `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` e molte altre utility.

## Come modificare i bordi delle celle

Di seguito creeremo una tabella semplice, modificheremo i bordi generali, quindi personalizzeremo le singole celle.

### Passo 1: Caricare un nuovo documento

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Passo 2: Creare la tabella e impostare i bordi globali

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Passo 3: Modificare i bordi di una singola cella

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### Cosa fa il codice
- **Bordi globali** – `table.setBorders` assegna all’intera tabella una linea nera di 2 punti.  
- **Ombreggiatura delle celle** – Dimostra come colorare singole celle (rosso e verde).  
- **Bordi personalizzati delle celle** – La terza cella riceve un bordo di 4 punti su tutti i lati, facendola risaltare.

## Applicare gli stili di tabella (incluso lo stile Prima colonna)

Gli stili di tabella ti consentono di applicare un aspetto coerente con una singola chiamata. Mostreremo anche come abilitare lo *stile prima colonna* e adattare automaticamente la tabella al suo contenuto.

### Passo 4: Creare un nuovo documento per lo styling

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Passo 5: Applicare uno stile predefinito e abilitare la formattazione della prima colonna

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Passo 6: Popolare la tabella con i dati

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Perché è importante
- **Identificatore di stile** – `MEDIUM_SHADING_1_ACCENT_1` conferisce alla tabella un aspetto pulito e ombreggiato.  
- **Stile prima colonna** – Evidenziare la prima colonna migliora la leggibilità, soprattutto nei report.  
- **Bande di riga** – Le righe alternate con colori diversi rendono le tabelle grandi più facili da leggere.  
- **Auto‑fit** – Garantisce che la larghezza della tabella si adatti al contenuto, evitando testo troncato.

## Problemi comuni e risoluzione

| Problema | Causa tipica | Correzione rapida |
|----------|--------------|-------------------|
| I bordi non compaiono | Uso di `clearFormatting()` dopo aver impostato i bordi | Imposta i bordi **dopo** aver cancellato la formattazione, o riapplicali. |
| L’ombreggiatura ignorata su celle unite | Ombreggiatura applicata prima dell’unione | Applica l’ombreggiatura **dopo** aver unito le celle. |
| La larghezza della tabella supera i margini della pagina | Nessun auto‑fit applicato | Chiama `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` o imposta una larghezza fissa. |
| Lo stile non viene applicato | Valore di `StyleIdentifier` errato | Verifica che l’identificatore esista nella versione di Aspose.Words in uso. |

## Domande frequenti

**D: Posso usare stili di tabella personalizzati non inclusi nelle opzioni predefinite?**  
R: Sì, puoi creare e applicare stili personalizzati programmaticamente. Consulta la [documentazione di Aspose.Words](https://reference.aspose.com/words/java/) per i dettagli.

**D: Come posso applicare formattazione condizionale alle celle?**  
R: Usa la logica Java standard per ispezionare i valori delle celle, quindi chiama i metodi di formattazione appropriati (ad es. cambia il colore di sfondo se un valore supera una soglia).

**D: È possibile formattare le celle unite allo stesso modo delle celle normali?**  
R: Assolutamente. Dopo aver unito le celle, applica ombreggiatura o bordi usando le stesse API `CellFormat`.

**D: Cosa fare se la tabella deve ridimensionarsi dinamicamente in base all’input dell’utente?**  
R: Regola le larghezze delle colonne o chiama nuovamente `autoFit` dopo aver inserito nuovi dati per ricalcolare il layout.

**D: Dove posso trovare altri esempi di styling delle tabelle?**  
R: La [documentazione ufficiale dell’Aspose.Words API](https://reference.aspose.com/words/java/) contiene un set completo di esempi.

## Conclusione

Ora disponi di un set completo di strumenti per **modificare i bordi delle celle**, applicare lo *stile prima colonna* e **adattare automaticamente i contenuti della tabella** usando Aspose.Words per Java. Padroneggiando queste tecniche potrai produrre documenti ricchi di dati e visivamente accattivanti—perfetti per report, fatture e qualsiasi output aziendale critico.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Ultimo aggiornamento:** 2025-11-28  
**Testato con:** Aspose.Words per Java 24.12 (ultima versione al momento della stesura)  
**Autore:** Aspose