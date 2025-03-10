---
title: Přesunout uzel ve sledovaném dokumentu
linktitle: Přesunout uzel ve sledovaném dokumentu
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se přesouvat uzly ve sledovaném dokumentu Word pomocí Aspose.Words for .NET s naším podrobným průvodcem krok za krokem. Ideální pro vývojáře.
weight: 10
url: /cs/net/working-with-revisions/move-node-in-tracked-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přesunout uzel ve sledovaném dokumentu

## Zavedení

Ahoj, nadšenci Aspose.Words! Pokud jste někdy potřebovali přesunout uzel v dokumentu aplikace Word při sledování revizí, jste na správném místě. Dnes se ponoříme do toho, jak toho dosáhnout pomocí Aspose.Words pro .NET. Nejen, že se naučíte postup krok za krokem, ale také si vyzvednete několik tipů a triků, díky kterým bude manipulace s dokumenty hladká a efektivní.

## Předpoklady

Než si ušpiníme ruce nějakým kódem, ujistěte se, že máte vše, co potřebujete:

-  Aspose.Words pro .NET: Stáhněte si ji[zde](https://releases.aspose.com/words/net/).
- Prostředí .NET: Ujistěte se, že máte nastaveno kompatibilní vývojové prostředí .NET.
- Základní znalosti C#: Tento tutoriál předpokládá, že máte základní znalosti C#.

Máš všechno? Velký! Pojďme k jmenným prostorům, které potřebujeme importovat.

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory. Ty jsou nezbytné pro práci s Aspose.Words a manipulaci s uzly dokumentu.

```csharp
using Aspose.Words;
using System;
```

Dobře, pojďme si tento proces rozdělit na zvládnutelné kroky. Každý krok bude podrobně vysvětlen, aby bylo zajištěno, že porozumíte tomu, co se v každém bodě děje.

## Krok 1: Inicializujte dokument

 Pro začátek musíme inicializovat nový dokument a použít a`DocumentBuilder` přidat nějaké odstavce.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Přidání několika odstavců
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// Zkontrolujte počáteční počet odstavců
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Krok 2: Spusťte sledování revizí

Dále musíme začít se sledováním revizí. To je zásadní, protože nám to umožňuje vidět změny provedené v dokumentu.

```csharp
// Začněte sledovat revize
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Krok 3: Přesun uzlů

Nyní přichází hlavní část našeho úkolu: přesunutí uzlu z jednoho místa na druhé. Přesuneme třetí odstavec a umístíme jej před odstavec první.

```csharp
// Definujte uzel, který se má přesunout, a jeho koncový rozsah
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// Přesuňte uzly v definovaném rozsahu
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## Krok 4: Zastavte sledování revizí

Jakmile jsme přesunuli uzly, musíme zastavit sledování revizí.

```csharp
// Zastavit sledování revizí
doc.StopTrackRevisions();
```

## Krok 5: Uložte dokument

Nakonec uložme náš upravený dokument do zadaného adresáře.

```csharp
// Uložte upravený dokument
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Zadejte konečný počet odstavců
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Závěr

A tady to máte! Úspěšně jste přesunuli uzel ve sledovaném dokumentu pomocí Aspose.Words for .NET. Tato výkonná knihovna usnadňuje programovou manipulaci s dokumenty Wordu. Ať už vytváříte, upravujete nebo sledujete změny, Aspose.Words vám pomůže. Takže do toho a vyzkoušejte to. Šťastné kódování!

## FAQ

### Co je Aspose.Words for .NET?

Aspose.Words for .NET je knihovna tříd pro programovou práci s dokumenty Wordu. Umožňuje vývojářům vytvářet, upravovat, převádět a tisknout dokumenty Wordu v aplikacích .NET.

### Jak mohu sledovat revize v dokumentu aplikace Word pomocí Aspose.Words?

 Chcete-li sledovat revize, použijte`StartTrackRevisions` metoda na`Document` objekt. To povolí sledování revizí a zobrazí všechny změny provedené v dokumentu.

### Mohu v Aspose.Words přesunout více uzlů?

Ano, můžete přesunout více uzlů jejich opakováním a použitím metod jako`InsertBefore` nebo`InsertAfter` abyste je umístili na požadované místo.

### Jak zastavím sledování revizí v Aspose.Words?

 Použijte`StopTrackRevisions` metoda na`Document` objekt zastavit sledování revizí.

### Kde najdu další dokumentaci k Aspose.Words pro .NET?

 Můžete najít podrobnou dokumentaci[zde](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
