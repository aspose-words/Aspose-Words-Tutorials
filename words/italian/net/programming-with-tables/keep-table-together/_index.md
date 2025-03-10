---
title: Mantieni il tavolo unito
linktitle: Mantieni il tavolo unito
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come impedire che le tabelle si dividano tra le pagine nei documenti Word usando Aspose.Words per .NET. Segui la nostra guida per mantenere documenti professionali e leggibili.
weight: 10
url: /it/net/programming-with-tables/keep-table-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mantieni il tavolo unito

## Introduzione

Ti sei mai sentito frustrato quando una tabella nel tuo documento Word si divide su due pagine? È come se le tue informazioni attentamente disposte avessero improvvisamente deciso di prendersi una pausa a metà! Mantenere le tabelle insieme su una pagina è fondamentale per la leggibilità e la presentazione. Che si tratti di un report, di una proposta di progetto o semplicemente di un documento personale, avere le tabelle divise può essere piuttosto stridente. Fortunatamente per noi, Aspose.Words per .NET ha un modo ingegnoso per risolvere questo problema. In questo tutorial, ti guideremo attraverso i passaggi per mantenere le tue tabelle intatte e dall'aspetto nitido. Tuffiamoci!

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1.  Aspose.Words per .NET - Se non lo hai ancora installato, puoi scaricarlo da[Qui](https://releases.aspose.com/words/net/).
2. Un documento Word con una tabella: lavoreremo con un documento di esempio che contiene una tabella che si estende su più pagine.
3. Conoscenza di base di C#: questo tutorial presuppone una conoscenza di base della programmazione in C#.

## Importazione degli spazi dei nomi

Per prima cosa, importiamo i namespace necessari. Questo ci darà accesso alle classi e ai metodi di cui abbiamo bisogno da Aspose.Words per .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Suddividiamo il processo in semplici passaggi digeribili. Inizieremo caricando il nostro documento e finiremo salvando il documento aggiornato in cui la tabella rimane unita.

## Passaggio 1: caricare il documento

 Per lavorare con un documento Word, dobbiamo prima caricarlo. Utilizzeremo il`Document` classe per questo.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Passaggio 2: accedi alla tabella

Poi, dobbiamo ottenere la tabella che vogliamo tenere insieme. Supponiamo che sia la prima tabella nel documento.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Passaggio 3: imposta KeepWithNext per i paragrafi

 Per evitare che la tabella si divida tra le pagine, dobbiamo impostare`KeepWithNext` proprietà per ogni paragrafo della tabella, ad eccezione degli ultimi paragrafi dell'ultima riga.

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

## Passaggio 4: Salvare il documento

Infine, salviamo il documento aggiornato. Questo applicherà le nostre modifiche e assicurerà che la tabella resti unita su una pagina.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Conclusione

Ed ecco fatto! Con solo poche righe di codice, puoi evitare che le tue tabelle si dividano tra le pagine nei tuoi documenti Word. Questa soluzione semplice ma efficace assicura che le tue tabelle rimangano ordinate e professionali, migliorando la leggibilità dei tuoi documenti. Aspose.Words per .NET semplifica la gestione di tali problemi di formattazione, consentendoti di concentrarti sulla creazione di ottimi contenuti.

## Domande frequenti

### Posso tenere insieme più tabelle usando questo metodo?  
Sì, puoi applicare la stessa logica a più tabelle eseguendo un'iterazione su ogni tabella del documento.

### Cosa succede se la mia tabella è troppo grande per stare su una sola pagina?  
Se una tabella è troppo grande per stare in una sola pagina, si estenderà comunque su più pagine. Questo metodo assicura che le tabelle più piccole rimangano intatte senza dividersi.

### Esiste un modo per automatizzare questa operazione per tutte le tabelle di un documento?  
 Sì, puoi scorrere tutte le tabelle nel tuo documento e applicare il`KeepWithNext` proprietà a ciascun paragrafo.

### Ho bisogno di una licenza a pagamento per Aspose.Words per .NET?  
Puoi iniziare con una prova gratuita da[Qui](https://releases.aspose.com/), ma per una funzionalità completa si consiglia una licenza a pagamento.

### Posso applicare altre formattazioni alla tabella mantenendola unita?  
Assolutamente! Puoi formattare la tua tabella come preferisci, assicurandoti che rimanga unita su una pagina.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
