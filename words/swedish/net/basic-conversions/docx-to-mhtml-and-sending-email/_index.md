---
title: Konvertera Docx till Mhtml och skicka e-post
linktitle: Konvertera Docx till Mhtml och skicka e-post
second_title: Aspose.Words Document Processing API
description: Lär dig hur du konverterar DOCX till MHTML och skickar e-post med Aspose.Words för .NET i denna steg-för-steg-guide. Öka din produktivitet med enkel automatisering.
weight: 10
url: /sv/net/basic-conversions/docx-to-mhtml-and-sending-email/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konvertera Docx till Mhtml och skicka e-post

## Introduktion

dagens digitala tidsålder är det en vanlig uppgift att konvertera dokument från ett format till ett annat och skicka dem via e-post. Den här artikeln går igenom processen att konvertera en DOCX-fil till MHTML-format och sedan skicka den som ett e-postmeddelande med Aspose.Words för .NET. Vi kommer att dela upp varje steg i en detaljerad, lätt att följa guide, så att du förstår processen från början till slut. Låt oss dyka in!

## Förutsättningar

Innan vi börjar, se till att du har följande förutsättningar på plats:

1.  Aspose.Words for .NET: Ladda ner och installera Aspose.Words for .NET-biblioteket från[Aspose releaser sida](https://releases.aspose.com/words/net/).
2.  Aspose.Email for .NET: Ladda ner och installera Aspose.Email for .NET-biblioteket från[Aspose releaser sida](https://releases.aspose.com/email/net/).
3. .NET Framework: Se till att du har .NET Framework installerat på din dator.
4. SMTP-server: Du behöver tillgång till en SMTP-server för att skicka e-post.

## Importera namnområden

För att använda Aspose.Words och Aspose.Email i ditt projekt måste du importera de nödvändiga namnrymden. Lägg till följande med hjälp av direktiv överst i din C#-fil:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Låt oss dela upp processen i flera steg för att säkerställa att du förstår varje del tydligt.

## Steg 1: Ladda DOCX-dokumentet

 Först måste du ladda DOCX-dokumentet du vill konvertera. Använd`Document` klass från Aspose.Words för att ladda din DOCX-fil.

```csharp
// Sökvägen till dokumentkatalogen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Steg 2: Spara dokumentet som MHTML

 Spara sedan det laddade dokumentet som en MHTML-fil. Detta görs med hjälp av`Save` metod för`Document` klass.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Spola tillbaka strömmen till början så att Aspose.Email kan läsa den.
stream.Position = 0;
```

## Steg 3: Skapa ett e-postmeddelande

 Skapa nu ett e-postmeddelande från MHTML-strömmen med Aspose.Email. Du kommer att använda`MailMessage` klass för detta ändamål.

```csharp
// Skapa ett Aspose.Email MIME-e-postmeddelande från strömmen.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Steg 4: Skicka e-postmeddelandet

 Slutligen, skicka e-postmeddelandet med en SMTP-klient. Konfigurera SMTP-klienten med dina SMTP-serverdetaljer och använd`Send` sätt att skicka meddelandet.

```csharp
// Skicka meddelandet med Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Slutsats

Grattis! Du har framgångsrikt konverterat ett DOCX-dokument till MHTML och skickat det via e-post med Aspose.Words för .NET. Denna process involverar att ladda dokumentet, konvertera det till MHTML, skapa ett e-postmeddelande och skicka det med en SMTP-klient. Med dessa steg kan du enkelt automatisera konvertering och e-post av dokument i dina applikationer.

## FAQ's

### Kan jag använda den här metoden för att konvertera andra dokumentformat?
Ja, Aspose.Words stöder olika format, och du kan konvertera dokument som DOC, DOCX, RTF och mer till MHTML.

### Hur kan jag lägga till bilagor till e-postmeddelandet?
 Du kan använda`Attachments` egendom av`MailMessage` klass för att lägga till bilagor till din e-post.

### Är Aspose.Words kompatibelt med .NET Core?
Ja, Aspose.Words är kompatibelt med .NET Core. Du kan också använda den i .NET Core-applikationer.

### Behöver jag en licens för Aspose.Words och Aspose.Email?
 Ja, båda biblioteken kräver licenser. Du kan få en tillfällig licens från[Aspose köpsida](https://purchase.aspose.com/temporary-license/) i utvärderingssyfte.

### Var kan jag hitta mer dokumentation?
 Du kan hitta detaljerad dokumentation för Aspose.Words[här](https://reference.aspose.com/words/net/) och för Aspose.Email[här](https://reference.aspose.com/email/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
