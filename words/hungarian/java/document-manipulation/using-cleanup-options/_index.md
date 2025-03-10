---
title: A Cleanup Options használata az Aspose.Words for Java programban
linktitle: A tisztítási beállítások használata
second_title: Aspose.Words Java Document Processing API
description: Növelje a dokumentumok egyértelműségét az Aspose.Words a Java tisztítási opciókkal. Ismerje meg, hogyan távolíthat el üres bekezdéseket, nem használt régiókat stb.
weight: 10
url: /hu/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# A Cleanup Options használata az Aspose.Words for Java programban


## Bevezetés a Cleanup Options használatába az Aspose.Words for Java programban

Ebben az oktatóanyagban megvizsgáljuk, hogyan használhatjuk az Aspose.Words for Java tisztítási beállításait a dokumentumok kezeléséhez és megtisztításához a körlevél-egyesítési folyamat során. A tisztítási beállítások lehetővé teszik a dokumentumtisztítás különféle aspektusainak vezérlését, például az üres bekezdések, a nem használt régiók és egyebek eltávolítását.

## Előfeltételek

 Mielőtt elkezdené, győződjön meg arról, hogy az Aspose.Words for Java könyvtár integrálva van a projektjébe. Letöltheti innen[itt](https://releases.aspose.com/words/java/).

## 1. lépés: Az üres bekezdések eltávolítása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Egyesítési mezők beszúrása
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Állítsa be a tisztítási beállításokat
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Az írásjelekkel ellátott bekezdések tisztításának engedélyezése
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Körlevél végrehajtása
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Mentse el a dokumentumot
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

Ebben a példában új dokumentumot hozunk létre, egyesítési mezőket szúrunk be, és a tisztítási beállításokat az üres bekezdések eltávolítására állítjuk be. Ezenkívül lehetővé tesszük az írásjeleket tartalmazó bekezdések eltávolítását. A körlevél-összevonás végrehajtása után a dokumentum elmentésre kerül a megadott tisztítás alkalmazásával.

## 2. lépés: A nem egyesített régiók eltávolítása

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Állítsa be a tisztítási beállításokat a nem használt régiók eltávolításához
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Levélegyesítés végrehajtása a régiókkal
doc.getMailMerge().executeWithRegions(data);

// Mentse el a dokumentumot
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

Ebben a példában megnyitunk egy meglévő dokumentumot egyesítési régiókkal, beállítjuk a tisztítási beállításokat a nem használt régiók eltávolítására, majd végrehajtjuk a körlevél-összevonást üres adatokkal. Ez a folyamat automatikusan eltávolítja a nem használt régiókat a dokumentumból.

## 3. lépés: Az üres mezők eltávolítása

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Állítsa be a tisztítási beállításokat az üres mezők eltávolításához
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Körlevél végrehajtása
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Mentse el a dokumentumot
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

Ebben a példában megnyitunk egy dokumentumot egyesítési mezőkkel, beállítjuk a tisztítási beállításokat az üres mezők eltávolításához, és végrehajtjuk a körlevél-egyesítést az adatokkal. Az összevonás után az üres mezők törlődnek a dokumentumból.

## 4. lépés: Távolítsa el a nem használt mezőket

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Állítsa be a tisztítási beállításokat a nem használt mezők eltávolításához
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Körlevél végrehajtása
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Mentse el a dokumentumot
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

Ebben a példában megnyitunk egy dokumentumot egyesítési mezőkkel, beállítjuk a tisztítási beállításokat a nem használt mezők eltávolításához, és végrehajtjuk az adatokkal való körlevél-összevonást. Az egyesítés után a fel nem használt mezők törlődnek a dokumentumból.

## 5. lépés: Távolítsa el a tartalmazott mezőket

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Állítsa be a tisztítási beállításokat a tartalmazó mezők eltávolításához
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Körlevél végrehajtása
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Mentse el a dokumentumot
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

Ebben a példában megnyitunk egy dokumentumot egyesítési mezőkkel, beállítjuk a tisztítási beállításokat a tartalmazó mezők eltávolításához, és végrehajtjuk az adatokkal való levélegyesítést. Az összevonás után maguk a mezők törlődnek a dokumentumból.

## 6. lépés: Az üres táblázatsorok eltávolítása

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Állítsa be a tisztítási beállításokat az üres táblázatsorok eltávolításához
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Körlevél végrehajtása
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Mentse el a dokumentumot
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

Ebben a példában megnyitunk egy dokumentumot egy táblázattal és egyesítési mezőkkel, beállítjuk a tisztítási beállításokat az üres táblasorok eltávolításához, és végrehajtjuk a körlevél-összevonást az adatokkal. Az összevonás után az üres táblázatsorok eltávolításra kerülnek a dokumentumból.

## Következtetés

Ebben az oktatóanyagban megtanulta, hogyan használhatja az Aspose.Words for Java törlési beállításait dokumentumok kezeléséhez és tisztításához a körlevél-egyesítési folyamat során. Ezek az opciók finom vezérlést biztosítanak a dokumentumtisztítás felett, lehetővé téve a csiszolt és testreszabott dokumentumok könnyű létrehozását.

## GYIK

### Mik az Aspose.Words for Java tisztítási lehetőségei?

Az Aspose.Words for Java tisztítási beállításai olyan beállítások, amelyek lehetővé teszik a dokumentumtisztítás különféle szempontjainak szabályozását a körlevél-egyesítési folyamat során. Lehetővé teszik a felesleges elemek, például az üres bekezdések, a nem használt régiók és egyebek eltávolítását, így biztosítva, hogy a végleges dokumentum jól strukturált és csiszolt legyen.

### Hogyan távolíthatom el az üres bekezdéseket a dokumentumomból?

 Az üres bekezdések eltávolításához a dokumentumból az Aspose.Words for Java segítségével beállíthatja a`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` opció igazra. Ez automatikusan kiküszöböli azokat a bekezdéseket, amelyeknek nincs tartalmuk, ami tisztább dokumentumot eredményez.

###  Mi a célja a`REMOVE_UNUSED_REGIONS` cleanup option?

 A`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` Az opció a körlevél-összevonási folyamat során a dokumentumok azon régióinak eltávolítására szolgál, amelyek nem rendelkeznek megfelelő adatokkal. Segít megőrizni a dokumentum rendezettségét azáltal, hogy megszabadul a nem használt helyőrzőktől.

### Eltávolíthatom az üres táblázatsorokat a dokumentumból az Aspose.Words for Java segítségével?

 Igen, eltávolíthatja az üres táblázatsorokat a dokumentumból a`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`tisztítási lehetőség igazra. Ez automatikusan törli az összes adatot nem tartalmazó táblázatsort, így biztosítva a jól strukturált táblázatot a dokumentumban.

###  Mi történik, ha beállítom a`REMOVE_CONTAINING_FIELDS` option?

 Beállítása a`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` Az opció eltávolítja a teljes egyesítési mezőt, beleértve a bekezdést is, a dokumentumból a körlevél-egyesítési folyamat során. Ez akkor hasznos, ha el szeretné távolítani az egyesítési mezőket és a hozzájuk tartozó szöveget.

### Hogyan távolíthatom el a fel nem használt egyesítési mezőket a dokumentumomból?

 A nem használt egyesítési mezők dokumentumból való eltávolításához beállíthatja a`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` opció igazra. Ez automatikusan megszünteti azokat az egyesítési mezőket, amelyek nem töltődnek ki a körlevélkészítés során, így tisztább dokumentumot kap.

###  Mi a különbség között`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

 A`REMOVE_EMPTY_FIELDS` Az opció eltávolítja azokat az egyesítési mezőket, amelyek nem tartalmaznak adatokat, vagy üresek a körlevél-egyesítési folyamat során. Másrészt a`REMOVE_UNUSED_FIELDS`Az opció eltávolítja azokat az egyesítési mezőket, amelyek nem töltődnek fel adatokkal az egyesítés során. A közöttük való választás attól függ, hogy el kívánja-e távolítani a tartalom nélküli mezőket, vagy azokat, amelyeket az adott egyesítési művelet során nem használnak.

### Hogyan engedélyezhetem az írásjeleket tartalmazó bekezdések eltávolítását?

 Az írásjeleket tartalmazó bekezdések eltávolításának engedélyezéséhez beállíthatja a`cleanupParagraphsWithPunctuationMarks` opciót igazra állítsa, és adja meg a tisztításkor figyelembe veendő írásjeleket. Ez lehetővé teszi, hogy kifinomultabb dokumentumot hozzon létre a szükségtelen, csak írásjeleket tartalmazó bekezdések eltávolításával.

### Testreszabhatom az Aspose.Words for Java tisztítási beállításait?

Igen, testreszabhatja a tisztítási beállításokat az Ön egyedi igényei szerint. Kiválaszthatja, hogy mely tisztítási beállításokat kívánja alkalmazni, és beállíthatja azokat a dokumentumtisztítási követelményeknek megfelelően, így biztosítva, hogy a végleges dokumentum megfeleljen a kívánt szabványoknak.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
