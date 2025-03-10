---
title: Vytváření a podepisování nového podpisového řádku
linktitle: Vytváření a podepisování nového podpisového řádku
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak vytvořit a digitálně podepsat podpisový řádek v dokumentu aplikace Word pomocí Aspose.Words for .NET pomocí tohoto podrobného kurzu. Ideální pro automatizaci dokumentů.
weight: 10
url: /cs/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytváření a podepisování nového podpisového řádku

## Zavedení

Ahoj! Takže máte dokument aplikace Word a musíte přidat řádek podpisu a poté jej digitálně podepsat. Zní to složitě? Vůbec ne! Díky Aspose.Words pro .NET toho můžete dosáhnout bez problémů s několika řádky kódu. V tomto tutoriálu vás provedeme celým procesem od nastavení prostředí až po uložení dokumentu s novým zářivým podpisem. Připraveni? Pojďme se ponořit!

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte vše, co potřebujete:
1.  Aspose.Words for .NET - Můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Důrazně doporučujeme vývojové prostředí .NET – Visual Studio.
3. Dokument k podpisu – vytvořte jednoduchý dokument aplikace Word nebo použijte existující.
4.  Soubor certifikátu – je potřeba pro digitální podpisy. Můžete použít a`.pfx` soubor.
5. Obrázky pro řádek podpisu – volitelně soubor obrázku pro podpis.

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory. Tento krok je zásadní, protože nastavuje prostředí pro používání funkcí Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Krok 1: Nastavení adresáře dokumentů

Každý projekt potřebuje dobrý začátek. Pojďme nastavit cestu k vašemu adresáři dokumentů. Zde budou vaše dokumenty uloženy a načteny.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vytvoření nového dokumentu

Nyní vytvořte nový dokument aplikace Word pomocí Aspose.Words. Toto bude naše plátno, kam přidáme podpisový řádek.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Vložení řádku podpisu

 Tady se děje kouzlo. Do našeho dokumentu vložíme řádek podpisu pomocí`DocumentBuilder` třída.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Krok 4: Uložení dokumentu pomocí řádku podpisu

Jakmile je řádek podpisu na svém místě, musíme dokument uložit. Toto je mezikrok před tím, než přistoupíme k podpisu.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Krok 5: Nastavení možností podpisu

Nyní nastavíme možnosti podepisování dokumentu. To zahrnuje specifikaci ID řádku podpisu a obrázku, který se má použít.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## Krok 6: Načtení certifikátu

Digitální podpisy vyžadují certifikát. Zde načteme soubor certifikátu, který bude použit k podpisu dokumentu.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## Krok 7: Podepsání dokumentu

 Toto je poslední krok. Používáme`DigitalSignatureUtil`třídy dokument podepsat. Podepsaný dokument se uloží pod novým názvem.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Závěr

A tady to máte! Pomocí těchto kroků jste úspěšně vytvořili nový dokument aplikace Word, přidali řádek podpisu a digitálně jej podepsali pomocí Aspose.Words for .NET. Je to výkonný nástroj, díky kterému je automatizace dokumentů hračkou. Ať už se zabýváte smlouvami, dohodami nebo jinými formálními dokumenty, tato metoda zajišťuje, že jsou bezpečně podepsány a ověřeny.

## FAQ

### Mohu pro řádek podpisu použít jiné formáty obrázků?
Ano, můžete použít různé formáty obrázků jako PNG, JPG, BMP atd.

###  Je nutné použít a`.pfx` file for the certificate?
 Ano, a`.pfx` soubor je běžný formát pro ukládání kryptografických informací včetně certifikátů a soukromých klíčů.

### Mohu přidat více řádků podpisu do jednoho dokumentu?
Absolutně! Můžete vložit více řádků podpisu opakováním kroku vložení pro každý podpis.

### Co když nemám digitální certifikát?
Budete muset získat digitální certifikát od důvěryhodné certifikační autority nebo jej vygenerovat pomocí nástrojů, jako je OpenSSL.

### Jak ověřím digitální podpis v dokumentu?
Podepsaný dokument můžete otevřít ve Wordu a přejít na podrobnosti podpisu a ověřit pravost a integritu podpisu.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
