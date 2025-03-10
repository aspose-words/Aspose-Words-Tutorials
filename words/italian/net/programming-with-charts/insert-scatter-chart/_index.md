---
title: Inserisci grafico a dispersione nel documento Word
linktitle: Inserisci grafico a dispersione nel documento Word
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come inserire un grafico a dispersione in Word con Aspose.Words per .NET. Semplici passaggi per integrare rappresentazioni di dati visivi nei tuoi documenti.
weight: 10
url: /it/net/programming-with-charts/insert-scatter-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci grafico a dispersione nel documento Word

## Introduzione

In questo tutorial, imparerai come sfruttare Aspose.Words per .NET per inserire un grafico a dispersione nel tuo documento Word. I grafici a dispersione sono potenti strumenti visivi che possono visualizzare efficacemente i punti dati in base a due variabili, rendendo i tuoi documenti più coinvolgenti e informativi.

## Prerequisiti

Prima di immergerci nella creazione di grafici a dispersione con Aspose.Words per .NET, assicurati di disporre dei seguenti prerequisiti:

1.  Installazione di Aspose.Words per .NET: Scarica e installa Aspose.Words per .NET da[Qui](https://releases.aspose.com/words/net/).
   
2. Conoscenza di base di C#: sarà utile avere familiarità con il linguaggio di programmazione C# e con il framework .NET.

## Importazione degli spazi dei nomi

Per iniziare, devi importare gli spazi dei nomi necessari nel tuo progetto C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

Ora analizziamo il processo di inserimento di un grafico a dispersione in un documento Word utilizzando Aspose.Words per .NET:

## Passaggio 1: inizializzare il documento e DocumentBuilder

 Per prima cosa, inizializza una nuova istanza di`Document` classe e`DocumentBuilder` classe per iniziare a creare il tuo documento.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Passaggio 2: inserire il grafico a dispersione

 Utilizzare il`InsertChart` metodo del`DocumentBuilder` classe per inserire un grafico a dispersione nel documento.

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## Passaggio 3: aggiungere serie di dati al grafico

Ora, aggiungi serie di dati al tuo grafico a dispersione. Questo esempio dimostra come aggiungere una serie con punti dati specifici.

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## Passaggio 4: Salvare il documento

 Infine, salva il documento modificato nella posizione desiderata utilizzando`Save` metodo del`Document` classe.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## Conclusione

Congratulazioni! Hai imparato con successo come inserire un grafico a dispersione nel tuo documento Word usando Aspose.Words per .NET. I grafici a dispersione sono strumenti eccellenti per visualizzare le relazioni tra dati e, con Aspose.Words, puoi integrarli senza sforzo nei tuoi documenti per migliorare la chiarezza e la comprensione.

## Domande frequenti

### Posso personalizzare l'aspetto del grafico a dispersione utilizzando Aspose.Words?
Sì, Aspose.Words consente un'ampia personalizzazione delle proprietà del grafico, come colori, assi ed etichette.

### Aspose.Words è compatibile con le diverse versioni di Microsoft Word?
Aspose.Words supporta diverse versioni di Microsoft Word, garantendo la compatibilità tra le piattaforme.

### Aspose.Words supporta altri tipi di grafici?
Sì, Aspose.Words supporta un'ampia gamma di tipi di grafici, tra cui grafici a barre, grafici a linee e grafici a torta.

### Posso aggiornare dinamicamente i dati nel grafico a dispersione a livello di programmazione?
Certamente, puoi aggiornare dinamicamente i dati del grafico utilizzando le chiamate API di Aspose.Words.

### Dove posso ottenere ulteriore assistenza o supporto per Aspose.Words?
 Per ulteriore assistenza, visitare il[Forum di supporto di Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
