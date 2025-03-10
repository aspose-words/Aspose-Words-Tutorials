---
title: Schreibschutz im Word-Dokument
linktitle: Schreibschutz im Word-Dokument
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie Ihre Word-Dokumente schützen, indem Sie mit Aspose.Words für .NET einen schreibgeschützten Schutz anwenden. Folgen Sie unserer Schritt-für-Schritt-Anleitung.
weight: 10
url: /de/net/document-protection/read-only-protection/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Schreibschutz im Word-Dokument

## Einführung

Beim Verwalten von Word-Dokumenten müssen Sie diese manchmal schreibgeschützt machen, um ihren Inhalt zu schützen. Ob zum Teilen wichtiger Informationen ohne das Risiko versehentlicher Änderungen oder zum Sicherstellen der Integrität juristischer Dokumente – der schreibgeschützte Schutz ist eine wertvolle Funktion. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET einen schreibgeschützten Schutz in einem Word-Dokument implementieren. Wir führen Sie ausführlich und ansprechend durch jeden Schritt, sodass Sie ihn problemlos nachvollziehen können.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, müssen einige Voraussetzungen erfüllt sein:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek Aspose.Words für .NET installiert haben. Sie können sie von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Richten Sie eine Entwicklungsumgebung mit installiertem .NET ein. Visual Studio ist eine gute Wahl.
3. Grundlegende Kenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie über grundlegende Kenntnisse der C#-Programmierung verfügen.

## Namespaces importieren

Stellen wir zunächst sicher, dass wir die erforderlichen Namespaces importiert haben. Dies ist wichtig, da wir so auf die Klassen und Methoden zugreifen können, die wir von Aspose.Words für .NET benötigen.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Einrichten des Dokuments

In diesem Schritt erstellen wir ein neues Dokument und einen Dokumentgenerator. Dies bildet die Grundlage für unsere Vorgänge.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Schreiben Sie einen Text in das Dokument.
builder.Write("Open document as read-only");
```

Erläuterung:

- Wir beginnen mit der Definition des Verzeichnispfads, in dem das Dokument gespeichert wird.
-  Ein neues`Document` Objekt wird erstellt und ein`DocumentBuilder` ist damit verbunden.
- Mithilfe des Builders fügen wir dem Dokument eine einfache Textzeile hinzu.

## Schritt 2: Schreibschutz-Passwort festlegen

Als nächstes müssen wir ein Passwort für den Schreibschutz festlegen. Dieses Passwort kann maximal 15 Zeichen lang sein.

```csharp
// Geben Sie ein maximal 15 Zeichen langes Passwort ein.
doc.WriteProtection.SetPassword("MyPassword");
```

Erläuterung:

-  Der`SetPassword` -Methode wird aufgerufen auf`WriteProtection` Eigenschaft des Dokuments.
- Wir stellen ein Passwort bereit (in diesem Fall „MyPassword“), das zum Aufheben des Schutzes erforderlich ist.

## Schritt 3: Schreibgeschützte Empfehlung aktivieren

In diesem Schritt empfehlen wir, das Dokument schreibgeschützt zu machen. Das bedeutet, dass der Benutzer beim Öffnen des Dokuments aufgefordert wird, es im schreibgeschützten Modus zu öffnen.

```csharp
// Es wird empfohlen, das Dokument schreibgeschützt zu machen.
doc.WriteProtection.ReadOnlyRecommended = true;
```

Erläuterung:

-  Der`ReadOnlyRecommended` Die Eigenschaft ist auf`true`.
- Dadurch werden Benutzer aufgefordert, das Dokument im schreibgeschützten Modus zu öffnen. Sie können diese Empfehlung jedoch auch ignorieren.

## Schritt 4: Schreibschutz anwenden

Zum Schluss wenden wir den Nur-Lese-Schutz auf das Dokument an. Dieser Schritt erzwingt den Schutz.

```csharp
// Schreibschutz auf schreibgeschützt anwenden.
doc.Protect(ProtectionType.ReadOnly);
```

Erläuterung:

-  Der`Protect` -Methode wird für das Dokument aufgerufen mit`ProtectionType.ReadOnly` als Argument.
- Diese Methode erzwingt den Nur-Lese-Schutz und verhindert jegliche Änderungen am Dokument ohne Kennwort.

## Schritt 5: Speichern Sie das Dokument

Der letzte Schritt besteht darin, das Dokument mit den angewendeten Schutzeinstellungen zu speichern.

```csharp
// Speichern Sie das geschützte Dokument.
doc.Save(dataDir + "DocumentProtection.ReadOnlyProtection.docx");
```

Erläuterung:

-  Der`Save` Die Methode wird für das Dokument aufgerufen und gibt den Pfad und den Namen der Datei an.
- Das Dokument wird mit aktiviertem Leseschutz gespeichert.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich ein schreibgeschütztes Word-Dokument mit Aspose.Words für .NET erstellt. Diese Funktion stellt sicher, dass der Inhalt Ihres Dokuments intakt und unverändert bleibt, und bietet so eine zusätzliche Sicherheitsebene. Egal, ob Sie vertrauliche Informationen oder juristische Dokumente weitergeben, der schreibgeschützte Schutz ist ein unverzichtbares Tool in Ihrem Dokumentenverwaltungsarsenal.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, mit der Entwickler Word-Dokumente programmgesteuert mit C# oder anderen .NET-Sprachen erstellen, ändern, konvertieren und schützen können.

### Kann ich den Leseschutz von einem Dokument entfernen?
 Ja, Sie können den Nur-Lese-Schutz entfernen, indem Sie den`Unprotect` Methode und geben Sie das richtige Passwort ein.

### Ist das im Dokument festgelegte Passwort verschlüsselt?
Ja, Aspose.Words verschlüsselt das Passwort, um die Sicherheit des geschützten Dokuments zu gewährleisten.

### Kann ich mit Aspose.Words für .NET andere Arten von Schutz anwenden?
Ja, Aspose.Words für .NET unterstützt verschiedene Arten des Schutzes, darunter das Zulassen nur von Kommentaren, das Ausfüllen von Formularen oder das Verfolgen von Änderungen.

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?
 Ja, Sie können eine kostenlose Testversion herunterladen von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
