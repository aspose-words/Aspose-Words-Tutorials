---
title: Vytvořte nový řádek podpisu a nastavte ID poskytovatele
linktitle: Vytvořte nový řádek podpisu a nastavte ID poskytovatele
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak vytvořit nový řádek podpisu a nastavit ID poskytovatele v dokumentech aplikace Word pomocí Aspose.Words for .NET. Průvodce krok za krokem.
weight: 10
url: /cs/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte nový řádek podpisu a nastavte ID poskytovatele

## Zavedení

Ahoj, tech nadšenci! Přemýšleli jste někdy, jak programově přidat řádek podpisu do dokumentů aplikace Word? No, dnes se ponoříme právě do toho pomocí Aspose.Words pro .NET. Tato příručka vás provede každým krokem, takže vytvoření nového řádku podpisu a nastavení ID poskytovatele ve vašich dokumentech aplikace Word bude snadné. Ať už automatizujete zpracování dokumentů nebo jen chcete zefektivnit svůj pracovní postup, tento tutoriál vám pomůže.

## Předpoklady

Než si ušpiníme ruce, ujistěte se, že máme vše, co potřebujeme:

1.  Aspose.Words for .NET: Pokud jste to ještě neudělali, stáhněte si ji[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí C#.
3. .NET Framework: Ujistěte se, že máte nainstalované rozhraní .NET Framework.
4. Certifikát PFX: K podepisování dokumentů budete potřebovat certifikát PFX. Můžete jej získat od důvěryhodné certifikační autority.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory do vašeho projektu C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Dobře, pojďme se pustit do toho natvrdlého. Zde je podrobný rozpis každého kroku pro vytvoření nového řádku podpisu a nastavení ID poskytovatele.

## Krok 1: Vytvořte nový dokument

Chcete-li začít, musíme vytvořit nový dokument aplikace Word. Toto bude plátno pro naši podpisovou řadu.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 V tomto úryvku inicializujeme nový`Document` a a`DocumentBuilder` . The`DocumentBuilder` nám pomáhá přidávat prvky do našeho dokumentu.

## Krok 2: Definujte možnosti podpisové linky

Dále definujeme možnosti pro náš podpisový řádek. To zahrnuje jméno podepsaného, titul, e-mail a další podrobnosti.

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

Tyto možnosti přizpůsobují linii podpisu, činí ji jasnou a profesionální.

## Krok 3: Vložte řádek podpisu

S našimi nastavenými možnostmi nyní můžeme vložit řádek podpisu do dokumentu.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 Tady,`InsertSignatureLine` metoda přidá řádek podpisu a my mu přiřadíme jedinečné ID poskytovatele.

## Krok 4: Uložte dokument

Po vložení řádku podpisu dokument uložíme.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Tím se dokument uloží s nově přidaným řádkem podpisu.

## Krok 5: Nastavte možnosti podepisování

Nyní musíme nastavit možnosti pro podepisování dokumentu. To zahrnuje ID řádku podpisu, ID poskytovatele, komentáře a čas podpisu.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Tyto možnosti zajišťují, že dokument je podepsán se správnými detaily.

## Krok 6: Vytvořte držitele certifikátu

K podpisu dokumentu použijeme certifikát PFX. Vytvořme pro něj držitele certifikátu.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Nezapomeňte vyměnit`"morzal.pfx"` s vaším skutečným souborem certifikátu a`"aw"` s heslem k certifikátu.

## Krok 7: Podepište dokument

Nakonec dokument podepíšeme pomocí nástroje pro digitální podpis.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Tím se dokument podepíše a uloží jako nový soubor.

## Závěr

A tady to máte! Úspěšně jste vytvořili nový řádek podpisu a nastavili ID poskytovatele v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato výkonná knihovna neuvěřitelně usnadňuje správu a automatizaci úloh zpracování dokumentů. Vyzkoušejte to a uvidíte, jak to může zefektivnit váš pracovní postup.

## FAQ

### Mohu přizpůsobit vzhled řádku podpisu?
 Absolutně! Můžete vyladit různé možnosti v`SignatureLineOptions`aby vyhovoval vašim potřebám.

### Co když nemám certifikát PFX?
Budete jej muset získat od důvěryhodné certifikační autority. Je to nezbytné pro digitální podepisování dokumentů.

### Mohu do dokumentu přidat více řádků podpisu?
Ano, můžete přidat tolik řádků podpisu, kolik potřebujete, opakováním procesu vkládání s různými možnostmi.

### Je Aspose.Words for .NET kompatibilní s .NET Core?
Ano, Aspose.Words for .NET podporuje .NET Core, takže je univerzální pro různá vývojová prostředí.

### Jak bezpečné jsou digitální podpisy?
Digitální podpisy vytvořené pomocí Aspose.Words jsou vysoce bezpečné za předpokladu, že používáte platný a důvěryhodný certifikát.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
