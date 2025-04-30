---
"description": "Scopri come definire le proprietà degli assi XY in un grafico utilizzando Aspose.Words per .NET con questa guida passo passo. Perfetta per gli sviluppatori .NET."
"linktitle": "Definire le proprietà dell'asse XY in un grafico"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Definire le proprietà dell'asse XY in un grafico"
"url": "/it/net/programming-with-charts/define-xyaxis-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Definire le proprietà dell'asse XY in un grafico

## Introduzione

grafici sono uno strumento potente per visualizzare i dati. Quando si desidera creare documenti professionali con grafici dinamici, Aspose.Words per .NET è una libreria preziosa. Questo articolo vi guiderà attraverso il processo di definizione delle proprietà degli assi XY in un grafico utilizzando Aspose.Words per .NET, analizzando ogni passaggio per garantire chiarezza e semplicità di comprensione.

## Prerequisiti

Prima di immergerti nella codifica, ecco alcuni prerequisiti che devi soddisfare:

1. Aspose.Words per .NET: assicurati di avere la libreria Aspose.Words per .NET. Puoi [scaricalo qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: è necessario un ambiente di sviluppo integrato (IDE) come Visual Studio.
3. .NET Framework: assicurati che il tuo ambiente di sviluppo sia configurato per lo sviluppo .NET.
4. Conoscenza di base di C#: questa guida presuppone una conoscenza di base della programmazione C#.

## Importa spazi dei nomi

Per iniziare, è necessario importare gli spazi dei nomi necessari nel progetto. Questo garantisce l'accesso a tutte le classi e i metodi necessari per creare e manipolare documenti e grafici.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Suddivideremo il processo in semplici passaggi, ognuno dei quali si concentrerà su una parte specifica della definizione delle proprietà degli assi XY in un grafico.

## Passaggio 1: inizializzare il documento e DocumentBuilder

Per prima cosa, devi inizializzare un nuovo documento e un `DocumentBuilder` oggetto. L' `DocumentBuilder` aiuta a inserire contenuti nel documento.

```csharp
// Percorso alla directory dei documenti 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Passaggio 2: inserire un grafico

Successivamente, inserirai un grafico nel documento. In questo esempio, useremo un grafico ad area. Puoi personalizzare le dimensioni del grafico a seconda delle tue esigenze.

```csharp
// Inserisci grafico
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## Passaggio 3: cancellare le serie predefinite e aggiungere dati personalizzati

Per impostazione predefinita, il grafico avrà alcune serie predefinite. Le elimineremo e aggiungeremo le nostre serie di dati personalizzate.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## Passaggio 4: definire le proprietà dell'asse X

Ora è il momento di definire le proprietà per l'asse X. Ciò include l'impostazione del tipo di categoria, la personalizzazione dell'intersezione degli assi e la regolazione dei segni di spunta e delle etichette.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; // Misurato in unità di visualizzazione dell'asse Y (centinaia).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## Passaggio 5: definire le proprietà dell'asse Y

Allo stesso modo, imposterai le proprietà per l'asse Y. Ciò include l'impostazione della posizione dell'etichetta di spunta, delle unità principali e secondarie, dell'unità di visualizzazione e della scala.

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## Passaggio 6: salvare il documento

Infine, salva il documento nella directory specificata. Verrà generato il documento Word con il grafico personalizzato.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Conclusione

Creare e personalizzare grafici nei documenti Word utilizzando Aspose.Words per .NET è semplice una volta compresi i passaggi necessari. Questa guida vi ha illustrato il processo di definizione delle proprietà degli assi XY in un grafico, dall'inizializzazione del documento al salvataggio del prodotto finale. Grazie a queste competenze, potrete creare grafici dettagliati e dall'aspetto professionale che arricchiranno i vostri documenti.

## Domande frequenti

### Quali tipi di grafici posso creare con Aspose.Words per .NET?
È possibile creare vari tipi di grafici, tra cui grafici ad area, a barre, a linee, a torta e altri ancora.

### Come faccio a installare Aspose.Words per .NET?
Puoi scaricare Aspose.Words per .NET da [Qui](https://releases.aspose.com/words/net/) e seguire le istruzioni di installazione fornite.

### Posso personalizzare l'aspetto dei miei grafici?
Sì, Aspose.Words per .NET consente un'ampia personalizzazione dei grafici, inclusi colori, caratteri e proprietà degli assi.

### È disponibile una versione di prova gratuita di Aspose.Words per .NET?
Sì, puoi ottenere una prova gratuita [Qui](https://releases.aspose.com/).

### Dove posso trovare altri tutorial e documentazione?
Puoi trovare altri tutorial e documentazione dettagliata su [Pagina di documentazione di Aspose.Words per .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}