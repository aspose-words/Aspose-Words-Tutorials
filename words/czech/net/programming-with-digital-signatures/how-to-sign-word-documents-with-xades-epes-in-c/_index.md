---
category: general
date: 2026-09-08
description: Jak podepsat dokumenty Word pomocí workflow digitálního podpisu docx,
  načíst certifikát pfx a vytvořit XAdES podpis v C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign word
- digital signature docx
- load pfx certificate
- digitally sign word
- create xades signature
language: cs
lastmod: 2026-09-08
og_description: Jak podepisovat dokumenty Word pomocí digitálního podpisu v rámci
  docx workflow, načíst certifikát pfx a vytvořit podpis XAdES v C#. Sledujte kompletní
  příklad.
og_image_alt: Screenshot showing a Word document signed with XAdES EPES digital signature
og_title: Jak podepsat dokumenty Word pomocí XAdES EPES v C# – průvodce krok po kroku
schemas:
- author: GroupDocs
  dateModified: '2026-09-08'
  description: How to sign word documents using a digital signature docx workflow,
    load pfx certificate, and create XAdES signature in C#.
  headline: How to sign word documents with XAdES EPES in C#
  type: TechArticle
tags:
- digital-signature
- C#
- Word
- XAdES
title: Jak podepsat dokumenty Word pomocí XAdES EPES v C#
url: /cs/net/programming-with-digital-signatures/how-to-sign-word-documents-with-xades-epes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak podepsat Word dokumenty pomocí XAdES EPES v C#

Pokud potřebujete **jak podepsat Word** soubory programově, tento průvodce vám ukáže kompletní, připravené řešení pro produkci. Naučíte se, jak načíst PFX certifikát, nakonfigurovat digitální podpis docx a vytvořit XAdES‑EPES podpis, který může ověřit Microsoft Word i třetí strany.

Příklad používá knihovnu GroupDocs.Signature pro .NET, ale koncepty platí pro jakékoli API podporující XAdES. Na konci tutoriálu budete mít podepsaný `Signed_XAdES_EPES.docx` připravený k distribuci.

## Co budete potřebovat

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.7+)
- Platný soubor PFX certifikátu (`.pfx`) obsahující soukromý klíč
- Heslo k souboru PFX
- Word dokument (`.docx`), který chcete podepsat
- NuGet balíček **GroupDocs.Signature** (nainstalujte pomocí `dotnet add package GroupDocs.Signature`)

## Krok 1: Nainstalujte požadovaný NuGet balíček

```bash
dotnet add package GroupDocs.Signature
```

Balíček poskytuje třídu `Document`, `XadesSignatureOptions` a pomocné typy pro vytvoření **digitálně podepsaného Word** souboru.

## Krok 2: Načtěte nepodepsaný Word dokument

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;
using System;
using System.Security.Cryptography.X509Certificates;

...

// Load the original Word file (must be a .docx)
var documentPath = @"C:\Docs\Unsigned.docx";
Document document = new Document(documentPath);
```

Načtení dokumentu vám poskytne objektový model, který můžete upravit před aplikací podpisu.

## Krok 3: Načtěte PFX certifikát (load pfx certificate)

```csharp
// Load the certificate that holds the private key
var certPath = @"C:\Certificates\mycert.pfx";
var certPassword = "yourPassword";          // keep this secret!
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword);
```

> **Tip:** Pokud je certifikát uložen v úložišti certifikátů Windows, můžete jej získat pomocí `X509Store` místo načítání souboru. Přístup `load pfx certificate` funguje na jakékoli platformě, včetně Linux kontejnerů.

## Krok 4: (Volitelné) Přidejte vizuální řádek podpisu

Vizuální nápověda pomáhá příjemcům vidět, kde se podpis v aplikaci Word objeví.

```csharp
// Create a signature line that will be displayed in the document
SignatureLine signatureLine = new SignatureLine(document);
signatureLine.Id = Guid.NewGuid().ToString();
signatureLine.Signer = "John Smith";
signatureLine.Title = "Approved";

// Append the line to the first paragraph of the first section
document.FirstSection.Body.FirstParagraph.AppendChild(signatureLine);
```

Pokud dáváte přednost neviditelnému podpisu, můžete tento krok přeskočit. **Digitální podpis docx** bude i nadále kryptograficky platný.

## Krok 5: Nakonfigurujte možnosti XAdES‑EPES (create xades signature)

Příznak `XadesSignatureType.XAdES_EPES` říká knihovně, aby vložila podpis podle profilu EPES (Explicit Policy-based Electronic Signature), který je široce akceptován nařízeními EU e‑IDAS.

```csharp
// Set up XAdES‑EPES options – this creates a “qualified” electronic signature
XadesSignatureOptions signOptions = new XadesSignatureOptions
{
    SignatureType = XadesSignatureType.XAdES_EPES,
    // Optional: add a custom signing reason or location
    Reason = "Document approval",
    Location = "New York, USA"
};
```

## Krok 6: Aplikujte digitální podpis

```csharp
// Sign the document with the loaded certificate and options
document.DigitalSignatures.Sign(certificate, signOptions);
```

Metoda `Sign` provádí veškerou kryptografickou práci: hashuje části dokumentu, vytváří strukturu XML‑DSig a vkládá XAdES obálku do souboru Word.

## Krok 7: Uložte podepsaný dokument

```csharp
// Save the signed file – you can overwrite or create a new file
var signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
document.Save(signedPath);
Console.WriteLine($"Document signed and saved to: {signedPath}");
```

Po uložení otevřete `Signed_XAdES_EPES.docx` v Microsoft Word. Měli byste vidět řádek podpisu (pokud jste jej přidali) a stavový řádek **digitálně podepsaný Word**, který naznačuje, že soubor je podepsán a podpis je platný.

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat a vložit do konzolové aplikace.

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

namespace WordXadesSigner
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the unsigned Word document
            string docPath = @"C:\Docs\Unsigned.docx";
            Document document = new Document(docPath);

            // 2️⃣ Load the signing certificate (load pfx certificate)
            string pfxPath = @"C:\Certificates\mycert.pfx";
            string pfxPassword = "yourPassword";
            X509Certificate2 cert = new X509Certificate2(pfxPath, pfxPassword);

            // 3️⃣ (Optional) Add a visual signature line
            SignatureLine sigLine = new SignatureLine(document)
            {
                Id = Guid.NewGuid().ToString(),
                Signer = "John Smith",
                Title = "Approved"
            };
            document.FirstSection.Body.FirstParagraph.AppendChild(sigLine);

            // 4️⃣ Configure XAdES‑EPES options (create xades signature)
            XadesSignatureOptions xadesOptions = new XadesSignatureOptions
            {
                SignatureType = XadesSignatureType.XAdES_EPES,
                Reason = "Document approval",
                Location = "New York, USA"
            };

            // 5️⃣ Apply the digital signature (digitally sign word)
            document.DigitalSignatures.Sign(cert, xadesOptions);

            // 6️⃣ Save the signed document
            string signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
            document.Save(signedPath);

            Console.WriteLine($"Signed document saved to: {signedPath}");
        }
    }
}
```

### Očekávaný výstup

```
Signed document saved to: C:\Docs\Signed_XAdES_EPES.docx
```

Otevření souboru ve Wordu zobrazí zelený banner „Signed“ a pokud jste přidali vizuální řádek, řádek podpisu se objeví na určeném místě.

## Řešení běžných problémů

| Problém | Proč k tomu dochází | Řešení |
|-------|----------------|-----|
| **Nesprávné heslo certifikátu** | Konstruktor `X509Certificate2` vyhodí `CryptographicException`. | Ověřte heslo nebo použijte bezpečný správce tajemství (Azure Key Vault, AWS Secrets Manager). |
| **Word zobrazuje „Signature is invalid“** | Dokument byl po podpisu změněn, nebo chybí politika podpisu. | Ujistěte se, že soubor je uložen **po** podpisu a není dále upravován. Vložte správnou XAdES politiku, pokud ji vyžaduje váš regulátor. |
| **Řádek podpisu není viditelný** | Dokument používá jiný rozvrh sekcí. | Přidejte `SignatureLine` do správného odstavce nebo vytvořte nový odstavec před jeho přidáním. |
| **Zpomalení výkonu u velkých dokumentů** | XAdES podpisy hashují každou část balíčku. | Použijte streamingové API (`SignAsync`) nebo zvýšte zdroje stroje pro velmi velké soubory (>50 MB). |

## Rozšíření řešení

- **Více podepisujících** – volajte `Sign` opakovaně s různými certifikáty a nastavte `SignatureId` pro rozlišení každého podepisujícího.
- **Časové razítko** – přidejte objekt `TimestampOptions` do `XadesSignatureOptions` pro vložení důvěryhodného časového razítka.
- **Vlastní politiky** – poskytněte XML soubor politiky pomocí `XadesSignatureOptions.PolicyFilePath` pro soulad s konkrétními standardy.

## Závěr

Nyní víte, **jak podepsat Word** dokumenty programově, jak **načíst pfx certifikát** a jak **vytvořit xades podpis** pomocí GroupDocs.Signature. Tutoriál pokryl každý krok od načtení dokumentu po uložení podepsaného výstupu, včetně praktických tipů pro běžné okrajové případy.  

Dále prozkoumejte související témata, jako jsou **digitálně podepsané PDF**, integrace ověření **digitálního podpisu docx**, nebo přidání podpory **timestamp** pro splnění pokročilých požadavků na soulad. Šťastné podepisování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Detekovat digitální podpis ve Word dokumentu](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Podepisování existujícího řádku podpisu ve Word dokumentu](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)
- [Přístup a ověření podpisu ve Word dokumentu](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}