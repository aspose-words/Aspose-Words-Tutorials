---
category: general
date: 2026-10-10
description: Créez des options de signature et signez un document Word en utilisant
  XAdES EPES en Java. Apprenez à signer un document Office avec un certificat en quelques
  étapes claires.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: fr
lastmod: 2026-10-10
og_description: Créez des options de signature et signez un document Word en utilisant
  XAdES EPES en Java. Ce guide vous montre comment signer un document Office en toute
  sécurité avec un certificat.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: Créer des options de signature et signer un document Word avec XAdES EPES
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
title: Créer des options de signature et signer un document Word avec XAdES EPES
url: /fr/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer des options de signature et signer un document Word avec XAdES EPES

Si vous devez **créer des options de signature** pour un fichier DOCX, ce guide vous montre comment signer un document Word en utilisant le niveau XAdES‑EPES en Java. Vous obtiendrez un exemple complet, exécutable, qui signe un document Office avec un certificat PFX en quelques lignes de code seulement.

Signer des documents Office est une exigence courante pour les flux de travail juridiques, le traitement automatisé des contrats et l’échange sécurisé de documents. Dans ce tutoriel, vous apprendrez :

* Comment configurer `SignatureOptions` pour XAdES‑EPES.  
* Comment appeler `DigitalSignatureUtil.sign` pour **signer des fichiers word doc**.  
* Comment gérer les pièges courants tels que le chargement du certificat et les erreurs de mot de passe.

> **Prérequis** – Java 17 ou version ultérieure, la bibliothèque GroupDocs.Signature for Java (ou une bibliothèque XAdES compatible), et un fichier de certificat `.pfx` valide.

---

## Ce dont vous avez besoin

| Élément | Raison |
|------|--------|
| Java 17+ | Fonctionnalités modernes du langage et meilleures API de sécurité |
| GroupDocs.Signature for Java (ou équivalent) | Fournit `SignatureOptions`, `XmlDsigLevel` et `DigitalSignatureUtil` |
| Un certificat PFX (`.pfx`) | Fournit la clé privée pour la signature numérique |
| Mot de passe du certificat | Nécessaire pour déverrouiller la clé privée |
| Un fichier DOCX non signé (`Unsigned.docx`) | Le document source que vous souhaitez **signer un document office** |

Assurez‑vous que le JAR de la bibliothèque est présent dans votre classpath :

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

---

## Étape 1 : Importer les classes requises

Commencez par importer les classes qui gèrent les signatures et les entrées/sorties de fichiers.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

Ces imports vous donnent accès à l’API utilisée pour **créer des options de signature** et pour exécuter l’opération de signature proprement dite.

---

## Étape 2 : Créer les options de signature

L’objet `SignatureOptions` contient toute la configuration nécessaire au processus de signature, comme le niveau de signature, l’apparence visuelle et les paramètres de timestamp.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Créer une nouvelle instance de `SignatureOptions` est la première étape pour **comment signer des docx**, car cela isole chaque demande de signature, évitant les effets de bord entre documents.

---

## Étape 3 : Spécifier le niveau de signature XAdES EPES

XAdES‑EPES (Explicit Policy‑based Electronic Signature) est une politique largement acceptée pour les signatures de documents Office. Définir le niveau indique à la bibliothèque quel profil cryptographique utiliser.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

Pourquoi XAdES‑EPES ? Il intègre la politique de signature directement dans la signature, rendant le document signé autonome et conforme à de nombreuses réglementations e‑signature.

---

## Étape 4 : Signer le fichier DOCX

Appelez maintenant `DigitalSignatureUtil.sign`. Cette méthode lit le fichier source, applique la signature et écrit le résultat signé.

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

**Que se passe‑t‑il en coulisses ?**  
1. La bibliothèque charge le fichier `.pfx` et extrait la clé privée à l’aide du mot de passe fourni.  
2. Elle crée une structure XML‑DSig correspondant au profil XAdES‑EPES.  
3. La signature est intégrée dans le package DOCX, en préservant la mise en page originale du document.  

Si le mot de passe du certificat est incorrect ou si le fichier ne peut pas être lu, une `IOException` est levée, que vous devez gérer comme indiqué.

---

## Étape 5 : Vérifier le document signé (facultatif)

Après la signature, vous pouvez vouloir confirmer que la signature est bien présente et valide. GroupDocs propose une API de vérification, mais une vérification manuelle rapide peut être effectuée avec Microsoft Word :

1. Ouvrez `SignedXades.docx` dans Word.  
2. Cliquez sur **Fichier → Informations → Afficher les signatures**.  
3. Word doit afficher une coche verte indiquant une signature numérique valide.

La vérification automatisée avec la bibliothèque se présente ainsi :

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

Exécuter l’étape de vérification vous donne la certitude programmatique que **signer un document office** a réussi.

---

## Exemple complet, exécutable

En rassemblant tous les morceaux, voici une classe Java autonome que vous pouvez copier, coller et exécuter.

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

**Sortie attendue**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

En cas de problème, la console affichera un message d’erreur clair, vous aidant à dépanner les questions de certificat ou de chemin de fichier.

---

## Questions fréquentes et gestion des cas limites

| Question | Réponse |
|----------|--------|
| **Puis‑je utiliser un autre niveau de signature ?** | Oui. Remplacez `XmlDsigLevel.XAdES_EPES` par `XAdES_BES`, `XAdES_T`, etc., selon les exigences de conformité. |
| **Et si mon certificat est stocké dans un keystore au lieu d’un fichier .pfx ?** | Chargez le `KeyStore` manuellement, extrayez le `PrivateKey` et le `Certificate`, puis passez‑les à une surcharge de `sign` qui accepte un objet `KeyStore`. |
| **Comment ajouter une image de signature visible ?** | Utilisez `signatureOptions.setSignatureImage("path/to/image.png")` avant d’appeler `sign`. |
| **Le processus de signature est‑il thread‑safe ?** | La méthode `DigitalSignatureUtil.sign` est sans état ; vous pouvez l’appeler en toute sécurité depuis plusieurs threads tant que chaque thread utilise sa propre instance de `SignatureOptions`. |
| **Que se passe‑t‑il si le DOCX contient déjà des signatures ?** | La bibliothèque ajoutera une nouvelle entrée de signature, en préservant les signatures existantes. Vérifiez que la politique de signature autorise plusieurs signatures si nécessaire. |

---

## Astuces et bonnes pratiques (E‑E‑A‑T)

* **Astuce pro :** Stockez le mot de passe de votre certificat dans un coffre sécurisé (par ex., Azure Key Vault) plutôt que de le coder en dur.  
* **Attention à :** Les séparateurs de chemins sous Windows (`\`) vs. Unix (`/`). Utilisez `Paths.get(...)` pour construire des chemins indépendants de la plateforme.  
* **Performance :** La signature de gros fichiers DOCX peut être limitée par les I/O ; envisagez le streaming du fichier d’entrée si vous traitez de nombreux documents en lot.  
* **Conformité :** XAdES‑EPES est conforme au règlement eIDAS de l’UE ; vérifiez vos exigences légales locales avant de choisir un niveau de signature.

---

## Conclusion

Dans ce tutoriel, vous avez appris à **créer des options de signature** et à **signer un document Word** avec le niveau XAdES‑EPES en Java. L’exemple complet couvre le chargement du certificat, la configuration des options, l’appel de signature et la vérification optionnelle, vous offrant une solution prête à l’emploi pour **comment signer des docx** en production.

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants abordent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer des options de chargement en Java – Détecter les polices manquantes & comment charger un DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)  
- [Utiliser les options et paramètres de document dans Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)  
- [Comment créer des plages éditables dans des documents en lecture seule avec Aspose.Words for Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}