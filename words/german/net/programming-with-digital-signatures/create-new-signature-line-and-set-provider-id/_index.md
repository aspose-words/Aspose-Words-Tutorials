---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET eine neue Signaturzeile erstellen und die Anbieter-ID in Word-Dokumenten festlegen. Schritt-für-Schritt-Anleitung."
"linktitle": "Neue Signaturzeile erstellen und Anbieter-ID festlegen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Neue Signaturzeile erstellen und Anbieter-ID festlegen"
"url": "/de/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Neue Signaturzeile erstellen und Anbieter-ID festlegen

## Einführung

Hallo Technikbegeisterte! Wollten Sie schon immer mal eine Signaturzeile in Ihre Word-Dokumente einfügen? Heute zeigen wir Ihnen genau das mit Aspose.Words für .NET. Diese Anleitung führt Sie Schritt für Schritt durch die Erstellung einer neuen Signaturzeile und das Festlegen der Anbieter-ID in Ihren Word-Dokumenten. Egal, ob Sie die Dokumentenverarbeitung automatisieren oder einfach nur Ihren Workflow optimieren möchten – dieses Tutorial hilft Ihnen dabei.

## Voraussetzungen

Bevor wir uns die Hände schmutzig machen, stellen wir sicher, dass wir alles haben, was wir brauchen:

1. Aspose.Words für .NET: Falls noch nicht geschehen, laden Sie es herunter [Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder eine andere C#-Entwicklungsumgebung.
3. .NET Framework: Stellen Sie sicher, dass Sie .NET Framework installiert haben.
4. PFX-Zertifikat: Zum Signieren von Dokumenten benötigen Sie ein PFX-Zertifikat. Dieses erhalten Sie bei einer vertrauenswürdigen Zertifizierungsstelle.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces in Ihr C#-Projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Okay, kommen wir zum Wesentlichen. Hier ist eine detaillierte Aufschlüsselung der einzelnen Schritte zum Erstellen einer neuen Signaturzeile und Festlegen der Anbieter-ID.

## Schritt 1: Erstellen Sie ein neues Dokument

Zunächst erstellen wir ein neues Word-Dokument. Dies dient als Vorlage für unsere Signaturzeile.

```csharp
// Der Pfad zum Dokumentenverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

In diesem Snippet initialisieren wir ein neues `Document` und ein `DocumentBuilder`. Der `DocumentBuilder` hilft uns, Elemente zu unserem Dokument hinzuzufügen.

## Schritt 2: Signaturzeilenoptionen festlegen

Als Nächstes definieren wir die Optionen für unsere Signaturzeile. Dazu gehören Name, Titel, E-Mail-Adresse und weitere Details des Unterzeichners.

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

Hier ist die `InsertSignatureLine` Die Methode fügt die Signaturzeile hinzu und wir weisen ihr eine eindeutige Anbieter-ID zu.

## Schritt 4: Speichern Sie das Dokument

Nachdem wir die Signaturzeile eingefügt haben, speichern wir das Dokument.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Dadurch wird Ihr Dokument mit der neu hinzugefügten Signaturzeile gespeichert.

## Schritt 5: Signaturoptionen einrichten

Nun müssen wir die Optionen für die Signatur des Dokuments einrichten. Dazu gehören die Signaturzeilen-ID, die Anbieter-ID, Kommentare und die Signaturzeit.

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

## Schritt 6: Zertifikatsinhaber erstellen

Zum Signieren des Dokuments verwenden wir ein PFX-Zertifikat. Erstellen wir einen Zertifikatsinhaber dafür.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

Stellen Sie sicher, dass Sie `"morzal.pfx"` mit Ihrer aktuellen Zertifikatsdatei und `"aw"` mit Ihrem Zertifikatspasswort.

## Schritt 7: Unterschreiben Sie das Dokument

Abschließend unterzeichnen wir das Dokument mit dem Dienstprogramm für digitale Signaturen.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Dadurch wird das Dokument signiert und als neue Datei gespeichert.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich eine neue Signaturzeile erstellt und die Anbieter-ID in einem Word-Dokument mit Aspose.Words für .NET festgelegt. Diese leistungsstarke Bibliothek vereinfacht die Verwaltung und Automatisierung von Dokumentverarbeitungsaufgaben enorm. Probieren Sie es aus und überzeugen Sie sich selbst, wie es Ihren Workflow optimieren kann.

## Häufig gestellte Fragen

### Kann ich das Erscheinungsbild der Signaturzeile anpassen?
Absolut! Sie können verschiedene Optionen im `SignatureLineOptions` um Ihren Bedürfnissen gerecht zu werden.

### Was ist, wenn ich kein PFX-Zertifikat habe?
Sie benötigen eine solche Berechtigung von einer vertrauenswürdigen Zertifizierungsstelle. Sie ist für die digitale Signatur von Dokumenten unerlässlich.

### Kann ich einem Dokument mehrere Signaturzeilen hinzufügen?
Ja, Sie können beliebig viele Signaturzeilen hinzufügen, indem Sie den Einfügevorgang mit verschiedenen Optionen wiederholen.

### Ist Aspose.Words für .NET mit .NET Core kompatibel?
Ja, Aspose.Words für .NET unterstützt .NET Core und ist daher vielseitig für verschiedene Entwicklungsumgebungen einsetzbar.

### Wie sicher sind die digitalen Signaturen?
Mit Aspose.Words erstellte digitale Signaturen sind hochsicher, vorausgesetzt, Sie verwenden ein gültiges und vertrauenswürdiges Zertifikat.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}