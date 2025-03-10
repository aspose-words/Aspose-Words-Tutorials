---
title: Unbeschränkt bearbeitbare Bereiche im Word-Dokument
linktitle: Unbeschränkt bearbeitbare Bereiche im Word-Dokument
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser umfassenden Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET uneingeschränkt bearbeitbare Bereiche in einem Word-Dokument erstellen.
weight: 10
url: /de/net/document-protection/unrestricted-editable-regions/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Unbeschränkt bearbeitbare Bereiche im Word-Dokument

## Einführung

Wenn Sie schon immer ein Word-Dokument schützen, aber dennoch bestimmte Teile editierbar lassen wollten, sind Sie hier richtig! Diese Anleitung führt Sie durch den Prozess der Einrichtung uneingeschränkt editierbarer Bereiche in einem Word-Dokument mit Aspose.Words für .NET. Wir decken alles ab, von den Voraussetzungen bis zu den detaillierten Schritten, um sicherzustellen, dass Sie ein reibungsloses Erlebnis haben. Bereit? Tauchen wir ein!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1.  Aspose.Words für .NET: Wenn Sie es noch nicht getan haben, laden Sie es herunter[Hier](https://releases.aspose.com/words/net/).
2. Eine gültige Aspose-Lizenz: Sie können eine temporäre Lizenz erhalten[Hier](https://purchase.aspose.com/temporary-license/).
3. Visual Studio: Jede aktuelle Version sollte einwandfrei funktionieren.
4. Grundkenntnisse in C# und .NET: Diese helfen Ihnen dabei, dem Code zu folgen.

Nun, da Sie fertig sind, können wir mit dem spaßigen Teil beginnen!

## Namespaces importieren

Um Aspose.Words für .NET verwenden zu können, müssen Sie die erforderlichen Namespaces importieren. So können Sie das tun:

```csharp
using Aspose.Words;
using Aspose.Words.Editing;
```

## Schritt 1: Einrichten Ihres Projekts

Lassen Sie uns zunächst ein neues C#-Projekt in Visual Studio erstellen.

1. Öffnen Sie Visual Studio: Öffnen Sie zunächst Visual Studio und erstellen Sie ein neues Konsolen-App-Projekt.
2. Installieren Sie Aspose.Words: Verwenden Sie den NuGet-Paketmanager, um Aspose.Words zu installieren. Sie können dies tun, indem Sie den folgenden Befehl in der Paketmanager-Konsole ausführen:
   ```sh
   Install-Package Aspose.Words
   ```

## Schritt 2: Laden des Dokuments

Laden wir nun das Dokument, das Sie schützen möchten. Stellen Sie sicher, dass in Ihrem Verzeichnis ein Word-Dokument bereitliegt.

1. Legen Sie das Dokumentverzeichnis fest: Definieren Sie den Pfad zu Ihrem Dokumentverzeichnis.
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```
2.  Laden Sie das Dokument: Verwenden Sie die`Document` Klasse, um Ihr Word-Dokument zu laden.
   ```csharp
   Document doc = new Document(dataDir + "Document.docx");
   ```

## Schritt 3: Schützen des Dokuments

Als nächstes setzen wir das Dokument auf schreibgeschützt. Dadurch wird sichergestellt, dass ohne das Passwort keine Änderungen vorgenommen werden können.

1.  Initialisieren Sie DocumentBuilder: Erstellen Sie eine Instanz von`DocumentBuilder` , um Änderungen am Dokument vorzunehmen.
   ```csharp
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```
2. Schutzstufe festlegen: Schützen Sie das Dokument mit einem Kennwort.
   ```csharp
   doc.Protect(ProtectionType.ReadOnly, "MyPassword");
   ```
3. Schreibgeschützten Text hinzufügen: Fügen Sie schreibgeschützten Text ein.
   ```csharp
   builder.Writeln("Hello world! Since we have set the document's protection level to read-only, we cannot edit this paragraph without the password.");
   ```

## Schritt 4: Editierbare Bereiche erstellen

Und hier geschieht die Magie. Wir erstellen Abschnitte im Dokument, die trotz des allgemeinen Nur-Lese-Schutzes bearbeitet werden können.

1. Beginn des bearbeitbaren Bereichs: Definieren Sie den Beginn des bearbeitbaren Bereichs.
   ```csharp
   EditableRangeStart edRangeStart = builder.StartEditableRange();
   ```
2.  Editierbares Bereichsobjekt erstellen: Ein`EditableRange` Objekt wird automatisch erstellt.
   ```csharp
   EditableRange editableRange = edRangeStart.EditableRange;
   ```
3. Bearbeitbaren Text einfügen: Fügen Sie Text innerhalb des bearbeitbaren Bereichs hinzu.
   ```csharp
   builder.Writeln("Paragraph inside first editable range");
   ```

## Schritt 5: Schließen des bearbeitbaren Bereichs

Ein editierbarer Bereich ist ohne Ende nicht vollständig. Das fügen wir als Nächstes hinzu.

1. Ende des bearbeitbaren Bereichs: Definieren Sie das Ende des bearbeitbaren Bereichs.
   ```csharp
   EditableRangeEnd edRangeEnd = builder.EndEditableRange();
   ```
2. Fügen Sie schreibgeschützten Text außerhalb des Bereichs hinzu: Fügen Sie Text außerhalb des bearbeitbaren Bereichs ein, um den Schutz zu demonstrieren.
   ```csharp
   builder.Writeln("This paragraph is outside any editable ranges, and cannot be edited.");
   ```

## Schritt 6: Speichern des Dokuments

Lassen Sie uns abschließend das Dokument mit dem angewendeten Schutz und den bearbeitbaren Bereichen speichern.

1.  Speichern Sie das Dokument: Verwenden Sie die`Save` Methode, um Ihr geändertes Dokument zu speichern.
   ```csharp
   doc.Save(dataDir + "DocumentProtection.UnrestrictedEditableRegions.docx");
   ```

## Abschluss

Und da haben Sie es! Sie haben mit Aspose.Words für .NET erfolgreich uneingeschränkt bearbeitbare Bereiche in einem Word-Dokument erstellt. Diese Funktion ist unglaublich nützlich für kollaborative Umgebungen, in denen bestimmte Teile eines Dokuments unverändert bleiben müssen, während andere bearbeitet werden können. 

 Experimentieren Sie mit komplexeren Szenarien und verschiedenen Schutzstufen, um das Beste aus Aspose.Words herauszuholen. Wenn Sie Fragen haben oder auf Probleme stoßen, zögern Sie nicht, sich die[Dokumentation](https://reference.aspose.com/words/net/) oder wenden Sie sich an[Unterstützung](https://forum.aspose.com/c/words/8).

## Häufig gestellte Fragen

### Kann ich mehrere bearbeitbare Bereiche in einem Dokument haben?
Ja, Sie können mehrere bearbeitbare Bereiche erstellen, indem Sie bearbeitbare Bereiche an verschiedenen Teilen des Dokuments beginnen und enden lassen.

### Welche anderen Schutzarten sind in Aspose.Words verfügbar?
Aspose.Words unterstützt verschiedene Schutztypen wie AllowOnlyComments, AllowOnlyFormFields und NoProtection.

### Ist es möglich, den Schutz eines Dokuments aufzuheben?
 Ja, Sie können den Schutz entfernen mit dem`Unprotect` Methode und geben Sie das richtige Passwort ein.

### Kann ich für verschiedene Bereiche unterschiedliche Passwörter festlegen?
Nein, der Schutz auf Dokumentebene wendet ein einziges Kennwort für das gesamte Dokument an.

### Wie beantrage ich eine Lizenz für Aspose.Words?
Sie können eine Lizenz anwenden, indem Sie sie aus einer Datei oder einem Stream laden. Detaillierte Schritte finden Sie in der Dokumentation.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
