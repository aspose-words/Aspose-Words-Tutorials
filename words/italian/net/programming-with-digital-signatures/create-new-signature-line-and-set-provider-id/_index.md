---
"description": "Scopri come creare una nuova riga per la firma e impostare l'ID del provider nei documenti Word utilizzando Aspose.Words per .NET. Guida passo passo."
"linktitle": "Crea una nuova riga di firma e imposta l'ID del fornitore"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Crea una nuova riga di firma e imposta l'ID del fornitore"
"url": "/it/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Crea una nuova riga di firma e imposta l'ID del fornitore

## Introduzione

Ciao a tutti, appassionati di tecnologia! Vi siete mai chiesti come aggiungere una riga per la firma nei vostri documenti Word tramite codice? Oggi approfondiremo proprio questo aspetto utilizzando Aspose.Words per .NET. Questa guida vi guiderà passo passo, rendendo semplicissimo creare una nuova riga per la firma e impostare l'ID del provider nei vostri documenti Word. Che stiate automatizzando l'elaborazione dei documenti o semplicemente cercando di semplificare il vostro flusso di lavoro, questo tutorial vi aiuterà.

## Prerequisiti

Prima di sporcarci le mani, assicuriamoci di avere tutto il necessario:

1. Aspose.Words per .NET: se non l'hai ancora fatto, scaricalo [Qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: Visual Studio o qualsiasi altro ambiente di sviluppo C#.
3. .NET Framework: assicurati di aver installato .NET Framework.
4. Certificato PFX: per firmare i documenti, è necessario un certificato PFX. È possibile ottenerne uno da un'autorità di certificazione attendibile.

## Importa spazi dei nomi

Per prima cosa, importiamo gli spazi dei nomi necessari nel tuo progetto C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Bene, andiamo al dunque. Ecco una descrizione dettagliata di ogni passaggio per creare una nuova riga di firma e impostare l'ID del provider.

## Passaggio 1: creare un nuovo documento

Per iniziare, dobbiamo creare un nuovo documento Word. Questo sarà il nostro spazio per la riga della firma.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

In questo frammento, stiamo inizializzando un nuovo `Document` e un `DocumentBuilder`. IL `DocumentBuilder` ci aiuta ad aggiungere elementi al nostro documento.

## Passaggio 2: definire le opzioni della riga della firma

Successivamente, definiamo le opzioni per la riga della firma. Queste includono il nome, il titolo, l'indirizzo email e altri dettagli del firmatario.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Queste opzioni personalizzano la riga della firma, rendendola chiara e professionale.

## Passaggio 3: inserire la riga della firma

Una volta impostate le opzioni, possiamo ora inserire la riga della firma nel documento.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

Qui, il `InsertSignatureLine` Il metodo aggiunge la riga della firma e le assegniamo un ID provider univoco.

## Passaggio 4: salvare il documento

Dopo aver inserito la riga della firma, salviamo il documento.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

In questo modo il documento verrà salvato con la nuova riga della firma aggiunta.

## Passaggio 5: impostare le opzioni di firma

Ora dobbiamo impostare le opzioni per la firma del documento. Queste includono l'ID della riga di firma, l'ID del provider, i commenti e l'ora della firma.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Queste opzioni garantiscono che il documento venga firmato con i dati corretti.

## Passaggio 6: creare il titolare del certificato

Per firmare il documento, useremo un certificato PFX. Creiamo un titolare del certificato.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

Assicurati di sostituire `"morzal.pfx"` con il tuo file di certificato effettivo e `"aw"` con la password del certificato.

## Fase 7: Firmare il documento

Infine, firmiamo il documento utilizzando lo strumento di firma digitale.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Questo firma il documento e lo salva come un nuovo file.

## Conclusione

Ed ecco fatto! Hai creato con successo una nuova riga per la firma e impostato l'ID del provider in un documento Word utilizzando Aspose.Words per .NET. Questa potente libreria semplifica incredibilmente la gestione e l'automazione delle attività di elaborazione dei documenti. Provala e scopri come può semplificare il tuo flusso di lavoro.

## Domande frequenti

### Posso personalizzare l'aspetto della riga della firma?
Assolutamente! Puoi modificare varie opzioni nel `SignatureLineOptions` in base alle tue esigenze.

### Cosa succede se non ho un certificato PFX?
Dovrai ottenerne uno da un'autorità di certificazione attendibile. È essenziale per la firma digitale dei documenti.

### Posso aggiungere più righe di firma a un documento?
Sì, puoi aggiungere tutte le righe di firma che desideri ripetendo il processo di inserimento con opzioni diverse.

### Aspose.Words per .NET è compatibile con .NET Core?
Sì, Aspose.Words per .NET supporta .NET Core, rendendolo versatile per diversi ambienti di sviluppo.

### Quanto sono sicure le firme digitali?
Le firme digitali create con Aspose.Words sono estremamente sicure, a condizione che si utilizzi un certificato valido e attendibile.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}