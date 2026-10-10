---
category: general
date: 2026-10-10
description: Vytvořte možnosti podpisu a podepište dokument Word pomocí XAdES EPES
  v Javě. Naučte se, jak v několika jasných krocích podepsat kancelářský dokument
  certifikátem.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: cs
lastmod: 2026-10-10
og_description: Vytvořte možnosti podpisu a podepište dokument Word pomocí XAdES EPES
  v Javě. Tento průvodce vám ukáže, jak bezpečně podepsat kancelářský dokument pomocí
  certifikátu.
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: Vytvořte možnosti podpisu a podepište Word dokument pomocí XAdES EPES
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
title: Vytvořte možnosti podpisu a podepište dokument Word pomocí XAdES EPES
url: /cs/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte možnosti podpisu a podepište dokument Word pomocí XAdES EPES

Pokud potřebujete **vytvořit možnosti podpisu** pro soubor DOCX, tento průvodce vám ukáže, jak podepsat dokument Word pomocí úrovně XAdES‑EPES v Javě. Získáte kompletní, spustitelný příklad, který podepíše Office dokument pomocí PFX certifikátu během několika řádků kódu.

Podepisování office dokumentů je běžnou požadavkem pro právní workflow, automatizované zpracování smluv a bezpečnou výměnu dokumentů. V tomto tutoriálu se naučíte:

* Jak nakonfigurovat `SignatureOptions` pro XAdES‑EPES.
* Jak zavolat `DigitalSignatureUtil.sign` pro **podepsání souborů Word**.
* Jak řešit běžné úskalí, jako je načítání certifikátu a chyby hesla.

> **Požadavek** – Java 17 nebo novější, knihovna GroupDocs.Signature for Java (nebo kompatibilní XAdES knihovna) a platný soubor certifikátu `.pfx`.

---

## Co budete potřebovat

| Položka | Důvod |
|------|--------|
| Java 17+ | Moderní jazykové funkce a lepší bezpečnostní API |
| GroupDocs.Signature for Java (or equivalent) | Poskytuje `SignatureOptions`, `XmlDsigLevel` a `DigitalSignatureUtil` |
| A PFX certificate (`.pfx`) | Poskytuje soukromý klíč pro digitální podpis |
| Password for the certificate | Vyžadováno k odemčení soukromého klíče |
| An unsigned DOCX file (`Unsigned.docx`) | Zdrojový dokument, který chcete **podepsat office dokument** |

Ujistěte se, že JAR knihovny je ve vaší classpath:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

---

## Krok 1: Importujte požadované třídy

Začněte importováním tříd, které zpracovávají podpisy a vstup/výstup souborů.

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

Tento import vám poskytuje přístup k API používanému k **vytvoření možností podpisu** a k provedení samotné operace podepisování.

---

## Krok 2: Vytvořte možnosti podpisu

Objekt `SignatureOptions` obsahuje veškerou konfiguraci potřebnou pro proces podepisování, jako je úroveň podpisu, vizuální vzhled a nastavení časové razítka.

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

Vytvoření nové instance `SignatureOptions` je prvním krokem v **jak podepsat docx** soubory, protože izoluje každý požadavek na podpis a zabraňuje vedlejším efektům mezi dokumenty.

---

## Krok 3: Zadejte úroveň podpisu XAdES EPES

XAdES‑EPES (Explicit Policy-based Electronic Signature) je široce akceptovaná politika pro podpisy Office dokumentů. Nastavením úrovně řeknete knihovně, který kryptografický profil použít.

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

Proč XAdES‑EPES? Vkládá politiku podpisu přímo do podpisu, což dělá podepsaný dokument samostatným a v souladu s mnoha předpisy o elektronickém podpisu.

---

## Krok 4: Podepište soubor DOCX

Nyní zavolejte `DigitalSignatureUtil.sign`. Tato metoda načte zdrojový soubor, aplikuje podpis a zapíše podepsaný výstup.

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

**Co se děje uvnitř?**  
1. Knihovna načte soubor `.pfx` a pomocí zadaného hesla extrahuje soukromý klíč.  
2. Vytvoří strukturu XML‑DSig odpovídající profilu XAdES‑EPES.  
3. Podpis je vložen do balíčku DOCX, přičemž zachovává původní rozvržení dokumentu.  

Pokud je heslo k certifikátu špatné nebo soubor nelze přečíst, je vyhozena výjimka `IOException`, kterou byste měli ošetřit, jak je ukázáno.

---

## Krok 5: Ověřte podepsaný dokument (volitelné)

Po podepsání možná budete chtít potvrdit, že podpis je přítomen a platný. GroupDocs poskytuje ověřovací API, ale rychlou manuální kontrolu lze provést v Microsoft Word:

1. Otevřete `SignedXades.docx` ve Wordu.  
2. Klikněte na **File → Info → View signatures**.  
3. Word by měl zobrazit zelenou kontrolku, která naznačuje platný digitální podpis.

Automatické ověření pomocí knihovny vypadá takto:

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

Spuštění kroku ověření vám poskytne programovou jistotu, že **podepsání office dokumentu** bylo úspěšné.

---

## Kompletní, spustitelný příklad

Spojením všech částí dohromady je zde samostatná Java třída, kterou můžete zkopírovat, vložit a spustit.

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

**Očekávaný výstup**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

Pokud se něco pokazí, konzole zobrazí jasnou chybovou zprávu, která vám pomůže řešit problémy s certifikátem nebo cestou k souboru.

---

## Časté otázky a řešení okrajových případů

| Otázka | Odpověď |
|----------|--------|
| **Mohu použít jinou úroveň podpisu?** | Ano. Nahraďte `XmlDsigLevel.XAdES_EPES` za `XAdES_BES`, `XAdES_T` atd., v závislosti na požadavcích na shodu. |
| **Co když je můj certifikát uložen v keystore místo souboru .pfx?** | Nahrajte `KeyStore` ručně, extrahujte `PrivateKey` a `Certificate`, a poté je předajte přetížené metodě `sign`, která přijímá objekt `KeyStore`. |
| **Jak přidám viditelný obrázek podpisu?** | Použijte `signatureOptions.setSignatureImage("path/to/image.png")` před voláním `sign`. |
| **Je proces podepisování thread‑safe?** | Metoda `DigitalSignatureUtil.sign` je bezstavová; můžete ji bezpečně volat z více vláken, pokud každé vlákno používá vlastní instanci `SignatureOptions`. |
| **Co když DOCX obsahuje existující podpisy?** | Knihovna přidá nový záznam podpisu do balíčku, přičemž zachová předchozí podpisy. Ověřte, že politika podpisu povoluje více podpisů, pokud je to nutné. |

---

## Tipy a osvědčené postupy (E‑E‑A‑T)

* **Pro tip:** Uložte heslo k certifikátu v zabezpečeném úložišti (např. Azure Key Vault) místo jeho pevného zakódování.  
* **Dejte pozor na:** Oddělovače cest k souborům ve Windows (`\`) vs. Unix (`/`). Použijte `Paths.get(...)` pro vytvoření cest nezávislých na platformě.  
* **Výkon:** Podepisování velkých souborů DOCX může být omezeno I/O; zvažte streamování vstupního souboru, pokud zpracováváte mnoho dokumentů najednou.  
* **Shoda:** XAdES‑EPES je v souladu s regulací EU eIDAS; před výběrem úrovně podpisu ověřte místní právní požadavky.

---

## Závěr

V tomto tutoriálu jste se naučili, jak **vytvořit možnosti podpisu** a **podepsat dokument Word** s úrovní XAdES‑EPES pomocí Javy. Kompletní příklad zahrnuje načítání certifikátu, konfiguraci možností, volání podepisování a volitelné ověření, což vám poskytuje připravené řešení pro **jak podepsat docx** soubory v produkci.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořte možnosti načítání v Javě – Detekce chybějících fontů a jak načíst DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Používání možností dokumentu a nastavení v Aspose.Words pro Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Jak vytvořit editovatelné oblasti v dokumentech jen pro čtení pomocí Aspose.Words pro Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}