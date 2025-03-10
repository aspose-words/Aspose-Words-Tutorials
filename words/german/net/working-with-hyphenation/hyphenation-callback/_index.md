---
title: Silbentrennungs-Rückruf
linktitle: Silbentrennungs-Rückruf
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser umfassenden Schritt-für-Schritt-Anleitung, wie Sie in Aspose.Words für .NET die Silbentrennungs-Rückruffunktion implementieren, um die Dokumentformatierung zu verbessern.
weight: 10
url: /de/net/working-with-hyphenation/hyphenation-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Silbentrennungs-Rückruf


## Einführung

Hallo! Haben Sie sich schon einmal mit den Komplexitäten der Textformatierung herumgeschlagen, insbesondere bei Sprachen, die Silbentrennung erfordern? Damit sind Sie nicht allein. Silbentrennung ist zwar für ein korrektes Textlayout entscheidend, kann aber auch ein wenig Kopfzerbrechen bereiten. Aber wissen Sie was? Aspose.Words für .NET unterstützt Sie dabei. Mit dieser leistungsstarken Bibliothek können Sie die Textformatierung nahtlos verwalten, einschließlich der Silbentrennung über einen Rückrufmechanismus. Neugierig geworden? Lassen Sie uns in die Einzelheiten eintauchen und sehen, wie Sie mit Aspose.Words für .NET einen Silbentrennungsrückruf implementieren können.

## Voraussetzungen

Bevor wir uns mit dem Code beschäftigen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1. Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek haben. Sie können[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. IDE: Eine Entwicklungsumgebung wie Visual Studio.
3. Grundlegende Kenntnisse in C#: Verständnis von C# und .NET Framework.
4. Silbentrennungswörterbücher: Silbentrennungswörterbücher für die Sprachen, die Sie verwenden möchten.
5.  Aspose-Lizenz: Eine gültige Aspose-Lizenz. Sie erhalten eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) wenn Sie keines haben.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces. Dadurch wird sichergestellt, dass unser Code Zugriff auf alle Klassen und Methoden hat, die wir von Aspose.Words benötigen.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## Schritt 1: Silbentrennungs-Callback registrieren

Zu Beginn müssen wir unseren Silbentrennungs-Callback registrieren. Hier weisen wir Aspose.Words an, unsere benutzerdefinierte Silbentrennungslogik zu verwenden.

```csharp
try
{
    // Silbentrennungs-Rückruf registrieren.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

 Hier erstellen wir eine Instanz unseres benutzerdefinierten Callbacks und weisen sie zu`Hyphenation.Callback`.

## Schritt 2: Dokumentpfad festlegen

Als nächstes müssen wir das Verzeichnis definieren, in dem unsere Dokumente gespeichert sind. Dies ist wichtig, da wir Dokumente aus diesem Pfad laden und speichern werden.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihren Dokumenten.

## Schritt 3: Laden Sie das Dokument

Laden wir nun das Dokument, das eine Silbentrennung erfordert.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

Hier laden wir ein deutsches Textdokument. Sie können ersetzen`"German text.docx"` durch den Dateinamen Ihres Dokuments.

## Schritt 4: Speichern Sie das Dokument

Nachdem wir das Dokument geladen haben, speichern wir es in einer neuen Datei und wenden dabei den Silbentrennungs-Callback an.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

Diese Zeile speichert das Dokument als PDF mit angewendeter Silbentrennung.

## Schritt 5: Behandeln der Wörterbuchausnahme „Fehlende Silbentrennung“

Manchmal kann es vorkommen, dass das Silbentrennungswörterbuch fehlt. Wir kümmern uns darum.

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

In diesem Block fangen wir die spezifische Ausnahme im Zusammenhang mit fehlenden Wörterbüchern ab und drucken die Meldung.

## Schritt 6: Implementieren der benutzerdefinierten Silbentrennungs-Rückrufklasse

 Lassen Sie uns nun die`CustomHyphenationCallback` Klasse, die die Anforderung von Silbentrennungswörterbüchern verarbeitet.

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        // Wörterbuch für die gewünschte Sprache registrieren.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

 In dieser Klasse`RequestDictionary` Die Methode wird immer dann aufgerufen, wenn ein Silbentrennungswörterbuch benötigt wird. Sie prüft die Sprache und registriert das entsprechende Wörterbuch.

## Abschluss

Und da haben Sie es! Sie haben gerade gelernt, wie Sie einen Silbentrennungs-Callback in Aspose.Words für .NET implementieren. Indem Sie diese Schritte befolgen, können Sie sicherstellen, dass Ihre Dokumente unabhängig von der Sprache schön formatiert sind. Egal, ob Sie mit Englisch, Deutsch oder einer anderen Sprache arbeiten, mit dieser Methode können Sie die Silbentrennung mühelos handhaben.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek zur Dokumentbearbeitung, mit der Entwickler Dokumente programmgesteuert erstellen, ändern und konvertieren können.

### Warum ist die Silbentrennung bei der Dokumentformatierung wichtig?
Durch die Silbentrennung wird das Textlayout verbessert, indem Wörter an den entsprechenden Stellen getrennt werden. Auf diese Weise wird das Dokument besser lesbar und optisch ansprechender.

### Kann ich Aspose.Words kostenlos nutzen?
 Aspose.Words bietet eine kostenlose Testversion an. Sie können es bekommen[Hier](https://releases.aspose.com/).

### Wie bekomme ich ein Silbentrennungswörterbuch?
Sie können Silbentrennungswörterbücher aus verschiedenen Online-Ressourcen herunterladen oder bei Bedarf Ihr eigenes erstellen.

### Was passiert, wenn ein Silbentrennungswörterbuch fehlt?
 Wenn ein Wörterbuch fehlt,`RequestDictionary`Methode löst eine Ausnahme aus, die Sie behandeln können, um den Benutzer zu informieren oder einen Fallback bereitzustellen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
