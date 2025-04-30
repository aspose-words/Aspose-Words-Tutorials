---
"description": "Naučte se, jak vytvořit a digitálně podepsat řádek podpisu v dokumentu Word pomocí Aspose.Words pro .NET v tomto podrobném návodu. Ideální pro automatizaci dokumentů."
"linktitle": "Vytvoření a podepsání nového řádku podpisu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vytvoření a podepsání nového řádku podpisu"
"url": "/cs/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření a podepsání nového řádku podpisu

## Zavedení

Ahoj! Takže máte dokument Wordu a potřebujete do něj přidat řádek pro podpis a poté ho digitálně podepsat. Zní to složitě? Vůbec ne! Díky Aspose.Words pro .NET toho můžete bez problémů dosáhnout jen pomocí několika řádků kódu. V tomto tutoriálu vás provedeme celým procesem od nastavení prostředí až po uložení dokumentu s novým a zářivým podpisem. Připraveni? Pojďme se do toho pustit!

## Předpoklady

Než se pustíme do kódu, ujistěme se, že máte vše potřebné:
1. Aspose.Words pro .NET - Můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí .NET – Visual Studio je důrazně doporučeno.
3. Dokument k podepsání – Vytvořte jednoduchý dokument aplikace Word nebo použijte existující.
4. Soubor certifikátu – Je potřeba pro digitální podpisy. Můžete použít `.pfx` soubor.
5. Obrázky pro řádek podpisu – Volitelně soubor s obrázkem pro podpis.

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory. Tento krok je klíčový, protože nastavuje prostředí pro používání funkcí Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Krok 1: Nastavení adresáře dokumentů

Každý projekt potřebuje dobrý začátek. Nastavme cestu k adresáři s dokumenty. Zde se budou vaše dokumenty ukládat a načítat.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vytvoření nového dokumentu

Nyní si vytvořme nový dokument Wordu pomocí Aspose.Words. Toto bude naše plátno, kam přidáme řádek pro podpis.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Vložení řádku pro podpis

A tady se děje ta magie. Do dokumentu vložíme řádek podpisu pomocí `DocumentBuilder` třída.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Krok 4: Uložení dokumentu s řádkem pro podpis

Jakmile je řádek pro podpis na místě, musíme dokument uložit. Toto je mezikrok předtím, než přistoupíme k jeho podpisu.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Krok 5: Nastavení možností podepisování

Nyní nastavme možnosti pro podepisování dokumentu. To zahrnuje zadání ID řádku podpisu a použitého obrázku.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Krok 6: Načtení certifikátu

Digitální podpisy vyžadují certifikát. Zde načteme soubor s certifikátem, který bude použit k podepsání dokumentu.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Krok 7: Podepsání dokumentu

Toto je poslední krok. Používáme `DigitalSignatureUtil` třída pro podepsání dokumentu. Podepsaný dokument se uloží pod novým názvem.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Závěr

tady to máte! Pomocí těchto kroků jste úspěšně vytvořili nový dokument Word, přidali řádek pro podpis a digitálně jej podepsali pomocí Aspose.Words pro .NET. Je to výkonný nástroj, který usnadňuje automatizaci dokumentů. Ať už pracujete se smlouvami, dohodami nebo jakýmikoli formálními dokumenty, tato metoda zajišťuje jejich bezpečné podepsání a ověření.

## Často kladené otázky

### Mohu pro řádek podpisu použít jiné formáty obrázků?
Ano, můžete použít různé formáty obrázků, jako například PNG, JPG, BMP atd.

### Je nutné použít `.pfx` soubor pro certifikát?
Ano, a `.pfx` Soubor je běžný formát pro ukládání kryptografických informací, včetně certifikátů a soukromých klíčů.

### Mohu do jednoho dokumentu přidat více řádků podpisu?
Rozhodně! Více řádků podpisu můžete vložit opakováním kroku vkládání pro každý podpis.

### Co když nemám digitální certifikát?
Budete muset získat digitální certifikát od důvěryhodné certifikační autority nebo si jej vygenerovat pomocí nástrojů, jako je OpenSSL.

### Jak ověřím digitální podpis v dokumentu?
Podepsaný dokument můžete otevřít ve Wordu a přejít na podrobnosti o podpisu, abyste ověřili pravost a integritu podpisu.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}