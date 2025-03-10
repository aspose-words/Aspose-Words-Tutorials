---
title: Neue Signaturzeile erstellen und Provider-ID festlegen
linktitle: Neue Signaturzeile erstellen und Provider-ID festlegen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET eine neue Signaturzeile erstellen und die Anbieter-ID in Word-Dokumenten festlegen. Schritt-für-Schritt-Anleitung.
weight: 10
url: /de/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Neue Signaturzeile erstellen und Provider-ID festlegen

## Einführung

Hallo Technikbegeisterte! Haben Sie sich schon einmal gefragt, wie Sie Ihren Word-Dokumenten programmgesteuert eine Signaturzeile hinzufügen können? Heute tauchen wir genau in diese Richtung ein und verwenden dafür Aspose.Words für .NET. Diese Anleitung führt Sie durch jeden Schritt und macht es kinderleicht, eine neue Signaturzeile zu erstellen und die Anbieter-ID in Ihren Word-Dokumenten festzulegen. Egal, ob Sie die Dokumentenverarbeitung automatisieren oder einfach nur Ihren Workflow optimieren möchten, dieses Tutorial ist für Sie da.

## Voraussetzungen

Bevor wir uns die Hände schmutzig machen, stellen wir sicher, dass wir alles haben, was wir brauchen:

1.  Aspose.Words für .NET: Wenn Sie es noch nicht getan haben, laden Sie es herunter[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder eine andere C#-Entwicklungsumgebung.
3. .NET Framework: Stellen Sie sicher, dass Sie .NET Framework installiert haben.
4. PFX-Zertifikat: Zum Signieren von Dokumenten benötigen Sie ein PFX-Zertifikat. Sie können eines von einer vertrauenswürdigen Zertifizierungsstelle erhalten.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces in Ihr C#-Projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Okay, kommen wir zum Wesentlichen. Hier ist eine detaillierte Aufschlüsselung der einzelnen Schritte zum Erstellen einer neuen Signaturzeile und Festlegen der Anbieter-ID.

## Schritt 1: Neues Dokument erstellen

Zu Beginn müssen wir ein neues Word-Dokument erstellen. Dies dient als Vorlage für unsere Signaturzeile.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 In diesem Snippet initialisieren wir ein neues`Document` und ein`DocumentBuilder` . Der`DocumentBuilder` hilft uns, Elemente zu unserem Dokument hinzuzufügen.

## Schritt 2: Optionen für die Signaturzeile festlegen

Als Nächstes definieren wir die Optionen für unsere Signaturzeile. Dazu gehören der Name, der Titel, die E-Mail-Adresse und andere Details des Unterzeichners.

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

Diese Optionen personalisieren die Signaturzeile und machen sie klar und professionell.

## Schritt 3: Einfügen der Signaturzeile

Nachdem wir unsere Optionen festgelegt haben, können wir nun die Signaturzeile in das Dokument einfügen.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 Hier die`InsertSignatureLine` Methode fügt die Signaturzeile hinzu und wir weisen ihr eine eindeutige Provider-ID zu.

## Schritt 4: Speichern Sie das Dokument

Nachdem wir die Signaturzeile eingefügt haben, speichern wir das Dokument.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Dadurch wird Ihr Dokument mit der neu hinzugefügten Signaturzeile gespeichert.

## Schritt 5: Signaturoptionen einrichten

Nun müssen wir die Optionen zum Signieren des Dokuments einrichten. Dazu gehören die Signaturzeilen-ID, die Anbieter-ID, Kommentare und die Signierzeit.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Diese Optionen stellen sicher, dass das Dokument mit den richtigen Angaben unterzeichnet wird.

## Schritt 6: Zertifikatsinhaber anlegen

Um das Dokument zu signieren, verwenden wir ein PFX-Zertifikat. Lassen Sie uns einen Zertifikatsinhaber dafür erstellen.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Ersetzen Sie unbedingt`"morzal.pfx"` mit Ihrer aktuellen Zertifikatsdatei und`"aw"` mit Ihrem Zertifikatspasswort.

## Schritt 7: Unterschreiben Sie das Dokument

Abschließend unterzeichnen wir das Dokument mithilfe des Dienstprogramms für digitale Signaturen.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Dadurch wird das Dokument signiert und als neue Datei gespeichert.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich eine neue Signaturzeile erstellt und die Anbieter-ID in einem Word-Dokument mit Aspose.Words für .NET festgelegt. Diese leistungsstarke Bibliothek macht es unglaublich einfach, Dokumentverarbeitungsaufgaben zu verwalten und zu automatisieren. Probieren Sie es aus und sehen Sie, wie es Ihren Arbeitsablauf optimieren kann.

## Häufig gestellte Fragen

### Kann ich das Erscheinungsbild der Signaturzeile anpassen?
 Auf jeden Fall! Sie können verschiedene Optionen im`SignatureLineOptions`um Ihren Bedürfnissen gerecht zu werden.

### Was ist, wenn ich kein PFX-Zertifikat habe?
Sie müssen ein Zertifikat von einer vertrauenswürdigen Zertifizierungsstelle erhalten. Es ist für die digitale Signatur von Dokumenten unerlässlich.

### Kann ich einem Dokument mehrere Signaturzeilen hinzufügen?
Ja, Sie können beliebig viele Signaturzeilen hinzufügen, indem Sie den Einfügevorgang mit unterschiedlichen Optionen wiederholen.

### Ist Aspose.Words für .NET mit .NET Core kompatibel?
Ja, Aspose.Words für .NET unterstützt .NET Core und ist daher vielseitig für verschiedene Entwicklungsumgebungen einsetzbar.

### Wie sicher sind die digitalen Signaturen?
Mit Aspose.Words erstellte digitale Signaturen sind hochsicher, sofern Sie ein gültiges und vertrauenswürdiges Zertifikat verwenden.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
