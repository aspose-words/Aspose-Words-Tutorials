---
title: Signieren eines verschlüsselten Word-Dokuments
linktitle: Signieren eines verschlüsselten Word-Dokuments
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser ausführlichen Schritt-für-Schritt-Anleitung, wie Sie verschlüsselte Word-Dokumente mit Aspose.Words für .NET signieren. Perfekt für Entwickler.
weight: 10
url: /de/net/programming-with-digital-signatures/signing-encrypted-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Signieren eines verschlüsselten Word-Dokuments

## Einführung

Haben Sie sich schon einmal gefragt, wie man ein verschlüsseltes Word-Dokument signiert? Heute führen wir diesen Prozess mit Aspose.Words für .NET durch. Schnall dich an und mach dich bereit für ein detailliertes, spannendes und unterhaltsames Tutorial!

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1.  Aspose.Words für .NET: Herunterladen und installieren von[Hier](https://releases.aspose.com/words/net/).
2. Visual Studio: Stellen Sie sicher, dass Sie es installiert haben.
3. Ein gültiges Zertifikat: Sie benötigen eine PFX-Zertifikatsdatei.
4. Grundlegende C#-Kenntnisse: Durch das Verständnis der Grundlagen wird dieses Tutorial flüssiger.

## Namespaces importieren

Importieren wir zunächst die erforderlichen Namespaces. Diese sind für den Zugriff auf die Aspose.Words-Funktionen von entscheidender Bedeutung.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.DigitalSignatures;
```

Lassen Sie uns den Prozess nun in einfache, überschaubare Schritte unterteilen.

## Schritt 1: Einrichten Ihres Projekts

Richten Sie zunächst Ihr Visual Studio-Projekt ein. Öffnen Sie Visual Studio und erstellen Sie eine neue C#-Konsolenanwendung. Geben Sie ihr einen beschreibenden Namen wie „SignEncryptedWordDoc“.

## Schritt 2: Hinzufügen von Aspose.Words zu Ihrem Projekt

Als nächstes müssen wir Aspose.Words zu Ihrem Projekt hinzufügen. Es gibt mehrere Möglichkeiten, dies zu tun, aber die Verwendung von NuGet ist die einfachste. 

1. Öffnen Sie die NuGet-Paket-Manager-Konsole über Tools > NuGet-Paket-Manager > Paket-Manager-Konsole.
2. Führen Sie den folgenden Befehl aus:

```powershell
Install-Package Aspose.Words
```

## Schritt 3: Vorbereiten des Dokumentverzeichnisses

Sie benötigen ein Verzeichnis zum Speichern Ihrer Word-Dokumente und Zertifikate. Lassen Sie uns eines erstellen.

1. Erstellen Sie ein Verzeichnis auf Ihrem Computer. Der Einfachheit halber nennen wir es „DocumentDirectory“.
2. Platzieren Sie Ihr Word-Dokument (z. B. „Dokument.docx“) und Ihr .pfx-Zertifikat (z. B. „morzal.pfx“) in diesem Verzeichnis.

## Schritt 4: Schreiben des Codes

 Tauchen wir nun in den Code ein. Öffnen Sie Ihre`Program.cs` Datei und beginnen Sie mit der Einrichtung des Pfades zu Ihrem Dokumentverzeichnis und der Initialisierung des`SignOptions` mit dem Entschlüsselungskennwort.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
SignOptions signOptions = new SignOptions { DecryptionPassword = "decryptionPassword" };
```

## Schritt 5: Laden des Zertifikats

 Laden Sie anschließend Ihr Zertifikat mit dem`CertificateHolder`Klasse. Dazu benötigen Sie den Pfad zu Ihrer PFX-Datei und das Passwort des Zertifikats.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Schritt 6: Unterzeichnen des Dokuments

 Verwenden Sie abschließend die`DigitalSignatureUtil.Sign` Methode zum Signieren Ihres verschlüsselten Word-Dokuments. Diese Methode erfordert die Eingabedatei, die Ausgabedatei, den Zertifikatsinhaber und die Signaturoptionen.

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Document.docx",
    dataDir + "DigitallySignedDocument.docx",
    certHolder,
    signOptions);
```

## Schritt 7: Ausführen des Codes

Speichern Sie Ihre Datei und führen Sie das Projekt aus. Wenn alles richtig eingerichtet ist, sollten Sie Ihr signiertes Dokument im angegebenen Verzeichnis sehen.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich ein verschlüsseltes Word-Dokument mit Aspose.Words für .NET signiert. Mit dieser leistungsstarken Bibliothek wird das digitale Signieren selbst für verschlüsselte Dateien zum Kinderspiel. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Kann ich einen anderen Zertifikatstyp verwenden?
Ja, Aspose.Words unterstützt verschiedene Zertifikattypen, solange sie im richtigen Format vorliegen.

### Ist es möglich, mehrere Dokumente gleichzeitig zu unterzeichnen?
Auf jeden Fall! Sie können eine Sammlung von Dokumenten durchlaufen und jedes einzelne programmgesteuert signieren.

### Was passiert, wenn ich das Entschlüsselungskennwort vergesse?
Ohne das Entschlüsselungskennwort können Sie das Dokument leider nicht unterzeichnen.

### Kann ich dem Dokument eine sichtbare Signatur hinzufügen?
Ja, Aspose.Words ermöglicht Ihnen auch das Hinzufügen sichtbarer digitaler Signaturen.

### Gibt es eine Möglichkeit, die Signatur zu überprüfen?
 Ja, Sie können die`DigitalSignatureUtil.Verify` Methode zur Überprüfung von Signaturen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
