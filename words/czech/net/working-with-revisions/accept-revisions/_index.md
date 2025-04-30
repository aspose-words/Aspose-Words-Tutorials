---
"description": "Zvládněte revize dokumentů s Aspose.Words pro .NET. Naučte se bez námahy sledovat, přijímat a odmítat změny. Zlepšete si své dovednosti ve správě dokumentů."
"linktitle": "Přijmout revize"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přijmout revize"
"url": "/cs/net/working-with-revisions/accept-revisions/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přijmout revize

## Zavedení

Ocitli jste se někdy v bludišti revizí dokumentů a snažili jste se sledovat každou změnu provedenou více přispěvateli? S Aspose.Words pro .NET se správa revizí v dokumentech Word stává hračkou. Tato výkonná knihovna umožňuje vývojářům bez námahy sledovat, přijímat a odmítat změny a zajišťuje, že vaše dokumenty zůstanou organizované a aktuální. V tomto tutoriálu se ponoříme do podrobného procesu zpracování revizí dokumentů pomocí Aspose.Words pro .NET, od inicializace dokumentu až po přijetí všech změn.

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

- Visual Studio nainstalované na vašem počítači.
- .NET framework (nejlépe nejnovější verze).
- Knihovna Aspose.Words pro .NET. Můžete si ji stáhnout. [zde](https://releases.aspose.com/words/net/).
- Základní znalost programování v C#.

Nyní se pojďme podívat na detaily a zjistit, jak zvládneme revize dokumentů pomocí Aspose.Words pro .NET.

## Importovat jmenné prostory

Nejdříve je potřeba importovat potřebné jmenné prostory pro práci s Aspose.Words. Na začátek souboru s kódem přidejte následující direktivy using:

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
```

Rozdělme si proces na zvládnutelné kroky. Každý krok bude podrobně vysvětlen, abyste pochopili každou část kódu.

## Krok 1: Inicializace dokumentu

Pro začátek musíme vytvořit nový dokument a přidat několik odstavců. Tím připravíme půdu pro sledování revizí.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
Body body = doc.FirstSection.Body;
Paragraph para = body.FirstParagraph;

// Přidejte text do prvního odstavce a poté přidejte další dva odstavce.
para.AppendChild(new Run(doc, "Paragraph 1. "));
body.AppendParagraph("Paragraph 2. ");
body.AppendParagraph("Paragraph 3. ");
```

V tomto kroku jsme vytvořili nový dokument a přidali do něj tři odstavce. Tyto odstavce budou sloužit jako základ pro naše sledování revizí.

## Krok 2: Začněte sledovat revize

Dále musíme povolit sledování revizí. To nám umožní zachytit všechny změny provedené v dokumentu.

```csharp
// Začněte sledovat revize.
doc.StartTrackRevisions("John Doe", DateTime.Now);
```

Zavoláním `StartTrackRevisions`umožníme dokumentu sledovat všechny následné změny. Jako parametry se předává jméno autora a aktuální datum.

## Krok 3: Přidání revize

Nyní, když je sledování revizí povoleno, přidejme nový odstavec. Tento přídavek bude označen jako revize.

```csharp
// Tento odstavec je revizí a bude mít nastavený odpovídající příznak „IsInsertRevision“.
para = body.AppendParagraph("Paragraph 4. ");
```

Zde je přidán nový odstavec („Odstavec 4.“). Protože je povoleno sledování revizí, je tento odstavec označen jako revize.

## Krok 4: Odstranění odstavce

Dále odstraníme existující odstavec a budeme sledovat, jak je revize sledována.

```csharp
// Získejte kolekci odstavců dokumentu a odeberte odstavec.
ParagraphCollection paragraphs = body.Paragraphs;
para = paragraphs[2];
para.Remove();
```

V tomto kroku je třetí odstavec odstraněn. Kvůli sledování revizí je toto odstranění zaznamenáno a odstavec je označen k odstranění, nikoli okamžitě odstraněn z dokumentu.

## Krok 5: Přijmout všechny revize

Nakonec přijměme všechny sledované revize a zafixujeme tak změny v dokumentu.

```csharp
// Přijměte všechny revize.
doc.AcceptAllRevisions();
```

Zavoláním `AcceptAllRevisions`, zajišťujeme, aby všechny změny (doplnění a odstranění) byly přijaty a použity v dokumentu. Revize již nejsou označeny a jsou integrovány do dokumentu.

## Krok 6: Zastavení sledování revizí

### Zakázat sledování revizí

Na závěr můžeme zakázat sledování revizí, abychom zastavili zaznamenávání dalších změn.

```csharp
// Zastavit sledování revizí.
doc.StopTrackRevisions();
```

Tento krok zastaví sledování nových změn v dokumentu a všechny následné úpravy budou považovány za běžný obsah.

## Krok 7: Uložte dokument

Nakonec uložte upravený dokument do zadaného adresáře.

```csharp
// Uložte dokument.
doc.Save(dataDir + "WorkingWithRevisions.AcceptRevisions.docx");
```

Uložením dokumentu zajistíme, že budou zachovány všechny naše změny a přijaté revize.

## Závěr

Správa revizí dokumentů může být náročný úkol, ale s Aspose.Words pro .NET se stává přímočarou a efektivní. Dodržováním kroků uvedených v této příručce můžete snadno sledovat, přijímat a odmítat změny ve svých dokumentech Word a zajistit tak, aby vaše dokumenty byly vždy aktuální a přesné. Tak proč čekat? Ponořte se do světa Aspose.Words a zefektivnite správu svých dokumentů ještě dnes!

## Často kladené otázky

### Jak začnu sledovat revize v Aspose.Words pro .NET?

Sledování revizí můžete spustit voláním metody `StartTrackRevisions` metodu na vašem objektu dokumentu a předání jména autora a aktuálního data.

### Mohu kdykoli zastavit sledování revizí?

Ano, sledování revizí můžete zastavit voláním metody `StopTrackRevisions` metodu na vašem objektu dokumentu.

### Jak přijmu všechny revize v dokumentu?

Chcete-li přijmout všechny revize, použijte `AcceptAllRevisions` metodu na vašem objektu dokumentu.

### Mohu odmítnout konkrétní revize?

Ano, konkrétní revize můžete odmítnout tak, že na ně přejdete a použijete `Reject` metoda.

### Kde si mohu stáhnout Aspose.Words pro .NET?

Aspose.Words pro .NET si můžete stáhnout z [odkaz ke stažení](https://releases.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}