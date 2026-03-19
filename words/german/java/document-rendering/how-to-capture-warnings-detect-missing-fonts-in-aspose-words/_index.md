---
category: general
date: 2026-03-19
description: Erfahren Sie, wie Sie Warnungen in Aspose.Words für Java erfassen und
  fehlende Schriftarten erkennen. Diese Schritt‑für‑Schritt‑Anleitung zeigt außerdem,
  wie Sie fehlende Schriftarten elegant handhaben.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: de
og_description: Wie man Warnungen in Aspose.Words für Java erfasst, fehlende Schriftarten
  erkennt und fehlende Schriftarten mit einem vollständigen Codebeispiel behandelt.
og_title: Wie man Warnungen erfasst – Fehlende Schriftarten in Aspose.Words erkennen
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Wie man Warnungen erfasst – Fehlende Schriftarten in Aspose.Words erkennen
url: /de/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Warnungen erfasst – Fehlende Schriftarten in Aspose.Words erkennen

Haben Sie sich jemals gefragt, **wie man Warnungen erfasst**, wenn ein Word‑Dokument geladen wird und einige Schriftarten auf dem Rechner nicht verfügbar sind? Sie sind nicht allein. In vielen realen Projekten führen fehlende Schriftarten zu stillen Layout‑Verschiebungen, und der einzige Weg, zu erfahren, was passiert ist, besteht darin, den Warnungs‑Stream zu beobachten, den Aspose.Words ausgibt.  

In diesem Tutorial führen wir Sie durch ein vollständiges, sofort ausführbares Beispiel, das **fehlende Schriftarten erkennt**, Ihnen **zeigt, wie man fehlende Schriftarten** programmgesteuert erkennt, und sogar einen kurzen Hinweis zur **Behandlung fehlender Schriftarten** gibt, damit Ihre Ausgabe vorhersehbar bleibt.

> **Kurzer Hinweis:** Der Code funktioniert mit Aspose.Words 23.9 (oder neuer) und erfordert Java 8+.

---

## Was Sie benötigen

- **Aspose.Words for Java** (Maven/Gradle‑Abhängigkeit oder JAR im Klassenpfad)  
- Eine Word‑Datei (`input.docx`), die eine Schriftart referenziert, die nicht auf Ihrem System installiert ist (z. B. „Comic Sans MS“)  
- Eine Java‑IDE oder ein einfacher `javac`/`java`‑Kommandozeilen‑Setup  

Keine weiteren Bibliotheken sind erforderlich – alles andere befindet sich im Aspose.Words‑Paket.

---

## Schritt 1 – LoadOptions einrichten, um Warnungen zu erfassen  

Um mit dem Lauschen von Warnungen zu beginnen, müssen Sie eine `LoadOptions`‑Instanz erstellen. Dieses Objekt weist den Loader an, alle auftretenden Probleme, wie fehlende Schriftarten, zu protokollieren.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Warum das wichtig ist:** Ohne `LoadOptions` ersetzt der Loader fehlende Schriftarten stillschweigend durch die Standardsystemschriftart, und Sie würden nie erfahren, dass eine Substitution stattgefunden hat. Das Aktivieren von Warnungen verschafft Ihnen vollständige Transparenz.

---

## Schritt 2 – Das Dokument mit den LoadOptions laden  

Jetzt laden wir das Dokument tatsächlich. Die zuvor erstellten `LoadOptions` werden dem Konstruktor übergeben, sodass alle während des Parsens erzeugten Warnungen erfasst werden.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Pro‑Tipp:** Wenn Sie viele Dateien stapelweise verarbeiten, verwenden Sie dieselbe `LoadOptions`‑Instanz erneut, um unnötige Objekt­erzeugungen zu vermeiden.

---

## Schritt 3 – Über die erfassten Warnungen iterieren  

Aspose.Words speichert jede Warnung als ein `WarningInfo`‑Objekt. Wir interessieren uns nur für schriftbezogene Warnungen, daher filtern wir nach `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Erklärung:**  
- `document.getWarnings()` gibt eine Liste aller Warnungen zurück, die beim Laden aufgetreten sind.  
- `FontSubstitutionWarningInfo` enthält zwei entscheidende Daten: die **angeforderte Schriftart** (die, die das DOCX verlangt) und die **tatsächliche Schriftart**, auf die Aspose.Words ausgewichen ist.  
- Durch das Ausgeben beider Werte sehen Sie sofort, welche Schriftarten fehlen und welche Substitution stattgefunden hat.

---

## Schritt 4 – (Optional) Fehlende Schriftarten programmgesteuert behandeln  

Warnungen zu erfassen ist nur die halbe Geschichte. Sobald Sie wissen, dass eine Schriftart fehlt, möchten Sie möglicherweise **fehlende Schriftarten behandeln**, indem Sie eine benutzerdefinierte Substitution bereitstellen oder das Problem für eine spätere Überprüfung protokollieren.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Warum das tun?**  
- Garantiert ein konsistentes Rendering auf verschiedenen Rechnern.  
- Verhindert unerwartete Layout‑Änderungen in später erzeugten PDFs oder Bildern.  

Sie können die Warnungsdetails auch in einer Datenbank speichern, eine E‑Mail an das Content‑Team senden oder den Prozess sogar abbrechen, wenn eine kritische Schriftart fehlt.

---

## Vollständiges funktionierendes Beispiel  

Unten finden Sie das komplette, ausführbare Programm. Ersetzen Sie einfach `YOUR_DIRECTORY/input.docx` durch den Pfad zu Ihrer Testdatei, fügen Sie das Aspose.Words‑JAR zu Ihrem Klassenpfad hinzu und führen Sie das Programm aus.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Erwartete Ausgabe** (wenn „Comic Sans MS“ fehlt):

```
Requested: Comic Sans MS → Substituted: Arial
```

Nachdem der optionale Fallback‑Code ausgeführt wurde, rendert das gespeicherte `output.docx` überall dort, wo ursprünglich „Comic Sans MS“ referenziert wurde, mit **Arial**.

---

## Häufige Fragen & Sonderfälle  

| Frage | Antwort |
|----------|--------|
| *Was ist, wenn das Dokument mehrere fehlende Schriftarten hat?* | Die Schleife gibt für jede fehlende Schriftart eine Warnung aus. Sie können sie in einer `Map<String, String>` für die Stapelverarbeitung sammeln. |
| *Funktioniert das für PDFs, die aus dem Dokument erzeugt werden?* | Absolut. Die Schriftart‑Substitution erfolgt während der Ladephase, sodass jeder spätere Export (PDF, HTML, Bild) die aufgelösten Schriftarten verwendet. |
| *Kann ich die Warnungen unterdrücken, anstatt sie zu erfassen?* | Ja – setzen Sie `loadOptions.setWarningCallback(null);`, aber Sie verlieren die Sichtbarkeit auf fehlende Schriftarten. |
| *Wird die Warnungsliste nach dem Speichern geleert?* | Die Warnungssammlung gehört zur `Document`‑Instanz. Nach dem Aufruf von `document.save()` bleibt die Liste unverändert, es sei denn, Sie erstellen ein neues `Document`. |
| *Wie ist es mit benutzerdefinierten, im DOCX eingebetteten Schriftarten?* | Eingebettete Schriftarten werden als verfügbar behandelt; Aspose.Words verwendet sie, selbst wenn sie nicht auf dem Host‑System installiert sind. |

---

## Pro‑Tipps für den Produktionseinsatz  

- **FontSettings zwischenspeichern:** Wenn Sie Hunderte von Dateien verarbeiten, erstellen Sie ein einzelnes `FontSettings` mit Ihren bevorzugten Fallbacks und verwenden Sie es erneut, um Overhead zu vermeiden.  
- **Strukturierte Daten protokollieren:** Anstatt einfaches `System.out` zu verwenden, schreiben Sie Warnungen in ein JSON‑Log – das macht nachgelagerte Analysen (z. B. „häufigste fehlende Schriftarten“) trivial.  
- **Frühzeitig validieren:** Führen Sie ein schnelles „Trocken‑Laden“ mit `LoadOptions` vor der intensiven Verarbeitung durch; brechen Sie früh ab, wenn kritische Schriftarten fehlen.  
- **Thread‑Sicherheit:** `Document`‑Objekte sind nicht thread‑sicher. Verarbeiten Sie jede Datei in einem eigenen Thread oder verwenden Sie ein thread‑lokales `LoadOptions`.  

---

## Fazit  

Sie wissen jetzt, **wie man Warnungen** in Aspose.Words für Java erfasst, **fehlende Schriftarten erkennt** und **fehlende Schriftarten** mit einer sauberen Fallback‑Strategie behandelt. Durch die Nutzung von `LoadOptions` und das Iterieren über `document.getWarnings()` erhalten Sie vollständige Einblicke in Schriftart‑Substitutionsereignisse, sodass Ihre erzeugten Dokumente in allen Umgebungen exakt wie beabsichtigt aussehen.

Bereit für den nächsten Schritt? Versuchen Sie, dieses Muster zu erweitern, um **fehlende Bilder zu erkennen**, **nicht unterstützte Features zu verfolgen** oder sogar **fehlende Schriftarten automatisch in die Ausgabedatei einzubetten**. Der gleiche Ansatz zur Warnungserfassung funktioniert für viele andere Dokumenten‑Verarbeitungsszenarien und macht Ihren Code robust und zukunftssicher.

Viel Spaß beim Programmieren, und möge Ihre Dokumente stets schön rendern!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}