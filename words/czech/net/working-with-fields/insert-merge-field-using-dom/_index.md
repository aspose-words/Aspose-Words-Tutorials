---
title: Vložit slučovací pole pomocí DOM
linktitle: Vložit slučovací pole pomocí DOM
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se vkládat a konfigurovat slučovací pole v dokumentech aplikace Word pomocí Aspose.Words for .NET s tímto komplexním, podrobným výukovým programem.
weight: 10
url: /cs/net/working-with-fields/insert-merge-field-using-dom/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložit slučovací pole pomocí DOM

## Zavedení

Pokud pracujete se zpracováním dokumentů v .NET, pravděpodobně jste narazili na Aspose.Words. Tato výkonná knihovna nabízí širokou škálu funkcí pro programovou manipulaci s dokumenty Wordu. V tomto tutoriálu se zaměříme na jednu konkrétní funkci: vložení slučovacího pole pomocí Document Object Model (DOM) v Aspose.Words pro .NET. Tato příručka vás provede každým krokem, od nastavení prostředí až po vložení a aktualizaci slučovacího pole v dokumentu aplikace Word.

## Předpoklady

Než se ponoříte do kódu, ujistěte se, že máte v tomto návodu vše, co potřebujete.

1. Základní znalost C#: Měli byste být spokojeni s programováním v C#.
2. Nainstalované Visual Studio: Ujistěte se, že máte na počítači nainstalované Visual Studio nebo jakékoli jiné IDE C#.
3.  Aspose.Words for .NET: Stáhněte si a nainstalujte nejnovější verzi Aspose.Words pro .NET z webu[Vydání](https://releases.aspose.com/words/net/).
4.  Platná licence: Pokud nemáte licenci, můžete získat a[dočasná licence](https://purchase.aspose.com/temporary-license/) pro hodnocení.

## Krok 1: Nastavte svůj projekt

Za prvé, pojďme nastavit nový projekt ve Visual Studiu.

1. Otevřete Visual Studio.
2. Vytvoření nového projektu: Přejděte na Soubor > Nový > Projekt. Vyberte aplikaci C# Console.
3. Pojmenujte svůj projekt: Dejte projektu smysluplný název a klikněte na Vytvořit.

## Krok 2: Nainstalujte Aspose.Words

Chcete-li používat Aspose.Words, musíte je přidat do svého projektu. To lze provést pomocí Správce balíčků NuGet.

1. Otevřete Správce balíčků NuGet: Klikněte pravým tlačítkem na svůj projekt v Průzkumníku řešení a vyberte Spravovat balíčky NuGet.
2. Hledat Aspose.Words: Ve Správci balíčků NuGet vyhledejte "Apose.Words".
3. Instalace balíčku: Klepnutím na Instalovat přidáte Aspose.Words do svého projektu.

## Krok 3: Import jmenných prostorů

Chcete-li začít používat Aspose.Words, musíte do projektu importovat potřebné jmenné prostory. Můžete to udělat takto:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

## Krok 4: Inicializujte svůj dokument

Nyní, když je vše nastaveno, vytvořte nový dokument aplikace Word a inicializujte DocumentBuilder.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Vytvořte dokument a DocumentBuilder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 5: Přesuňte kurzor na konkrétní odstavec

Dále musíme přesunout kurzor na konkrétní odstavec v dokumentu, kam chceme vložit slučovací pole.

```csharp
Paragraph para = (Paragraph) doc.GetChild(NodeType.Paragraph, 0, true);
builder.MoveTo(para);
```

## Krok 6: Vložte slučovací pole

 Vložení slučovacího pole je jednoduché. Budeme používat`InsertField` metoda`DocumentBuilder` třída.

```csharp
// Vložit pole sloučení pole.
FieldMergeField field = (FieldMergeField)builder.InsertField(FieldType.FieldMergeField, false);
```

## Krok 7: Nakonfigurujte slučovací pole

Po vložení slučovacího pole můžete nastavit různé vlastnosti a nakonfigurovat jej podle svých potřeb.

```csharp
field.FieldName = "Test1";
field.TextBefore = "Test2";
field.TextAfter = "Test3";
field.IsMapped = true;
field.IsVerticalFormatting = true;
```

## Krok 8: Aktualizujte a uložte dokument

Nakonec aktualizujte pole, abyste zajistili použití všech nastavení a uložte dokument.

```csharp
// Aktualizujte pole.
field.Update();

// Uložte dokument.
doc.Save(dataDir + "InsertionChampMergeChamp.docx");
```

## Závěr

Podle těchto kroků můžete snadno vložit a nakonfigurovat slučovací pole v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tento výukový program se zabýval základními kroky od nastavení prostředí až po uložení konečného dokumentu. S Aspose.Words můžete automatizovat složité úlohy zpracování dokumentů, díky čemuž budou vaše aplikace .NET výkonnější a efektivnější.

## FAQ

###  Co je slučovací pole?
Slučovací pole je zástupný symbol v dokumentu, který lze dynamicky nahradit daty ze zdroje dat, jako je databáze nebo soubor CSV.

###  Mohu používat Aspose.Words zdarma?
 Aspose.Words nabízí bezplatnou zkušební verzi, kterou si můžete stáhnout[zde](https://releases.aspose.com/). Pro dlouhodobé používání si budete muset zakoupit licenci.

###  Jak získám dočasnou licenci pro Aspose.Words?
 Dočasnou licenci můžete získat z webu Aspose[zde](https://purchase.aspose.com/temporary-license/).

### Jaké verze .NET jsou podporovány Aspose.Words?
Aspose.Words podporuje několik verzí .NET, včetně .NET Framework, .NET Core a .NET Standard.

###  Kde najdu dokumentaci API pro Aspose.Words?
 K dispozici je dokumentace API[zde](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
