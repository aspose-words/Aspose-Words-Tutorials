---
category: general
date: 2026-03-17
description: Lernen Sie das Aspose‑Warnungs‑Callback‑Tutorial, um fehlende Schriftarten
  zu erkennen und fehlende Schriftarten in Java‑Dokumenten zu verfolgen, mit einem
  vollständigen, ausführbaren Beispiel.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: de
og_description: Meistern Sie das Aspose‑Warnungs‑Callback‑Tutorial, um fehlende Schriftarten
  zu erkennen und fehlende Schriftarten in Ihrem Java‑Word‑Verarbeitungs‑Workflow
  zu verfolgen.
og_title: Aspose Warnungs‑Callback‑Tutorial – Fehlende Schriftarten erkennen
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Aspose‑Warnungs‑Callback‑Tutorial – Erkennen und Verfolgen fehlender Schriftarten
url: /de/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – Fehlende Schriftarten erkennen und verfolgen

Haben Sie sich schon einmal gefragt, wie man **fehlende Schriftarten** beim Konvertieren oder Bearbeiten von Word‑Dateien mit Aspose.Words **erkennen** kann? Sie sind nicht allein. In vielen realen Projekten kann eine fehlende Schriftart Layout‑Fehler verursachen, und Sie benötigen eine zuverlässige Methode, um **fehlende Schriftarten zu verfolgen**, bevor sie später Probleme machen.  

Die gute Nachricht: Das **aspose warning callback tutorial** bietet einen sauberen, programmatischen Hook, der genau diese Schriftart‑Ersetzungs‑Warnungen ausgibt, sobald sie auftreten. In diesem Leitfaden gehen wir Schritt für Schritt durch das Einrichten des Callbacks, das Laden eines Dokuments und das Anzeigen der Warnungen – alles in Java.

Am Ende dieses Artikels können Sie fehlende Schriftarten automatisch erkennen, protokollieren und entscheiden, ob Sie eine Ersatzschrift einbetten oder Ihre Quelldateien anpassen wollen. Keine externen Tools nötig.

## Voraussetzungen

- **Java 8+** (der Code kompiliert mit jeder aktuellen JDK)
- **Aspose.Words for Java** Version 23.10 oder neuer – Download vom Aspose‑Portal oder als Maven‑Abhängigkeit hinzufügen.
- Eine Beispiel‑DOCX, die bewusst eine Schriftart referenziert, die nicht installiert ist (z. B. „Comic Sans MS“ auf einer Linux‑Box).

Das war’s – keine zusätzlichen Bibliotheken, keine komplexen Build‑Schritte.

## Schritt 1: Einen Warning‑Callback registrieren – Der Kern des aspose warning callback tutorial

Der erste Schritt im Tutorial zeigt, wie man einen Warn‑Listener anhängt. Aspose.Words erzeugt für jedes auftretende Problem ein `WarningInfo`‑Objekt, und das Flag `WarningSource.FONT_SUBSTITUTION` signalisiert genau dann, wenn eine Schriftart ausgetauscht wird.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Warum das wichtig ist:** Ohne den Callback ersetzt Aspose stillschweigend fehlende Schriftarten, und Sie wissen nie, welche Glyphen möglicherweise falsch dargestellt werden. Durch das Protokollieren der Warnung können Sie **fehlende Schriftarten** frühzeitig **erkennen** und entscheiden, ob Sie die korrekte Schrift einbetten.

> **Pro‑Tipp:** Wenn Sie Warnungen später auswerten möchten, speichern Sie sie in einer `List<WarningInfo>` statt sie direkt auszugeben.

## Schritt 2: Das Dokument laden – Wo fehlende Schriftarten versteckt sein können

Jetzt laden wir die DOCX, die möglicherweise Schriftarten referenziert, die auf dem Rechner nicht vorhanden sind. Das Laden löst den Warn‑Callback aus, falls Schriftarten fehlen.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Was im Hintergrund passiert:** Aspose analysiert die Stil‑Definitionen des Dokuments, durchsucht jeden Text‑Run und prüft das System‑Schriftarten‑Repository. Wenn keine exakte Übereinstimmung gefunden wird, greift es auf eine Ersatzschrift zurück und löst die gerade registrierte Warnung aus.

## Schritt 3: Das Dokument speichern – Die Warnungen ausgeben

Abschließend speichern wir das Dokument. Der Save‑Vorgang prüft die Schriftarten erneut, sodass alle Warnungen, die beim Laden nicht ausgelöst wurden, jetzt erscheinen.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Wenn Sie das Programm ausführen, sehen Sie eine Konsolenausgabe ähnlich wie:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Diese Ausgabe beweist, dass das **aspose warning callback tutorial** funktioniert, Sie haben **fehlende Schriftarten** erfolgreich **erkannt** und **verfolgen** jetzt über das Log.

## Wie man fehlende Schriftarten in einem Word‑Dokument erkennt – Über die Grundlagen hinaus

Der Callback‑Ansatz eignet sich gut für einmalige Durchläufe, aber manchmal benötigen Sie ein wiederverwendbares Hilfsprogramm. Hier ein kurzer Wrapper, den Sie in jedes Projekt einbinden können:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Aufrufbeispiel:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Damit haben Sie eine wiederverwendbare **detect missing fonts**‑Methode, die eine Liste zurückgibt, die Sie in eine CI‑Pipeline oder UI einspeisen können.

## Fehlende Schriftarten mit Aspose.Words verfolgen – Reporting für Teams

In einem größeren Team möchten Sie vielleicht einen CSV‑Report aller fehlenden Schriftarten über viele Dokumente hinweg erzeugen. Kombinieren Sie das vorherige Hilfsprogramm mit einer einfachen Dateischleife:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

Durch Ausführen dieses Skripts erhalten Sie eine **track missing fonts**‑CSV, die jeder Entwickler vor dem Commit eines Dokuments prüfen kann.

## Häufige Stolperfallen & wie man sie vermeidet

| Stolperfalle | Warum sie auftritt | Lösung |
|--------------|-------------------|--------|
| **Callback wird nicht ausgelöst** | Der Callback wurde **nach** dem Laden des Dokuments gesetzt. | `Document.setWarningCallback` ganz oben in `main` platzieren. |
| **Nur die erste Warnung erscheint** | Aspose cached Warnungen pro `Document`‑Instanz. | Für jede Datei ein frisches `Document`‑Objekt verwenden oder den Callback zwischen den Durchläufen zurücksetzen. |
| **Falscher Schriftartname im Log** | Die Beschreibung enthält zusätzlichen Text („Font … not found“). | Mit dem im CSV‑Beispiel gezeigten Regex entfernen. |
| **Performance‑Einbußen bei großen Stapeln** | Der Callback wird für jeden Text‑Run ausgeführt, was teuer sein kann. | Prüfung auf einen Pre‑Flight‑Schritt beschränken; Speichern überspringen, wenn nur Erkennung nötig ist. |

## Erwartete Ergebnisse & Verifikation

1. **Konsolenausgabe** – Es sollte mindestens eine Zeile „Font substitution warning“ pro fehlender Schriftart erscheinen.  
2. **CSV‑Report** – Nach Abschluss des Stapel‑Skripts `missing-fonts-report.csv` öffnen und prüfen, dass jede Zeile den Dokumentnamen und die genaue fehlende Schriftart enthält.  
3. **Gespeichertes Dokument** – Das ausgegebene DOCX verwendet die Ersatzschriftarten, das Layout kann jedoch vom Original abweichen.

Falls einer dieser Schritte nicht wie beschrieben funktioniert, prüfen Sie, ob das Aspose.Words‑JAR im Klassenpfad liegt und ob `input.docx` wirklich eine Schriftart referenziert, die auf Ihrem OS nicht vorhanden ist.

## Fazit

Sie haben gerade ein **aspose warning callback tutorial** abgeschlossen, das zeigt, wie man **fehlende Schriftarten** erkennt und **fehlende Schriftarten** in Java‑Anwendungen **verfolgt**. Durch das Registrieren eines Warn‑Listeners, das Laden des Dokuments und optionales Exportieren der Ergebnisse erhalten Sie volle Transparenz über Schrift‑Probleme, bevor sie in der Produktion auftauchen.

Als nächstes könnten Sie:

- Die fehlende Schriftart direkt mit `LoadOptions.setFontSubstitution` einbetten.
- Die Klasse `FontSettings` verwenden, um fehlende Schriftarten bestimmten Ersatzschriften zuzuordnen.
- Den CSV‑Report in eine CI/CD‑Pipeline integrieren, um Builds bei undocumented fonts fehlschlagen zu lassen.

Probieren Sie es aus, passen Sie die Callbacks an Ihr Logging‑Framework an und machen Sie Ihren Dokumenten‑Workflow deutlich robuster. Viel Spaß beim Coden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}