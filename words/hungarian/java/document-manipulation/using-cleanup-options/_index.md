---
"description": "Növelje dokumentumai érthetőségét az Aspose.Words Java Cleanup beállításaival. Ismerje meg, hogyan távolíthat el üres bekezdéseket, nem használt területeket és egyebeket."
"linktitle": "Tisztítási beállítások használata"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Tisztítási beállítások használata az Aspose.Words for Java programban"
"url": "/hu/java/document-manipulation/using-cleanup-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tisztítási beállítások használata az Aspose.Words for Java programban


## Bevezetés a takarítási beállítások használatába az Aspose.Words for Java programban

Ebben az oktatóanyagban azt vizsgáljuk meg, hogyan használhatjuk az Aspose.Words for Java tisztítási beállításait a dokumentumok kezelésére és tisztítására a körlevelezési folyamat során. A tisztítási beállítások lehetővé teszik a dokumentumtisztítás különböző aspektusainak szabályozását, például az üres bekezdések, a nem használt területek eltávolítását és egyebeket.

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg róla, hogy az Aspose.Words for Java könyvtár integrálva van a projektedbe. Letöltheted innen: [itt](https://releases.aspose.com/words/java/).

## 1. lépés: Üres bekezdések eltávolítása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Egyesítési mezők beszúrása
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Takarítási beállítások megadása
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Írásjelekkel ellátott bekezdések tisztításának engedélyezése
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Körlevél végrehajtása
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Mentse el a dokumentumot
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

Ebben a példában létrehozunk egy új dokumentumot, beszúrunk egyesítési mezőket, és beállítjuk a tisztítási beállításokat az üres bekezdések eltávolításához. Ezenkívül engedélyezzük az írásjeleket tartalmazó bekezdések eltávolítását. A körlevél végrehajtása után a dokumentum a megadott tisztítási beállításokkal kerül mentésre.

## 2. lépés: Nem egyesített régiók eltávolítása

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Tisztítási beállítások beállítása a nem használt területek eltávolításához
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Körlevél végrehajtása régiókkal
doc.getMailMerge().executeWithRegions(data);

// Mentse el a dokumentumot
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

Ebben a példában megnyitunk egy meglévő dokumentumot egyesítési régiókkal, beállítjuk a tisztítási beállításokat a nem használt régiók eltávolítására, majd végrehajtjuk a körlevélkészítést üres adatokkal. Ez a folyamat automatikusan eltávolítja a nem használt régiókat a dokumentumból.

## 3. lépés: Üres mezők eltávolítása

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Tisztítási beállítások megadása az üres mezők eltávolításához
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Körlevél végrehajtása
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Mentse el a dokumentumot
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

Ebben a példában megnyitunk egy dokumentumot, amely tartalmaz egyesítési mezőket, beállítjuk a tisztítási beállításokat az üres mezők eltávolítására, és végrehajtjuk a körlevélkészítést az adatokkal. Az egyesítés után az üres mezők eltávolításra kerülnek a dokumentumból.

## 4. lépés: Nem használt mezők eltávolítása

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Tisztítási beállítások beállítása a nem használt mezők eltávolításához
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Körlevél végrehajtása
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Mentse el a dokumentumot
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

Ebben a példában megnyitunk egy dokumentumot, amely tartalmaz egyesítési mezőket, beállítjuk a tisztítási beállításokat a nem használt mezők eltávolításához, és végrehajtjuk a körlevélkészítést az adatokkal. Az egyesítés után a nem használt mezők eltávolításra kerülnek a dokumentumból.

## 5. lépés: Tartalmazó mezők eltávolítása

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Tisztítási beállítások beállítása a mezők eltávolításához
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Körlevél végrehajtása
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Mentse el a dokumentumot
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

Ebben a példában megnyitunk egy dokumentumot, amely tartalmaz egyesítési mezőket, beállítjuk a tisztítási beállításokat a mezőket tartalmazó mezők eltávolítására, és végrehajtjuk az adatokkal való körlevélkészítést. Az egyesítés után maguk a mezők is eltávolításra kerülnek a dokumentumból.

## 6. lépés: Üres táblázatsorok eltávolítása

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Tisztítási beállítások megadása az üres táblázatsorok eltávolításához
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Körlevél végrehajtása
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Mentse el a dokumentumot
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

Ebben a példában megnyitunk egy táblázatot és egyesítési mezőket tartalmazó dokumentumot, beállítjuk a tisztítási beállításokat az üres táblázatsorok eltávolításához, és végrehajtjuk a körlevélkészítést az adatokkal. Az egyesítés után az üres táblázatsorok eltávolításra kerülnek a dokumentumból.

## Következtetés

Ebben az oktatóanyagban megtanultad, hogyan használhatod az Aspose.Words for Java tisztítási beállításait a dokumentumok kezeléséhez és tisztításához a körlevelezési folyamat során. Ezek a beállítások részletes szabályozást biztosítanak a dokumentumok tisztítása felett, lehetővé téve a letisztult és testreszabott dokumentumok egyszerű létrehozását.

## GYIK

### Milyen tisztítási lehetőségek vannak az Aspose.Words Java-ban?

Az Aspose.Words for Java takarítási beállításai lehetővé teszik a dokumentumtisztítás különböző aspektusainak szabályozását a körlevélkészítési folyamat során. Lehetővé teszik a felesleges elemek, például az üres bekezdések, a nem használt területek és egyebek eltávolítását, biztosítva, hogy a végső dokumentum jól strukturált és kidolgozott legyen.

### Hogyan tudom eltávolítani az üres bekezdéseket a dokumentumomból?

Az Aspose.Words for Java használatával üres bekezdések eltávolításához beállíthatja a következőt: `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` opciót igazra. Ez automatikusan eltávolítja a tartalom nélküli bekezdéseket, ami tisztább dokumentumot eredményez.

### Mi a célja a `REMOVE_UNUSED_REGIONS` takarítási lehetőség?

A `MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` A beállítással a körlevélkészítés során eltávolíthatók a dokumentum azon régiói, amelyekhez nem tartozik adat. Segít a dokumentum rendezetten tartásában a nem használt helyőrzők eltávolításával.

### Eltávolíthatok üres táblázatsorokat egy dokumentumból az Aspose.Words for Java használatával?

Igen, a beállítással eltávolíthatja az üres táblázatsorokat egy dokumentumból. `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS` cleanup opciót igazra kell állítani. Ez automatikusan törli az adatokat nem tartalmazó táblázatsorokat, biztosítva ezzel a dokumentumban a jól strukturált táblázatot.

### Mi történik, ha beállítom a `REMOVE_CONTAINING_FIELDS` opció?

A beállítás `MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` A „körlevél” opció eltávolítja a teljes körlevélmezőt a dokumentumból a körlevélkészítés során, beleértve a benne lévő bekezdést is. Ez akkor hasznos, ha el szeretné távolítani az körlevélmezőket és a hozzájuk tartozó szöveget.

### Hogyan távolíthatok el nem használt mezőket a dokumentumomból?

A nem használt egyesítési mezők eltávolításához egy dokumentumból beállíthatja a `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` opciót igaz értékre állítja. Ez automatikusan eltávolítja azokat az egyesítési mezőket, amelyek nem kerülnek kitöltésre a körlevelezés során, így tisztább dokumentumot eredményez.

### Mi a különbség a ... és ... között? `REMOVE_EMPTY_FIELDS` és `REMOVE_UNUSED_FIELDS` takarítási lehetőségek?

A `REMOVE_EMPTY_FIELDS` opció eltávolítja az adatokat nem tartalmazó vagy üres mezőket a körlevélkészítési folyamat során. Másrészt a `REMOVE_UNUSED_FIELDS` Az egyesítési opció eltávolítja azokat az egyesítési mezőket, amelyeket az egyesítés során nem töltöttek ki adatokkal. A választás attól függ, hogy a tartalom nélküli mezőket vagy a konkrét egyesítési műveletben fel nem használt mezőket szeretné-e eltávolítani.

### Hogyan engedélyezhetem az írásjeleket tartalmazó bekezdések eltávolítását?

Az írásjeleket tartalmazó bekezdések eltávolításának engedélyezéséhez beállíthatja a `cleanupParagraphsWithPunctuationMarks` opciót igazra kell állítani, és meg kell adni a tisztítás során figyelembe veendő írásjeleket. Ez lehetővé teszi egy finomabb dokumentum létrehozását a felesleges, csak írásjeleket tartalmazó bekezdések eltávolításával.

### Testreszabhatom a tisztítási beállításokat az Aspose.Words for Java fájlban?

Igen, testreszabhatja a tisztítási beállításokat az Ön igényei szerint. Kiválaszthatja, hogy mely tisztítási beállításokat alkalmazza, és konfigurálhatja azokat a dokumentumtisztítási követelményeinek megfelelően, biztosítva, hogy a végső dokumentum megfeleljen a kívánt szabványoknak.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}