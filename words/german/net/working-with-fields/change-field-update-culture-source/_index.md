---
title: Feld „Kulturquelle aktualisieren“ ändern
linktitle: Feld „Kulturquelle aktualisieren“ ändern
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem Handbuch, wie Sie die Kulturquelle für Feldaktualisierungen in Aspose.Words für .NET ändern. Steuern Sie die Datumsformatierung basierend auf verschiedenen Kulturen ganz einfach.
weight: 10
url: /de/net/working-with-fields/change-field-update-culture-source/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Feld „Kulturquelle aktualisieren“ ändern

## Einführung

In diesem Tutorial tauchen wir in die Welt von Aspose.Words für .NET ein und erkunden, wie man die Kulturquelle für Feldaktualisierungen ändert. Wenn Sie mit Word-Dokumenten arbeiten, die Datumsfelder enthalten, und Sie steuern müssen, wie diese Daten basierend auf verschiedenen Kulturen formatiert werden, ist dieser Leitfaden genau das Richtige für Sie. Lassen Sie uns den Prozess Schritt für Schritt durchgehen, um sicherzustellen, dass Sie jedes Konzept verstehen und es effektiv in Ihren Projekten anwenden können.

## Voraussetzungen

Bevor wir in den Code einsteigen, stellen Sie sicher, dass Sie über Folgendes verfügen:

-  Aspose.Words für .NET: Sie können es herunterladen von[Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Jede .NET-kompatible IDE (z. B. Visual Studio).
- Grundkenntnisse in C#: Dieses Tutorial setzt grundlegende Kenntnisse der C#-Programmierung voraus.

## Namespaces importieren

Importieren wir zunächst die erforderlichen Namespaces für unser Projekt. Dadurch wird sichergestellt, dass wir Zugriff auf alle erforderlichen Klassen und Methoden von Aspose.Words haben.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Lassen Sie uns das Beispiel nun in mehrere Schritte aufteilen, damit Sie verstehen, wie Sie die Kulturquelle für die Feldaktualisierung in Aspose.Words für .NET ändern.

## Schritt 1: Initialisieren Sie das Dokument

 Der erste Schritt besteht in der Erstellung einer neuen Instanz des`Document` Klasse und eine`DocumentBuilder`Dies legt die Grundlage für die Erstellung und Bearbeitung unseres Word-Dokuments.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Felder mit spezifischem Gebietsschema einfügen

Als nächstes müssen wir Felder in das Dokument einfügen. Für dieses Beispiel fügen wir zwei Datumsfelder ein. Wir setzen das Gebietsschema der Schriftart auf Deutsch (LocaleId = 1031), um zu demonstrieren, wie sich die Kultur auf das Datumsformat auswirkt.

```csharp
builder.Font.LocaleId = 1031; // Deutsch
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Schritt 3: Kulturquelle für Feldaktualisierung festlegen

 Um die Kultur zu steuern, die beim Aktualisieren der Felder verwendet wird, setzen wir die`FieldUpdateCultureSource` Eigentum der`FieldOptions`Klasse. Diese Eigenschaft bestimmt, ob die Kultur aus dem Feldcode oder dem Dokument übernommen wird.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Schritt 4: Serienbrief ausführen

Wir müssen nun einen Serienbrief ausführen, um die Felder mit tatsächlichen Daten zu füllen. In diesem Beispiel setzen wir das zweite Datumsfeld (`Date2`) bis 1. Januar 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Schritt 5: Speichern Sie das Dokument

Abschließend speichern wir das Dokument im angegebenen Verzeichnis. Damit ist die Änderung der Kulturquelle für das Feldupdate abgeschlossen.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Abschluss

Und da haben Sie es! Sie haben die Kulturquelle für die Feldaktualisierung in Aspose.Words für .NET erfolgreich geändert. Indem Sie diese Schritte befolgen, können Sie sicherstellen, dass Ihre Word-Dokumente Datumsangaben und andere Feldwerte entsprechend den angegebenen Kultureinstellungen anzeigen. Dies kann insbesondere beim Erstellen von Dokumenten für ein internationales Publikum nützlich sein.

## Häufig gestellte Fragen

###  Was ist der Zweck der Festlegung der`LocaleId`?
 Der`LocaleId` Gibt die Kultureinstellungen für den Text an, die sich auf die Formatierung von Datumsangaben und anderen gebietsschemaabhängigen Daten auswirken.

### Kann ich ein anderes Gebietsschema als Deutsch verwenden?
 Ja, Sie können die`LocaleId`zu jedem gültigen Gebietsschemabezeichner. Zum Beispiel 1033 für Englisch (USA).

###  Was passiert, wenn ich die`FieldUpdateCultureSource` property?
Wenn diese Eigenschaft nicht festgelegt ist, werden beim Aktualisieren von Feldern die Standardkultureinstellungen des Dokuments verwendet.

### Ist es möglich, Felder basierend auf der Kultur des Dokuments statt auf dem Feldcode zu aktualisieren?
 Ja, Sie können einstellen`FieldUpdateCultureSource` Zu`FieldUpdateCultureSource.Document` um die Kultureinstellungen des Dokuments zu verwenden.

### Wie formatiere ich Daten in einem anderen Muster?
 Sie können das Datumsformatmuster im`InsertField` Methode durch Ändern der`\\@` Schalterwert.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
