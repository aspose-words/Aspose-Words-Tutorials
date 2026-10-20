---
category: general
date: 2026-07-06
description: Erstellen Sie DocumentConfig in Java, um fehlende Schriftarten mit Aspose.Words
  zu verfolgen – ein vollständiger, Schritt‑für‑Schritt‑Leitfaden für Entwickler.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: de
og_description: Erstellen Sie DocumentConfig in Java, um fehlende Schriftarten mit
  Aspose.Words zu verfolgen. Lernen Sie den gesamten Workflow kennen, von der Einrichtung
  bis zur Behandlung von Warnungen.
og_title: DocumentConfig in Java erstellen – Fehlende Schriftarten nachverfolgen
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: DocumentConfig in Java erstellen – Fehlende Schriftarten mit Aspose.Words verfolgen
url: /de/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DocumentConfig in Java erstellen – Fehlende Schriftarten mit Aspose.Words verfolgen

**DocumentConfig in Java erstellen**, um Font‑Substitutionswarnungen beim Laden eines Word‑Dokuments zu überwachen. Haben Sie sich jemals gefragt, warum einige Zeichen nach dem Öffnen einer DOCX seltsam aussehen? Wahrscheinlich ist die Originalschriftart nicht auf dem Rechner installiert, und Aspose.Words ersetzt sie stillschweigend. In diesem Tutorial zeigen wir Ihnen genau, wie Sie **fehlende Schriftarten verfolgen** können, damit Sie nie wieder von einem fehlenden Glyph überrascht werden.

Wir gehen alles durch, was Sie benötigen: die Maven/Gradle‑Einrichtung, den Code, der ein `DocumentConfig` erstellt, ein benutzerdefiniertes `IWarningCallback`, das nur Font‑Substitutionswarnungen filtert, und eine schnelle Möglichkeit, diese Meldungen zu protokollieren. Am Ende haben Sie ein ausführbares Beispiel, das jede fehlende‑Schriftart‑Warnung in die Konsole ausgibt (oder in eine Datei, falls Sie das bevorzugen).

---

## Was Sie lernen werden

- Warum ein `DocumentConfig` der richtige Ort ist, um Font‑Substitutionsereignisse abzufangen.  
- Wie Sie **fehlende Schriftarten verfolgen** können, ohne Ihre Protokolle mit irrelevanten Warnungen zu verschmutzen.  
- Ein vollständiges, sofort einsetzbares Java‑Programm, das die Technik demonstriert.  
- Tipps zur Erweiterung der Lösung – z. B. das Schreiben von Warnungen in eine Datenbank oder das Senden von E‑Mail‑Benachrichtigungen.

### Voraussetzungen

| Anforderung | Grund |
|-------------|-------|
| Java 8 oder neuer | Aspose.Words für Java unterstützt JDK 8+. |
| Aspose.Words für Java Bibliothek (neueste Version) | Stellt `DocumentConfig`, `IWarningCallback` usw. bereit. |
| Eine IDE oder ein Build‑Tool (IntelliJ, Eclipse, Maven/Gradle) | Zum Kompilieren und Ausführen des Beispiels. |
| Eine DOCX‑Datei, die Schriftarten referenziert, die nicht installiert sind | Um die Warnung in Aktion zu sehen. |

Wenn Sie bereits ein Projekt haben, fügen Sie einfach die Aspose‑Abhängigkeit hinzu und Sie können loslegen.

---

## Schritt 1: Aspose.Words zu Ihrem Build hinzufügen

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **Pro‑Tipp:** Die kostenlose Testversion funktioniert einwandfrei für Tests, aber denken Sie daran, in der Produktion eine Lizenz zu aktivieren, um das Evaluations‑Wasserzeichen zu entfernen.

---

## Schritt 2: DocumentConfig erstellen und einen Warning‑Callback registrieren

Der Kern der Lösung befindet sich in diesem Snippet. Wir **erstellen ein DocumentConfig**, hängen ein benutzerdefiniertes `IWarningCallback` an und weisen es an, nur **fehlende Schriftarten zu verfolgen**.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**Warum das funktioniert:** Wenn Aspose.Words ein Dokument analysiert, erzeugt es `WarningInfo`‑Objekte für alle Unregelmäßigkeiten. Durch das Bereitstellen eines Callbacks fangen Sie diese Warnungen *bevor* sie ins Leere verschwinden ab. Die `if`‑Prüfung stellt sicher, dass wir nur **fehlende Schriftarten verfolgen**, während andere Warnungen wie veraltete Tags oder nicht unterstützte Features ignoriert werden.

---

## Schritt 3: Beispiel ausführen und die Ausgabe beobachten

Legen Sie eine DOCX‑Datei ab, die eine Schriftart referenziert, die Sie nicht haben (z. B. „Comic Sans MS“ auf einem Linux‑System). Führen Sie das Programm aus:

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

Sie sollten etwas Ähnliches sehen wie:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Jede Zeile entspricht einer fehlenden Schriftart, die Aspose automatisch ersetzt hat. Wenn keine fehlenden Schriftarten vorhanden sind, bleibt das Programm still – genau das, was Sie für ein sauberes Protokoll wollen.

---

## Schritt 4: Fehlende‑Schriftarten‑Liste speichern (optional)

Das Ausgeben in die Konsole ist praktisch für Demos, aber in einem realen Service würden Sie die Daten wahrscheinlich speichern. Hier ist ein schneller Weg, die Warnungen in eine Textdatei zu schreiben.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

Jetzt fügt jedes fehlende‑Schriftart‑Ereignis eine Zeile zu `missing-fonts.log` hinzu. Sie können die Datei später auswerten, in ein Monitoring‑Dashboard einspeisen oder sogar einen Alarm auslösen, wenn eine kritische Schriftart von Ihrem Server verschwindet.

---

## Schritt 5: Häufige Fallstricke und wie man sie vermeidet

| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|------------------------|--------|
| Keine Warnungen erscheinen, obwohl das DOCX unbekannte Schriftarten verwendet | Callback nicht registriert oder `setWarningCallback` nach dem Laden des Dokuments aufgerufen | Stellen Sie sicher, dass `config.setWarningCallback(...)` **vor** der Erstellung der `Document`‑Instanz ausgeführt wird. |
| Anwendung stürzt mit `NullPointerException` ab | `info.getDescription()` gibt für einige seltene Warnungstypen `null` zurück | Schützen Sie sich vor null: `String desc = info.getDescription(); if (desc != null) …` |
| Zu viele irrelevante Warnungen fluten die Konsole | Callback filtert nur `FONT_SUBSTITUTION`? | Überprüfen Sie die Bedingung `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)` erneut. |
| Leistungsverlust bei großen Stapeln | Schreiben in die Datei synchron für jede Warnung | Stapelweise schreiben oder einen `BufferedWriter` verwenden, um den I/O‑Overhead zu reduzieren. |

---

## Schritt 6: Lösung erweitern – von der Konsole zur Enterprise‑Umgebung

- **Datenbank‑Logging:** Ersetzen Sie den `FileWriter` durch einen JDBC‑Insert; speichern Sie `documentName`, `missingFont` und `timestamp`.  
- **E‑Mail‑Benachrichtigungen:** An JavaMail anbinden; nach der Verarbeitung eines Stapels von Dokumenten eine Zusammenfassung senden.  
- **Benutzerdefinierte Substitutionslogik:** Anstatt Aspose eine Ersatzschriftart wählen zu lassen, können Sie eine lokale Schriftartsammlung über `FontSettings.setFontsFolder()` laden und das Laden erneut ausführen, wenn eine Substitution auftritt.

Diese Erweiterungen erhalten die Kernidee – **DocumentConfig erstellen** und **fehlende Schriftarten verfolgen** – unverändert, während sie auf Produktionsanforderungen skalieren.

---

## Fazit

Sie haben nun ein solides, sofort einsetzbares Muster für **das Erstellen eines DocumentConfig** in Java und dessen Nutzung zum **Verfolgen fehlender Schriftarten** mit Aspose.Words. Der Ansatz ist leichtgewichtig, erfordert nur wenige Code‑Zeilen und gibt Ihnen die volle Kontrolle darüber, wie Font‑Substitutionswarnungen behandelt werden. Egal, ob Sie einen Dokument‑Konvertierungsservice, einen automatisierten Berichtsgenerator oder ein Compliance‑Audit‑Tool bauen – das genaue Wissen, welche Schriftarten fehlen, kann Stunden an Fehlersuche sparen.

Nächste Schritte? Versuchen Sie, die Konsolenausgabe durch ein strukturiertes JSON‑Log zu ersetzen, oder integrieren Sie den Callback in einen Spring Boot‑Microservice, der Uploads in Echtzeit verarbeitet. Und wenn Sie auf Sonderfälle stoßen – etwa eine benutzerdefinierte OpenType‑Schrift, die Aspose nicht parsen kann – hinterlassen Sie unten einen Kommentar; wir lösen das gemeinsam.

Viel Spaß beim Coden, und mögen Ihre PDFs stets mit den erwarteten Schriftarten rendern!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Schriftarten in Aspose.Words für Java verwenden](/words/english/java/using-document-elements/using-fonts/)
- [Themenfarben & Schriftarten in Aspose.Words Java anpassen: Ein umfassender Leitfaden](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Wie man PDF‑Dokumente mit Aspose.Words für Java erstellt | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}