---
category: general
date: 2026-02-18
description: Erstellen Sie Ladeoptionen in Java, um fehlende Schriftarten zu erkennen,
  und erfahren Sie, wie Sie DOCX‑Dateien mit einem Warnungs‑Callback laden.
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: de
og_description: Erstellen Sie Ladeoptionen in Java, um fehlende Schriftarten zu erkennen,
  und lernen Sie, wie Sie DOCX‑Dateien mit einem Warnungs‑Callback laden.
og_title: Erstellen von Ladeoptionen in Java – Fehlende Schriftarten erkennen und
  DOCX laden
tags:
- java
- aspose-words
- document-processing
title: Ladeoptionen in Java erstellen – Fehlende Schriftarten erkennen & DOCX laden
url: /de/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

agram.png){: .center-image alt="Flussdiagramm zum Erstellen von Ladeoptionen"}

But need to keep the attribute syntax exactly. We'll translate the alt attribute.

Now translate bullet lists.

Let's produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Load‑Optionen in Java erstellen – Fehlende Schriften erkennen & DOCX laden

Haben Sie sich schon einmal gefragt, wie man **Lade‑Optionen** erstellt, die nicht nur ein DOCX einlesen, sondern auch melden, wenn eine Schrift fehlt? Sie sind nicht allein. Fehlende Schriften können ein perfekt formatiertes Dokument in ein wirres Durcheinander verwandeln, und sie frühzeitig zu erkennen spart Stunden an Fehlersuche. In diesem Tutorial gehen wir Schritt für Schritt durch, wie man **fehlende Schriften erkennt** und gleichzeitig **DOCX**‑Dateien mit einem benutzerdefinierten Warn‑Callback lädt.

## Was Sie lernen werden

- Wie man `LoadOptions` instanziiert und einen Warn‑Handler konfiguriert.  
- Warum der Warn‑Callback entscheidend ist, um Probleme mit Schrift‑Substitution zu erfassen.  
- Der exakte Code, der ein **DOCX**‑Datei sicher lädt, plus ein paar praktische Tipps für reale Projekte.  
- Umgang mit Sonderfällen, z. B. anderen Warn‑Typen oder dem Laden von PDFs mit demselben Ansatz.

Keine externe Dokumentation nötig – alles, was Sie brauchen, finden Sie hier.

## Voraussetzungen

- Java 17 oder höher (die API funktioniert auch mit älteren Versionen, aber 17 ist optimal).  
- Aspose.Words for Java‑Bibliothek in Ihrem Projekt (`aspose-words-x.x.jar`).  
- Grundlegendes Verständnis von Java‑Exception‑Handling.  

Wenn Sie das haben, legen wir los.

![Diagramm, das den Ablauf des Erstellens von Ladeoptionen, dem Setzen eines Warn‑Callbacks und dem Laden einer DOCX‑Datei zeigt](/images/create-load-options-diagram.png){: .center-image alt="Flussdiagramm zum Erstellen von Ladeoptionen"}

## Schritt 1: Lade‑Optionen erstellen (Wie man DOCX lädt)

Das Erste, was Sie tun müssen, ist **Lade‑Optionen** zu **erstellen**. Dieses Objekt sagt Aspose.Words, wie es sich verhalten soll, wenn es eine Datei öffnet. Denken Sie daran wie an eine Reihe von Anweisungen, die Sie der Bibliothek geben, bevor sie überhaupt das DOCX sieht.

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Warum nicht einfach `new Document("file.docx")` aufrufen? Ohne `LoadOptions` verlieren Sie die Möglichkeit, auf Warnungen – wie fehlende Schriften – zu reagieren, bevor das Dokument bereits geladen ist, was für bestimmte Workflows zu spät sein kann.

## Schritt 2: Warn‑Callback einrichten, um fehlende Schriften zu erkennen

Jetzt hängen wir einen Callback an, der immer dann aufgerufen wird, wenn Aspose.Words eine Situation entdeckt, über die es Sie warnen möchte. In unserem Fall interessieren wir uns für `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // React only to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Missing font detected: " + info.getDescription());
        }
    }
});
```

Ein paar Hinweise:

- **Warum ein Callback?** Er läuft *während* des Ladevorgangs und gibt Ihnen die Chance, zu protokollieren oder sogar den Vorgang abzubrechen, bevor das Dokument vollständig materialisiert ist.  
- **Warum `WarningType.FONT_SUBSTITUTION` prüfen?** Das ist der genaue Enum‑Wert, den Aspose.Words für fehlende Schriften verwendet. Andere Warn‑Typen (z. B. `TABLE_STRUCTURE`) können analog gefiltert werden, falls Sie sie benötigen.  
- **Performance‑Tipp:** Der Callback ist leichtgewichtig; vermeiden Sie schwere I/O‑Operationen darin. Wenn Sie in eine Datei schreiben müssen, sammeln Sie die Nachrichten in einer Queue und schreiben Sie sie nach dem Laden.

## Schritt 3: DOCX‑Datei mit den konfigurierten Optionen laden

Mit den Optionen und dem Callback bereit, können Sie endlich das DOCX laden. Das ist der Teil, der beantwortet, **wie man DOCX lädt**, während die gesetzten Warnungen beachtet werden.

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**Was passiert im Hintergrund?** Während die Datei gestreamt wird, prüft Aspose.Words jede Schriftreferenz. Wenn eine referenzierte Schrift nicht installiert ist, wird der zuvor definierte Warn‑Callback ausgelöst. Sie erhalten eine Ausgabe wie:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

Dieses sofortige Feedback ist unbezahlbar, wenn Sie Stapel von Dateien auf einem Server verarbeiten.

## Vollständiges Beispiel

Alles zusammengefügt, hier ein eigenständiges Programm, das Sie in Ihre IDE kopieren können.

```java
import com.aspose.words.*;

public class DetectMissingFonts {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register warning callback to detect missing fonts
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Missing font: " + info.getDescription());
                }
            }
        });

        // 3️⃣ Load the DOCX using the configured options
        try {
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            System.out.println("DOCX loaded – you can now work with it.");
        } catch (Exception ex) {
            System.err.println("Error loading DOCX: " + ex.getMessage());
        }
    }
}
```

**Erwartete Ausgabe**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

Enthält die Datei keine fehlenden Schriften, bleibt der Callback still und die Zeile „DOCX loaded“ erscheint.

## Profi‑Tipps & Sonderfälle

| Situation | Was zu tun ist |
|-----------|----------------|
| **Mehrere fehlende Schriften** | Der Callback wird für jede ausgelöst, Sie erhalten also eine Zeile pro Schrift. Aggregieren Sie sie in einer `List<String>`, wenn Sie später eine Zusammenfassung benötigen. |
| **Weitere Warnungen abfangen** | Fügen Sie `else if`‑Zweige für `WarningType.TABLE_STRUCTURE`, `WarningType.UNKNOWN_FILE_FORMAT` usw. hinzu. |
| **Große DOCX‑Dateien laden** | Verwenden Sie `LoadOptions.setLoadFormat(LoadFormat.DOCX)`, um das Format zu hintieren und die Erkennung zu beschleunigen. |
| **In einem Web‑Service laufen** | Vermeiden Sie `System.out.println`; injizieren Sie stattdessen einen Logger (`SLF4J`, `Log4j`) im Callback. |
| **Schriften zur Laufzeit installieren** | Nach dem Erkennen einer fehlenden Schrift können Sie sie programmgesteuert via `GraphicsEnvironment.registerFont(...)` laden und das Dokument erneut öffnen. |

## Warum dieser Ansatz die reine „Try‑Catch“-Methode übertrifft

Viele Entwickler wickeln `new Document(...)` einfach in ein try‑catch‑Block, in der Hoffnung, dass eine Ausnahme über fehlende Schriften informiert. Leider behandelt Aspose.Words Schrift‑Substitution als *Warnung*, nicht als Fehler, sodass keine Ausnahme geworfen wird. Durch **Erstellen von Lade‑Optionen** und Anbinden eines Warn‑Callbacks erhalten Sie deterministische Einblicke in Schrift‑Probleme, ohne die Performance zu opfern.

## Nächste Schritte

- **Fehlende Schriften in PDFs erkennen** – das gleiche `LoadOptions`‑Muster funktioniert für PDFs, nur Pfad und Ladeformat anpassen.  
- **Automatisierte Schrift‑Installation** – kombinieren Sie den Callback mit einem Skript, das fehlende Schriften aus einem gemeinsamen Repository holt.  
- **Weitere Warn‑Typen erkunden** – Aspose.Words kann Sie über veraltete Tags, komplexe Tabellen und mehr informieren.  

Probieren Sie es aus: Ersetzen Sie den `Document`‑Konstruktor durch einen Stream (`new Document(InputStream, loadOptions)`), wenn Sie mit In‑Memory‑Daten arbeiten, oder verketten Sie mehrere Callbacks mittels Composite‑Pattern für groß angelegte Verarbeitungspipelines.

---

### TL;DR

Wir haben gezeigt, wie man **Lade‑Optionen** in Java **erstellt**, einen Callback einrichtet, der **fehlende Schriften erkennt**, und schließlich **DOCX**‑Dateien sicher **lädt**. Mit nur drei knappen Schritten besitzen Sie nun ein wiederverwendbares Muster, das in jedes Aspose.Words‑Projekt eingefügt werden kann.

Fragen zu anderen Dateiformaten oder Anpassungsbedarf für Ihren speziellen Anwendungsfall? Hinterlassen Sie einen Kommentar unten – happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}