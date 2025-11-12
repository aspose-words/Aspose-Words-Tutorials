---
date: '2025-11-12'
description: Tanulja meg, hogyan használja az Aspose.Words for Java LayoutCollector
  és LayoutEnumerator osztályait a lapozás elemzéséhez, a dokumentum elrendezésének
  bejárásához, az elrendezési visszahívások megvalósításához, valamint a folyamatos
  szakaszokban az oldalszámozás újraindításához.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
- analyze pagination java
- use layoutcollector page span
- traverse document layout
- restart page numbering sections
- implement layout callback
language: hu
title: Java lapozási elemzés az Aspose.Words elrendező eszközökkel
url: /java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java oldalszámozás elemzése az Aspose.Words elrendezési eszközökkel

## Bevezetés  

Ha **oldalszámozást kell elemezni** vagy **a dokumentum elrendezését bejárni** szeretnél egy Java‑alkalmazásban, az Aspose.Words for Java két erőteljes API‑t biztosít: **`LayoutCollector`** és **`LayoutEnumerator`**. Ezek az osztályok lehetővé teszik, hogy megtudd, hány oldalra terjed ki egy csomópont, végigjárd az összes elrendezési elemet, reagálj az elrendezési eseményekre, sőt újraindíthasd az oldalszámozást folytonos szekciókban. Ebben az útmutatóban lépésről‑lépésre bemutatjuk minden funkciót, valós kódrészleteket mutatunk, és elmagyarázzuk a várt eredményeket, hogy azonnal alkalmazhasd őket.

Megtanulod, hogyan:

* **használd a LayoutCollector‑t** a bármely csomópont kezdő‑ és befejező oldalának lekérdezéséhez (layoutcollector page span használata)  
* **bejárd a dokumentum elrendezését** a LayoutEnumerator‑rel (traverse document layout)  
* **implementálj elrendezési callback‑eket** az oldalszámozási eseményekre reagálva (implement layout callback)  
* **újraindítsd az oldalszámozást** folytonos szekciókban (restart page numbering sections)  

Kezdjük is.

## Előkövetelmények  

### Szükséges könyvtárak  

| Építőeszköz | Függőség |
|------------|------------|
| **Maven** | ```xml<br><dependency><groupId>com.aspose</groupId><artifactId>aspose-words</artifactId><version>25.3</version></dependency>``` |
| **Gradle** | ```gradle<br>implementation 'com.aspose:aspose-words:25.3'``` |

> **Megjegyzés:** A verziószám a kompatibilitás érdekében maradt; a kód bármely friss Aspose.Words for Java kiadással működik.

### Környezet  

* JDK 8 vagy újabb  
* Egy IDE, például IntelliJ IDEA vagy Eclipse  

### Tudás  

Alapvető Java programozás és a Maven/Gradle ismerete elegendő a példák követéséhez.

## Az Aspose.Words beállítása  

Mielőtt bármely elrendezési API‑t meghívnád, a könyvtárat licencelni kell (vagy próbaverzióban használni). Az alábbi kódrészlet a minimális inicializálást mutatja:

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Load your license file – skip this line for a trial evaluation
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

*A kód nem módosít semmilyen dokumentumot; csak előkészíti az Aspose környezetet.*  

Most belevághatunk a fő funkciókba.

## 1. funkció: **LayoutCollector** használata az oldalszámozás elemzéséhez  

A `LayoutCollector` minden `Document`‑beli csomópontot hozzárendel a lefedett oldalakhoz. Ez a legmegbízhatóbb módja a **layoutcollector page span** használatának az oldalszámozás elemzéséhez.

### Lépésről‑lépésre megvalósítás  

1. **Új dokumentum létrehozása és LayoutCollector csatolása.**  
2. **Olyan tartalom beszúrása, amely oldaltörést vagy szekciótörést eredményez.**  
3. **Az elrendezés frissítése** a `updatePageLayout()`‑vel.  
4. **A gyűjtő lekérdezése** a kezdő‑, befejező‑ és összes lefedett oldalra.

#### 1️⃣ Dokumentum és LayoutCollector inicializálása  

```java
Document doc = new Document();                 // Empty document
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

#### 2️⃣ Dokumentum feltöltése  

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

#### 3️⃣ Elrendezés frissítése és metrikák lekérése  

```java
layoutCollector.clear();          // Reset any previous mappings
doc.updatePageLayout();           // Force pagination calculation

int pagesSpanned = layoutCollector.getNumPagesSpanned(doc);
assert pagesSpanned == 5;         // Expected: the document occupies 5 pages
System.out.println("Document spans " + pagesSpanned + " pages.");
```

**Várt kimenet**

```
Document spans 5 pages.
```

> **Miért működik:** A `updatePageLayout()` arra kényszeríti az Aspose.Words‑t, hogy újraszámolja az elrendezést, ezután a `LayoutCollector` pontosan tudja jelenteni az oldal‑tartományokat.

## 2. funkció: Dokumentum elrendezés bejárása a **LayoutEnumerator**‑rel  

Amikor **a dokumentum elrendezését kell bejárni** (például egyedi renderelés vagy elemzés céljából), a `LayoutEnumerator` egy fa‑szerű nézetet biztosít az oldalakról, bekezdésekről, sorokról és szavakról.

### Lépésről‑lépésre megvalósítás  

1. Tölts be egy meglévő dokumentumot, amely tartalmaz elrendezési elemeket.  
2. Hozz létre egy `LayoutEnumerator` példányt.  
3. Mozgasd a mutatót a gyökér `PAGE` entitásra.  
4. Járd be az elrendezést előre és hátra rekurzív segédfüggvényekkel.

#### 1️⃣ Dokumentum betöltése és enumerátor létrehozása  

```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

#### 2️⃣ Pozicionálás az oldal szintjén  

```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);
```

#### 3️⃣ Előre bejárás (mélységi keresés)  

```java
traverseLayoutForward(layoutEnumerator, 1);
```

#### 4️⃣ Hátra bejárás  

```java
traverseLayoutBackward(layoutEnumerator, 1);
```

> **Segédfüggvények** (`traverseLayoutForward` / `traverseLayoutBackward`) rekurzívan látogatják meg minden gyermek entitást, és kiírják annak típusát és oldal‑indexét. Ezeket átalakíthatod statisztikák gyűjtésére, grafika renderelésére vagy az elrendezési tulajdonságok módosítására.

## 3. funkció: **Layout Callback**‑ek megvalósítása  

Néha reagálnod kell, amikor az Aspose.Words befejezi egy dokumentumrész elrendezését. Az `IPageLayoutCallback` implementálásával **layout callback** logikát hozhatsz létre, például minden oldal PNG‑ként való mentését.

### Lépésről‑lépésre megvalósítás  

1. Adj egy callback példányt a dokumentum `LayoutOptions`‑ához.  
2. A callback‑ben kezeld a `PART_REFLOW_FINISHED` és `CONVERSION_FINISHED` eseményeket.  
3. Rendereld az aktuális oldalt PNG‑be az `ImageSaveOptions` használatával.

#### 1️⃣ Callback regisztrálása  

```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();                     // Triggers the callback events
```

#### 2️⃣ Callback osztály  

```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream(
                "YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }

    // You can add custom logic here for partFinished / conversionFinished
}
```

**Mi történik:** Minden alkalommal, amikor egy el