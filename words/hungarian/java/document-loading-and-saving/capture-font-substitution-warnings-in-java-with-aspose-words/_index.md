---
category: general
date: 2026-01-11
description: Tanulja meg, hogyan lehet rögzíteni a betűtípus helyettesítési figyelmeztetéseket
  az Aspose.Words for Java használatával. Ez a lépésről‑lépésre útmutató a LoadOptions
  és a figyelmeztetési visszahívások témakörét is lefedi.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: hu
og_description: Rögzítse a betűkészlet‑helyettesítési figyelmeztetéseket az Aspose.Words
  for Java segítségével. Kövesse ezt az útmutatót a LoadOptions és egy figyelmeztetési
  visszahívás beállításához a megbízható dokumentumbetöltés érdekében.
og_title: Betűtípus helyettesítési figyelmeztetések rögzítése Java-ban – Teljes útmutató
tags:
- Aspose.Words
- Java
- Document Processing
title: Betűtípus-helyettesítési figyelmeztetések rögzítése Java-ban az Aspose.Words
  segítségével – Teljes útmutató
url: /hu/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Betűkészlet-helyettesítési figyelmeztetések rögzítése – Teljes Java útmutató

Szüksége volt már **betűkészlet‑helyettesítési figyelmeztetések rögzítésére**, amikor egy hiányzó betűtípussal rendelkező Word‑dokumentumot nyit? Gyakori fejfájás, különösen PDF‑készítés vagy nyomtatás szerveren, ahol nem minden betűtípus van telepítve. A jó hír? Az Aspose.Words for Java ezt egyszerűvé teszi – csak állíts be egy `LoadOptions` objektumot, és csatlakoztass egy figyelmeztetési visszahívást. Ebben az útmutatóban pontosan megmutatjuk, hogyan kell ezt megtenni, miért fontos, és mit várhatsz, amikor a figyelmeztetés aktiválódik.

Érinteni fogjuk a kapcsolódó témákat is, mint az **Aspose.Words betűkészlet‑helyettesítés**, egy **Java figyelmeztetési visszahívás** használata, valamint a **LoadOptions** helyes alkalmazása. A végére egy kész, futtatható kódrészletet kapsz, amely minden hiányzó betűtípus eseményt naplóz, így az azt követő feldolgozás sosem fog meglepetést okozni.

## Előfeltételek

Mielőtt belevágnánk, győződj meg róla, hogy a következők rendelkezésre állnak:

- Java 17 (vagy bármely újabb JDK) telepítve és beállítva.
- Aspose.Words for Java 23.10 (vagy újabb) a classpath‑on.
- Egy Word‑dokumentum, amely olyan betűtípust hivatkozik, amely nincs helyben (pl. `DocWithMissingFont.docx`).
- Alapvető ismeretek a Java try/catch blokkokról – semmi bonyolult.

Ha valamelyik pont ismeretlen, állj meg egy pillanatra, és telepítsd a könyvtárat a Maven Central‑ról:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Most, hogy az alapok készen állnak, nézzük a kódot.

## 1. lépés: Figyelmeztetési visszahívás beállítása a **betűkészlet‑helyettesítési figyelmeztetések rögzítéséhez**

Az első dolog, amire szükséged van, egy visszahívás, amelyet az Aspose.Words meghív, amikor hiányzó betűtípust talál. Itt **rögzítjük a betűkészlet‑helyettesítési figyelmeztetéseket**. A visszahívás implementálja az `IWarningCallback` interfészt, és ellenőrzi a `WarningType`‑ot.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Miért fontos:** Visszahívás nélkül az Aspose.Words csendben egy alapértelmezett betűtípusra cseréli a hiányzót, és sosem tudod meg, hogy a vizuális megjelenés megváltozott. A figyelmeztetés rögzítésével naplózhatsz, riaszthatsz, vagy akár megszakíthatod a betöltést, ha a hiányzó betűtípus kritikus.

## 2. lépés: **LoadOptions** konfigurálása és a visszahívás regisztrálása

Most létrehozunk egy `LoadOptions` példányt, és csatoljuk a `FontWarningCallback`‑et. Ez a lépés elengedhetetlen a **LoadOptions** használatához, és biztosítja, hogy minden dokumentumbetöltés ugyanazon figyelmeztetési szűrőn menjen keresztül.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Tipp:** Ugyanazt a `LoadOptions` objektumot újra felhasználhatod több dokumentumhoz, ami néhány sor boilerplate‑t takarít meg, és garantálja a **dokumentumbetöltési figyelmeztetések** egységes kezelését az alkalmazásodban.

## 3. lépés: Dokumentum betöltése és a kimenet megfigyelése

Miután a visszahívást bekötöttük, egyszerűen töltsd be a Word‑fájlt. Ha a dokumentum egy nem telepített betűtípust hivatkozik, a visszahívás aktiválódik, és a konzolra írja a részleteket.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Várható konzolkimenet

Tegyük fel, hogy a `DocWithMissingFont.docx` a hiányzó *„Comic Sans MS”* betűtípust használja, akkor valami ilyesmit látsz majd:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Ha a dokumentumban **nincsenek hiányzó betűtípusok**, a konzol csak az utolsó sort mutatja, ami megerősíti, hogy a visszahívás nem adott hamis pozitív eredményt.

## 4. lépés: Szélsőséges esetek és gyakori buktatók kezelése

### Több hiányzó betűtípus

Ha egy dokumentum több nem elérhető betűtípust használ, a visszahívás minden betűtípusra egyszer lefut. Sorozatos üzeneteket kapsz, mindegyik saját `source` és `description` mezővel. Nem szükséges extra kód – csak győződj meg róla, hogy a naplózási rendszered képes a gyors egymást követő hívások kezelésére.

### Figyelmeztetések elnyomása

Ritka esetekben előfordulhat, hogy bizonyos helyettesítéseket figyelmen kívül szeretnél hagyni (pl. tudod, hogy egy adott fallback elfogadható). Bővítsd a visszahívás logikáját:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Szálbiztonság

Az Aspose.Words `LoadOptions` alapértelmezés szerint nem szálbiztos. Ha párhuzamosan töltesz dokumentumokat, hozz létre egy külön `LoadOptions` példányt szálanként, vagy szinkronizáld a visszahívást a versenyhelyzetek elkerülése érdekében.

## 5. lépés: A helyettesített betűkészlet ellenőrzése a kapott dokumentumban

Betöltés után érdemes megerősíteni, hogy a helyettesítés ténylegesen megtörtént. Az API lehetővé teszi, hogy végigiterálj az összes run‑on, és megvizsgáld a tényleges betűtípusnevet:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Ez a kódrészlet minden szövegrun‑t kiír a végleges betűtípusával. Hasznos ellenőrzés, ha automatizált PDF‑konverziós csővezetékeket építesz.

## Teljes működő példa

Mindent összegezve, itt a komplett, futtatható program:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Mentsd el `FontSubstitutionInfo.java` néven, fordítsd `javac`‑el, és futtasd `java FontSubstitutionInfo`‑val. A figyelmeztető üzeneteket (ha vannak) majd a run‑ok és végleges betűtípusaik listáját fogod látni.

## Vizuális segédlet

![Screenshot of console output showing font substitution warnings](/images/font-substitution-warning.png "capture font substitution warnings example")

*Alt szöveg:* **betűkészlet‑helyettesítési figyelmeztetések rögzítése** – konzolkimenet egy hiányzó betűtípusú dokumentum betöltése után

## Összegzés

Most már tudod, hogyan **rögzítsd a betűkészlet‑helyettesítési figyelmeztetéseket** az Aspose.Words for Java segítségével. Egy `LoadOptions` objektum beállításával és egy egyedi `IWarningCallback` biztosításával teljes átláthatóságot kapsz minden hiányzó betűtípus‑eseményre, amely egyébként csendben befolyásolná a dokumentum megjelenését. Ez a technika közvetlenül az **Aspose.Words betűkészlet‑helyettesítés** kezelésébe illeszkedik, megbízható **dokumentumbetöltési figyelmeztetéseket** biztosít, és rugalmasságot ad a naplózáshoz, riasztáshoz vagy a betöltés megszakításához az üzleti szabályaid szerint.

### Mi következik?

- Fedezd fel a **Java figyelmeztetési visszahívás** mintákat más figyelmeztetéstípusokhoz (pl. `DEPRECATED_FEATURE`).
- Kombináld ezt a megközelítést **PDF konverzióval**, hogy biztosítsd, a helyettesített betűkészletek ne rombolják a layoutot.
- Mélyedj el a **LoadOptions** használatában – kísérletezz a `Password`, `Encoding`, és `ResourceLoadingCallback` beállításokkal összetettebb forgatókönyvekhez.

Nyugodtan módosítsd a visszahívást, irányítsd a figyelmeztetéseket egy naplókeretrendszerbe, vagy dobj egy egyedi kivételt, ha kritikus betűtípus hiányzik. A lehetőségek tárháza nyitott, és most már szilárd alapokkal rendelkezel a további fejlesztéshez.

Boldog kódolást, és legyenek a dokumentumaid mindig úgy megjelenítve, ahogy elvárod!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}