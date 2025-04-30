---
"description": "Scopri come creare tabelle con impostazioni di larghezza assolute, relative e automatiche in Aspose.Words per .NET con questa guida dettagliata."
"linktitle": "Impostazioni di larghezza preferite"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Impostazioni di larghezza preferite"
"url": "/it/net/programming-with-tables/preferred-width-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Impostazioni di larghezza preferite

## Introduzione

Le tabelle sono uno strumento potente per organizzare e presentare le informazioni nei documenti Word. Quando si lavora con le tabelle in Aspose.Words per .NET, sono disponibili diverse opzioni per impostare la larghezza delle celle della tabella, in modo da garantire che si adattino perfettamente al layout del documento. Questa guida illustra il processo di creazione di tabelle con le impostazioni di larghezza preferite utilizzando Aspose.Words per .NET, concentrandosi sulle opzioni di ridimensionamento assoluto, relativo e automatico. 

## Prerequisiti

Prima di immergerti nel tutorial, assicurati di avere quanto segue:

1. Aspose.Words per .NET: assicurati di aver installato Aspose.Words per .NET nel tuo ambiente di sviluppo. Puoi scaricarlo. [Qui](https://releases.aspose.com/words/net/).

2. Ambiente di sviluppo .NET: avere configurato un ambiente di sviluppo .NET, come Visual Studio.

3. Conoscenza di base di C#: la familiarità con la programmazione C# ti aiuterà a comprendere meglio i frammenti di codice e gli esempi.

4. Documentazione di Aspose.Words: fare riferimento a [Documentazione di Aspose.Words](https://reference.aspose.com/words/net/) per informazioni dettagliate sulle API e ulteriori approfondimenti.

## Importa spazi dei nomi

Prima di iniziare a scrivere il codice, è necessario importare gli spazi dei nomi necessari nel progetto C#:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Questi namespace forniscono l'accesso alle funzionalità principali di Aspose.Words e all'oggetto Table, consentendo di manipolare le tabelle dei documenti.

Analizziamo nel dettaglio il processo di creazione di una tabella con diverse impostazioni di larghezza preferite in passaggi chiari e gestibili.

## Passaggio 1: inizializzare il documento e DocumentBuilder

Titolo: Creazione di un nuovo documento e DocumentBuilder

Spiegazione: Inizia creando un nuovo documento Word e un `DocumentBuilder` esempio. Il `DocumentBuilder` La classe fornisce un modo semplice per aggiungere contenuti al documento.

```csharp
// Definire il percorso in cui salvare il documento.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Crea un nuovo documento.
Document doc = new Document();

// Crea un DocumentBuilder per questo documento.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Qui si specifica la directory in cui verrà salvato il documento e si inizializza il `Document` E `DocumentBuilder` oggetti.

## Passaggio 2: inserire la prima cella della tabella con larghezza assoluta

Inserisci la prima cella nella tabella con una larghezza fissa di 40 punti. Questo garantirà che la cella mantenga sempre una larghezza di 40 punti, indipendentemente dalle dimensioni della tabella.

```csharp
// Inserire una cella di dimensione assoluta.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

In questo passaggio, inizi a creare la tabella e inserisci una cella con una larghezza assoluta. `PreferredWidth.FromPoints(40)` il metodo imposta la larghezza della cella a 40 punti e `Shading.BackgroundPatternColor` applica uno sfondo di colore giallo chiaro.

## Passaggio 3: inserire una cella di dimensioni relative

Inserisci un'altra cella con una larghezza pari al 20% della larghezza totale della tabella. Questo ridimensionamento relativo garantisce che la cella si adatti proporzionalmente alla larghezza della tabella.

```csharp
// Inserire una cella di dimensione relativa (percentuale).
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

La larghezza di questa cella sarà pari al 20% della larghezza totale della tabella, rendendola adattabile a diverse dimensioni dello schermo o layout di documenti.

### Passaggio 4: inserire una cella con dimensione automatica

Infine, inserisci una cella che si ridimensioni automaticamente in base allo spazio disponibile rimanente nella tabella.

```csharp
// Inserisci una cella con dimensione automatica.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. IL size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

The `PreferredWidth.Auto` L'impostazione consente a questa cella di espandersi o contrarsi in base allo spazio rimanente dopo aver considerato le altre celle. Questo garantisce che il layout della tabella appaia equilibrato e professionale.

## Passaggio 5: finalizzare e salvare il documento

Dopo aver inserito tutte le celle, completa la tabella e salva il documento nel percorso specificato.

```csharp
// Salvare il documento.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Questo passaggio finalizza la tabella e salva il documento con il nome file "WorkingWithTables.PreferredWidthSettings.docx" nella directory designata.

## Conclusione

Creare tabelle con le impostazioni di larghezza preferite in Aspose.Words per .NET è semplice una volta comprese le diverse opzioni di ridimensionamento disponibili. Che si necessiti di larghezze di cella fisse, relative o automatiche, Aspose.Words offre la flessibilità necessaria per gestire in modo efficiente diversi scenari di layout delle tabelle. Seguendo i passaggi descritti in questa guida, è possibile garantire che le tabelle siano ben strutturate e visivamente accattivanti nei documenti Word.

## Domande frequenti

### Qual è la differenza tra larghezza assoluta e relativa delle celle?
Le larghezze assolute delle celle sono fisse e non cambiano, mentre le larghezze relative si adattano in base alla larghezza totale della tabella.

### Posso usare percentuali negative per le larghezze relative?
No, le percentuali negative non sono valide per le larghezze delle celle. Sono consentite solo percentuali positive.

### Come funziona la funzione di dimensionamento automatico?
Il ridimensionamento automatico regola la larghezza della cella per riempire lo spazio rimanente nella tabella dopo che sono state ridimensionate altre celle.

### Posso applicare stili diversi alle celle con impostazioni di larghezza diverse?
Sì, puoi applicare vari stili e formattazioni alle celle, indipendentemente dalle impostazioni di larghezza.

### Cosa succede se la larghezza totale della tabella è inferiore alla somma delle larghezze di tutte le celle?
La tabella adatterà automaticamente la larghezza delle celle per adattarle allo spazio disponibile, il che potrebbe causare il restringimento di alcune celle.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}