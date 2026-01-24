---
date: 2026-01-24
description: Ismerje meg, hogyan lehet XML adatokat egyesíteni az Aspose.Words for
  Java-val, automatizálni a dokumentumgenerálást Java-ban, és Mustache szintaxist
  használni dinamikus dokumentumokhoz.
linktitle: Using XML Data
second_title: Aspose.Words Java Document Processing API
title: Hogyan egyesítsük az XML-t az Aspose.Words for Java-ban
url: /hu/java/document-manipulation/using-xml-data/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan egyesítsük az XML-t az Aspose.Words for Java-ban

Ebben az átfogó útmutatóban megtudja, **hogyan egyesítsük az XML** adatokat az Aspose.Words for Java segítségével. Áttekintjük az egyszerű és a beágyazott mail‑merge forgatókönyveket, megmutatjuk, **hogyan használjuk a Mustache szintaxist**, és elmagyarázzuk, **hogyan automatizáljuk a dokumentumgenerálást Java‑stílusú projektekben**. A végére képes lesz személyre szabott Word‑dokumentumokat generálni XML forrásokból néhány kódsorral.

## Gyors válaszok
- **Mi a fő osztály a mail merge‑hez?** `Document` és annak `MailMerge` tulajdonsága.  
- **Egyesíthetek beágyazott XML‑táblákat?** Igen – használja a `executeWithRegions`‑t hierarchikus adatokhoz.  
- **Támogatott a Mustache szintaxis?** Engedélyezze a `setUseNonMergeFields(true)`‑val.  
- **Szükség van licencre a termeléshez?** Egy kereskedelmi Aspose.Words licenc szükséges.  
- **Melyik Java verzió kompatibilis?** A Java 8+ és későbbi verziók teljesen támogatottak.

## Mi az az XML Mail Merge az Aspose.Words‑ben?
Az XML mail merge lehetővé teszi, hogy XML‑alapú adatkészleteket kössünk a Word sablon helyőrzőihez. A motor minden helyőrzőt a megfelelő XML‑csomópont értékével helyettesít, így manuális szerkesztés nélkül kész dokumentumot kapunk.

## Miért használjuk az Aspose.Words‑t XML‑alapú dokumentumgeneráláshoz?
- **Automatizálja a dokumentumgenerálást Java** projektekben, Microsoft Office függőség nélkül.  
- **Támogatja a komplex hierarchiákat** – beágyazott táblák, ismétlődő szakaszok és feltételes tartalom.  
- **Mustache szintaxis** rugalmas, nem‑merge‑field helyőrzőket biztosít a fejlett sablonoláshoz.  
- **Keresztplatformos** – Windows, Linux és macOS rendszereken egyaránt működik.

## Előfeltételek

Mielőtt elkezdenénk, győződjön meg róla, hogy a következők rendelkezésre állnak:

- [Aspose.Words for Java](https://products.aspose.com/words/java/) telepítve (a legújabb verzió).  
- Minta XML‑fájlok ügyfelekről, rendelvekről és szállítókról (a bemutató a `Mail merge data - Customers.xml`, `Orders.xml` és `Vendors.xml` fájlokat használja).  
- Word sablon dokumentumok, amelyek tartalmazx`, `Invoice.docx`, `Vendor.docx`).  

## Hogyan egyesítsük az XML‑t – Alap mail merge

Az alap mail merge egyetlen XML‑táblát húz be egy Word sablonba. Kövesse az alábbi lépéseket:

1. Töltse be az XML‑fájlt egy `DataSet`‑be.  
2. Nyissa meg a cél Word dokumentumot.  
3. Hajtsa végre a merge‑t a tábla nevével.  
4. Mentse el az egyesített dokumentumot.

```java
DataSet customersDs = new DataSet();
customersDs.readXml("Your Directory Path" + "Mail merge data - Customers.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Registration complete.docx");
doc.getMailMerge().execute(customersDs.getTables().get("Customer"));
doc.save("Your Directory Path" + "BasicMailMerge.docx");
```

**Pro tipp:** Tartsa az XML‑struktúrát laposra az egyszerű merge‑ekhez – minden tábla közvetlenül egy merge mezőcsoporthoz kell, hogy legyen rendelve.

## Hogyan egyesítsük az XML‑t – Beágyazott mail merge

Ha az XML szülő‑gyermek kapcsolatokat tartalmaz (pl. rendelések sorokkal), beágyazott merge‑re van szükség. Az `executeWithRegions` metódus rekurzívan dolgozza fel a régiókat.

1. Töltse be a hierarchikus XML‑t egy `DataSet`‑be.  
2. Tiltsa le a szóközök levágását, ha pontos formázásra van szükség.  
3. Hívja meg az `executeWithRegions`‑t a beágyazott táblák kezeléséhez.  
4. Mentse el az eredményt.

```java
DataSet pizzaDs = new DataSet();
pizzaDs.readXml("Your Directory Path" + "Mail merge data - Orders.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Invoice.docx");
doc.getMailMerge().setTrimWhitespaces(false);
doc.getMailMerge().executeWithRegions(pizzaDs);
doc.save("Your Directory Path" + "NestedMailMerge.docx");
```

**Gyakori hibaforrás:** Ha elfelejti beállítani a `setTrimWhitespaces(false)`‑t, akkor nem kívánt szóközök jelenhetnek meg a végdokumentumban, különösen pénznem vagy numerikus mezők esetén.

## Mustache szintaxis használata DataSet‑tel

A Mustache szintaxis lehetővé teszi, hogy nem‑merge‑field helyőrzőket (pl. `{{CustomerName}}`) ágyazzunk be a sablonba. Engedélyezze, majd futtassa a régió‑alapú merge‑t a szállító XML‑t.  
. Hajtsa végre a merge‑t régiókkal.  
4. Mentse el a kimenetet.

```java
DataSet ds = new DataSet();
ds.readXml("Your Directory Path" + "Mail merge data - Vendors.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Vendor.docx");
doc.getMailMerge().setUseNonMergeFields(true);
doc.getMailMerge().executeWithRegions(ds);
doc.save("Your Directory Path" + "MustacheSyntaxUsingDataSet.docx");
```

**Miért használjunk Mustache‑t?** Tiszta, nyelvfüggetlen módot biztosít az adatok hivatkozására, így a sablonok könnyebben olvashatóak és karbantarthatóak, különösen **XML‑vezérelt dokumentumgenerálás** esetén.

## Gyakori problémák és megoldások

| Probléma | Megoldás |
|----------|----------|
| Az XML csomópontok nem egyeznek a merge mezőkkel | Ellenőrizze, hogy az XML elemnevek pontosan megegyeznek a merge mezőnevekkel (kis‑nagybetű érzékeny). |
| Szóközök jelennek meg a merge‑elt értékek körül | Használja a `doc.getMailMerge().setTrimWhitespaces(false)`‑t az eredeti szóközök megőrzéséhez. |
| A beágyazott táblák figyelmen kívül maradnak | Győződjön meg róla, hogy a szülő tábla régiója definiálva van a sablonban (pl. `{{#Orders}}| A Mustache helyőrzők nem kerülnek helyettesítésre | Hívja meg a `setUseNonMergeFields(true)`‑t a merge végrehajtása előtt. |

## GYIK

### Hogyan készítsem elő az XML adatokat a mail merge‑hez?

Győződjön meg róla, hogy az XML táblázatos szerkezetet követ, ahol minden `<TableName>` elem sorokat (`<Row>`) és oszlopokat tartalmaz, amelyek megfelelnek a Word sablon merge mezőinek.

### Testreszabhatom a trim viselkedést a mail merge értékeknél?

Igen. Használja a `doc.getMailMerge().setTrimWhitespaces(false)`‑t a vezető és záró szóközök pontos megtartásához, ahogy az XML‑ben szerepelnek.

### Mi a Mustache szintaxis, és mikor érdemes használni?

A Mustache szintaxis (`{{FieldName}}`) rugalmas helyőrzőket biztosít, amelyek nem korlátozódnak a hagyományos merge mezőkre. Engedélyezze a `setUseNonMergeFields(true)`‑t, ha tisztább sablont szeretne, vagy el akarja választani az adatlogikát a Word mezőkódjaitól.

### Hogyan automatizálhatom a dokumentumgenerálást Java projektekben ezzel a megközelítéssel?

Integrálja a fenti kódrészleteket a szolgáltatási rétegbe, olvassa be az XML‑t adatbázisokból vagy API‑kból, és hívja meg a merge rutinot minden alkalommal, amikor új dokumentumra van szükség (pl. számla generálás, szerződéskészítés).

### Szükséges-e kereskedelmi licenc a termeléshez?

Igen, az Aspose.Words-nek érvényes licencre van szüksége a termelési környezetben. Egy ingyenes ideiglenes licenc elérhető értékeléshez.

---

**Utoljára frissítve:** 2026-01-24  
**Tesztelt verzió:** Aspose.Words for Java (legújabb kiadás)  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}