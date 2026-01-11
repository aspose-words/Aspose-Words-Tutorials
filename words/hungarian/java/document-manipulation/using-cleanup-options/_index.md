---
date: 2026-01-11
description: Ismerje meg, hogyan tisztíthatja meg a Word-dokumentumot az Aspose.Words
  for Java tisztítási beállításaival, beleértve az üres bekezdések, üres táblázatsorok
  és fel nem használt mezők eltávolítását.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Word-dokumentum tisztítása az Aspose.Words takarítási beállításokkal (Java)
url: /hu/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum tisztítása Aspose.Words takarítási beállításokkal (Java)

Ebben az útmutatóban megismerheti, hogyan **tisztíthatja meg a Word dokumentum** fájlokat az Aspose.Words for Java segítségével. Akár számlákat, szerződéseket vagy tömeges levélösszevonási jelentéseket generál, a nem kívánt üres bekezdések, fel nem használt mezők vagy üres táblázatsorok a végső kimenetet amatőr módúvá tehetik. Lépésről lépésre végigvezetjük minden takarítási beállításon, megmutatjuk a pontos kódot, és elmagyarázzuk, *miért* fontos minden beállítás, hogy minden alkalommal kifinomult dokumentumokat készíthessen.

## Gyors válaszok
- **Mi jelent a “Word dokumentum tisztítása”?** Üres bekezdések, fel nem használt összevonási régiók, üres táblázatsorok és egyéb felesleges elemek eltávolítása a levélösszevonási művelet után.  
- **Melyik takarítási beállítás távolítja el az üres bekezdéseket?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **Hogyan törölhetem az üres táblázatsorokat?** Használja a `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`-t.  
- **Eltávolíthatók a soha fel nem töltött mezők?** Igen – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` vagy `REMOVE_EMPTY_FIELDS`.  
- **Szükséges licenc a példák futtatásához?** Egy ingyenes próba verzió elegendő értékeléshez; a gyártási használathoz kereskedelmi licenc szükséges.

## Mi az a “Word dokumentum tisztítása” a levélösszevonás kontextusában?
Amikor levélösszevonást hajt végre, az Aspose.Words adatokat illeszt be az összevonási mezőkbe és régiókba. Ha egyes mezők `null` vagy üres karakterláncot kapnak, a dokumentumban elhagyott bekezdések, üres táblázatok vagy helyőrző régiók maradhatnak. A **takarítási beállítások** automatikusan eltávolítják ezeket a maradványokat, egy tiszta, nyomtatásra kész dokumentumot hagyva.

## Miért használjunk takarítási beállításokat?
- **Professzionális megjelenés:** Nincsenek üres sorok vagy árva táblázatok.  
- **Kisebb fájlméret:** A fel nem használt elemek eltávolítása csökkenti a dokumentum súlyát.  
- **Egyszerűbb további feldolgozás:** A tiszta dokumentumok könnyebben konvertálhatók PDF, HTML vagy más formátumokra.  
- **Időmegtakarítás:** Egy soros beállítások helyettesítik a kézi utófeldolgozó szkripteket.

## Előfeltételek
- Java fejlesztői környezet (JDK 8+).  
- Aspose.Words for Java könyvtár – töltse le [innen](https://releases.aspose.com/words/java/).  
- Alapvető ismeretek a levélösszevonás koncepcióiról.

## Lépésről‑lépésre útmutató

### 1. lépés: Üres bekezdések eltávolítása (Java)
Először bemutatjuk, hogyan lehet eltávolítani azokat a bekezdéseket, amelyek nem tartalmaznak látható szöveget. Ez különösen hasznos, ha egy összevonási mező `null` értékre kerül.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**Mi történik itt?**  
- A `REMOVE_EMPTY_PARAGRAPHS` azt mondja az Aspose.Words-nek, hogy távolítson el minden bekezdést, amely a összevonás után üres marad.  
- A `cleanupParagraphsWithPunctuationMarks` engedélyezése továbbá eltávolítja azokat a bekezdéseket, amelyek csak központozási jeleket tartalmaznak (pl. “?”).

### 2. lépés: Nem összevont régiók eltávolítása
Ha egy levélösszevonási régiónak nincs megfelelő adata, teljesen eldobhatja.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**Miért fontos:**  
A fel nem használt régiók gyakran üres szakaszokat vagy elhagyott címsorokat hagynak. A `REMOVE_UNUSED_REGIONS` jelző automatikusan megtisztítja őket.

### 3. lépés: Üres mezők eltávolítása

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### 4. lépés: Fel nem használt mezők eltávolítása

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### 5. lépés: Tartalmazó mezők eltávolítása

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### 6. lépés: Üres táblázatsorok eltávolítása

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Gyakori problémák és hibaelhárítás
- **A bekezdések nem kerülnek eltávolításra:** Győződjön meg arról, hogy a `setCleanupParagraphsWithPunctuationMarks(true)` a takarítási beállítás beállítása *után* van meghívva.  
- **Az üres táblázatsorok megmaradnak:** Ellenőrizze, hogy a táblázat cellái valóban üres karakterláncot (nem szóközt) tartalmaznak.  
- **A fel nem használt mezők maradnak:** Ellenőrizze, hogy a megfelelő enumot (`REMOVE_UNUSED_FIELDS`) használja, és hogy a összevonási mezők nem kerülnek véletlenül máshol feltöltésre.

## Gyakran feltett kérdések

**K: Mi a különbség a `REMOVE_EMPTY_FIELDS` és a `REMOVE_UNUSED_FIELDS` között?**  
V: A `REMOVE_EMPTY_FIELDS` törli azokat a mezőket, amelyek az összevonás során üres karakterláncot vagy `null`-t kapnak, míg a `REMOVE_UNUSED_FIELDS` eltávolítja azokat a mezőket, amelyeket a teljes összevonási művelet során soha nem hivatkoztak.

**K: Kombinálhatok több takarítási beállítást?**  
V: Igen. A `setCleanupOptions` metódus bitenkénti OR-t fogad el az enum értékekből, lehetővé téve, hogy egy hívással tisztítsa meg a bekezdéseket, táblázatokat és régiókat.

**K: Befolyásolja a `cleanupParagraphsWithPunctuationMarks` engedélyezése a normál szöveget?**  
V: Csak azokat a bekezdéseket távolítja el, amelyek kizárólag központozási karaktereket tartalmaznak (pl. “?” vagy “---”). A normál mondatok érintetlenek maradnak.

**K: Lehet testre szabni, hogy mely központozási jeleket vegye figyelembe?**  
V: A jelenlegi API előre definiált központozási karakterkészletet használ. Egyedi viselkedéshez a dokumentumot a összevonás után kell utófeldolgozni.

**K: Működnek ezek a takarítási beállítások PDF konverzióval?**  
V: Teljesen. Miután a Word dokumentum tisztításra került, konvertálható PDF, HTML vagy bármely más támogatott formátumba anélkül, hogy a nem kívánt elemek átkerülnének.

## Következtetés
Most már rendelkezik egy teljes eszköztárral a **Word dokumentum** fájlok tisztításához a levélösszevonás során az Aspose.Words for Java segítségével. A megfelelő `MailMergeCleanupOptions` kiválasztásával automatikusan eltávolíthatja az üres bekezdéseket, üres táblázatsorokat, fel nem használt mezőket és még sok mást – így minden alkalommal egy letisztult, gyártásra kész dokumentumot kap.

---

**Legutóbb frissítve:** 2026-01-11  
**Tesztelve a következővel:** Aspose.Words for Java 24.11  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}