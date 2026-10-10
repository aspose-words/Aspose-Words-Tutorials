---
category: general
date: 2026-10-10
description: Crea opzioni di firma e firma un documento Word usando XAdES EPES in
  Java. Scopri come firmare un documento Office con un certificato in pochi passaggi
  chiari.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: it
lastmod: 2026-10-10
og_description: Crea opzioni di firma e firma un documento Word usando XAdES EPES
  in Java. Questa guida ti mostra come firmare in modo sicuro un documento Office
  con un certificato.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: Crea opzioni di firma e firma un documento Word con XAdES EPES
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
title: Crea opzioni di firma e firma un documento Word con XAdES EPES
url: /it/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea opzioni di firma e firma un documento Word con XAdES EPES

Se hai bisogno di **creare opzioni di firma** per un file DOCX, questa guida ti mostra come firmare un documento Word utilizzando il livello XAdES‑EPES in Java. Otterrai un esempio completo e eseguibile che firma un documento Office con un certificato PFX in poche righe di codice.

Firmare documenti Office è una necessità comune per flussi di lavoro legali, elaborazione automatizzata di contratti e scambio sicuro di documenti. In questo tutorial imparerai:

* Come configurare `SignatureOptions` per XAdES‑EPES.  
* Come chiamare `DigitalSignatureUtil.sign` per **firmare file word doc**.  
* Come gestire le difficoltà più comuni, come il caricamento del certificato e gli errori di password.

> **Prerequisito** – Java 17 o successiva, la libreria GroupDocs.Signature for Java (o una libreria XAdES compatibile) e un file certificato `.pfx` valido.

---

## Cosa ti servirà

| Elemento | Motivo |
|------|--------|
| Java 17+ | Funzionalità moderne del linguaggio e API di sicurezza migliorate |
| GroupDocs.Signature for Java (or equivalent) | Fornisce `SignatureOptions`, `XmlDsigLevel` e `DigitalSignatureUtil` |
| Un certificato PFX (`.pfx`) | Fornisce la chiave privata per la firma digitale |
| Password per il certificato | Necessaria per sbloccare la chiave privata |
| Un file DOCX non firmato (`Unsigned.docx`) | Il documento sorgente che desideri **firmare documento office** |

Assicurati che il JAR della libreria sia nel tuo classpath:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

---

## Passo 1: Importa le classi necessarie

Inizia importando le classi che gestiscono le firme e l'I/O dei file.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

Queste importazioni ti danno accesso all'API usata per **creare opzioni di firma** e per eseguire l'operazione di firma effettiva.

---

## Passo 2: Crea opzioni di firma

L'oggetto `SignatureOptions` contiene tutta la configurazione necessaria per il processo di firma, come il livello di firma, l'aspetto visivo e le impostazioni del timestamp.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Creare una nuova istanza di `SignatureOptions` è il primo passo in **come firmare docx** perché isola ogni richiesta di firma, evitando effetti collaterali tra documenti.

---

## Passo 3: Specifica il livello di firma XAdES EPES

XAdES‑EPES (Explicit Policy-based Electronic Signature) è una politica ampiamente accettata per le firme di documenti Office. Impostare il livello indica alla libreria quale profilo crittografico utilizzare.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

Perché XAdES‑EPES? Inserisce la politica di firma direttamente nella firma, rendendo il documento firmato autonomo e conforme a molte normative sulle firme elettroniche.

---

## Passo 4: Firma il file DOCX

Ora invoca `DigitalSignatureUtil.sign`. Questo metodo legge il file sorgente, applica la firma e scrive l'output firmato.

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

**Cosa succede dietro le quinte?**  
1. La libreria carica il file `.pfx` ed estrae la chiave privata usando la password fornita.  
2. Crea una struttura XML‑DSig conforme al profilo XAdES‑EPES.  
3. La firma viene incorporata nel pacchetto DOCX, preservando il layout originale del documento.  

Se la password del certificato è errata o il file non può essere letto, viene generata un'`IOException`, che dovresti gestire come mostrato.

---

## Passo 5: Verifica il documento firmato (opzionale)

Dopo la firma, potresti voler confermare che la firma sia presente e valida. GroupDocs fornisce un'API di verifica, ma è possibile fare un rapido controllo manuale con Microsoft Word:

1. Apri `SignedXades.docx` in Word.  
2. Fai clic su **File → Info → Visualizza firme**.  
3. Word dovrebbe mostrare un segno di spunta verde che indica una firma digitale valida.

La verifica automatizzata con la libreria è così:

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

Eseguire il passaggio di verifica ti dà la certezza programmatica che **firmare documento office** sia riuscito.

---

## Esempio completo e eseguibile

Riunendo tutti i pezzi, ecco una classe Java autonoma che puoi copiare, incollare e eseguire.

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

**Output previsto**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

Se qualcosa va storto, la console mostrerà un messaggio di errore chiaro, aiutandoti a risolvere problemi di certificato o di percorso file.

---

## Domande comuni e gestione dei casi limite

| Domanda | Risposta |
|----------|--------|
| **Posso usare un livello di firma diverso?** | Sì. Sostituisci `XmlDsigLevel.XAdES_EPES` con `XAdES_BES`, `XAdES_T`, ecc., a seconda delle esigenze di conformità. |
| **E se il mio certificato è memorizzato in un keystore invece di un file .pfx?** | Carica manualmente il `KeyStore`, estrai `PrivateKey` e `Certificate`, quindi passali a una sovraccarico di `sign` che accetta un oggetto `KeyStore`. |
| **Come aggiungo un'immagine di firma visibile?** | Usa `signatureOptions.setSignatureImage("path/to/image.png")` prima di chiamare `sign`. |
| **Il processo di firma è thread‑safe?** | Il metodo `DigitalSignatureUtil.sign` è senza stato; puoi chiamarlo in sicurezza da più thread purché ogni thread utilizzi la propria istanza di `SignatureOptions`. |
| **E se il DOCX contiene firme esistenti?** | La libreria aggiungerà una nuova voce di pacchetto firma, preservando le firme precedenti. Verifica che la politica di firma consenta firme multiple, se necessario. |

---

## Suggerimenti e migliori pratiche (E‑E‑A‑T)

* **Pro tip:** Conserva la password del certificato in un vault sicuro (ad es., Azure Key Vault) anziché codificarla direttamente.  
* **Attenzione a:** I separatori di percorso su Windows (`\`) vs. Unix (`/`). Usa `Paths.get(...)` per costruire percorsi indipendenti dalla piattaforma.  
* **Performance:** Firmare file DOCX di grandi dimensioni può essere limitato dall'I/O; considera lo streaming del file di input se elabori molti documenti in batch.  
* **Conformità:** XAdES‑EPES è conforme al regolamento eIDAS dell'UE; verifica i requisiti legali locali prima di scegliere un livello di firma.

---

## Conclusione

In questo tutorial hai imparato come **creare opzioni di firma** e **firmare un documento Word** con il livello XAdES‑EPES usando Java. L'esempio completo copre il caricamento del certificato, la configurazione delle opzioni, la chiamata di firma e la verifica opzionale, fornendoti una soluzione pronta all'uso per **come firmare docx** in produzione.

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea Opzioni di Caricamento in Java – Rileva Font Mancanti e Come Caricare DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Utilizzo di Opzioni e Impostazioni del Documento in Aspose.Words per Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Come Creare Aree Modificabili in Documenti a Sola Lettura Utilizzando Aspose.Words per Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}