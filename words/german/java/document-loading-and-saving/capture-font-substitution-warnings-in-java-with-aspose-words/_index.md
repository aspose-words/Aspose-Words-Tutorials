---
category: general
date: 2026-01-11
description: Erfahren Sie, wie Sie Schriftart‑Ersetzungshinweise mit Aspose.Words
  für Java erfassen können. Dieses Schritt‑für‑Schritt‑Tutorial behandelt außerdem
  LoadOptions und Warnungs‑Callbacks.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: de
og_description: Erfassen Sie Schriftart‑Ersetzungshinweise mit Aspose.Words für Java.
  Befolgen Sie diese Anleitung, um LoadOptions und einen Warnungs‑Callback für zuverlässiges
  Laden von Dokumenten einzurichten.
og_title: Erfassung von Schriftart‑Substitutionswarnungen in Java – Vollständiges
  Tutorial
tags:
- Aspose.Words
- Java
- Document Processing
title: Erfassung von Schriftart‑Substitutionswarnungen in Java mit Aspose.Words –
  Vollständiger Leitfaden
url: /de/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erfassung von Font-Substitutionswarnungen – Vollständiges Java-Tutorial

Haben Sie jemals **Font-Substitutionswarnungen erfassen** müssen, wenn Sie ein Word-Dokument mit fehlenden Schriften öffnen? Das ist ein häufiges Ärgernis, besonders wenn Sie PDFs erzeugen oder auf einem Server drucken, auf dem nicht jede Schriftart installiert ist. Die gute Nachricht? Aspose.Words for Java macht es mühelos – konfigurieren Sie einfach ein `LoadOptions`‑Objekt und binden Sie einen Warn‑Callback ein. In diesem Leitfaden sehen Sie genau, wie das geht, warum es wichtig ist und was zu erwarten ist, wenn die Warnung ausgelöst wird.

Wir werden auch verwandte Themen ansprechen wie **Aspose.Words font substitution**, die Verwendung eines **Java warning callback**, und bewährte Methoden für **LoadOptions usage**. Am Ende haben Sie ein sofort einsatzbereites Snippet, das jedes fehlende‑Schrift‑Ereignis protokolliert, sodass Ihre nachgelagerte Verarbeitung Sie nie überrascht.

## Voraussetzungen

- Java 17 (oder ein aktuelles JDK) installiert und konfiguriert.
- Aspose.Words for Java 23.10 (oder neuer) im Klassenpfad.
- Ein Word‑Dokument, das eine Schriftart referenziert, die Sie lokal nicht haben (z. B. `DocWithMissingFont.docx`).
- Grundlegende Kenntnisse von Java‑try/catch‑Blöcken – nichts Besonderes.

Wenn Ihnen etwas davon unbekannt ist, machen Sie eine kurze Pause und installieren Sie die Bibliothek aus Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Jetzt, da die Grundlagen geschaffen sind, gehen wir zum Code über.

## Schritt 1: Einen Warn‑Callback einrichten, um **Font-Substitutionswarnungen zu erfassen**

Das Erste, was Sie benötigen, ist ein Callback, den Aspose.Words aufruft, sobald es auf eine fehlende Schriftart stößt. Hier erfassen wir **Font-Substitutionswarnungen**. Der Callback implementiert das Interface `IWarningCallback` und prüft den `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Warum das wichtig ist:** Ohne einen Callback tauscht Aspose.Words die fehlende Schriftart stillschweigend gegen eine Standardschrift aus, und Sie wissen nie, dass sich die visuelle Ausgabe geändert hat. Durch das Erfassen der Warnung können Sie protokollieren, alarmieren oder sogar das Laden abbrechen, wenn die fehlende Schriftart kritisch ist.

## Schritt 2: **LoadOptions** konfigurieren und den Callback registrieren

Jetzt erstellen wir eine `LoadOptions`‑Instanz und hängen unseren `FontWarningCallback` an. Dieser Schritt ist entscheidend für **LoadOptions usage** und stellt sicher, dass jeder Dokument‑Ladevorgang denselben Warnfilter durchläuft.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Tipp:** Sie können dasselbe `LoadOptions`‑Objekt für mehrere Dokumente wiederverwenden, was einige Zeilen Boilerplate spart und eine konsistente Handhabung von **document loading warnings** in Ihrer Anwendung gewährleistet.

## Schritt 3: Das Dokument laden und die Ausgabe beobachten

Mit dem angeschlossenen Callback laden Sie einfach Ihre Word‑Datei. Wenn das Dokument eine nicht installierte Schriftart referenziert, wird der Callback ausgelöst und gibt Details in der Konsole aus.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Erwartete Konsolenausgabe

Angenommen, `DocWithMissingFont.docx` referenziert die fehlende Schriftart *„Comic Sans MS“*, dann sehen Sie etwa Folgendes:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Enthält das Dokument **keine fehlenden Schriften**, zeigt die Konsole nur die letzte Zeile, was bestätigt, dass Ihr Callback keine Fehlalarme erzeugt hat.

## Schritt 4: Umgang mit Randfällen und häufigen Stolperfallen

### Mehrere fehlende Schriften

Verwendet ein Dokument mehrere nicht verfügbare Schriften, wird der Callback einmal pro Schriftart ausgeführt. Sie erhalten eine Reihe von Meldungen, jede mit eigenem `source` und `description`. Kein zusätzlicher Code ist nötig – stellen Sie lediglich sicher, dass Ihr Protokollierungssystem schnelle aufeinanderfolgende Aufrufe verarbeiten kann.

### Warnungen unterdrücken

In seltenen Fällen möchten Sie möglicherweise bestimmte Substitutionen ignorieren (z. B. weil Sie wissen, dass ein bestimmter Fallback akzeptabel ist). Erweitern Sie die Callback‑Logik:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Thread‑Sicherheit

Aspose.Words `LoadOptions` ist standardmäßig nicht thread‑sicher. Wenn Sie Dokumente parallel laden, erstellen Sie für jeden Thread eine separate `LoadOptions`‑Instanz oder synchronisieren Sie den Callback, um Rennbedingungen zu vermeiden.

## Schritt 5: Die substituierte Schrift im resultierenden Dokument überprüfen

Nach dem Laden möchten Sie möglicherweise bestätigen, dass die Substitution tatsächlich stattgefunden hat. Die API ermöglicht das Durchlaufen aller Runs und das Prüfen des effektiven Schriftartnamens:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Dieses Snippet gibt jeden Text‑Run mit seiner endgültigen Schriftart aus. Es ist ein praktischer Plausibilitätscheck, wenn Sie automatisierte PDF‑Konvertierungspipelines erstellen.

## Vollständiges funktionierendes Beispiel

Wenn wir alles zusammenfügen, erhalten Sie das vollständige, sofort auszuführende Programm:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Speichern Sie dies als `FontSubstitutionInfo.java`, kompilieren Sie mit `javac` und führen Sie `java FontSubstitutionInfo` aus. Sie sollten die Warnmeldungen (falls vorhanden) gefolgt von der Liste der Runs und ihrer endgültigen Schriften sehen.

## Visuelle Hilfe

![Screenshot der Konsolenausgabe, die Font-Substitutionswarnungen zeigt](/images/font-substitution-warning.png "Beispiel für das Erfassen von Font-Substitutionswarnungen")

*Alt-Text:* **capture font substitution warnings** – Konsolenausgabe nach dem Laden eines Dokuments mit fehlenden Schriften.

## Fazit

Sie wissen jetzt, wie Sie **Font-Substitutionswarnungen** mit Aspose.Words for Java **erfassen** können. Durch die Konfiguration eines `LoadOptions`‑Objekts und das Bereitstellen eines benutzerdefinierten `IWarningCallback` erhalten Sie vollständige Sichtbarkeit auf alle fehlende‑Schrift‑Ereignisse, die sonst stillschweigend das Aussehen Ihres Dokuments beeinflussen könnten. Diese Technik greift direkt in die **Aspose.Words font substitution**‑Verarbeitung ein, sorgt für zuverlässige **document loading warnings** und gibt Ihnen die Flexibilität, basierend auf Ihren Geschäftsregeln zu protokollieren, zu alarmieren oder abzubrechen.

### Was kommt als Nächstes?

- Untersuchen Sie **Java warning callback**‑Muster für andere Warnungstypen (z. B. `DEPRECATED_FEATURE`).
- Kombinieren Sie diesen Ansatz mit **PDF conversion**, um sicherzustellen, dass substituierte Schriften das Layout nicht zerstören.
- Tauchen Sie tiefer in **LoadOptions usage** ein – experimentieren Sie mit `Password`, `Encoding` und `ResourceLoadingCallback` für fortgeschrittene Szenarien.

Passen Sie den Callback gern an, leiten Sie Warnungen an ein Logging‑Framework weiter oder werfen Sie sogar eine benutzerdefinierte Ausnahme, wenn eine kritische Schrift fehlt. Der Himmel ist die Grenze, und jetzt haben Sie eine solide Grundlage zum Weiterbauen.

Viel Spaß beim Programmieren, und möge Ihre Dokumente stets genau so gerendert werden, wie Sie es erwarten!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}