---
title: Convertire Docx in Mhtml e inviare e-mail
linktitle: Convertire Docx in Mhtml e inviare e-mail
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come convertire DOCX in MHTML e inviare email usando Aspose.Words per .NET in questa guida passo-passo. Aumenta la tua produttività con una facile automazione.
weight: 10
url: /it/net/basic-conversions/docx-to-mhtml-and-sending-email/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convertire Docx in Mhtml e inviare e-mail

## Introduzione

Nell'era digitale odierna, convertire documenti da un formato a un altro e inviarli via e-mail è un'attività comune. Questo articolo ti guiderà attraverso il processo di conversione di un file DOCX in formato MHTML e quindi di invio tramite e-mail utilizzando Aspose.Words per .NET. Analizzeremo ogni passaggio in una guida dettagliata e facile da seguire, assicurandoti di comprendere il processo dall'inizio alla fine. Immergiamoci!

## Prerequisiti

Prima di iniziare, assicurati di avere i seguenti prerequisiti:

1.  Aspose.Words per .NET: Scarica e installa la libreria Aspose.Words per .NET da[Pagina delle release di Aspose](https://releases.aspose.com/words/net/).
2.  Aspose.Email per .NET: Scarica e installa la libreria Aspose.Email per .NET da[Pagina delle release di Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: assicurati che .NET Framework sia installato sul tuo computer.
4. Server SMTP: per inviare e-mail è necessario avere accesso a un server SMTP.

## Importazione degli spazi dei nomi

Per usare Aspose.Words e Aspose.Email nel tuo progetto, devi importare i namespace necessari. Aggiungi le seguenti direttive using in cima al tuo file C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Per assicurarci che tu comprenda chiaramente ogni parte, scomponiamo il processo in più fasi.

## Passaggio 1: caricare il documento DOCX

 Per prima cosa, devi caricare il documento DOCX che vuoi convertire. Usa il`Document` classe da Aspose.Words per caricare il file DOCX.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Passaggio 2: salvare il documento come MHTML

 Successivamente, salva il documento caricato come file MHTML. Questo viene fatto utilizzando`Save` metodo del`Document` classe.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Riavvolgere il flusso fino all'inizio in modo che Aspose.Email possa leggerlo.
stream.Position = 0;
```

## Passaggio 3: creare un messaggio e-mail

 Ora, crea un messaggio email dal flusso MHTML usando Aspose.Email. Utilizzerai`MailMessage` classe per questo scopo.

```csharp
// Crea un messaggio e-mail MIME Aspose.Email dal flusso.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Passaggio 4: Invia l'e-mail

 Infine, invia l'email utilizzando un client SMTP. Configura il client SMTP con i dettagli del tuo server SMTP e utilizza`Send` metodo per inviare il messaggio.

```csharp
// Invia il messaggio tramite Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Conclusione

Congratulazioni! Hai convertito con successo un documento DOCX in MHTML e lo hai inviato via email usando Aspose.Words per .NET. Questo processo prevede il caricamento del documento, la sua conversione in MHTML, la creazione di un messaggio email e l'invio tramite un client SMTP. Con questi passaggi, puoi facilmente automatizzare la conversione e l'invio di documenti tramite email nelle tue applicazioni.

## Domande frequenti

### Posso usare questo metodo per convertire altri formati di documenti?
Sì, Aspose.Words supporta vari formati e puoi convertire documenti come DOC, DOCX, RTF e altri in MHTML.

### Come posso aggiungere allegati all'email?
 Puoi usare il`Attachments` proprietà del`MailMessage` classe per aggiungere allegati alla tua email.

### Aspose.Words è compatibile con .NET Core?
Sì, Aspose.Words è compatibile con .NET Core. Puoi utilizzarlo anche nelle applicazioni .NET Core.

### Ho bisogno di una licenza per Aspose.Words e Aspose.Email?
 Sì, entrambe le librerie richiedono licenze. Puoi ottenere una licenza temporanea da[Pagina di acquisto Aspose](https://purchase.aspose.com/temporary-license/) a fini di valutazione.

### Dove posso trovare ulteriore documentazione?
 Puoi trovare la documentazione dettagliata per Aspose.Words[Qui](https://reference.aspose.com/words/net/) e per Aspose.Email[Qui](https://reference.aspose.com/email/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
