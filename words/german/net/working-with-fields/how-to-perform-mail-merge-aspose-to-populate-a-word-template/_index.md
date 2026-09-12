---
category: general
date: 2026-09-11
description: Mail Merge Aspose ermöglicht das Laden einer Word‑Vorlage und das Befüllen
  der Word‑Vorlage mit Daten, wodurch die Dokumentenerstellung automatisiert wird,
  um personalisierte Briefe zu erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- mail merge aspose
- populate word template
- load word template
- automate document generation
- create personalized letters
language: de
lastmod: 2026-09-11
og_description: Mail-Merge von Aspose ermöglicht das Laden einer Word-Vorlage und
  das Befüllen derselben, wodurch die Dokumentenerstellung optimiert wird, sodass
  Sie schnell personalisierte Briefe erstellen können.
og_image_alt: Screenshot of C# code using Aspose.Words to perform a mail merge on
  a Word template
og_title: 'Mail-Merge Aspose: Word‑Vorlage in wenigen Minuten befüllen'
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Mail merge aspose lets you load word template and populate word template
    with data, automating document generation for creating personalized letters.
  headline: How to perform mail merge aspose to populate a Word template
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
title: Wie man Mail‑Merge mit Aspose verwendet, um eine Word‑Vorlage zu füllen
url: /de/net/working-with-fields/how-to-perform-mail-merge-aspose-to-populate-a-word-template/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Mail Merge mit Aspose ausführt, um eine Word‑Vorlage zu befüllen

Wenn Sie **Mail Merge mit Aspose** benötigen, um eine Charge personalisierter Briefe zu erzeugen, zeigt Ihnen diese Anleitung genau, wie Sie eine Word‑Vorlage laden, mit Daten befüllen und die Dokumentenerstellung in wenigen Zeilen C# automatisieren. Egal, ob Sie ein Mailing‑System oder ein Reporting‑Tool bauen – das vollständige Beispiel unten ermöglicht Ihnen das Erstellen personalisierter Briefe, ohne manuelle Merge‑Logik schreiben zu müssen.

Sie lernen, wie Sie **Word‑Vorlage laden**, die Low‑Code‑Klasse `MailMerger` verwenden und **Word‑Vorlage** mit einer anonymen Datenquelle **befüllen**. Am Ende des Tutorials besitzen Sie eine sofort ausführbare Konsolen‑App, die ein zusammengeführtes Word‑Dokument erzeugt, das Sie per E‑Mail versenden, drucken oder archivieren können.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 SDK oder neuer installiert  
* Eine gültige Aspose.Words for .NET Lizenz (oder einen kostenlosen Evaluierungsschlüssel)  
* Das NuGet‑Paket `Aspose.Words` (Version 23.10 oder neuer) in Ihrem Projekt installiert  
* Eine Word‑Datei (`MailMergeTemplate.docx`), die MERGEFIELD‑Platzhalter wie **«Name»** und **«Age»** enthält  

Sie können die Vorlage in Microsoft Word erstellen, indem Sie *Einfügen → Schnellbausteine → Feld → MergeField* einfügen und die Felder exakt mit den Eigenschaftsnamen Ihrer Datenquelle benennen.

## Schritt 1 – Datenquelle für das Mail Merge vorbereiten

Der Low‑Code‑Merge funktioniert mit jeder aufzählbaren Sammlung. In diesem Beispiel verwenden wir ein Array anonymer Objekte, Sie könnten aber auch ein `DataTable`, eine Liste von POCOs oder Daten aus einer Datenbank übergeben.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

// Sample data that will replace the MERGEFIELDs in the template
var data = new[]
{
    new { Name = "Alice",   Age = 30 },
    new { Name = "Bob",     Age = 45 },
    new { Name = "Charlie", Age = 28 }
};
```

**Warum das wichtig ist:**  
Der Name jeder Eigenschaft des Objekts (`Name`, `Age`) muss einem MERGEFIELD in der Vorlage entsprechen. Die Klasse `MailMerger` ordnet die Eigenschaften automatisch den Feldern zu und eliminiert damit die Notwendigkeit manueller `FieldMerging`‑Events.

## Schritt 2 – Word‑Vorlage laden, die MERGEFIELDs enthält

Das Laden der Vorlage ist mit der Klasse `Document` unkompliziert. Der Pfad kann absolut oder relativ zum Arbeitsverzeichnis der ausführbaren Datei sein.

```csharp
// Load the Word template that contains MERGEFIELDs
Document template = new Document("YOUR_DIRECTORY/MailMergeTemplate.docx");
```

**Profi‑Tipp:**  
Wenn Sie den Code aus Visual Studio ausführen, setzen Sie für die Vorlagendatei *Copy to Output Directory* auf **Copy always**. Das stellt sicher, dass die Datei verfügbar ist, wenn das kompilierte Binary ausgeführt wird.

## Schritt 3 – MailMerger‑Instanz erstellen, die an die Vorlage gebunden ist

Die Klasse `MailMerger` befindet sich im Namespace `Aspose.Words.LowCode` und stellt eine einzelne Methode `Execute` bereit, die die Datenquelle akzeptiert.

```csharp
// Bind the template to a MailMerger instance
MailMerger merger = new MailMerger(template);
```

**Warum MailMerger verwenden?**  
`MailMerger` abstrahiert die Boilerplate‑Aufrufe von `MailMerge.Execute`, übernimmt die Feld‑Erkennung, Datenbindung und das Klonen des Dokuments intern. Das macht den Code ideal für **Automatisierung der Dokumentenerstellung**‑Szenarien, bei denen Sie eine saubere Low‑Code‑Lösung wünschen.

## Schritt 4 – Low‑Code‑Merge mit den vorbereiteten Daten ausführen

Der Aufruf von `Execute` liefert ein neues `Document`, das enthält


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word‑Merge‑Felder umbenennen mit Aspose.Words für Java](/words/english/java/mail-merge-reporting/rename-word-merge-fields-aspose-words-java/)
- [Word‑Dokument mit Kopf‑ und Fußzeile erstellen mit Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Word‑Dokument erstellen und formatieren in Aspose.Words für .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}