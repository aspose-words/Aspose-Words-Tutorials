---
title: Verschlüsselt in Word-Dokument laden
linktitle: Verschlüsseltes Dokument in Word-Dokument laden
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie verschlüsselte Word-Dokumente mit Aspose.Words für .NET laden und speichern. Sichern Sie Ihre Dokumente ganz einfach mit neuen Passwörtern. Schritt-für-Schritt-Anleitung enthalten.
weight: 10
url: /de/net/programming-with-loadoptions/load-encrypted-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verschlüsselt in Word-Dokument laden

## Einführung

In diesem Tutorial erfahren Sie, wie Sie ein verschlüsseltes Word-Dokument laden und mit einem neuen Passwort speichern, indem Sie Aspose.Words für .NET verwenden. Der Umgang mit verschlüsselten Dokumenten ist für die Aufrechterhaltung der Dokumentsicherheit unerlässlich, insbesondere beim Umgang mit vertraulichen Informationen.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  Aspose.Words für .NET-Bibliothek installiert. Sie können es herunterladen von[Hier](https://downloads.aspose.com/words/net).
2.  Eine gültige Aspose-Lizenz. Sie können eine kostenlose Testversion erhalten oder eine kaufen bei[Hier](https://purchase.aspose.com/buy).
3. Visual Studio oder eine andere .NET-Entwicklungsumgebung.

## Namespaces importieren

Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importiert haben:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Laden Sie das verschlüsselte Dokument

 Zuerst laden Sie das verschlüsselte Dokument mit dem`LoadOptions` Klasse. Mit dieser Klasse können Sie das zum Öffnen des Dokuments erforderliche Kennwort angeben.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Laden Sie ein verschlüsseltes Dokument mit dem angegebenen Passwort
Document doc = new Document(dataDir + "Encrypted.docx", new LoadOptions("password"));
```

## Schritt 2: Speichern Sie das Dokument mit einem neuen Passwort

 Als nächstes speichern Sie das geladene Dokument als ODT-Datei und legen dieses Mal ein neues Passwort fest.`OdtSaveOptions` Klasse.

```csharp
// Speichern Sie ein verschlüsseltes Dokument mit einem neuen Passwort
doc.Save(dataDir + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newpassword"));
```

## Abschluss

Wenn Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie verschlüsselte Word-Dokumente mit Aspose.Words für .NET problemlos laden und speichern. Dadurch wird sichergestellt, dass Ihre Dokumente sicher bleiben und nur autorisierte Personen darauf zugreifen können.

## Häufig gestellte Fragen

### Kann ich Aspose.Words zum Laden und Speichern anderer Dateiformate verwenden?
Ja, Aspose.Words unterstützt eine Vielzahl von Dateiformaten, darunter DOC, DOCX, PDF, HTML und mehr.

### Was passiert, wenn ich das Passwort für ein verschlüsseltes Dokument vergesse?
Wenn Sie das Passwort vergessen, können Sie das Dokument leider nicht laden. Achten Sie darauf, Passwörter sicher aufzubewahren.

### Ist es möglich, die Verschlüsselung eines Dokuments zu entfernen?
Ja, durch das Speichern des Dokuments ohne Angabe eines Passworts können Sie die Verschlüsselung aufheben.

### Kann ich unterschiedliche Verschlüsselungseinstellungen anwenden?
Ja, Aspose.Words bietet verschiedene Optionen zum Verschlüsseln von Dokumenten, einschließlich der Angabe verschiedener Arten von Verschlüsselungsalgorithmen.

### Gibt es eine Begrenzung für die Größe des Dokuments, das verschlüsselt werden kann?
Nein, Aspose.Words kann Dokumente jeder Größe verarbeiten, vorbehaltlich der Speicherbeschränkungen Ihres Systems.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
