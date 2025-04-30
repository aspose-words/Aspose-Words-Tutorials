---
"description": "Scopri come modificare i tag dei documenti strutturati in Word utilizzando Aspose.Words per .NET. Aggiorna testo, menu a discesa e immagini passo dopo passo."
"linktitle": "Modifica i controlli del contenuto"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Modifica i controlli del contenuto"
"url": "/it/net/programming-with-sdt/modify-content-controls/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Modifica i controlli del contenuto

## Introduzione

Se hai mai lavorato con documenti Word e hai avuto bisogno di modificare controlli di contenuto strutturati, come testo normale, elenchi a discesa o immagini, utilizzando Aspose.Words per .NET, sei nel posto giusto! I tag di documento strutturato (SDT) sono strumenti potenti che semplificano e rendono più flessibile l'automazione dei documenti. In questo tutorial, spiegheremo nel dettaglio come modificare questi SDT in base alle tue esigenze. Che tu stia aggiornando il testo, modificando le selezioni a discesa o sostituendo le immagini, questa guida ti guiderà passo dopo passo nel processo.

## Prerequisiti

Prima di addentrarci nei dettagli della modifica dei controlli dei contenuti, assicurati di avere quanto segue:

1. Aspose.Words per .NET installato: assicurarsi di aver installato la libreria Aspose.Words. In caso contrario, è possibile [scaricalo qui](https://releases.aspose.com/words/net/).

2. Conoscenza di base di C#: questo tutorial presuppone che tu abbia familiarità con i concetti base della programmazione C#.

3. Un ambiente di sviluppo .NET: dovresti avere un IDE come Visual Studio configurato per eseguire le applicazioni .NET.

4. Un documento di esempio: useremo un documento Word di esempio con vari tipi di SDT. Puoi usare quello dell'esempio o crearne uno tuo.

5. Accesso alla documentazione di Aspose: per informazioni più dettagliate, consultare [Documentazione di Aspose.Words](https://reference.aspose.com/words/net/).

## Importa spazi dei nomi

Per iniziare a lavorare con Aspose.Words, è necessario importare gli spazi dei nomi pertinenti nel progetto C#. Ecco come fare:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Questi namespace ti daranno accesso alle classi e ai metodi necessari per manipolare i tag dei documenti strutturati nei tuoi documenti Word.

## Passaggio 1: imposta il percorso del documento

Prima di apportare modifiche, è necessario specificare il percorso del documento. Sostituisci `"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo in cui è archiviato il documento.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Passaggio 2: scorrere i tag dei documenti strutturati

Per modificare gli SDT, è necessario prima scorrere tutti gli SDT nel documento. Questo viene fatto utilizzando `GetChildNodes` metodo per ottenere tutti i nodi di tipo `StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Modificare gli SDT in base al loro tipo
}
```

## Passaggio 3: modificare gli SDT in testo normale

Se l'SDT è di tipo testo normale, è possibile sostituirne il contenuto. Innanzitutto, cancellare il contenuto esistente, quindi aggiungere nuovo testo.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

Spiegazione: Qui, `RemoveAllChildren()` cancella il contenuto esistente dell'SDT. Quindi creiamo un nuovo `Paragraph` E `Run` oggetto per inserire il nuovo testo.

## Passaggio 4: modificare gli SDT dell'elenco a discesa

Per gli SDT con elenco a discesa, è possibile modificare l'elemento selezionato accedendo a `ListItems` collezione. Qui selezioniamo il terzo elemento nell'elenco.

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

Spiegazione: Questo codice controlla se la forma contiene un'immagine e quindi la sostituisce con una nuova immagine situata in `ImagesDir`.

## Passaggio 6: salva il documento modificato

Dopo aver apportato tutte le modifiche necessarie, salva il documento modificato con un nuovo nome per mantenere intatto il documento originale.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Spiegazione: questo salva il documento con un nuovo nome file in modo da poterlo distinguere facilmente dall'originale.

## Conclusione

Modificare i controlli del contenuto in un documento Word utilizzando Aspose.Words per .NET è semplice una volta compresi i passaggi necessari. Che si tratti di aggiornare il testo, modificare le selezioni a discesa o scambiare immagini, Aspose.Words fornisce un'API affidabile per queste attività. Seguendo questo tutorial, è possibile gestire e personalizzare efficacemente i controlli del contenuto strutturato del documento, rendendolo più dinamico e personalizzato in base alle proprie esigenze.

## Domande frequenti

1. Che cosa è uno Structured Document Tag (SDT)?

Gli SDT sono elementi nei documenti Word che aiutano a gestire e formattare il contenuto del documento, come caselle di testo, elenchi a discesa o immagini.

2. Come posso aggiungere un nuovo elemento a discesa a un SDT?

Per aggiungere un nuovo elemento, utilizzare il `ListItems` proprietà e aggiungi un nuovo `SdtListItem` alla collezione.

3. Posso usare Aspose.Words per rimuovere gli SDT da un documento?

Sì, è possibile rimuovere gli SDT accedendo ai nodi del documento ed eliminando l'SDT desiderato.

4. Come posso gestire gli SDT annidati in altri elementi?

Utilizzare il `GetChildNodes` metodo con parametri appropriati per accedere agli SDT annidati.

5. Cosa devo fare se l'SDT che devo modificare non è visibile nel documento?

Assicurati che l'SDT non sia nascosto o protetto. Controlla le impostazioni del documento e assicurati che il codice sia correttamente indirizzato al tipo SDT.


### Esempio di codice sorgente per la modifica dei controlli del contenuto utilizzando Aspose.Words per .NET 

```csharp
// Percorso alla directory dei documenti 
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

Ecco fatto! Hai modificato con successo diversi tipi di controlli contenuto nel tuo documento Word utilizzando Aspose.Words per .NET.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}