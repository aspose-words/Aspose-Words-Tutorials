---
title: Nascondi l'asse del grafico in un documento Word
linktitle: Nascondi l'asse del grafico in un documento Word
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come nascondere l'asse del grafico in un documento Word utilizzando Aspose.Words per .NET con il nostro tutorial dettagliato e passo dopo passo.
weight: 10
url: /it/net/programming-with-charts/hide-chart-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nascondi l'asse del grafico in un documento Word

## Introduzione

La creazione di documenti Word dinamici e visivamente accattivanti spesso comporta l'incorporazione di diagrammi e grafici. Uno scenario del genere potrebbe richiedere di nascondere l'asse del grafico per una presentazione più pulita. Aspose.Words per .NET fornisce un'API completa e facile da usare per tali attività. Questo tutorial ti guiderà attraverso i passaggi per nascondere un asse del grafico in un documento Word utilizzando Aspose.Words per .NET.

## Prerequisiti

Prima di immergerci nel tutorial, assicurati di disporre dei seguenti prerequisiti:

-  Aspose.Words per .NET: puoi scaricarlo da[Qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: qualsiasi IDE che supporti lo sviluppo .NET, come Visual Studio.
- .NET Framework: assicurati di avere .NET Framework installato sul tuo computer.
- Conoscenza di base di C#: la familiarità con il linguaggio di programmazione C# sarà vantaggiosa.

## Importazione degli spazi dei nomi

Per iniziare a lavorare con Aspose.Words per .NET, devi importare i namespace richiesti nel tuo progetto. Ecco come puoi farlo:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Scomponiamo il processo in passaggi semplici e facili da seguire.

## Passaggio 1: inizializzare il documento e DocumentBuilder

Il primo passo consiste nel creare un nuovo documento Word e nell'inizializzare l'oggetto DocumentBuilder.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 In questo passaggio definiamo il percorso in cui verrà salvato il documento. Creiamo quindi un nuovo`Document` oggetto e un`DocumentBuilder` oggetto per iniziare a costruire il nostro documento.

## Passaggio 2: inserire un grafico

 Successivamente, inseriremo un grafico nel documento utilizzando il`DocumentBuilder` oggetto.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

 Qui inseriamo un grafico a colonne con dimensioni specificate. Il`InsertChart` il metodo restituisce un`Shape` oggetto che contiene il grafico.

## Passaggio 3: Cancella le serie esistenti

Prima di aggiungere nuovi dati al grafico, dobbiamo cancellare tutte le serie esistenti.

```csharp
chart.Series.Clear();
```

Questo passaggio garantisce che tutti i dati predefiniti nel grafico vengano rimossi, lasciando spazio ai nuovi dati che aggiungeremo in seguito.

## Passaggio 4: aggiungere dati di serie

Ora aggiungiamo le nostre serie di dati al grafico.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

In questo passaggio aggiungiamo una serie denominata "Aspose Series 1" con le categorie e i valori corrispondenti.

## Passaggio 5: nascondere l'asse Y

 Per nascondere l'asse Y del grafico, impostiamo semplicemente`Hidden` proprietà dell'asse Y a`true`.

```csharp
chart.AxisY.Hidden = true;
```

Questa riga di codice nasconde l'asse Y, rendendolo invisibile nel grafico.

## Passaggio 6: Salvare il documento

Infine, salva il documento nella directory specificata.

```csharp
doc.Save(dataDir + "WorkingWithCharts.HideChartAxis.docx");
```

Questo comando salva il documento Word con il grafico nel percorso specificato.

## Conclusione

Congratulazioni! Hai imparato con successo come nascondere un asse di un grafico in un documento Word usando Aspose.Words per .NET. Questa potente libreria semplifica la manipolazione dei documenti Word a livello di programmazione. Seguendo questi passaggi, puoi creare documenti personalizzati e dall'aspetto professionale con il minimo sforzo.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente API per creare, modificare, convertire e manipolare documenti Word all'interno di applicazioni .NET.

### Posso nascondere sia l'asse X che l'asse Y in un grafico?
 Sì, puoi nascondere entrambi gli assi impostando`Hidden` proprietà di entrambi`AxisX` E`AxisY` A`true`.

### È disponibile una prova gratuita per Aspose.Words per .NET?
 Sì, puoi ottenere una prova gratuita[Qui](https://releases.aspose.com/).

### Dove posso trovare ulteriore documentazione?
 Puoi trovare la documentazione dettagliata su Aspose.Words per .NET[Qui](https://reference.aspose.com/words/net/).

### Come posso ottenere supporto per Aspose.Words per .NET?
 Puoi ottenere supporto dalla comunità Aspose[Qui](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
