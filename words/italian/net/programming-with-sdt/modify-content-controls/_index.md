---
title: Modificare i controlli del contenuto
linktitle: Modificare i controlli del contenuto
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come modificare i tag dei documenti strutturati in Word usando Aspose.Words per .NET. Aggiorna testo, menu a discesa e immagini passo dopo passo.
weight: 10
url: /it/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Modificare i controlli del contenuto

## Introduzione

Se hai mai lavorato con documenti Word e hai avuto bisogno di modificare controlli di contenuto strutturati, come testo normale, elenchi a discesa o immagini, utilizzando Aspose.Words per .NET, sei nel posto giusto! Gli Structured Document Tag (SDT) sono potenti strumenti che rendono l'automazione dei documenti più semplice e flessibile. In questo tutorial, approfondiremo come puoi modificare questi SDT per adattarli alle tue esigenze. Che tu stia aggiornando il testo, modificando le selezioni a discesa o sostituendo le immagini, questa guida ti guiderà passo dopo passo nel processo.

## Prerequisiti

Prima di addentrarci nei dettagli della modifica dei controlli dei contenuti, assicurati di avere quanto segue:

1.  Aspose.Words per .NET installato: assicurati di avere la libreria Aspose.Words installata. In caso contrario, puoi[scaricalo qui](https://releases.aspose.com/words/net/).

2. Conoscenza di base di C#: questo tutorial presuppone che tu abbia familiarità con i concetti di base della programmazione C#.

3. Un ambiente di sviluppo .NET: dovresti avere un IDE come Visual Studio configurato per eseguire le applicazioni .NET.

4. Un documento di esempio: useremo un documento Word di esempio con vari tipi di SDT. Puoi usare quello dell'esempio o crearne uno tuo.

5.  Accesso alla documentazione di Aspose: per informazioni più dettagliate, consulta il[Documentazione di Aspose.Words](https://reference.aspose.com/words/net/).

## Importazione degli spazi dei nomi

Per iniziare a lavorare con Aspose.Words, devi importare i namespace rilevanti nel tuo progetto C#. Ecco come fare:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Questi namespace ti daranno accesso alle classi e ai metodi necessari per manipolare i tag dei documenti strutturati nei tuoi documenti Word.

## Passaggio 1: imposta il percorso del documento

 Prima di apportare modifiche, devi specificare il percorso del tuo documento. Sostituisci`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo in cui è archiviato il documento.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Passaggio 2: scorrere i tag dei documenti strutturati

 Per modificare gli SDT, devi prima scorrere tutti gli SDT nel documento. Questo viene fatto usando`GetChildNodes` metodo per ottenere tutti i nodi di tipo`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Modificare gli SDT in base al tipo
}
```

## Passaggio 3: modificare gli SDT in testo normale

Se l'SDT è un tipo di testo normale, puoi sostituirne il contenuto. Per prima cosa, cancella il contenuto esistente, quindi aggiungi nuovo testo.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 Spiegazione: Qui,`RemoveAllChildren()`cancella il contenuto esistente dell'SDT. Quindi creiamo un nuovo`Paragraph` E`Run` oggetto per inserire il nuovo testo.

## Passaggio 4: modificare gli SDT dell'elenco a discesa

 Per gli SDT con elenco a discesa, è possibile modificare l'elemento selezionato accedendo a`ListItems` collezione. Qui selezioniamo il terzo elemento nell'elenco.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Spiegazione: Questo frammento di codice seleziona l'elemento all'indice 2 (terzo elemento) dall'elenco a discesa. Adatta l'indice in base alle tue esigenze.

## Passaggio 5: modifica gli SDT delle immagini

Per aggiornare un'immagine all'interno di un SDT, è possibile sostituire l'immagine esistente con una nuova.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 Spiegazione: Questo codice controlla se la forma contiene un'immagine e quindi la sostituisce con una nuova immagine situata in`ImagesDir`.

## Passaggio 6: salva il documento modificato

Dopo aver apportato tutte le modifiche necessarie, salva il documento modificato con un nuovo nome per mantenere intatto il documento originale.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Spiegazione: questo salva il documento con un nuovo nome file in modo da poterlo distinguere facilmente dall'originale.

## Conclusione

Modificare i controlli del contenuto in un documento Word usando Aspose.Words per .NET è semplice una volta compresi i passaggi coinvolti. Che tu stia aggiornando il testo, modificando le selezioni a discesa o scambiando immagini, Aspose.Words fornisce una solida API per queste attività. Seguendo questo tutorial, puoi gestire e personalizzare in modo efficace i controlli del contenuto strutturato del tuo documento, rendendo i tuoi documenti più dinamici e su misura per le tue esigenze.

## Domande frequenti

1. Che cosa è uno Structured Document Tag (SDT)?

Gli SDT sono elementi nei documenti Word che aiutano a gestire e formattare il contenuto del documento, come caselle di testo, elenchi a discesa o immagini.

2. Come posso aggiungere un nuovo elemento a discesa a un SDT?

 Per aggiungere un nuovo elemento, utilizzare il`ListItems` proprietà e aggiungi un nuovo`SdtListItem` alla collezione.

3. Posso usare Aspose.Words per rimuovere gli SDT da un documento?

Sì, è possibile rimuovere gli SDT accedendo ai nodi del documento ed eliminando l'SDT desiderato.

4. Come gestisco gli SDT annidati in altri elementi?

 Utilizzare il`GetChildNodes` metodo con parametri appropriati per accedere agli SDT nidificati.

5. Cosa devo fare se l'SDT che devo modificare non è visibile nel documento?

Assicurati che l'SDT non sia nascosto o protetto. Controlla le impostazioni del documento e assicurati che il tuo codice stia correttamente indirizzando il tipo SDT.


### Esempio di codice sorgente per modificare i controlli del contenuto utilizzando Aspose.Words per .NET 

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

Ecco fatto! Hai modificato con successo diversi tipi di controlli di contenuto nel tuo documento Word utilizzando Aspose.Words per .NET.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
