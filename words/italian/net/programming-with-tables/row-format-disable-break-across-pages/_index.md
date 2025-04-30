---
"description": "Scopri come disattivare le interruzioni di riga tra le pagine dei documenti Word utilizzando Aspose.Words per .NET per mantenere la leggibilità e la formattazione delle tabelle."
"linktitle": "Disabilita interruzione tra pagine nel formato riga"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Disabilita interruzione tra pagine nel formato riga"
"url": "/it/net/programming-with-tables/row-format-disable-break-across-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Disabilita interruzione tra pagine nel formato riga

## Introduzione

Quando si lavora con le tabelle nei documenti Word, potrebbe essere opportuno assicurarsi che le righe non si dividano tra le pagine, il che può essere essenziale per mantenere la leggibilità e la formattazione dei documenti. Aspose.Words per .NET offre un modo semplice per disabilitare le interruzioni di riga tra le pagine.

In questo tutorial ti guideremo attraverso il processo di disattivazione delle interruzioni di riga tra le pagine di un documento Word utilizzando Aspose.Words per .NET.

## Prerequisiti

Prima di iniziare, assicurati di avere i seguenti prerequisiti:
- Libreria Aspose.Words per .NET installata.
- Un documento Word con una tabella che si estende su più pagine.

## Importa spazi dei nomi

Per prima cosa, importa gli spazi dei nomi necessari nel tuo progetto:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Passaggio 1: caricare il documento

Caricare il documento contenente la tabella che si estende su più pagine.

```csharp
// Percorso alla directory dei documenti 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Passaggio 2: accedere alla tabella

Accedi alla prima tabella del documento. Questo presuppone che la tabella che desideri modificare sia la prima tabella del documento.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Passaggio 3: disabilitare la suddivisione tra pagine per tutte le righe

Passa attraverso ogni riga della tabella e imposta il `AllowBreakAcrossPages` proprietà a `false`In questo modo si garantisce che le righe non vengano divise tra le pagine.

```csharp
// Disattiva la suddivisione tra le pagine per tutte le righe della tabella.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Passaggio 4: salvare il documento

Salva il documento modificato nella directory specificata.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Conclusione

In questo tutorial, abbiamo mostrato come disabilitare le interruzioni di riga tra le pagine in un documento Word utilizzando Aspose.Words per .NET. Seguendo i passaggi descritti sopra, è possibile garantire che le righe della tabella rimangano intatte e non vengano suddivise tra le pagine, mantenendo la leggibilità e la formattazione del documento.

## Domande frequenti

### Posso disattivare le interruzioni di riga nelle pagine per una riga specifica anziché per tutte le righe?  
Sì, puoi disattivare le interruzioni di riga per righe specifiche accedendo alla riga desiderata e impostandone `AllowBreakAcrossPages` proprietà a `false`.

### Questo metodo funziona per le tabelle con celle unite?  
Sì, questo metodo funziona per le tabelle con celle unite. La proprietà `AllowBreakAcrossPages` si applica all'intera riga, indipendentemente dall'unione delle celle.

### Questo metodo funzionerà se la tabella è annidata all'interno di un'altra tabella?  
Sì, puoi accedere e modificare le tabelle nidificate allo stesso modo. Assicurati di fare riferimento correttamente alla tabella nidificata tramite il suo indice o altre proprietà.

### Come posso verificare se una riga consente la suddivisione in più pagine?  
È possibile verificare se una riga consente la suddivisione tra le pagine accedendo a `AllowBreakAcrossPages` proprietà del `RowFormat` e verificandone il valore.

### Esiste un modo per applicare questa impostazione a tutte le tabelle in un documento?  
Sì, puoi scorrere tutte le tabelle del documento e applicare questa impostazione a ciascuna di esse.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}