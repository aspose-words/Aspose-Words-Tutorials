---
title: Formato numero di etichetta dati in un grafico
linktitle: Formato numero di etichetta dati in un grafico
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come formattare le etichette dati nei grafici usando Aspose.Words per .NET con questa guida passo-passo. Migliora i tuoi documenti Word senza sforzo.
weight: 10
url: /it/net/programming-with-charts/format-number-of-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formato numero di etichetta dati in un grafico

## Introduzione

La creazione di documenti coinvolgenti e informativi spesso comporta l'inclusione di grafici con etichette dati ben formattate. Se sei uno sviluppatore .NET che desidera migliorare i propri documenti Word con grafici sofisticati, Aspose.Words per .NET è una fantastica libreria per aiutarti a raggiungere questo obiettivo. Questo tutorial ti guiderà passo dopo passo nel processo di formattazione delle etichette numeriche in un grafico utilizzando Aspose.Words per .NET.

## Prerequisiti

Prima di immergerti nel codice, ci sono alcuni prerequisiti che devi soddisfare:

-  Aspose.Words per .NET: assicurati di avere installata la libreria Aspose.Words per .NET. Se non l'hai ancora installata, puoi[scaricalo qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: dovresti avere un ambiente di sviluppo .NET configurato. Visual Studio è altamente raccomandato.
- Conoscenza di base di C#: la familiarità con la programmazione C# è essenziale poiché questo tutorial prevede la scrittura e la comprensione del codice C#.
-  Licenza temporanea: per utilizzare Aspose.Words senza alcuna limitazione, puoi ottenere una[licenza temporanea](https://purchase.aspose.com/temporary-license/).

Ora analizziamo passo dopo passo il processo di formattazione delle etichette numeriche in un grafico.

## Importazione degli spazi dei nomi

Per prima cosa, dobbiamo importare i namespace necessari per lavorare con Aspose.Words per .NET. Aggiungi le seguenti righe all'inizio del tuo file C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Passaggio 1: imposta la directory dei documenti

Prima di poter iniziare a manipolare il tuo documento Word, devi specificare la directory in cui verrà salvato il documento. Questo è essenziale per l'operazione di salvataggio successiva.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Sostituire`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo della directory del documento.

## Passaggio 2: inizializzare il documento e DocumentBuilder

 Il passo successivo è inizializzare un nuovo`Document` e un`DocumentBuilder` . IL`DocumentBuilder` è una classe helper che consente di costruire il contenuto del documento.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Passaggio 3: inserire un grafico nel documento

 Ora, inseriamo un grafico nel documento utilizzando il`DocumentBuilder`In questo tutorial useremo un grafico a linee come esempio.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Qui inseriamo un grafico a linee con larghezza e altezza specifiche e impostiamo il titolo del grafico.

## Passaggio 4: cancella la serie predefinita e aggiungi una nuova serie

Di default, il grafico avrà alcune serie pre-generate. Dobbiamo cancellarle e aggiungere le nostre serie con punti dati specifici.

```csharp
// Elimina le serie generate di default.
chart.Series.Clear();

// Aggiungi nuove serie con punti dati personalizzati.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Passaggio 5: abilitare le etichette dati

Per visualizzare le etichette dati sul grafico, dobbiamo abilitarle per la nostra serie.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Passaggio 6: formattare le etichette dati

Il fulcro di questo tutorial è la formattazione delle etichette dati. Possiamo applicare formati numerici diversi a ogni etichetta dati singolarmente.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Formato della valuta
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Formato data
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Formato percentuale
```

 Inoltre, puoi collegare il formato di un'etichetta dati a una cella sorgente. Quando è collegato, il`NumberFormat` verrà reimpostato su generale ed ereditato dalla cella di origine.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Passaggio 7: Salvare il documento

Infine, salva il documento nella directory specificata.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

In questo modo il documento viene salvato con il nome specificato e viene garantito il mantenimento del grafico con le etichette dati formattate.

## Conclusione

Formattare le etichette dati in un grafico usando Aspose.Words per .NET può migliorare notevolmente la leggibilità e la professionalità dei tuoi documenti Word. Seguendo questa guida passo passo, dovresti ora essere in grado di creare un grafico, aggiungere serie di dati e formattare le etichette dati per soddisfare le tue esigenze. Aspose.Words per .NET è un potente strumento che consente un'ampia personalizzazione e automazione dei documenti Word, rendendolo una risorsa inestimabile per gli sviluppatori .NET.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria per creare, manipolare e convertire documenti Word a livello di programmazione utilizzando C#.

### Posso formattare altri tipi di grafici con Aspose.Words per .NET?
Sì, Aspose.Words per .NET supporta diversi tipi di grafici, tra cui grafici a barre, a colonne, a torta e altri ancora.

### Come posso ottenere una licenza temporanea per Aspose.Words per .NET?
Puoi ottenere una licenza temporanea[Qui](https://purchase.aspose.com/temporary-license/).

### È possibile collegare le etichette dati alle celle di origine in Excel?
Sì, è possibile collegare le etichette dati alle celle di origine, consentendo che il formato numerico venga ereditato dalla cella di origine.

### Dove posso trovare una documentazione più dettagliata per Aspose.Words per .NET?
 Puoi trovare una documentazione completa[Qui](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
