---
"description": "Scopri come associare dinamicamente dati XML a tag di documenti strutturati in Word utilizzando Aspose.Words per .NET. Segui la nostra guida passo passo."
"linktitle": "Intervallo di tag del documento strutturato Avvia la mappatura XML"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Intervallo di tag del documento strutturato Avvia la mappatura XML"
"url": "/it/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Intervallo di tag del documento strutturato Avvia la mappatura XML

## Introduzione

Hai mai desiderato inserire dinamicamente dati XML in un documento Word? Beh, sei fortunato! Aspose.Words per .NET semplifica questa operazione. In questo tutorial, approfondiremo il mapping XML strutturato per l'intervallo di tag del documento. Questa funzionalità consente di associare parti XML personalizzate ai controlli contenuto, garantendo che il contenuto del documento si aggiorni perfettamente con i dati XML. Pronti a trasformare i vostri documenti in capolavori dinamici.

## Prerequisiti

Prima di passare alla parte di codifica, assicuriamoci di avere tutto il necessario:

1. Libreria Aspose.Words per .NET: assicurati di avere la versione più recente. Puoi scaricarla. [Qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: Visual Studio o qualsiasi altro IDE che supporti C#.
3. Conoscenza di base di C#: è indispensabile avere familiarità con la programmazione C#.
4. Documento Word: un esempio di documento Word con cui lavorare.

## Importa spazi dei nomi

Per prima cosa, importiamo i namespace necessari. Questo ci garantirà l'accesso a tutte le classi e i metodi richiesti in Aspose.Words per .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Passaggio 1: imposta la directory dei documenti

Ogni progetto ha bisogno di una base, giusto? Qui, impostiamo il percorso per la directory dei tuoi documenti.

```csharp
// Percorso alla directory dei documenti 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: caricare il documento Word

Poi, carichiamo il documento Word. È il documento in cui inseriremo i nostri dati XML.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Passaggio 3: aggiungere la parte XML personalizzata

Dobbiamo creare una parte XML contenente i dati che vogliamo inserire e aggiungerla alla raccolta CustomXmlPart del documento. Questa parte XML personalizzata fungerà da origine dati per i tag del nostro documento strutturato.

### Creazione di una parte XML

Per prima cosa, genera un ID univoco per la parte XML e definiscine il contenuto.

```csharp
// Costruisci una parte XML che contenga dati e aggiungila alla raccolta CustomXmlPart del documento.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Verificare il contenuto della parte XML

Per garantire che la parte XML sia stata aggiunta correttamente, ne stampiamo il contenuto.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Passaggio 4: creare un tag di documento strutturato

Un tag di documento strutturato (SDT) è un controllo di contenuto che può essere associato a una parte XML. Qui creiamo un SDT che visualizzerà il contenuto della nostra parte XML personalizzata.

Per prima cosa, individua l'inizio dell'intervallo SDT nel documento.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Passaggio 5: impostare il mapping XML per l'SDT

Ora è il momento di associare la nostra parte XML all'SDT. Impostando un mapping XML, specifichiamo quale parte dei dati XML deve essere visualizzata nell'SDT.

L'XPath punta all'elemento specifico nella parte XML che vogliamo visualizzare. Qui, puntiamo al secondo `<text>` elemento all'interno del `<root>` elemento.

```csharp
// Imposta una mappatura per il nostro StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Passaggio 6: salvare il documento

Infine, salva il documento per vedere le modifiche in azione. L'SDT nel documento Word ora visualizzerà il contenuto XML specificato.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Conclusione

Ed ecco fatto! Hai mappato con successo una parte XML a un tag di documento strutturato in un documento Word utilizzando Aspose.Words per .NET. Questa potente funzionalità ti consente di creare documenti dinamici e basati sui dati senza sforzo. Che tu stia generando report, fatture o qualsiasi altro tipo di documento, il mapping XML può semplificare notevolmente il tuo flusso di lavoro.

## Domande frequenti

### Che cos'è un tag di documento strutturato in Word?
I tag di documento strutturato, noti anche come controlli di contenuto, sono contenitori per tipi specifici di contenuto nei documenti Word. Possono essere utilizzati per associare dati, limitare le modifiche o guidare gli utenti nella creazione di documenti.

### Come posso aggiornare dinamicamente il contenuto della parte XML?
È possibile aggiornare il contenuto della parte XML modificando `xmlPartContent` stringa prima di aggiungerla al documento. Aggiorna semplicemente la stringa con i nuovi dati e aggiungila a `CustomXmlParts` collezione.

### Posso associare più parti XML a diversi SDT nello stesso documento?
Sì, è possibile associare più parti XML a diversi SDT nello stesso documento. Ogni SDT può avere una propria parte XML e una propria mappatura XPath.

### È possibile mappare strutture XML complesse in SDT?
Assolutamente! È possibile mappare strutture XML complesse in SDT utilizzando espressioni XPath dettagliate che puntano con precisione agli elementi desiderati all'interno della parte XML.

### Come posso rimuovere una parte XML da un documento?
È possibile rimuovere una parte XML chiamando il `Remove` metodo sul `CustomXmlParts` raccolta, passando il `xmlPartId` della parte XML che vuoi rimuovere.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}