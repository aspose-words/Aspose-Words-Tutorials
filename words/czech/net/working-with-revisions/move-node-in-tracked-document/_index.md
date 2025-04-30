---
"description": "Naučte se, jak přesouvat uzly ve sledovaném dokumentu Wordu pomocí Aspose.Words pro .NET s naším podrobným návodem krok za krokem. Ideální pro vývojáře."
"linktitle": "Přesunout uzel ve sledovaném dokumentu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přesunout uzel ve sledovaném dokumentu"
"url": "/cs/net/working-with-revisions/move-node-in-tracked-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přesunout uzel ve sledovaném dokumentu

## Zavedení

Ahoj, nadšenci do Aspose.Words! Pokud jste někdy potřebovali přesunout uzel v dokumentu Wordu a zároveň sledovat revize, jste na správném místě. Dnes se ponoříme do toho, jak toho dosáhnout pomocí Aspose.Words pro .NET. Nejenže se naučíte postup krok za krokem, ale také se dozvíte několik tipů a triků, jak manipulaci s dokumenty zefektivnit a zefektivnit.

## Předpoklady

Než se pustíme do kódování, ujistěme se, že máte vše potřebné:

- Aspose.Words pro .NET: Stáhněte si jej [zde](https://releases.aspose.com/words/net/).
- Prostředí .NET: Ujistěte se, že máte nastavené kompatibilní vývojové prostředí .NET.
- Základní znalost jazyka C#: Tento tutoriál předpokládá, že máte základní znalosti jazyka C#.

Máte všechno hotovo? Skvělé! Pojďme se přesunout k jmenným prostorům, které potřebujeme importovat.

## Importovat jmenné prostory

Nejdříve musíme importovat potřebné jmenné prostory. Ty jsou nezbytné pro práci s Aspose.Words a manipulaci s uzly dokumentů.

```csharp
using Aspose.Words;
using System;
```

Dobře, rozdělme si proces na zvládnutelné kroky. Každý krok bude podrobně vysvětlen, abyste pochopili, co se v každém okamžiku děje.

## Krok 1: Inicializace dokumentu

Pro začátek musíme inicializovat nový dokument a použít `DocumentBuilder` přidat nějaké odstavce.

```csharp
// Cesta k adresáři s dokumenty.
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

## Krok 2: Začněte sledovat revize

Dále musíme začít sledovat revize. To je klíčové, protože nám to umožňuje vidět změny provedené v dokumentu.

```csharp
// Začít sledovat revize
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Krok 3: Přesun uzlů

Nyní přichází na řadu klíčová část našeho úkolu: přesunutí uzlu z jednoho místa na druhé. Přesuneme třetí odstavec a umístíme ho před první odstavec.

```csharp
// Definujte uzel, který má být přesunut, a jeho koncový rozsah
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// Přesunout uzly v rámci definovaného rozsahu
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## Krok 4: Zastavení sledování revizí

Jakmile přesuneme uzly, musíme přestat sledovat revize.

```csharp
// Zastavit sledování revizí
doc.StopTrackRevisions();
```

## Krok 5: Uložte dokument

Nakonec uložme upravený dokument do zadaného adresáře.

```csharp
// Uložit upravený dokument
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Vypište konečný počet odstavců
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Závěr

A tady to máte! Úspěšně jste přesunuli uzel ve sledovaném dokumentu pomocí Aspose.Words pro .NET. Tato výkonná knihovna usnadňuje programovou manipulaci s dokumenty Wordu. Ať už vytváříte, upravujete nebo sledujete změny, Aspose.Words vám s tím pomůže. Tak se do toho pusťte. Hodně štěstí při programování!

## Často kladené otázky

### Co je Aspose.Words pro .NET?

Aspose.Words pro .NET je knihovna tříd pro programovou práci s dokumenty Wordu. Umožňuje vývojářům vytvářet, upravovat, převádět a tisknout dokumenty Wordu v aplikacích .NET.

### Jak mohu sledovat revize v dokumentu Word pomocí Aspose.Words?

Pro sledování revizí použijte `StartTrackRevisions` metoda na `Document` objekt. To umožní sledování revizí a zobrazení všech provedených změn v dokumentu.

### Mohu v Aspose.Words přesunout více uzlů?

Ano, můžete přesouvat více uzlů iterací nad nimi a použitím metod jako `InsertBefneboe` or `InsertAfter` aby je umístili na požadované místo.

### Jak zastavím sledování revizí v Aspose.Words?

Použijte `StopTrackRevisions` metoda na `Document` objekt pro zastavení sledování revizí.

### Kde najdu další dokumentaci k Aspose.Words pro .NET?

Podrobnou dokumentaci naleznete [zde](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}