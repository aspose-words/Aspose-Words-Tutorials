---
category: general
date: 2026-10-10
description: Erstellen Sie Signaturoptionen und signieren Sie ein Word‑Dokument mit
  XAdES EPES in Java. Lernen Sie, wie Sie ein Office‑Dokument mit einem Zertifikat
  in wenigen klaren Schritten signieren.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: de
lastmod: 2026-10-10
og_description: Erstellen Sie Signaturoptionen und signieren Sie ein Word‑Dokument
  mit XAdES EPES in Java. Dieser Leitfaden zeigt Ihnen, wie Sie ein Office‑Dokument
  sicher mit einem Zertifikat signieren.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: Erstellen Sie Signaturoptionen und signieren Sie ein Word‑Dokument mit XAdES EPES.
schemas:
- author: GroupDocs
  dateModified: '2026-10-10'
  description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  headline: Create signature options and sign a Word doc with XAdES EPES
  type: TechArticle
- description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  name: Create signature options and sign a Word doc with XAdES EPES
  steps:
  - name: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
    text: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
  - name: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
    text: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
  - name: The signature is embedded into the DOCX package, preserving the original
      document layout.
    text: The signature is embedded into the DOCX package, preserving the original
      document layout.
  - name: Open `SignedXades.docx` in Word.
    text: Open `SignedXades.docx` in Word.
  - name: Click **File → Info → View signatures**.
    text: Click **File → Info → View signatures**.
  - name: Word should display a green checkmark indicating a valid digital signature.
    text: Word should display a green checkmark indicating a valid digital signature.
  type: HowTo
tags:
- digital signature
- Java
- XAdES
title: Signaturoptionen erstellen und ein Word‑Dokument mit XAdES EPES signieren
url: /de/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen von Signaturoptionen und Signieren eines Word-Dokuments mit XAdES EPES

Wenn Sie **Signaturoptionen** für eine DOCX‑Datei erstellen müssen, zeigt Ihnen diese Anleitung, wie Sie ein Word‑Dokument mit dem XAdES‑EPES‑Level in Java signieren. Sie erhalten ein vollständiges, ausführbares Beispiel, das ein Office‑Dokument mit einem PFX‑Zertifikat in nur wenigen Code‑Zeilen signiert.

Das Signieren von Office‑Dokumenten ist eine häufige Anforderung für rechtliche Workflows, automatisierte Vertragsverarbeitung und sicheren Dokumentenaustausch. In diesem Tutorial lernen Sie:

* Wie man `SignatureOptions` für XAdES‑EPES konfiguriert.
* Wie man `DigitalSignatureUtil.sign` aufruft, um **Word‑Dokument signieren** Dateien.
* Wie man gängige Fallstricke wie das Laden von Zertifikaten und Passwortfehler behandelt.

> **Voraussetzung** – Java 17 oder höher, die GroupDocs.Signature for Java Bibliothek (oder eine kompatible XAdES‑Bibliothek) und eine gültige `.pfx`‑Zertifikatsdatei.

## Was Sie benötigen

| Item | Reason |
|------|--------|
| Java 17+ | Moderne Sprachfeatures und bessere Sicherheits‑APIs |
| GroupDocs.Signature for Java (or equivalent) | Stellt `SignatureOptions`, `XmlDsigLevel` und `DigitalSignatureUtil` bereit |
| A PFX certificate (`.pfx`) | Stellt den privaten Schlüssel für die digitale Signatur bereit |
| Password for the certificate | Erforderlich, um den privaten Schlüssel zu entsperren |
| An unsigned DOCX file (`Unsigned.docx`) | Die Quelldatei, die Sie **Office‑Dokument signieren** möchten. |

Make sure the library JAR is on your classpath:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

## Schritt 1: Importieren der benötigten Klassen

Beginnen Sie mit dem Importieren der Klassen, die Signaturen und Datei‑I/O verarbeiten.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

These imports give you access to the API used to **create signature options** and to perform the actual signing operation.

## Schritt 2: Signaturoptionen erstellen

Das Objekt `SignatureOptions` enthält alle Konfigurationen, die für den Signaturvorgang erforderlich sind, wie Signatur‑Level, visuelle Darstellung und Zeitstempel‑Einstellungen.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Das Erstellen einer neuen `SignatureOptions`‑Instanz ist der erste Schritt beim **Signieren von DOCX**‑Dateien, da es jede Signaturanfrage isoliert und Nebenwirkungen zwischen Dokumenten verhindert.

## Schritt 3: XAdES‑EPES‑Signaturlevel festlegen

XAdES‑EPES (Explicit Policy‑based Electronic Signature) ist eine weit verbreitete Richtlinie für Office‑Dokumentensignaturen. Das Festlegen des Levels teilt der Bibliothek mit, welches kryptografische Profil verwendet werden soll.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

Warum XAdES‑EPES? Es bettet die Signatur‑Richtlinie direkt in die Signatur ein, wodurch das signierte Dokument eigenständig ist und vielen e‑Signature‑Vorschriften entspricht.

## Schritt 4: DOCX‑Datei signieren

Rufen Sie nun `DigitalSignatureUtil.sign` auf. Diese Methode liest die Quelldatei, wendet die Signatur an und schreibt die signierte Ausgabe.

```java
// Step 4: Sign the document using the provided certificate
try {
    DigitalSignatureUtil.sign(
        "YOUR_DIRECTORY/Unsigned.docx",   // input file
        "YOUR_DIRECTORY/SignedXades.docx", // output file
        "YOUR_DIRECTORY/mycert.pfx",      // certificate file
        "password",                       // certificate password
        signatureOptions                  // options configured above
    );
    System.out.println("Document signed successfully: SignedXades.docx");
} catch (IOException e) {
    System.err.println("Failed to sign the document: " + e.getMessage());
}
```

**Was passiert im Hintergrund?**  
1. Die Bibliothek lädt die `.pfx`‑Datei und extrahiert den privaten Schlüssel mit dem angegebenen Passwort.  
2. Sie erstellt eine XML‑DSig‑Struktur, die dem XAdES‑EPES‑Profil entspricht.  
3. Die Signatur wird in das DOCX‑Paket eingebettet und bewahrt das ursprüngliche Dokumentlayout.

Wenn das Zertifikatspasswort falsch ist oder die Datei nicht gelesen werden kann, wird eine `IOException` ausgelöst, die Sie wie gezeigt behandeln sollten.

## Schritt 5: Signiertes Dokument überprüfen (optional)

Nach dem Signieren möchten Sie möglicherweise bestätigen, dass die Signatur vorhanden und gültig ist. GroupDocs bietet eine Verifizierungs‑API, aber eine schnelle manuelle Prüfung kann mit Microsoft Word durchgeführt werden:

1. Öffnen Sie `SignedXades.docx` in Word.  
2. Klicken Sie auf **Datei → Info → Signaturen anzeigen**.  
3. Word sollte ein grünes Häkchen anzeigen, das eine gültige digitale Signatur anzeigt.

Automated verification with the library looks like this:

```java
import com.groupdocs.signature.VerificationResult;

VerificationResult result = DigitalSignatureUtil.verify(
    "YOUR_DIRECTORY/SignedXades.docx",
    signatureOptions
);

if (result.isSuccessful()) {
    System.out.println("Signature verification succeeded.");
} else {
    System.out.println("Signature verification failed: " + result.getErrorMessage());
}
```

Running the verification step gives you programmatic confidence that **sign office document** succeeded.

## Vollständiges, ausführbares Beispiel

Wenn Sie alle Teile zusammenfügen, erhalten Sie eine eigenständige Java‑Klasse, die Sie kopieren, einfügen und ausführen können.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import com.groupdocs.signature.VerificationResult;
import java.io.IOException;

/**
 * Demonstrates how to create signature options and sign a DOCX file with XAdES EPES.
 */
public class XadesSignatureDemo {

    public static void main(String[] args) {
        // Paths – update these to match your environment
        String inputPath = "YOUR_DIRECTORY/Unsigned.docx";
        String outputPath = "YOUR_DIRECTORY/SignedXades.docx";
        String certPath = "YOUR_DIRECTORY/mycert.pfx";
        String certPassword = "password";

        // 1️⃣ Create signature options
        SignatureOptions signatureOptions = new SignatureOptions();

        // 2️⃣ Set XAdES EPES level
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 3️⃣ Sign the document
        try {
            DigitalSignatureUtil.sign(inputPath, outputPath, certPath, certPassword, signatureOptions);
            System.out.println("Document signed successfully: " + outputPath);
        } catch (IOException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // 4️⃣ (Optional) Verify the signature
        VerificationResult verification = DigitalSignatureUtil.verify(outputPath, signatureOptions);
        if (verification.isSuccessful()) {
            System.out.println("Signature verification succeeded.");
        } else {
            System.out.println("Signature verification failed: " + verification.getErrorMessage());
        }
    }
}
```

**Expected output**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

Falls etwas schiefgeht, zeigt die Konsole eine klare Fehlermeldung an, die Ihnen hilft, Zertifikats‑ oder Dateipfad‑Probleme zu beheben.

## Häufige Fragen und Sonderfall‑Behandlung

| Question | Answer |
|----------|--------|
| **Kann ich ein anderes Signaturlevel verwenden?** | Ja. Ersetzen Sie `XmlDsigLevel.XAdES_EPES` durch `XAdES_BES`, `XAdES_T` usw., je nach Compliance‑Bedarf. |
| **Was ist, wenn mein Zertifikat in einem Keystore und nicht in einer .pfx‑Datei gespeichert ist?** | Laden Sie den `KeyStore` manuell, extrahieren Sie den `PrivateKey` und das `Certificate` und übergeben Sie sie an eine Überladung von `sign`, die ein `KeyStore`‑Objekt akzeptiert. |
| **Wie füge ich ein sichtbares Signatur‑Bild hinzu?** | Verwenden Sie `signatureOptions.setSignatureImage("path/to/image.png")` bevor Sie `sign` aufrufen. |
| **Ist der Signaturvorgang thread‑sicher?** | Die Methode `DigitalSignatureUtil.sign` ist zustandslos; Sie können sie sicher aus mehreren Threads aufrufen, solange jeder Thread seine eigene `SignatureOptions`‑Instanz verwendet. |
| **Was ist, wenn das DOCX bereits vorhandene Signaturen enthält?** | Die Bibliothek fügt einen neuen Signatur‑Paket‑Eintrag hinzu und bewahrt frühere Signaturen. Prüfen Sie, ob die Signatur‑Richtlinie mehrere Signaturen zulässt, falls erforderlich. |

## Tipps und bewährte Verfahren (E‑E‑A‑T)

* **Pro Tipp:** Speichern Sie Ihr Zertifikatspasswort in einem sicheren Tresor (z. B. Azure Key Vault) anstatt es hart zu codieren.  
* **Achten Sie auf:** Dateipfad‑Trennzeichen unter Windows (`\`) vs. Unix (`/`). Verwenden Sie `Paths.get(...)`, um plattformunabhängige Pfade zu erstellen.  
* **Leistung:** Das Signieren großer DOCX‑Dateien kann I/O‑gebunden sein; erwägen Sie das Streamen der Eingabedatei, wenn Sie viele Dokumente im Batch verarbeiten.  
* **Compliance:** XAdES‑EPES entspricht der EU‑eIDAS‑Verordnung; prüfen Sie Ihre lokalen gesetzlichen Anforderungen, bevor Sie ein Signaturlevel wählen.

## Fazit

In diesem Tutorial haben Sie gelernt, wie man **Signaturoptionen erstellt** und ein **Word‑Dokument** mit dem XAdES‑EPES‑Level in Java signiert. Das vollständige Beispiel umfasst das Laden des Zertifikats, die Konfiguration der Optionen, den Signaturaufruf und die optionale Verifizierung und bietet Ihnen eine sofort einsetzbare Lösung für das **Signieren von DOCX**‑Dateien in der Produktion.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Load Options in Java – Detect Missing Fonts & How to Load DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [How to Create Editable Ranges in Read-Only Documents Using Aspose.Words for Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}