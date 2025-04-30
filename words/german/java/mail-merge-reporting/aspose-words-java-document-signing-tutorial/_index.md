---
"date": "2025-03-28"
"description": "Erfahren Sie, wie Sie die Dokumentsignatur mit Aspose.Words für Java automatisieren. Dieses Tutorial behandelt die Einrichtung Ihrer Umgebung, das Erstellen von Testdaten, das Hinzufügen von Signaturzeilen und das digitale Signieren von Dokumenten."
"title": "Automatisieren Sie die Dokumentsignierung in Java mit Aspose.Words – Ein umfassender Leitfaden"
"url": "/de/java/mail-merge-reporting/aspose-words-java-document-signing-tutorial/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Automatisieren Sie die Dokumentsignierung in Java mit Aspose.Words: Ein umfassender Leitfaden

## Einführung

In der heutigen schnelllebigen Geschäftswelt ist effizientes Dokumentenmanagement unerlässlich. Die Automatisierung der Erstellung und digitalen Signatur von Dokumenten spart Zeit und minimiert Fehler. Dieses Tutorial führt Sie durch die Verwendung von Aspose.Words für Java zum Erstellen von Testdaten für Unterzeichner, Hinzufügen von Signaturzeilen und digitalen Signieren von Dokumenten.

**Was Sie lernen werden:**
- Einrichten von Aspose.Words in einem Java-Projekt
- Erstellen von Testsignerdaten mit Java
- Hinzufügen von Signaturzeilen zu Word-Dokumenten
- Digitales Signieren von Dokumenten mithilfe digitaler Zertifikate

Beginnen wir mit der Vorbereitung Ihrer Entwicklungsumgebung!

## Voraussetzungen

Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass Ihr Setup die folgenden Anforderungen erfüllt:

- **Java Development Kit (JDK):** Version 8 oder höher.
- **Integrierte Entwicklungsumgebung (IDE):** Wie beispielsweise IntelliJ IDEA oder Eclipse.
- **Aspose.Words für Java:** Diese Bibliothek kann über Maven oder Gradle eingebunden werden.

### Voraussetzungen

Grundkenntnisse in Java-Programmierung und Erfahrung im Umgang mit Dateien und Streams sind von Vorteil. Wenn Sie Aspose noch nicht kennen, keine Sorge – wir decken die Grundlagen ab.

## Einrichten von Aspose.Words

Um Aspose.Words für Java in Ihrem Projekt zu verwenden, führen Sie die folgenden Schritte aus:

### Maven-Abhängigkeit

Fügen Sie die folgende Abhängigkeit zu Ihrem `pom.xml` Datei:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle-Abhängigkeit

Für Gradle-Projekte fügen Sie diese Zeile in Ihre `build.gradle` Datei:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Lizenzerwerb

Aspose bietet verschiedene Lizenzierungsoptionen:

- **Kostenlose Testversion:** Laden Sie eine kostenlose Testversion herunter, um die Funktionen zu testen.
- **Temporäre Lizenz:** Erwerben Sie eine temporäre Lizenz zu Evaluierungszwecken.
- **Kaufen:** Erwerben Sie für den vollständigen Zugriff eine Lizenz von der Aspose-Website.

Stellen Sie sicher, dass Ihr Projekt mit den erforderlichen Abhängigkeiten und Lizenzen konfiguriert ist. So können Sie die leistungsstarken Dokumentbearbeitungsfunktionen von Aspose nahtlos nutzen.

## Implementierungshandbuch

Wir gehen jede Funktion Schritt für Schritt durch und beginnen mit der Erstellung von Testunterzeichnerdaten.

### Funktion 1: Testdaten für Unterzeichner erstellen

#### Überblick

Diese Funktion generiert eine Liste von Unterzeichnern mit eindeutigen IDs, Namen, Positionen und Bildern. Dies ist wichtig, um Szenarien zur Dokumentsignatur ohne Verwendung realer Daten zu testen.

##### Schritt 1: Richten Sie Ihre Java-Klasse ein

Erstellen Sie eine Klasse mit dem Namen `SignPersonCreator` und importieren Sie die erforderlichen Bibliotheken:

```java
import java.io.ByteArrayOutputStream;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.UUID;

class DocumentHelper {
    public static byte[] getBytesFromStream(InputStream inputStream) throws IOException {
        int numRead; 
        byte[] buffer = new byte[1024]; 
        ByteArrayOutputStream baos = new ByteArrayOutputStream();

        while ((numRead = inputStream.read(buffer)) != -1) {
            baos.write(buffer, 0, numRead);
        }
        return baos.toByteArray();
    }
}

public class SignPersonCreator {
    private static ArrayList<SignPersonTestClass> gSignPersonList;

    public static void main(String[] args) throws IOException {
        createSignPersonData();
        System.out.println("Test data successfully added!");
    }

    private static void createSignPersonData() throws IOException {
        InputStream inputStream = new FileInputStream(YOUR_DOCUMENT_DIRECTORY + "Logo.jpg");

        gSignPersonList = new ArrayList<>();
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Ron Williams", "Chief Executive Officer",
                DocumentHelper.getBytesFromStream(inputStream)));
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Stephen Morse", "Head of Compliance",
                DocumentHelper.getBytesFromStream(inputStream)));
    }
}
```

##### Erläuterung

- **UUID:** Generiert eine eindeutige Kennung für jeden Unterzeichner.
- **BytesFromStream abrufen:** Konvertiert eine Bilddatei zur Speicherung in ein Byte-Array.

### Funktion 2: Signaturzeile zum Dokument hinzufügen

#### Überblick

Diese Funktion fügt Ihrem Dokument eine Signaturzeile hinzu und verknüpft sie mit den Angaben des Unterzeichners.

##### Schritt 1: Erstellen Sie die SignatureLineAdder-Klasse

Implementieren Sie die `SignatureLineAdder` Klasse wie folgt:

```java
import com.aspose.words.*;

class SignatureLineAdder {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        
        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            addSignatureLine(srcDocumentPath, dstDocumentPath, signPersonInfo);
            System.out.println("Signature line added successfully!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void addSignatureLine(final String srcDocumentPath, final String dstDocumentPath,
                                         final SignPersonTestClass signPersonInfo) throws Exception {
        Document document = new Document(srcDocumentPath);
        DocumentBuilder builder = new DocumentBuilder(document);

        SignatureLineOptions signatureLineOptions = new SignatureLineOptions();
        signatureLineOptions.setSigner(signPersonInfo.getName());
        signatureLineOptions.setSignerTitle(signPersonInfo.getPosition());

        SignatureLine signatureLine = builder.insertSignatureLine(signatureLineOptions).getSignatureLine();
        signatureLine.setId(String.valueOf(signPersonInfo.getPersonId()));

        builder.getDocument().save(dstDocumentPath);
    }
}
```

##### Erläuterung

- **SignatureLineOptions:** Konfiguriert den Namen und Titel des Unterzeichners.
- **Signaturzeile einfügen:** Fügt an der aktuellen Cursorposition eine Signaturzeile in das Dokument ein.

### Funktion 3: Dokument mit digitalem Zertifikat signieren

#### Überblick

Diese Funktion signiert das Dokument digital mit einem digitalen Zertifikat und stellt so Authentizität und Integrität sicher.

##### Schritt 1: DocumentSigner-Klasse erstellen

Implementieren Sie die `DocumentSigner` Klasse:

```java
import com.aspose.words.*;

class DocumentSigner {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        String certificatePath = YOUR_DOCUMENT_DIRECTORY + "morzal.pfx";
        String certificatePassword = "aw";

        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            signDocument(srcDocumentPath, dstDocumentPath, signPersonInfo, certificatePath, certificatePassword);
            System.out.println("Document successfully signed!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void signDocument(final String srcDocumentPath, final String dstDocumentPath,
                                     final SignPersonTestClass signPersonInfo, final String certificatePath,
                                     final String certificatePassword) throws Exception {
        Document document = new Document(dstDocumentPath);

        CertificateHolder certificateHolder = CertificateHolder.create(certificatePath, certificatePassword);

        SignOptions signOptions = new SignOptions();
        signOptions.setSignatureLineId(String.valueOf(
            signPersonInfo.getPersonId()));

        document.sign(signOptions, certificateHolder);
    }
}
```

##### Erläuterung

- **Zertifikatsinhaber:** Stellt das zum Signieren verwendete digitale Zertifikat dar.
- **Zeichen:** Methode, die das Dokument mit den angegebenen Optionen und dem angegebenen Zertifikat signiert.

## Abschluss

In diesem Tutorial haben Sie gelernt, wie Sie die Dokumenterstellung und -signierung in Java mit Aspose.Words automatisieren. Mit diesen Schritten können Sie Ihre Dokumentenverwaltungsprozesse optimieren, die Sicherheit erhöhen und die Datenintegrität gewährleisten. Für weitere Informationen können Sie sich mit den erweiterten Funktionen von Aspose.Words befassen.

**Nächste Schritte:**
- Entdecken Sie zusätzliche Aspose.Words-Funktionen wie Serienbriefe oder Berichterstellung.
- Ausführliche Anleitungen und API-Referenzen finden Sie in der Aspose-Dokumentation.
- Experimentieren Sie mit verschiedenen von Aspose.Words unterstützten Dokumentformaten.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}