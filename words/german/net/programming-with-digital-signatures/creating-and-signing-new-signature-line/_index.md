---
title: Erstellen und Unterzeichnen einer neuen Signaturzeile
linktitle: Erstellen und Unterzeichnen einer neuen Signaturzeile
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Words für .NET eine Signaturzeile in einem Word-Dokument erstellen und digital signieren. Perfekt für die Dokumentenautomatisierung.
weight: 10
url: /de/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen und Unterzeichnen einer neuen Signaturzeile

## Einführung

Hallo! Sie haben also ein Word-Dokument und müssen eine Signaturzeile hinzufügen und es dann digital unterschreiben. Klingt kompliziert? Überhaupt nicht! Dank Aspose.Words für .NET können Sie dies nahtlos mit nur wenigen Codezeilen erreichen. In diesem Tutorial führen wir Sie durch den gesamten Prozess vom Einrichten Ihrer Umgebung bis zum Speichern Ihres Dokuments mit einer brandneuen Signatur. Bereit? Dann legen wir los!

## Voraussetzungen

Bevor wir uns in den Code stürzen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:
1.  Aspose.Words für .NET - Sie können[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Eine .NET-Entwicklungsumgebung – Visual Studio – wird dringend empfohlen.
3. Ein zu unterzeichnendes Dokument – Erstellen Sie ein einfaches Word-Dokument oder verwenden Sie ein vorhandenes.
4.  Eine Zertifikatsdatei - Diese wird für digitale Signaturen benötigt. Sie können eine`.pfx` Datei.
5. Bilder für die Signaturzeile – Optional eine Bilddatei für die Signatur.

## Namespaces importieren

Zuerst müssen wir die erforderlichen Namespaces importieren. Dieser Schritt ist entscheidend, da er die Umgebung für die Verwendung der Aspose.Words-Funktionen einrichtet.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Schritt 1: Einrichten des Dokumentverzeichnisses

Jedes Projekt braucht einen guten Start. Lassen Sie uns den Pfad zu Ihrem Dokumentverzeichnis einrichten. Hier werden Ihre Dokumente gespeichert und abgerufen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Neues Dokument erstellen

Erstellen wir nun mit Aspose.Words ein neues Word-Dokument. Dies wird unsere Leinwand, auf der wir die Signaturzeile hinzufügen.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 3: Einfügen der Signaturzeile

 Hier geschieht die Magie. Wir fügen eine Signaturzeile in unser Dokument ein, indem wir`DocumentBuilder` Klasse.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Schritt 4: Speichern des Dokuments mit der Signaturzeile

Sobald die Signaturzeile vorhanden ist, müssen wir das Dokument speichern. Dies ist ein Zwischenschritt, bevor wir mit der Unterzeichnung fortfahren.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Schritt 5: Einrichten der Signaturoptionen

Richten wir nun die Optionen zum Signieren des Dokuments ein. Dazu gehört die Angabe der Signaturzeilen-ID und des zu verwendenden Bildes.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Schritt 6: Laden des Zertifikats

Für digitale Signaturen ist ein Zertifikat erforderlich. Hier laden wir die Zertifikatsdatei, mit der das Dokument signiert wird.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Schritt 7: Unterzeichnen des Dokuments

 Dies ist der letzte Schritt. Wir verwenden die`DigitalSignatureUtil`Klasse zum Signieren des Dokuments. Das signierte Dokument wird unter einem neuen Namen gespeichert.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Abschluss

Und da haben Sie es! Mit diesen Schritten haben Sie erfolgreich ein neues Word-Dokument erstellt, eine Signaturzeile hinzugefügt und es mit Aspose.Words für .NET digital signiert. Es ist ein leistungsstarkes Tool, das die Dokumentenautomatisierung zum Kinderspiel macht. Egal, ob Sie mit Verträgen, Vereinbarungen oder anderen formellen Dokumenten arbeiten, diese Methode stellt sicher, dass sie sicher signiert und authentifiziert werden.

## Häufig gestellte Fragen

### Kann ich für die Signaturzeile andere Bildformate verwenden?
Ja, Sie können verschiedene Bildformate wie PNG, JPG, BMP usw. verwenden.

###  Ist es notwendig, eine`.pfx` file for the certificate?
 Ja, ein`.pfx` Datei ist ein gängiges Format zum Speichern kryptografischer Informationen, einschließlich Zertifikaten und privaten Schlüsseln.

### Kann ich in einem einzelnen Dokument mehrere Signaturzeilen hinzufügen?
Auf jeden Fall! Sie können mehrere Signaturzeilen einfügen, indem Sie den Einfügeschritt für jede Signatur wiederholen.

### Was ist, wenn ich kein digitales Zertifikat habe?
Sie müssen ein digitales Zertifikat von einer vertrauenswürdigen Zertifizierungsstelle beziehen oder eines mit Tools wie OpenSSL generieren.

### Wie überprüfe ich die digitale Signatur im Dokument?
Sie können das signierte Dokument in Word öffnen und zu den Signaturdetails gehen, um die Authentizität und Integrität der Signatur zu überprüfen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
