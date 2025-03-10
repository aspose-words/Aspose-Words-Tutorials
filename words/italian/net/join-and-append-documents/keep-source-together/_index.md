---
title: Mantieni il tavolo unito
linktitle: Mantieni il tavolo unito
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come impedire che le tabelle si dividano tra le pagine usando Aspose.Words per .NET con questa guida passo-passo. Garantisci documenti Word ordinati e dall'aspetto professionale
weight: 10
url: /it/net/join-and-append-documents/keep-source-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mantieni il tavolo unito

## Introduzione

Le tabelle sono una parte essenziale di molti documenti Word, ma a volte potresti imbatterti in una situazione in cui la tua tabella si divide su due pagine. Ciò può interrompere il flusso del tuo documento e comprometterne la leggibilità. Non sarebbe bello se ci fosse un modo per tenere insieme l'intera tabella in una pagina? Bene, con Aspose.Words per .NET, c'è una soluzione semplice a questo problema! In questo tutorial, ti mostreremo come impedire che le tabelle si dividano su più pagine, assicurandoti che il tuo documento abbia un aspetto ordinato e professionale.

## Prerequisiti

Prima di iniziare il tutorial, assicuriamoci che tu abbia tutto il necessario per seguirlo senza problemi.

### Aspose.Words per la libreria .NET

Per prima cosa, devi avere installato Aspose.Words per .NET. Questa è la potente libreria che ti consente di lavorare con i documenti Word a livello di programmazione.

- [Scarica Aspose.Words per .NET](https://releases.aspose.com/words/net/)

### Ambiente di sviluppo

Dovresti avere un ambiente di sviluppo configurato per eseguire il codice C#, come:

- Visual Studio (qualsiasi versione recente)
- .NET Framework 2.0 o versione successiva

### Un documento Word con una tabella

 Avrai bisogno di un documento Word che contenga una tabella. In questo tutorial, lavoreremo con un documento di esempio chiamato`"Table spanning two pages.docx"`Questo file contiene una tabella che attualmente si estende su due pagine.

### Licenza temporanea (facoltativa)

 Sebbene Aspose.Words sia disponibile con una prova gratuita, potresti voler utilizzare un[licenza temporanea](https://purchase.aspose.com/temporary-license/) per sfruttare appieno il potenziale della biblioteca.

## Importa pacchetti

Prima di scrivere qualsiasi codice, dobbiamo importare i namespace necessari per lavorare con Aspose.Words per .NET. Aggiungi le seguenti importazioni all'inizio del tuo file di codice:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

 Questi namespace ti danno accesso a classi come`Document`, `Table`, `Cell`e altri che utilizzeremo in questo tutorial.

## Passaggio 1: caricare il documento

 La prima cosa che dobbiamo fare è caricare il documento Word che contiene la tabella. Per questo, useremo il`Document` classe da Aspose.Words. Questa classe consente di aprire e manipolare file Word a livello di programmazione.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

 In questo frammento di codice, specifichiamo la posizione del nostro documento. Sostituisci`"YOUR DOCUMENTS DIRECTORY"` con la directory effettiva in cui è archiviato il documento.

## Passaggio 2: accedi alla tabella

Una volta caricato il documento, il passo successivo è accedere alla tabella che vogliamo tenere insieme. In questo esempio, supponiamo che la tabella sia la prima tabella nel documento.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

 Questa riga di codice trova la prima tabella nel documento.`GetChild` il metodo recupera un tipo specifico di nodo, che in questo caso è`NodeType.Table` . IL`0` indica che vogliamo la prima tabella e la`true`flag garantisce che la ricerca venga effettuata ricorsivamente in tutti i nodi figlio.

## Passaggio 3: scorrere le celle della tabella

Ora, dobbiamo scorrere ogni cella della tabella. Poiché una tabella contiene più righe e ogni riga contiene più celle, scorreremo ogni cella e ci assicureremo che non si interrompa tra le pagine.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

 Qui,`GetChildNodes` recupera tutte le celle nella tabella e noi eseguiamo un ciclo attraverso ciascuna di esse. Il`EnsureMinimum()` Il metodo garantisce che ogni cella contenga almeno un paragrafo, poiché una cella vuota potrebbe causare problemi in seguito.

## Passaggio 4: impostare la proprietà KeepWithNext

 Per evitare che la tabella si divida tra le pagine, dobbiamo impostare`KeepWithNext` proprietà per ogni paragrafo all'interno della tabella. Questa proprietà assicura che il paragrafo rimanga con il paragrafo successivo, impedendo efficacemente le interruzioni di pagina tra di essi.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

 Questo ciclo controlla ogni paragrafo all'interno di ogni cella. La condizione assicura che non applichiamo il`KeepWithNext`proprietà all'ultimo paragrafo nell'ultima riga. Altrimenti, la proprietà non avrebbe alcun effetto poiché non c'è un paragrafo successivo.

## Passaggio 5: Salvare il documento

 Infine, dopo aver applicato il`KeepWithNext` proprietà, dobbiamo salvare il documento modificato.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Questa riga salva il documento aggiornato con un nuovo nome, preservando il file originale. Ora puoi aprire il file risultante e vedere che la tabella non è più divisa su due pagine!

## Conclusione

Ed ecco fatto! Seguendo questi semplici passaggi, puoi facilmente impedire che le tabelle si dividano tra le pagine nei documenti Word utilizzando Aspose.Words per .NET. Che tu stia lavorando su report, contratti o altri documenti, mantenere le tabelle intatte assicura un aspetto più curato e professionale.

La bellezza di Aspose.Words è la sua flessibilità e facilità d'uso, che ti consente di manipolare i documenti Word in modo programmatico senza dover installare Microsoft Word sul tuo computer. Ora che hai capito come tenere insieme le tabelle, esplora altre funzionalità della libreria per portare le tue capacità di elaborazione dei documenti a un livello superiore!

## Domande frequenti

### Perché la mia tabella continua a dividersi tra le pagine dopo aver utilizzato questo codice?

 Se il tuo tavolo si rompe ancora, assicurati di aver applicato il`KeepWithNext` proprietà correttamente. Controlla due volte che tutti i paragrafi, eccetto l'ultimo, in ogni cella abbiano questa proprietà impostata.

### Posso tenere insieme solo righe specifiche?

 Sì, puoi applicare selettivamente il`KeepWithNext` proprietà a righe o paragrafi specifici all'interno della tabella per controllare quali parti devono rimanere insieme.

### Questo metodo funziona con tabelle di grandi dimensioni?

Per tabelle molto grandi, Word potrebbe comunque suddividerle su più pagine se non c'è abbastanza spazio per contenere l'intera tabella in una pagina. Valuta di modificare la formattazione o i margini della tabella per adattarla a tabelle più grandi.

### Posso usare questo metodo con altri formati di documenti?

Sì! Aspose.Words per .NET supporta molti formati come DOC, DOCX, PDF e altri. Lo stesso metodo funziona in tutti i formati che supportano le tabelle.

### Aspose.Words per .NET è una libreria gratuita?

 Aspose.Words per .NET offre una prova gratuita, ma per l'accesso completo a tutte le funzionalità, dovrai acquistare una licenza. Puoi esplorare le opzioni di licenza su[Pagina di acquisto Aspose](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
