---
"description": "Naučte se, jak vytvořit nový řádek podpisu a nastavit ID poskytovatele v dokumentech Word pomocí Aspose.Words pro .NET. Podrobný návod."
"linktitle": "Vytvořit nový řádek podpisu a nastavit ID poskytovatele"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vytvořit nový řádek podpisu a nastavit ID poskytovatele"
"url": "/cs/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořit nový řádek podpisu a nastavit ID poskytovatele

## Zavedení

Ahoj, techničtí nadšenci! Přemýšleli jste někdy, jak programově přidat řádek pro podpis do dokumentů Wordu? Dnes se do toho ponoříme s využitím Aspose.Words pro .NET. Tato příručka vás provede každým krokem a usnadní vám vytvoření nového řádku pro podpis a nastavení ID poskytovatele v dokumentech Wordu. Ať už automatizujete zpracování dokumentů, nebo jen chcete zefektivnit svůj pracovní postup, tento tutoriál vám s tím pomůže.

## Předpoklady

Než si ušpiníme ruce, ujistěme se, že máme vše potřebné:

1. Aspose.Words pro .NET: Pokud jste tak ještě neučinili, stáhněte si jej [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí C#.
3. .NET Framework: Ujistěte se, že máte nainstalovaný .NET Framework.
4. Certifikát PFX: Pro podepisování dokumentů budete potřebovat certifikát PFX. Můžete ho získat od důvěryhodné certifikační autority.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory do vašeho projektu v C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Dobře, pojďme k věci. Zde je podrobný rozpis jednotlivých kroků pro vytvoření nového řádku podpisu a nastavení ID poskytovatele.

## Krok 1: Vytvořte nový dokument

Nejprve si musíme vytvořit nový dokument Wordu. Ten bude sloužit jako plátno pro náš podpisový řádek.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

V tomto úryvku inicializujeme nový `Document` a `DocumentBuilder`Ten/Ta/To `DocumentBuilder` pomáhá nám přidávat prvky do našeho dokumentu.

## Krok 2: Definování možností řádku podpisu

Dále definujeme možnosti pro řádek podpisu. Patří sem jméno podepisujícího, titul, e-mail a další podrobnosti.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Tyto možnosti přizpůsobují podpisový řádek, díky čemuž je jasný a profesionální.

## Krok 3: Vložte řádek podpisu

S nastavenými možnostmi nyní můžeme do dokumentu vložit řádek pro podpis.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

Zde, `InsertSignatureLine` Metoda přidá řádek podpisu a my mu přiřadíme jedinečné ID poskytovatele.

## Krok 4: Uložte dokument

Po vložení řádku pro podpis dokument uložme.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Tím se dokument uloží s nově přidaným řádkem pro podpis.

## Krok 5: Nastavení možností podepisování

Nyní musíme nastavit možnosti pro podepisování dokumentu. Patří sem ID řádku podpisu, ID poskytovatele, komentáře a čas podpisu.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Tyto možnosti zajišťují, že dokument je podepsán se správnými údaji.

## Krok 6: Vytvořte držitele certifikátu

K podepsání dokumentu použijeme certifikát PFX. Vytvořme pro něj držitele certifikátu.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

Nezapomeňte vyměnit `"morzal.pfx"` s vaším skutečným souborem certifikátu a `"aw"` s heslem k vašemu certifikátu.

## Krok 7: Podepište dokument

Nakonec dokument podepíšeme pomocí utility pro digitální podpis.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Tím se dokument podepíše a uloží jako nový soubor.

## Závěr

tady to máte! Úspěšně jste vytvořili nový řádek pro podpis a nastavili ID poskytovatele v dokumentu Word pomocí knihovny Aspose.Words pro .NET. Tato výkonná knihovna neuvěřitelně usnadňuje správu a automatizaci úloh zpracování dokumentů. Vyzkoušejte ji a uvidíte, jak vám může zefektivnit pracovní postup.

## Často kladené otázky

### Mohu si přizpůsobit vzhled podpisového řádku?
Rozhodně! Můžete upravit různé možnosti v `SignatureLineOptions` aby vyhovovaly vašim potřebám.

### Co když nemám certifikát PFX?
Budete si ho muset pořídit od důvěryhodné certifikační autority. Je nezbytný pro digitální podepisování dokumentů.

### Mohu do dokumentu přidat více řádků podpisu?
Ano, můžete přidat libovolný počet řádků podpisu opakováním procesu vkládání s různými možnostmi.

### Je Aspose.Words pro .NET kompatibilní s .NET Core?
Ano, Aspose.Words pro .NET podporuje .NET Core, takže je všestranný pro různá vývojová prostředí.

### Jak bezpečné jsou digitální podpisy?
Digitální podpisy vytvořené pomocí Aspose.Words jsou vysoce bezpečné, pokud používáte platný a důvěryhodný certifikát.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}