---
"description": "Naučte se, jak vkládat a konfigurovat slučovací pole v dokumentech Wordu pomocí Aspose.Words pro .NET v tomto komplexním návodu krok za krokem."
"linktitle": "Vložení slučovacího pole pomocí DOM"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vložení slučovacího pole pomocí DOM"
"url": "/cs/net/working-with-fields/insert-merge-field-using-dom/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložení slučovacího pole pomocí DOM

## Zavedení

Pokud pracujete se zpracováním dokumentů v .NET, pravděpodobně jste se setkali s knihovnou Aspose.Words. Tato výkonná knihovna nabízí širokou škálu funkcí pro programovou manipulaci s dokumenty Wordu. V tomto tutoriálu se zaměříme na jednu konkrétní funkci: vkládání slučovacího pole pomocí modelu objektů dokumentu (DOM) v knihovně Aspose.Words pro .NET. Tato příručka vás provede každým krokem, od nastavení prostředí až po vkládání a aktualizaci slučovacího pole v dokumentu Wordu.

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte vše, co potřebujete k dodržování tohoto tutoriálu.

1. Základní znalost C#: Měli byste se orientovat v programování v C#.
2. Nainstalované Visual Studio: Ujistěte se, že máte na počítači nainstalované Visual Studio nebo jiné vývojové prostředí pro jazyk C#.
3. Aspose.Words pro .NET: Stáhněte a nainstalujte nejnovější verzi Aspose.Words pro .NET z [Vydání](https://releases.aspose.com/words/net/).
4. Platná licence: Pokud licenci nemáte, můžete si ji pořídit [dočasná licence](https://purchase.aspose.com/temporary-license/) pro hodnocení.

## Krok 1: Nastavení projektu

Nejdříve si nastavme nový projekt ve Visual Studiu.

1. Otevřete Visual Studio.
2. Vytvoření nového projektu: Přejděte do nabídky Soubor > Nový > Projekt. Vyberte konzolovou aplikaci C#.
3. Pojmenujte svůj projekt: Dejte projektu smysluplný název a klikněte na Vytvořit.

## Krok 2: Instalace Aspose.Words

Chcete-li používat Aspose.Words, musíte jej přidat do svého projektu. To lze provést pomocí Správce balíčků NuGet.

1. Otevřete Správce balíčků NuGet: V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a poté vyberte možnost Spravovat balíčky NuGet.
2. Vyhledejte Aspose.Words: Ve Správci balíčků NuGet vyhledejte „Aspose.Words“.
3. Instalace balíčku: Kliknutím na tlačítko Instalovat přidáte Aspose.Words do svého projektu.

## Krok 3: Import jmenných prostorů

Abyste mohli začít používat Aspose.Words, musíte do svého projektu importovat potřebné jmenné prostory. Zde je návod, jak to udělat:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

## Krok 4: Inicializace dokumentu

Nyní, když je vše nastaveno, vytvořme nový dokument Wordu a inicializujeme DocumentBuilder.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Vytvořte dokument a nástroj DocumentBuilder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 5: Přesunutí kurzoru na konkrétní odstavec

Dále musíme přesunout kurzor na konkrétní odstavec v dokumentu, kam chceme vložit slučovací pole.

```csharp
Paragraph para = (Paragraph) doc.GetChild(NodeType.Paragraph, 0, true);
builder.MoveTo(para);
```

## Krok 6: Vložení slučovacího pole

Vložení slučovacího pole je jednoduché. Použijeme `InsertField` metoda `DocumentBuilder` třída.

```csharp
// Vložit pole slučovacího pole.
FieldMergeField field = (FieldMergeField)builder.InsertField(FieldType.FieldMergeField, false);
```

## Krok 7: Konfigurace slučovacího pole

Po vložení slučovacího pole můžete nastavit různé vlastnosti a konfigurovat ho podle svých potřeb.

```csharp
field.FieldName = "Test1";
field.TextBefore = "Test2";
field.TextAfter = "Test3";
field.IsMapped = true;
field.IsVerticalFormatting = true;
```

## Krok 8: Aktualizace a uložení dokumentu

Nakonec aktualizujte pole, abyste se ujistili, že jsou použita všechna nastavení, a uložte dokument.

```csharp
// Aktualizujte pole.
field.Update();

// Uložte dokument.
doc.Save(dataDir + "InsertionChampMergeChamp.docx");
```

## Závěr

Pomocí těchto kroků můžete snadno vkládat a konfigurovat slučovací pole v dokumentu Word pomocí Aspose.Words pro .NET. Tento tutoriál pokrýval základní kroky od nastavení prostředí až po uložení finálního dokumentu. S Aspose.Words můžete automatizovat složité úlohy zpracování dokumentů, čímž se vaše aplikace .NET stanou výkonnějšími a efektivnějšími.

## Často kladené otázky

###  Co je to slučovací pole?
Slučovací pole je zástupný symbol v dokumentu, který lze dynamicky nahradit daty ze zdroje dat, jako je databáze nebo soubor CSV.

###  Mohu používat Aspose.Words zdarma?
Aspose.Words nabízí bezplatnou zkušební verzi, kterou si můžete stáhnout. [zde](https://releases.aspose.com/)Pro dlouhodobé používání si budete muset zakoupit licenci.

###  Jak získám dočasnou licenci pro Aspose.Words?
Dočasnou licenci můžete získat na webových stránkách Aspose. [zde](https://purchase.aspose.com/temporary-license/).

### Jaké verze .NET podporuje Aspose.Words?
Aspose.Words podporuje více verzí .NET, včetně .NET Framework, .NET Core a .NET Standard.

###  Kde najdu dokumentaci k API pro Aspose.Words?
Dokumentace k API je k dispozici [zde](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}