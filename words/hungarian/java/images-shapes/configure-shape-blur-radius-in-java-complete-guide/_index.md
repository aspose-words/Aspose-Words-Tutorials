---
category: general
date: 2026-06-27
description: Tanulja meg, hogyan állíthatja be az alakzat elmosódási sugarát az Aspose.Words
  for Java használatával. Ez a lépésről‑lépésre útmutató a árnyékbeállításokat, az
  átlátszóságot és a dokumentum mentését is lefedi.
draft: false
keywords:
- configure shape blur radius
- Aspose.Words shape shadow
- Java shadow format
- Word document shape manipulation
- set blur radius
language: hu
og_description: Állítsa be a forma elmosódási sugárát egy Word dokumentumban Java
  használatával. Kövesse ezt a részletes útmutatót, hogy elsajátítsa az Aspose.Words
  formaárnyék beállításait.
og_title: Alakzat elmosódási sugár beállítása Java-ban – Teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  headline: Configure Shape Blur Radius in Java – Complete Guide
  type: TechArticle
- description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  name: Configure Shape Blur Radius in Java – Complete Guide
  steps:
  - name: Understanding the Numbers
    text: '- **Blur radius** (`setBlurRadius`) controls how fuzzy the shadow looks.
      A value of `0` gives a crisp edge, while `10` or higher yields a dreamy glow.
      - **DistanceX / DistanceY** shift the shadow relative to the shape. Positive
      X moves it right; positive Y moves it down. - **Transparency** makes the'
  - name: Targeting a Specific Shape by Name
    text: 'If your document contains many shapes, rely on the shape’s **name** (set
      in Word’s layout options) instead of index:'
  - name: Applying Different Blur Radii
    text: 'You might want a stronger blur for background graphics and a subtle one
      for icons. Loop through all shapes:'
  - name: Compatibility Notes
    text: '- **Units:** Aspose.Words uses points (1 pt = 1/72 inch). If you work with
      millimeters, convert accordingly. - **Version:** The API shown works with Aspose.Words
      for Java 24.9 and later. Older versions may use `setBlurRadius(double)` but
      lack some newer shadow properties.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Alakzat elmosódási sugár beállítása Java-ban – Teljes útmutató
url: /hu/java/images-shapes/configure-shape-blur-radius-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Alakzat elmosódási sugár beállítása Java-ban – Teljes útmutató

Valaha is szükséged volt **configure shape blur radius** beállítására egy Word dokumentumban Java-val dolgozva? Nem vagy egyedül, aki ezen agyazik. Legyen szó egy vállalati jelentés csiszolásáról vagy egy finom vizuális csavarról egy szórólapban, ennek a beállításnak a mesteri kezelése sokkal professzionálisabbá teheti a dokumentumaidat.

Ebben az útmutatóban végigvezetünk a teljes folyamaton – a `.docx` fájl betöltésétől a árnyék elmosódásának finomhangolásáig, egészen a mentésig. Útközben érintünk kapcsolódó témákat, mint a **Aspose.Words shape shadow**, **Java shadow format**, és az általános **Word document shape manipulation**. A végére egy kész, futtatható kódrészletet és egy világos megértést kapsz arról, hogy miért fontos minden egyes sor.

## Mit fogsz megtanulni

- Hogyan tölts be egy Word dokumentumot az Aspose.Words for Java segítségével.  
- Hogyan találod meg az első `Shape` objektumot a dokumentum törzsében.  
- A pontos lépéseket a **configure shape blur radius** és egyéb árnyék tulajdonságok, például távolság és átlátszóság beállításához.  
- Hogyan mented vissza a módosításokat egy új `.docx` fájlba.  

Nem szükséges semmilyen külső könyvtár az Aspose.Words-en kívül, a kód Java 8‑as és újabb verziókkal, valamint bármely friss Aspose.Words for Java verzióval (pl. 24.9) működik. Ha ismered az alapvető Java szintaxist, könnyedén megy.

---

## 1. lépés: A Word dokumentum betöltése

Mielőtt bármilyen alakzatot módosítanál, a dokumentumnak memóriában kell lennie. Az Aspose.Words ezt egyetlen sorra csökkenti.

```java
// Load the source .docx file
com.aspose.words.Document document = new com.aspose.words.Document("YOUR_DIRECTORY/input.docx");
```

**Miért fontos:**  
A `Document` objektum létrehozása beolvassa az egész fájlt, így hozzáférsz a szakaszokhoz, bekezdésekhez, táblázatokhoz **és alakzatokhoz** is. Ennek kihagyása nélkül nem lesz kontextusod az elmosódási sugár alkalmazásához.

> **Pro tipp:** Nagy fájlok esetén érdemes `LoadOptions`-t használni, hogy csak a szükséges részeket streameld. Ez drámaian csökkentheti a memóriahasználatot.

---

## 2. lépés: A cél alakzat lekérése

Az alakzatok bárhol megjelenhetnek – fejlécekben, láblécekben, táblázatokban, bárhol. Egyszerűség kedvéért az első szakasz fő törzsében található első alakzatot vesszük.

```java
// Navigate to the first shape in the document body
com.aspose.words.Shape shape = (com.aspose.words.Shape) document
        .getFirstSection()
        .getBody()
        .getChild(com.aspose.words.NodeType.SHAPE, 0, true);
```

**Miért fontos:**  
A `getChild` hívás mélységi bejárással járja be a csomópontfát, és visszaadja az *első* `NodeType.SHAPE` típusú alakzatot. Ha a dokumentum több alakzatot tartalmaz, módosíthatod az indexet (`0`) vagy iterálhatsz a `document.getChildNodes(NodeType.SHAPE, true)` segítségével.

> **Szélsőséges eset:** Ha a dokumentumnak nincs alakzata, a `shape` értéke `null` lesz, és a következő sor `NullPointerException`‑t dob. Mindig ellenőrizd ezt a termelési kódban.

---

## 3. lépés: Az alakzat árnyékának beállítása – Elmosódási sugár

Most jön a főszereplő: az elmosódási sugár finomhangolása. Ez a `ShadowFormat` objektumban található, amely az alakzathoz van csatolva.

```java
// Access the shadow format of the shape
com.aspose.words.ShadowFormat shadow = shape.getShadowFormat();

// Set the blur radius (in points). Larger values produce a softer edge.
shadow.setBlurRadius(5.0);

// Optional: fine‑tune other shadow attributes
shadow.setDistanceX(3.0);          // Horizontal offset
shadow.setDistanceY(3.0);          // Vertical offset
shadow.setTransparency(0.3);      // 0 = fully opaque, 1 = fully transparent
```

### A számok megértése

- **Elmosódási sugár** (`setBlurRadius`) szabályozza, mennyire homályos az árnyék. A `0` érték éles szegélyt ad, míg a `10` vagy nagyobb érték álomszerű fényt eredményez.  
- **DistanceX / DistanceY** eltolja az árnyékot az alakzathoz képest. Pozitív X jobbra, pozitív Y lefelé mozgat.  
- **Transparency** átlátszóvá teszi az árnyékot. Hasznos, ha finom hatást szeretnél egy szilárd fekete blokk helyett.

> **Miért állítsuk be az elmosódási sugarat?**  
> Sok vállalati sablonban egy könnyű elmosódás mélységet ad anélkül, hogy elterelné a figyelmet. Ez egy apró vizuális finomítás, amely drámaian javíthatja a minőségérzetet.

---

## 4. lépés: A módosított dokumentum mentése

Minden nehéz munka elkészült; most írd vissza a változásokat a lemezre.

```java
// Persist the modified document
document.save("YOUR_DIRECTORY/output.docx");
```

**Miért fontos:**  
A `save` hívás kiírja az egész dokumentumot, beleértve a frissített `ShadowFormat`-ot is. Ha csak az alakzatot képként szeretnéd, exportálhatod a `shape.getImageData().save(...)` segítségével is.

---

## Teljes működő példa

Az alábbiakban megtalálod a komplett, önálló programot, amelyet bármely Java IDE-be beilleszthetsz. Győződj meg róla, hogy az Aspose.Words for Java JAR a classpath‑odban van.

```java
import com.aspose.words.*;

public class ConfigureShapeBlurRadius {
    public static void main(String[] args) throws Exception {
        // 1. Load the document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Get the first shape (add null‑check for safety)
        Shape shape = (Shape) document.getFirstSection()
                .getBody()
                .getChild(NodeType.SHAPE, 0, true);
        if (shape == null) {
            System.out.println("No shape found in the document.");
            return;
        }

        // 3. Configure shadow – focus on blur radius
        ShadowFormat shadow = shape.getShadowFormat();
        shadow.setBlurRadius(5.0);          // Soft blur
        shadow.setDistanceX(3.0);           // Horizontal offset
        shadow.setDistanceY(3.0);           // Vertical offset
        shadow.setTransparency(0.3);        // Slightly transparent

        // 4. Save the result
        document.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved with configured shape blur radius.");
    }
}
```

**Várt kimenet:**  
A program futtatása egy új `output.docx` fájlt hoz létre, ahol az első alakzat egy enyhe, félig átlátszó árnyékkal és `5` pont elmosódási sugárral rendelkezik. Nyisd meg a fájlt Wordben, válaszd ki az alakzatot, és a **Shape Format → Shadow Effects → Shadow Options** menüpont alatt láthatod a beállított értékeket a felhasználói felületen.

---

## Több alakzat kezelése és haladó forgatókönyvek

### Konkrét alakzat célzása név alapján

Ha a dokumentum sok alakzatot tartalmaz, a **név** (a Word elrendezési beállításaiban megadható) használata index helyett célszerű:

```java
Shape target = (Shape) document.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getName().equals("MyLogo"))
        .findFirst()
        .orElse(null);
```

### Különböző elmosódási sugarak alkalmazása

Lehet, hogy a háttérgrafikáknak erősebb elmosódásra, az ikonoknak pedig finomabbra van szükséged. Iterálj az összes alakzaton:

```java
for (Node node : document.getChildNodes(NodeType.SHAPE, true)) {
    Shape s = (Shape) node;
    ShadowFormat sf = s.getShadowFormat();
    sf.setBlurRadius(s.getName().contains("Background") ? 10.0 : 3.0);
}
```

### Kompatibilitási megjegyzések

- **Mértékegységek:** Az Aspose.Words pontokat (1 pt = 1/72 hüvelyk) használ. Ha milliméterben dolgozol, konvertáld át.  
- **Verzió:** A bemutatott API az Aspose.Words for Java 24.9 és újabb verziókkal működik. Régebbi verziók esetén a `setBlurRadius(double)` létezhet, de hiányozhatnak a későbbi árnyék tulajdonságok.

---

## Gyakori hibák és elkerülésük módja

| Hiba | Miért fordul elő | Megoldás |
|------|------------------|----------|
| `NullPointerException` a `shape`-nél | A dokumentumnak nincs alakzata vagy az index kívül esik | Adj hozzá null‑ellenőrzést a `ShadowFormat` elérése előtt. |
| Az árnyék nem látható Wordben | Az árnyék színe alapértelmezés szerint átlátszó, vagy a távolság értékek kifelé tolják | Állíts be látható `ShadowColor`‑t (`shadow.setColor(Color.BLACK)`) és tartsd mérsékeltnek a `DistanceX/Y` értékeket. |
| Az elmosódási sugár nem változik | Elavult Aspose.Words verzió, amely figyelmen kívül hagyja a tulajdonságot | Frissíts a legújabb könyvtárra; a tulajdonság a 20.5‑ös verzióban került be. |
| Teljesítménycsökkenés nagy dokumentumoknál | Minden alakzat módosítása után a teljes dokumentumot újra mented | Gyűjtsd össze a módosításokat, majd egyszer hívd meg a `save`-et. |

---

## Összegzés

Most már tudod, **hogyan konfiguráld az alakzat elmosódási sugarát** egy Word dokumentumban Java és Aspose.Words segítségével. A fájl betöltésétől, a megfelelő `Shape` kiválasztásán, a `ShadowFormat` finomhangolásán, egészen a változások mentéséig – minden lépést magyarázatokkal és gyakorlati tippekkel fedtünk le.  

A technika nem korlátozódik egyetlen alakzatra; skálázható egész dokumentumokra, különböző elmosódási szintek alkalmazására, vagy kombinálható más árnyék attribútumokkal, mint a **shadow transparency Java**. A következő logikus lépés a **set blur radius** képekre, a **Java shadow format** kísérletezése diagramokon, vagy a **Word document shape manipulation** mélyebb felfedezése dinamikus jelentéskészítéshez.

Van olyan szituáció, amit itt nem fedtünk le? Írj kommentet, vagy nézd meg az Aspose.Words for Java dokumentációját a további árnyékhatásokért. Boldog kódolást!

---

<img src="configure-shape-blur-radius.png" alt="Configure shape blur radius using Aspose.Words Java example" style="max-width:100%;">

---


## Mit érdemes legközelebb megtanulni?


Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutató technikáira épülnek. Minden forrás komplett működő kódrészleteket és lépésről‑lépésre magyarázatokat tartalmaz, hogy további API‑funkciókat saját projektjeidben is könnyedén alkalmazhasd.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}