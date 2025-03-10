---
title: Feld-Update-Kultur
linktitle: Feld-Update-Kultur
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET die Feldaktualisierungskultur in Word-Dokumenten konfigurieren. Schritt-für-Schritt-Anleitung mit Codebeispielen und Tipps für genaue Aktualisierungen.
weight: 10
url: /de/net/working-with-fields/field-update-culture/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Feld-Update-Kultur

## Einführung

Stellen Sie sich vor, Sie arbeiten an einem Word-Dokument mit verschiedenen Feldern wie Datum, Uhrzeit oder benutzerdefinierten Informationen, die dynamisch aktualisiert werden müssen. Wenn Sie schon einmal Felder in Word verwendet haben, wissen Sie, wie wichtig es ist, die Aktualisierungen richtig vorzunehmen. Aber was ist, wenn Sie die Kultureinstellungen für diese Felder verwalten müssen? In einer globalen Welt, in der Dokumente über verschiedene Regionen hinweg gemeinsam genutzt werden, kann es einen großen Unterschied machen, wenn man weiß, wie man die Feldaktualisierungskultur konfiguriert. In diesem Handbuch erfahren Sie, wie Sie die Feldaktualisierungskultur in Word-Dokumenten mit Aspose.Words für .NET verwalten. Wir behandeln alles, vom Einrichten Ihrer Umgebung bis zum Implementieren und Speichern Ihrer Änderungen.

## Voraussetzungen

Bevor wir uns in die Einzelheiten der Feldaktualisierungskultur vertiefen, gibt es ein paar Dinge, die Sie für den Einstieg benötigen:

1. Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek Aspose.Words für .NET installiert haben. Wenn nicht, können Sie sie herunterladen[Hier](https://releases.aspose.com/words/net/).

2. Visual Studio: Dieses Tutorial setzt voraus, dass Sie Visual Studio oder eine ähnliche IDE verwenden, die .NET-Entwicklung unterstützt.

3. Grundkenntnisse in C#: Sie sollten mit der C#-Programmierung und der grundlegenden Bearbeitung von Word-Dokumenten vertraut sein.

4.  Aspose-Lizenz: Für die volle Funktionalität benötigen Sie möglicherweise eine Lizenz. Sie können eine erwerben[Hier](https://purchase.aspose.com/buy) oder holen Sie sich eine temporäre Lizenz[Hier](https://purchase.aspose.com/temporary-license/).

5.  Zugriff auf Dokumentation und Support: Für weitere Hilfe steht Ihnen die[Aspose-Dokumentation](https://reference.aspose.com/words/net/) Und[Support Forum](https://forum.aspose.com/c/words/8) sind großartige Ressourcen.

## Namespaces importieren

Um mit Aspose.Words zu beginnen, müssen Sie die relevanten Namespaces in Ihr C#-Projekt importieren. So geht's:

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

Nachdem Sie nun eingerichtet sind, unterteilen wir den Prozess der Konfiguration der Feldaktualisierungskultur in überschaubare Schritte.

## Schritt 1: Richten Sie Ihr Dokument und DocumentBuilder ein

 Zuerst müssen Sie ein neues Dokument erstellen und ein`DocumentBuilder` Objekt. Das`DocumentBuilder` ist eine praktische Klasse, mit der Sie Word-Dokumente einfach erstellen und ändern können.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Erstellen Sie das Dokument und den Dokumentgenerator.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 In diesem Schritt geben Sie das Verzeichnis an, in dem Sie Ihr Dokument speichern möchten.`Document` Klasse initialisiert ein neues Word-Dokument und die`DocumentBuilder` Klasse hilft Ihnen beim Einfügen und Formatieren von Inhalten.

## Schritt 2: Einfügen eines Zeitfelds

Als Nächstes fügen Sie ein Zeitfeld in das Dokument ein. Dies ist ein dynamisches Feld, das auf die aktuelle Zeit aktualisiert wird.

```csharp
// Fügen Sie das Zeitfeld ein.
builder.InsertField(FieldType.FieldTime, true);
```

 Hier,`FieldType.FieldTime` gibt an, dass Sie ein Zeitfeld einfügen möchten. Der zweite Parameter,`true`, gibt an, dass das Feld automatisch aktualisiert werden soll.

## Schritt 3: Feldaktualisierungskultur konfigurieren

Hier geschieht die Magie. Sie konfigurieren die Feldaktualisierungskultur, um sicherzustellen, dass die Felder entsprechend den angegebenen Kultureinstellungen aktualisiert werden.

```csharp
// Konfigurieren Sie die Feldaktualisierungskultur.
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
doc.FieldOptions.FieldUpdateCultureProvider = new FieldUpdateCultureProvider();
```

- `FieldUpdateCultureSource.FieldCode` weist Aspose.Words an, für Aktualisierungen die im Feldcode angegebene Kultur zu verwenden.
- `FieldUpdateCultureProvider` ermöglicht Ihnen, einen Kulturanbieter für Feldaktualisierungen anzugeben. Wenn Sie einen benutzerdefinierten Anbieter implementieren müssen, können Sie diese Klasse erweitern.

## Schritt 4: Implementieren des benutzerdefinierten Kulturanbieters

Jetzt müssen wir den benutzerdefinierten Kulturanbieter implementieren, der steuert, wie Kultureinstellungen wie Datumsformate angewendet werden, wenn das Feld aktualisiert wird.

Wir erstellen eine Klasse namens`FieldUpdateCultureProvider` das implementiert die`IFieldUpdateCultureProvider` Schnittstelle. Diese Klasse gibt je nach Region unterschiedliche Kulturformate zurück. Für dieses Beispiel konfigurieren wir die russischen und US-amerikanischen Kultureinstellungen.

```csharp
private class FieldUpdateCultureProvider : IFieldUpdateCultureProvider
{
    public CultureInfo GetCulture(string name, Field field)
    {
        switch (name)
        {
            case "ru-RU":
                CultureInfo culture = new CultureInfo(name, false);
                DateTimeFormatInfo format = culture.DateTimeFormat;

                format.MonthNames = new[] { "месяц 1", "месяц 2", "месяц 3", "месяц 4", "месяц 5", "месяц 6", "месяц 7", "месяц 8", "месяц 9", "месяц 10", "месяц 11", "месяц 12", "" };
                format.MonthGenitiveNames = format.MonthNames;
                format.AbbreviatedMonthNames = new[] { "мес 1", "мес 2", "мес 3", "мес 4", "мес 5", "мес 6", "мес 7", "мес 8", "мес 9", "мес 10", "мес 11", "мес 12", "" };
                format.AbbreviatedMonthGenitiveNames = format.AbbreviatedMonthNames;

                format.DayNames = new[] { "день недели 7", "день недели 1", "день недели 2", "день недели 3", "день недели 4", "день недели 5", "день недели 6" };
                format.AbbreviatedDayNames = new[] { "день 7", "день 1", "день 2", "день 3", "день 4", "день 5", "день 6" };
                format.ShortestDayNames = new[] { "д7", "д1", "д2", "д3", "д4", "д5", "д6" };

                format.AMDesignator = "До полудня";
                format.PMDesignator = "После полудня";

                const string pattern = "yyyy MM (MMMM) dd (dddd) hh:mm:ss tt";
                format.LongDatePattern = pattern;
                format.LongTimePattern = pattern;
                format.ShortDatePattern = pattern;
                format.ShortTimePattern = pattern;

                return culture;
            case "en-US":
                return new CultureInfo(name, false);
            default:
                return null;
        }
    }
}
```

## Schritt 5: Speichern Sie das Dokument

Speichern Sie Ihr Dokument abschließend im angegebenen Verzeichnis. So stellen Sie sicher, dass alle Ihre Änderungen erhalten bleiben.

```csharp
// Speichern Sie das Dokument.
doc.Save(dataDir + "UpdateCultureChamps.pdf");
```

 Ersetzen`"YOUR DOCUMENTS DIRECTORY"` mit dem Pfad, in dem Sie die Datei speichern möchten. Das Dokument wird als PDF mit dem Namen`UpdateCultureChamps.pdf`.

## Abschluss

Das Konfigurieren der Feldaktualisierungskultur in Word-Dokumenten kann komplex erscheinen, aber mit Aspose.Words für .NET wird es überschaubar und unkompliziert. Indem Sie diese Schritte befolgen, stellen Sie sicher, dass Ihre Dokumentfelder entsprechend den angegebenen kulturellen Einstellungen korrekt aktualisiert werden, wodurch Ihre Dokumente anpassungsfähiger und benutzerfreundlicher werden. Egal, ob Sie mit Zeitfeldern, Daten oder benutzerdefinierten Feldern arbeiten, das Verstehen und Anwenden dieser Einstellungen verbessert die Funktionalität und Professionalität Ihrer Dokumente.

## Häufig gestellte Fragen

### Was ist eine Feldaktualisierungskultur in Word-Dokumenten?

Die Feldaktualisierungskultur bestimmt, wie Felder in einem Word-Dokument basierend auf kulturellen Einstellungen wie Datumsformaten und Zeitkonventionen aktualisiert werden.

### Kann ich Aspose.Words verwenden, um Kulturen für andere Feldtypen zu verwalten?

Ja, Aspose.Words unterstützt verschiedene Feldtypen, einschließlich Datumsangaben und benutzerdefinierte Felder, und ermöglicht Ihnen, deren Update-Kultureinstellungen zu konfigurieren.

### Benötige ich eine spezielle Lizenz, um die Funktionen zur Feldaktualisierungskultur in Aspose.Words zu verwenden?

 Für die volle Funktionalität benötigen Sie möglicherweise eine gültige Aspose-Lizenz. Sie erhalten eine über[Aspose's Kaufseite](https://purchase.aspose.com/buy) oder verwenden Sie eine temporäre Lizenz[Hier](https://purchase.aspose.com/temporary-license/).

### Wie kann ich die Feldaktualisierungskultur weiter anpassen?

 Sie können die`FieldUpdateCultureProvider` Klasse, um einen benutzerdefinierten Kulturanbieter zu erstellen, der auf Ihre spezifischen Anforderungen zugeschnitten ist.

### Wo finde ich weitere Informationen oder bekomme Hilfe, wenn ich auf Probleme stoße?

 Ausführliche Dokumentation und Support finden Sie im[Aspose-Dokumentation](https://reference.aspose.com/words/net/) und die[Aspose Support Forum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
