---
category: general
date: 2026-02-18
description: Hozzon létre betöltési beállításokat Java-ban a hiányzó betűtípusok észleléséhez,
  és tanulja meg, hogyan töltsön be DOCX fájlokat figyelmeztető visszahívással.
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: hu
og_description: Készíts betöltési beállításokat Java-ban a hiányzó betűtípusok észleléséhez,
  és tanuld meg, hogyan tölts be DOCX fájlokat figyelmeztető visszahívással.
og_title: Load Options létrehozása Java-ban – Hiányzó betűtípusok észlelése és DOCX
  betöltése
tags:
- java
- aspose-words
- document-processing
title: Betöltési beállítások létrehozása Java-ban – Hiányzó betűtípusok észlelése
  és a DOCX betöltése
url: /hu/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Load Options létrehozása Java-ban – Hiányzó betűkészletek észlelése és DOCX betöltése

Gondolkodtál már azon, hogyan **hozz létre load options**-t, amely nem csak egy DOCX-et olvas be, hanem azt is jelzi, ha egy betűkészlet hiányzik? Nem vagy egyedül. A hiányzó betűkészletek egy tökéletesen formázott dokumentumot összezavart szöveggé változtathatnak, és a korai észlelés órákat spórol a hibakeresésben. Ebben az útmutatóban lépésről‑lépésre bemutatjuk, hogyan **észleld a hiányzó betűkészleteket**, miközben megmutatjuk, **hogyan tölts be DOCX** fájlokat egy egyedi figyelmeztető visszahívással.

## Mit fogsz megtanulni

- Hogyan példányosítsuk a `LoadOptions`‑t és állítsuk be a figyelmeztető kezelőt.  
- Miért elengedhetetlen a figyelmeztető visszahívás a betűkészlet‑helyettesítési problémák elkapásához.  
- A pontos kód, amely szükséges egy **DOCX** fájl biztonságos betöltéséhez, valamint néhány gyakorlati tipp a valós projektekhez.  
- Szélsőséges esetek kezelése, például más figyelmeztetéstípusok kezelése vagy PDF-ek betöltése ugyanazzal a megközelítéssel.

Nincs szükség külső dokumentációra – minden, amire szükséged van, itt van.

## Előfeltételek

- Java 17 vagy újabb (az API régebbi verziókon is működik, de a 17 a legoptimálisabb).  
- Aspose.Words for Java könyvtár hozzáadva a projektedhez (`aspose-words-x.x.jar`).  
- Alapvető ismeretek a Java kivételkezelésről.  

Ha ezek megvannak, vágjunk bele.

![Ábra a load options létrehozásának, a figyelmeztető visszahívás beállításának és a DOCX betöltésének folyamatáról](/images/create-load-options-diagram.png){: .center-image alt="Load Options létrehozásának folyamatábrája"}

## 1. lépés: Load Options létrehozása (Hogyan töltsünk be DOCX-et)

Az első dolog, amit meg kell tenned, **load options** létrehozása. Ez az objektum azt mondja meg az Aspose.Words‑nek, hogyan viselkedjen, amikor egy fájlt nyit meg. Tekintsd úgy, mint egy utasításkészletet, amelyet a könyvtárnak adsz át, mielőtt még csak a DOCX-et látná.

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Miért ne hívnád egyszerűen a `new Document("file.docx")`‑t? Mert `LoadOptions` nélkül elveszíted a lehetőséget, hogy a figyelmeztetésekre (például hiányzó betűkészletekre) reagálj, csak a dokumentum betöltése után, ami bizonyos munkafolyamatoknál már túl késő lehet.

## 2. lépés: Figyelmeztető visszahívás beállítása a hiányzó betűkészletek észleléséhez

Most csatolunk egy visszahívást, amely akkor hívódik meg, amikor az Aspose.Words olyan helyzetbe ütközik, amelyről figyelmeztetni szeretne. Ebben az esetben a `WarningType.FONT_SUBSTITUTION` érdekel minket.

```java
// Step 2: Register a warning callback
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // React only to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Missing font detected: " + info.getDescription());
        }
    }
});
```

Néhány fontos megjegyzés:

- **Miért visszahívás?** A betöltési folyamat *közben* fut, lehetőséget adva a naplózásra vagy akár a művelet megszakítására, mielőtt a dokumentum teljesen materializálódna.  
- **Miért ellenőrizni a `WarningType.FONT_SUBSTITUTION`‑t?** Ez az a pontos enum érték, amelyet az Aspose.Words a hiányzó betűkészletek esetén használ. Más figyelmeztetéstípusok (pl. `TABLE_STRUCTURE`) hasonlóan szűrhetők, ha szükséges.  
- **Teljesítmény tipp:** A visszahívás könnyű; kerüld a nehéz I/O műveleteket benne. Ha fájlba kell írni, sorold be az üzeneteket és a betöltés után írd ki őket.

## 3. lépés: A DOCX fájl betöltése a beállított opciókkal

A beállított opciókkal és a visszahívással most végre betöltheted a DOCX-et. Ez a rész válaszol arra, **hogyan tölts be docx**‑et, miközben tiszteletben tartja a beállított figyelmeztetéseket.

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**Mi történik a háttérben?** Ahogy a fájl beolvasásra kerül, az Aspose.Words ellenőrzi minden betűkészlet‑hivatkozást. Ha egy hivatkozott betűkészlet nincs telepítve, aktiválja a korábban definiált figyelmeztető visszahívást. A kimenet például így néz ki:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

Ez a azonnali visszajelzés felbecsülhetetlen, amikor szerveren fájlcsomagokat dolgozol fel.

## Teljes működő példa

Az összes lépést egy önálló programba foglalva, amelyet egyszerűen átmásolhatsz a kedvenc IDE‑dbe.

```java
import com.aspose.words.*;

public class DetectMissingFonts {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register warning callback to detect missing fonts
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Missing font: " + info.getDescription());
                }
            }
        });

        // 3️⃣ Load the DOCX using the configured options
        try {
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            System.out.println("DOCX loaded – you can now work with it.");
        } catch (Exception ex) {
            System.err.println("Error loading DOCX: " + ex.getMessage());
        }
    }
}
```

**Várható kimenet**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

Ha a fájl nem tartalmaz hiányzó betűkészleteket, a visszahívás egyszerűen csendben marad, és megjelenik a „DOCX loaded” sor.

## Pro Tips & Edge Cases

| Szituáció | Mit kell tenni |
|-----------|----------------|
| **Több hiányzó betűkészlet** | A visszahívás minden egyes hiányzó betűkészletnél lefut, így minden betűkészletről egy sor jelenik meg. Ha később összegzést szeretnél, gyűjtsd őket egy `List<String>`‑be. |
| **Más figyelmeztetéseket is el szeretnél kapni** | `else if` ágakat adj hozzá a `WarningType.TABLE_STRUCTURE`, `WarningType.UNKNOWN_FILE_FORMAT` stb. típusokhoz. |
| **Nagy DOCX fájlok betöltése** | Használd a `LoadOptions.setLoadFormat(LoadFormat.DOCX)`‑t a formátum jelzésére és a detektálás felgyorsítására. |
| **Webszolgáltatásban futtatás** | Kerüld a `System.out.println` használatát; helyette injektálj egy loggert (`SLF4J`, `Log4j`) a visszahívásba. |
| **Betűkészletek futásidőben történő telepítése** | Hiányzó betűkészlet észlelése után programozottan betöltheted a `GraphicsEnvironment.registerFont(...)` segítségével, majd újratöltheted a dokumentumot. |

## Miért felülmúlja ez a megközelítés a „csak try‑catch” módszert

Sok fejlesztő egyszerűen a `new Document(...)`‑t try‑catch blokkba helyezi, remélve, hogy egy kivétel jelzi a hiányzó betűkészleteket. Sajnos az Aspose.Words a betűkészlet‑helyettesítést *figyelmeztetésként* kezeli, nem hibaként, így nem dob kivételt. A **load options** létrehozásával és egy figyelmeztető visszahívás csatolásával determinisztikus betekintést nyersz a betűkészlet‑problémákba anélkül, hogy a teljesítményt feláldoznád.

## Következő lépések

- **Hiányzó betűkészletek észlelése PDF-ekben** – ugyanaz a `LoadOptions` minta működik PDF-eknél is, csak módosítsd a fájl útvonalát és a betöltési formátumot.  
- **Betűkészlet telepítés automatizálása** – kombináld a visszahívást egy szkripttel, amely a hiányzó betűkészleteket egy közös tárolóból húzza.  
- **Fedezd fel a többi figyelmeztetéstípust** – az Aspose.Words figyelmeztethet elavult címkékről, összetett táblákról és egyebekről.  

Nyugodtan kísérletezz: cseréld le a `Document` konstruktort egy stream‑re (`new Document(InputStream, loadOptions)`) ha memóriában dolgozol, vagy láncolj több visszahívást egy kompozit mintával nagy‑léptékű feldolgozási csővezetékekhez.

---

### TL;DR

Megmutattuk, hogyan **hozz létre load options**‑t Java‑ban, állíts be egy visszahívást, amely **észleli a hiányzó betűkészleteket**, és végül **biztonságosan betölts egy DOCX**‑et. Csak három tömör lépés, és már van egy újrahasználható minta, amely bármely Aspose.Words projektbe beilleszthető.

Van kérdésed más fájlformátumokkal kapcsolatban, vagy segítségre van szükséged a visszahívás finomhangolásához a saját környezetedben? Írj egy megjegyzést alább, és jó kódolást!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}