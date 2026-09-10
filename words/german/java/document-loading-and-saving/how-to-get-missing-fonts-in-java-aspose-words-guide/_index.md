---
category: general
date: 2026-02-15
description: Erfahren Sie, wie Sie fehlende Schriftarten beim Laden eines Word‑Dokuments
  in Java mit Aspose.Words ermitteln. Enthält Warn‑Callbacks und die Handhabung von
  Schriftart‑Substitutionen.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: de
og_description: Wie man fehlende Schriftarten in Java mit Aspose.Words erhält. Entdecken
  Sie Warnungs‑Callbacks, die Handhabung von Schriftart‑Substitutionen und bewährte
  Methoden für die Dokumentenverarbeitung.
og_title: Wie man fehlende Schriftarten in Java erhält – Aspose.Words Leitfaden
tags:
- Aspose.Words
- Java
- Font Management
title: Wie man fehlende Schriftarten in Java abruft – Aspose.Words-Leitfaden
url: /de/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man fehlende Schriftarten in Java – Aspose.Words‑Leitfaden

Haben Sie jemals ein Word‑Dokument in Java geöffnet und nur seltsame Schriftart‑Ersetzungen gesehen und sich gefragt, **wie man fehlende Schriftarten erhält**? Sie sind nicht der Erste, der diese Überraschung erlebt. In vielen Unternehmens‑Apps können Warnungen über fehlende Schriftarten die visuelle Treue von Berichten, Verträgen oder Marketing‑Materialien zerstören.

Die gute Nachricht? Aspose.Words bietet Ihnen eine saubere Möglichkeit, diese Warnungen über einen Callback abzufangen, sodass Sie sie protokollieren, ersetzen oder sogar Benutzer benachrichtigen können, bevor das Dokument gerendert wird. In diesem Tutorial führen wir Sie durch ein komplettes, ausführbares Beispiel, das **zeigt, wie man fehlende Schriftarten erhält**, erklärt, warum der Callback wichtig ist, und einige Randfall‑Tricks behandelt, die Sie in realen Projekten benötigen könnten.

> **Pro‑Tipp:** Wenn Sie bereits Aspose.Words 22.12 oder neuer verwenden, funktioniert die unten gezeigte API sofort ohne zusätzliche Konfiguration.

---

![Diagramm, das zeigt, wie man fehlende Schriftarten mit dem Aspose.Words‑Warn‑Callback erhält](how-to-get-missing-fonts-diagram.png "Diagramm, wie man fehlende Schriftarten erhält")

## Was dieses Tutorial abdeckt

- Einrichtung eines **Java LoadOptions warning callback**, um Schriftart‑Ersetzungs‑Warnungen abzufangen.  
- Filtern der Warnungen, sodass Sie nur diejenigen sehen, die sich auf fehlende Schriftarten beziehen.  
- Ausgabe eines klaren, menschenlesbaren Berichts darüber, welche Schriftarten ersetzt wurden und durch was sie ersetzt wurden.  
- Tipps zum Umgang mit großen Dokumenten, zur Anpassung der Warnstufe und zur Integration der Lösung in eine größere Verarbeitungspipeline.

Am Ende dieses Leitfadens können Sie die Frage “**wie man fehlende Schriftarten erhält**?” mit einem sofort einsatzbereiten Code‑Snippet und einem soliden Verständnis der zugrunde liegenden Mechanik beantworten.

### Voraussetzungen

- Java 8 oder neuer installiert.  
- Aspose.Words for Java‑Bibliothek (Download von der offiziellen Website oder Hinzufügen via Maven/Gradle).  
- Ein Word‑Dokument, das eine Schriftart referenziert, die nicht auf Ihrem Rechner installiert ist (z. B. `MissingFont.docx`).  

Wenn Ihnen etwas davon fehlt, holen Sie sich die Bibliothek jetzt – das Hinzufügen zu Maven ist so einfach wie:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Schritt 1: Eine Sammlung für Schriftart‑Ersetzungs‑Warnungen vorbereiten

Bevor das Dokument geladen wird, benötigen wir einen Ort, um alle Warnungen zu speichern, die Aspose.Words ausgibt. Eine `ArrayList<WarningInfo>` funktioniert gut, weil sie die Reihenfolge beibehält und späteres Durchlaufen ermöglicht.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Warum das wichtig ist:* Der Warn‑Callback kann für eine einzelne Datei Dutzende Male ausgelöst werden – denken Sie an jedes fehlende Glyph, jedes Problem mit eingebetteten Bildern usw. Durch das vorherige Sammeln bleiben die Ladevorgänge schnell, und die Verarbeitung kann in einer kontrollierten Schleife erfolgen.

---

## Schritt 2: LoadOptions mit einem Warn‑Callback konfigurieren

Aspose.Words lässt Sie ein `IWarningCallback` einbinden. Innerhalb des Callbacks fügen wir jedes `WarningInfo` zu unserer Liste aus Schritt 1 hinzu.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Erklärung:* Die Methode `warning` wird **synchron** während des Dokumenten‑Ladevorgangs aufgerufen. Indem wir das `WarningInfo` einfach in `fontWarnings` schieben, vermeiden wir schwere I/O‑Operationen (wie das Schreiben in eine Datei), die das Laden verlangsamen könnten. Dieses Muster – sammeln‑und‑dann‑verarbeiten – ist der empfohlene Weg, um große Mengen an Warnungen zu handhaben.

---

## Schritt 3: Das Dokument mit den konfigurierten Optionen laden

Jetzt lesen wir tatsächlich die Word‑Datei. Enthält das Dokument Schriftarten, die nicht installiert sind, ersetzt Aspose.Words sie automatisch und löst den zuvor konfigurierten Warn‑Callback aus.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*Was im Hintergrund passiert:* Aspose.Words analysiert die Schriftart‑Tabelle der Datei, vergleicht sie mit den auf dem Host‑OS verfügbaren Schriftarten und erstellt für jeden fehlenden Eintrag ein `WarningInfo` mit `WarningSource.FontSubstitution`. Diese Quelle ist der Schlüssel, den wir nutzen, um die fehlenden‑Schriftart‑Warnungen zu isolieren.

---

## Schritt 4: Nur Schriftart‑Ersetzungs‑Warnungen filtern und anzeigen

Nach dem Laden kann `fontWarnings` eine Mischung aus Meldungen enthalten (z. B. veraltete Features, Bildprobleme). Wir interessieren uns nur für fehlende Schriftarten, also durchlaufen wir die Liste und geben einen knappen Bericht aus.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Beispielausgabe**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Warum das nützlich ist:* Das Feld `description` sagt Ihnen, welche Schriftart das Dokument angefordert hat, während `additionalInfo` angibt, welche Schriftart Aspose.Words tatsächlich verwendet hat. Mit diesen Daten können Sie:

- Den Benutzer auffordern, die fehlende Schriftart zu installieren.  
- Programmgesteuert eine Ersatzschriftart in das Dokument einbetten (`doc.getFontInfos().add(...)`).  
- Das Ereignis für Compliance‑Audits protokollieren.

---

## Umgang mit Randfällen und gängigen Variationen

### 1. Unterdrücken von Nicht‑Schriftart‑Warnungen

Wenn Sie nur schriftartspezifische Meldungen wollen, können Sie den Callback straffen:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

Damit wird der Speicherverbrauch bei der Verarbeitung riesiger Stapel reduziert.

### 2. Anpassen der Warn‑Schwere

Aspose.Words kategorisiert Warnungen nach `WarningType`. Für fehlende Schriftarten sehen Sie typischerweise `WarningType.FontSubstitution`. Wenn Sie sie als Fehler behandeln müssen (z. B. das Laden abbrechen), werfen Sie innerhalb des Callbacks eine Ausnahme:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Arbeiten mit Streams anstelle von Dateien

Manchmal kommen Dokumente aus einer Datenbank oder einer HTTP‑Anfrage. Der gleiche Ansatz funktioniert mit einem `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Denken Sie nur daran, den Stream nach dem Laden zu schließen.

### 4. Verwendung eines benutzerdefinierten Schriftarten‑Ordners

Wenn Sie eine Sammlung von Unternehmens‑Schriftarten auf einem gemeinsamen Laufwerk gespeichert haben, verweisen Sie Aspose.Words auf diesen Ordner:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Die Bibliothek sucht nun dort *bevor* sie auf System‑Schriftarten zurückgreift, wodurch die Anzahl der fehlenden‑Schriftart‑Warnungen drastisch reduziert wird.

---

## Vollständiges funktionierendes Beispiel

Wenn wir alles zusammenführen, erhalten Sie eine eigenständige Klasse, die Sie in jedes Java‑Projekt einbinden können:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Führen Sie dieses Programm aus, und Sie erhalten eine übersichtliche Liste aller Schriftarten, die Aspose.Words ersetzen musste. Keine zusätzlichen Bibliotheken, keine versteckte Magie – nur reines Java und die Kraft der **Aspose.Words missing font**‑API.

---

## Fazit

Wir haben die Kernfrage **wie man fehlende Schriftarten erhält** in einer Java‑Umgebung mit Aspose.Words beantwortet. Durch das Anbinden eines `LoadOptions`‑Warn‑Callbacks, das Sammeln von `WarningInfo`‑Objekten und das Filtern nach `FontSubstitution`‑Quellen erhalten Sie vollständige Sichtbarkeit auf schriftartspezifische Probleme, bevor irgendeine Darstellung erfolgt. Der Ansatz skaliert von Einzeldatei‑Hilfsprogrammen bis hin zu massiven Batch‑Prozessoren und ist flexibel genug, um benutzerdefinierte Schriftarten‑Ordner, Schwere‑Behandlung oder stream‑basierte Eingaben zu unterstützen.

Nächste Schritte? Versuchen Sie, die ersetzten Schriftarten direkt in das Dokument einzubetten (`doc.getFontInfos().add(...)`), sodass die endgültige Datei wirklich eigenständig ist, oder integrieren Sie den Warn‑Bericht in ein Monitoring‑Dashboard. Sie können auch verwandte Themen wie **document processing Java**, **Aspose.Words font substitution warning** und **Java LoadOptions warning callback** erkunden, um Ihr Fachwissen zu vertiefen.

Viel Spaß beim Coden, und möge Ihr Dokument stets mit den erwarteten Schriftarten gerendert werden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}