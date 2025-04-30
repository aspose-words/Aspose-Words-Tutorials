---
"description": "Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie DOCX in MHTML konvertieren und E-Mails mit Aspose.Words für .NET versenden. Steigern Sie Ihre Produktivität durch einfache Automatisierung."
"linktitle": "Konvertieren Sie Docx in Mhtml und senden Sie E-Mails"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Konvertieren Sie Docx in Mhtml und senden Sie E-Mails"
"url": "/de/net/basic-conversions/docx-to-mhtml-and-sending-email/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Konvertieren Sie Docx in Mhtml und senden Sie E-Mails

## Einführung

Im digitalen Zeitalter ist das Konvertieren von Dokumenten von einem Format in ein anderes und deren Versand per E-Mail eine alltägliche Aufgabe. Dieser Artikel führt Sie durch die Konvertierung einer DOCX-Datei ins MHTML-Format und den anschließenden E-Mail-Versand mit Aspose.Words für .NET. Wir erklären jeden Schritt in einer detaillierten, leicht verständlichen Anleitung, damit Sie den Prozess von Anfang bis Ende verstehen. Los geht‘s!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

1. Aspose.Words für .NET: Laden Sie die Aspose.Words für .NET-Bibliothek herunter und installieren Sie sie von der [Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
2. Aspose.Email für .NET: Laden Sie die Aspose.Email für .NET-Bibliothek herunter und installieren Sie sie von der [Aspose-Veröffentlichungsseite](https://releases.aspose.com/email/net/).
3. .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem Computer installiert ist.
4. SMTP-Server: Sie benötigen Zugriff auf einen SMTP-Server, um E-Mails zu senden.

## Namespaces importieren

Um Aspose.Words und Aspose.Email in Ihrem Projekt zu verwenden, müssen Sie die erforderlichen Namespaces importieren. Fügen Sie oben in Ihrer C#-Datei die folgenden using-Direktiven hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Lassen Sie uns den Prozess in mehrere Schritte unterteilen, um sicherzustellen, dass Sie jeden Teil klar verstehen.

## Schritt 1: Laden Sie das DOCX-Dokument

Zuerst müssen Sie das zu konvertierende DOCX-Dokument laden. Verwenden Sie die `Document` Klasse von Aspose.Words, um Ihre DOCX-Datei zu laden.

```csharp
// Der Pfad zum Dokumentenverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Schritt 2: Speichern Sie das Dokument als MHTML

Anschließend speichern Sie das geladene Dokument als MHTML-Datei. Dies geschieht mit dem `Save` Methode der `Document` Klasse.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Spulen Sie den Stream zum Anfang zurück, damit Aspose.Email ihn lesen kann.
stream.Position = 0;
```

## Schritt 3: Erstellen einer E-Mail-Nachricht

Erstellen Sie nun eine E-Mail-Nachricht aus dem MHTML-Stream mit Aspose.Email. Sie verwenden die `MailMessage` Klasse für diesen Zweck.

```csharp
// Erstellen Sie eine Aspose.Email MIME-E-Mail-Nachricht aus dem Stream.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Schritt 4: Senden Sie die E-Mail

Senden Sie die E-Mail anschließend über einen SMTP-Client. Konfigurieren Sie den SMTP-Client mit Ihren SMTP-Serverdaten und verwenden Sie die `Send` Methode zum Senden der Nachricht.

```csharp
// Senden Sie die Nachricht mit Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Abschluss

Herzlichen Glückwunsch! Sie haben ein DOCX-Dokument erfolgreich in MHTML konvertiert und mit Aspose.Words für .NET per E-Mail versendet. Dieser Vorgang umfasst das Laden des Dokuments, die Konvertierung in MHTML, das Erstellen einer E-Mail-Nachricht und den Versand über einen SMTP-Client. Mit diesen Schritten können Sie die Konvertierung und den E-Mail-Versand von Dokumenten in Ihren Anwendungen ganz einfach automatisieren.

## Häufig gestellte Fragen

### Kann ich mit dieser Methode andere Dokumentformate konvertieren?
Ja, Aspose.Words unterstützt verschiedene Formate und Sie können Dokumente wie DOC, DOCX, RTF und mehr in MHTML konvertieren.

### Wie kann ich der E-Mail Anhänge hinzufügen?
Sie können die `Attachments` Eigentum der `MailMessage` Klasse, um Ihrer E-Mail Anhänge hinzuzufügen.

### Ist Aspose.Words mit .NET Core kompatibel?
Ja, Aspose.Words ist mit .NET Core kompatibel. Sie können es auch in .NET Core-Anwendungen verwenden.

### Benötige ich eine Lizenz für Aspose.Words und Aspose.Email?
Ja, beide Bibliotheken benötigen Lizenzen. Sie erhalten eine temporäre Lizenz von der [Aspose-Kaufseite](https://purchase.aspose.com/temporary-license/) zu Auswertungszwecken.

### Wo finde ich weitere Dokumentation?
Eine ausführliche Dokumentation zu Aspose.Words finden Sie [Hier](https://reference.aspose.com/words/net/) und für Aspose.Email [Hier](https://reference.aspose.com/email/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}