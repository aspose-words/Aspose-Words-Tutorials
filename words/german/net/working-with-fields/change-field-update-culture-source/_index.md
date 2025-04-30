---
"description": "Erfahren Sie in diesem Handbuch, wie Sie die Kulturquelle für Feldaktualisierungen in Aspose.Words für .NET ändern. Steuern Sie die Datumsformatierung basierend auf verschiedenen Kulturen ganz einfach."
"linktitle": "Feld „Kulturquelle aktualisieren“ ändern"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Feld „Kulturquelle aktualisieren“ ändern"
"url": "/de/net/working-with-fields/change-field-update-culture-source/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Feld „Kulturquelle aktualisieren“ ändern

## Einführung

In diesem Tutorial tauchen wir in die Welt von Aspose.Words für .NET ein und erfahren, wie Sie die Kulturquelle für Feldaktualisierungen ändern. Wenn Sie mit Word-Dokumenten arbeiten, die Datumsfelder enthalten, und die Formatierung dieser Daten basierend auf verschiedenen Kulturen steuern müssen, ist diese Anleitung genau das Richtige für Sie. Wir gehen den Prozess Schritt für Schritt durch, um sicherzustellen, dass Sie jedes Konzept verstehen und es effektiv in Ihren Projekten anwenden können.

## Voraussetzungen

Bevor wir uns in den Code stürzen, stellen Sie sicher, dass Sie über Folgendes verfügen:

- Aspose.Words für .NET: Sie können es herunterladen von [Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Jede .NET-kompatible IDE (z. B. Visual Studio).
- Grundkenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie über grundlegende Kenntnisse der C#-Programmierung verfügen.

## Namespaces importieren

Importieren wir zunächst die erforderlichen Namespaces für unser Projekt. Dadurch stellen wir sicher, dass wir Zugriff auf alle erforderlichen Klassen und Methoden von Aspose.Words haben.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Lassen Sie uns das Beispiel nun in mehrere Schritte aufteilen, damit Sie verstehen, wie Sie die Kulturquelle für die Feldaktualisierung in Aspose.Words für .NET ändern.

## Schritt 1: Initialisieren des Dokuments

Der erste Schritt besteht darin, eine neue Instanz des `Document` Klasse und eine `DocumentBuilder`Dies legt die Grundlage für die Erstellung und Bearbeitung unseres Word-Dokuments.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Felder mit spezifischem Gebietsschema einfügen

Als Nächstes müssen wir Felder in das Dokument einfügen. Für dieses Beispiel fügen wir zwei Datumsfelder ein. Wir setzen das Gebietsschema der Schriftart auf Deutsch (LocaleId = 1031), um zu veranschaulichen, wie sich die Kultur auf das Datumsformat auswirkt.

```csharp
builder.Font.LocaleId = 1031; // Deutsch
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Schritt 3: Kulturquelle für Feldaktualisierung festlegen

Um die Kultur zu steuern, die beim Aktualisieren der Felder verwendet wird, setzen wir die `FieldUpdateCultureSource` Eigentum der `FieldOptions` Klasse. Diese Eigenschaft bestimmt, ob die Kultur aus dem Feldcode oder dem Dokument übernommen wird.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Schritt 4: Serienbrief ausführen

Wir müssen nun einen Serienbrief ausführen, um die Felder mit den tatsächlichen Daten zu füllen. In diesem Beispiel setzen wir das zweite Datumsfeld (`Date2`) bis 1. Januar 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Schritt 5: Speichern Sie das Dokument

Abschließend speichern wir das Dokument im angegebenen Verzeichnis. Damit ist die Änderung der Feldaktualisierungskulturquelle abgeschlossen.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Abschluss

Und da haben Sie es! Sie haben die Kulturquelle für die Feldaktualisierung in Aspose.Words für .NET erfolgreich geändert. Mit diesen Schritten stellen Sie sicher, dass Ihre Word-Dokumente Datumsangaben und andere Feldwerte gemäß den angegebenen Kultureinstellungen anzeigen. Dies ist besonders nützlich, wenn Sie Dokumente für ein internationales Publikum erstellen.

## Häufig gestellte Fragen

### Was ist der Zweck der Festlegung der `LocaleId`?
Der `LocaleId` Gibt die Kultureinstellungen für den Text an, die sich auf die Formatierung von Datumsangaben und anderen gebietsschemaabhängigen Daten auswirken.

### Kann ich eine andere Sprache als Deutsch verwenden?
Ja, Sie können die `LocaleId` zu einer beliebigen gültigen Gebietsschemakennung. Beispielsweise 1033 für Englisch (USA).

### Was passiert, wenn ich die `FieldUpdateCultureSource` Eigentum?
Wenn diese Eigenschaft nicht festgelegt ist, werden beim Aktualisieren der Felder die Standardkultureinstellungen des Dokuments verwendet.

### Ist es möglich, Felder basierend auf der Kultur des Dokuments statt auf dem Feldcode zu aktualisieren?
Ja, Sie können einstellen `FieldUpdateCultureSource` Zu `FieldUpdateCultureSource.Document` um die Kultureinstellungen des Dokuments zu verwenden.

### Wie formatiere ich Datumsangaben in einem anderen Muster?
Sie können das Datumsformatmuster im `InsertField` Methode durch Ändern der `\\@` Schalterwert.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}