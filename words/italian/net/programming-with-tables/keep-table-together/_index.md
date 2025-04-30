---
"description": "Scopri come evitare che le tabelle si dividano tra le pagine nei documenti Word utilizzando Aspose.Words per .NET. Segui la nostra guida per mantenere documenti professionali e leggibili."
"linktitle": "Mantieni il tavolo unito"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Mantieni il tavolo unito"
"url": "/it/net/programming-with-tables/keep-table-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mantieni il tavolo unito

## Introduzione

Ti è mai capitato di sentirti frustrato quando una tabella in un documento Word si divide su due pagine? È come se le tue informazioni, così attentamente strutturate, avessero improvvisamente deciso di prendersi una pausa a metà! Mantenere le tabelle unite su una sola pagina è fondamentale per la leggibilità e la presentazione. Che si tratti di un report, di una proposta di progetto o semplicemente di un documento personale, avere le tabelle divise può essere piuttosto fastidioso. Fortunatamente, Aspose.Words per .NET offre un modo ingegnoso per risolvere questo problema. In questo tutorial, ti guideremo passo dopo passo per mantenere le tue tabelle intatte e dall'aspetto impeccabile. Iniziamo!

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1. Aspose.Words per .NET - Se non lo hai ancora installato, puoi scaricarlo da [Qui](https://releases.aspose.com/words/net/).
2. Un documento Word con una tabella: lavoreremo con un documento di esempio contenente una tabella che si estende su più pagine.
3. Conoscenza di base di C#: questo tutorial presuppone una conoscenza di base della programmazione C#.

## Importa spazi dei nomi

Per prima cosa, importiamo gli spazi dei nomi necessari. Questo ci darà accesso alle classi e ai metodi di cui abbiamo bisogno da Aspose.Words per .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Suddividiamo il processo in passaggi semplici e comprensibili. Inizieremo caricando il nostro documento e termineremo salvando il documento aggiornato, dove la tabella rimane unita.

## Passaggio 1: caricare il documento

Per lavorare con un documento Word, dobbiamo prima caricarlo. Useremo il `Document` classe per questo.

```csharp
// Percorso alla directory dei documenti
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Passaggio 2: accedere alla tabella

Ora dobbiamo trovare la tabella che vogliamo mantenere unita. Supponiamo che sia la prima tabella del documento.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Passaggio 3: imposta KeepWithNext per i paragrafi

Per evitare che la tabella si divida tra le pagine, dobbiamo impostare `KeepWithNext` proprietà per ogni paragrafo della tabella, ad eccezione degli ultimi paragrafi dell'ultima riga.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## Passaggio 4: salvare il documento

Infine, salviamo il documento aggiornato. Questo applicherà le modifiche e garantirà che la tabella rimanga unita su un'unica pagina.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Conclusione

Ed ecco fatto! Con poche righe di codice, puoi evitare che le tabelle si dividano tra le pagine dei tuoi documenti Word. Questa soluzione semplice ma efficace garantisce che le tue tabelle rimangano ordinate e professionali, migliorando la leggibilità dei tuoi documenti. Aspose.Words per .NET semplifica la gestione di questi problemi di formattazione, permettendoti di concentrarti sulla creazione di contenuti di qualità.

## Domande frequenti

### Posso tenere insieme più tabelle usando questo metodo?  
Sì, puoi applicare la stessa logica a più tabelle eseguendo un'iterazione su ogni tabella nel tuo documento.

### Cosa succede se la mia tabella è troppo grande per stare su una sola pagina?  
Se una tabella è troppo grande per essere contenuta in una sola pagina, si estenderà comunque su più pagine. Questo metodo garantisce che le tabelle più piccole rimangano intatte senza essere divise.

### Esiste un modo per automatizzare questa operazione per tutte le tabelle in un documento?  
Sì, puoi scorrere tutte le tabelle nel tuo documento e applicare il `KeepWithNext` proprietà a ciascun paragrafo.

### Ho bisogno di una licenza a pagamento per Aspose.Words per .NET?  
Puoi iniziare con una prova gratuita da [Qui](https://releases.aspose.com/), ma per una funzionalità completa si consiglia una licenza a pagamento.

### Posso applicare altre formattazioni alla tabella mantenendola unita?  
Assolutamente! Puoi formattare la tabella come preferisci, assicurandoti che rimanga unita su un'unica pagina.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}