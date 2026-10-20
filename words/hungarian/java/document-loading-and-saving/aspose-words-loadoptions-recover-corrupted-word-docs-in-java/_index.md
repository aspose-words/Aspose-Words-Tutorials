---
category: general
date: 2026-05-04
description: Tanulja meg, hogyan tudja az Aspose.Words LoadOptions helyreállítani
  a sérült Word‑fájlokat, használni a helyreállítási módot, javítani a sérült docx‑fájlokat,
  és egyetlen oktatóanyagban megkapni a Word oldalszámát.
draft: false
keywords:
- aspose words loadoptions
- recover corrupted word
- use recovery mode
- repair corrupted docx
- get word page count
language: hu
og_description: Mesteri Aspose.Words LoadOptions a sérült Word fájlok helyreállításához,
  válassza ki a megfelelő helyreállítási módot, javítsa a sérült docx-et és szerezze
  meg az oldalszámot.
og_title: aspose words loadoptions – Sérült Word dokumentumok helyreállítása
tags:
- Aspose.Words
- Java
- Document Recovery
title: aspose words loadoptions – Sérült Word dokumentumok helyreállítása Java-ban
url: /hu/java/document-loading-and-saving/aspose-words-loadoptions-recover-corrupted-word-docs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose words loadoptions – Sérült Word dokumentumok helyreállítása Java-ban

Próbált már megnyitni egy Word fájlt, amely hirtelen nem akar betöltődni? Az a kellemetlen érzés, amikor egy ügyfél egy **sérült docx**‑et küld, és nincs ötlete, hogy meg tudja‑e menteni. A jó hír? Az **aspose words loadoptions**‑szal pontosan megmondhatja az Aspose.Words‑nek, hogyan viselkedjen, ha a dokumentum sérült: dobjon kivételt vagy próbáljon meg csendes javítást végrehajtani.  

Ebben az útmutatóban végigvezetjük a `LoadOptions` használatát **sérült Word** fájlok helyreállításához, megvizsgáljuk a **use recovery mode** beállításokat, megnézzük, hogyan **javítható automatikusan a sérült docx**, és végül **lekérdezhetjük a szó oldalszámát** a helyreállított dokumentumból. Nincs szükség külső eszközökre, csak tiszta Java és Aspose.Words.

## Amit szükséges

- **Aspose.Words for Java** (v24.12 vagy újabb) – a legújabb verzió néhány extra biztonsági ellenőrzést tartalmaz.
- Egy **Java IDE** (IntelliJ IDEA, Eclipse, vagy akár egy egyszerű szövegszerkesztő a `javac`‑kel).
- A **sérült DOCX**, amelyet tesztelni szeretne (nevezzük `Corrupted.docx`‑nek).
- **Alapvető Java ismeretek** – semmi különös, csak a szokásos `public static void main`.

> **Hasznos tipp:** készítsen biztonsági másolatot az eredeti fájlról; a helyreállítási kísérletek néha felülírhatják a bináris egyes részeit.

## 1. lépés: LoadOptions létrehozása – a helyreállítás központja

Az első dolog, hogy példányosít egy `LoadOptions` objektumot. Ez az objektum a vezérlőpult, amely megmondja az Aspose.Words‑nek, hogyan kezelje a fájlt, ha problémába ütközik.

```java
// Step 1: Initialise LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Miért kulcsfontosságú ez a lépés? Mert `LoadOptions` nélkül a könyvtár az alapértelmezett viselkedésre támaszkodik, ami csendben figyelmen kívül hagyhatja a hibákat, vagy még rosszabb, részben betöltött dokumentumot adhat vissza, amely később összeomlik. Az opciók explicit beállításával determinisztikus hibakezelést kap.

## 2. lépés: A megfelelő helyreállítási mód kiválasztása

Az Aspose.Words két helyreállítási stratégiát kínál:

| Mód | Viselkedés |
|------|-----------|
| `RecoveryMode.STRICT` | Kivételt dob, ha a dokumentumot nem lehet teljesen javítani. |
| `RecoveryMode.REPAIR` | Megpróbálja kijavítani a fájlt, és folytatja a betöltést, még ha némi tartalom elveszik is. |

Egy **recover corrupted word** helyzetben, ahol tudni kell, hogy a javítás sikeres volt‑e, a `STRICT` a legbiztonságosabb választás. Ha inkább a legjobb erőfeszítést szeretné, válassza a `REPAIR`‑et.

```java
// Step 2: Set the recovery mode
loadOptions.setRecoveryMode(RecoveryMode.STRICT);
// loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // Uncomment to attempt automatic repair
```

> **Miért válasszon egyiket a másik helyett?**  
> *STRICT* egyértelmű jelzést ad – vagy a dokumentum használható, vagy értesíteni kell a felhasználót. *REPAIR* hasznos kötegelt feladatoknál, ahol el tudja engedni egy-egy kép vagy egyéb elem elvesztését.

## 3. lépés: A lehetséges‑sérült dokumentum betöltése

Most már ténylegesen megnyitja a fájlt, átadva a korábban konfigurált `LoadOptions`‑t. Ha a fájl javíthatatlan és `STRICT`‑ot választott, kivétel keletkezik; egyébként egy `Document` objektumot kap, amely készen áll a vizsgálatra.

```java
// Step 3: Load the document with the configured options
Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);
```

Figyelje meg, hogy az útvonal lehet abszolút vagy a projekt gyökérkönyvtárához relatív. A `Document` osztály absztrahálja a teljes Word fájlt, így egyszerűen lekérdezhet például oldalszámot, szekciókat, vagy akár módosíthatja a tartalmat a helyreállítás után.

## 4. lépés: A betöltés ellenőrzése – Word oldalszám lekérdezése

Egy gyors ellenőrzésként kérdezze meg az Aspose.Words‑t, hány oldalt tartalmaz a dokumentum. Ha a szám nem nulla, valószínűleg sikerült **repair corrupted docx**‑et végrehajtani.

```java
// Step 4: Output the page count to confirm successful loading
System.out.println("Loaded successfully, page count = " + document.getPageCount());
```

Tipikus kimenet:

```
Loaded successfully, page count = 12
```

Ha a dokumentum valóban olvashatatlan volt `STRICT` módban, a kód már a sor előtt kivételt dobott. Így a `page count` ellenőrzés egyszerre ellenőrzés és hasznos információ a további logikához (pl. lapozás egy webes megjelenítőben).

## Teljes működő példa

Az alábbiakban a komplett, futtatható Java program látható, amely összehozza az összes elemet. Másolja be egy `RecoveryModeDemo.java` nevű fájlba, állítsa be az útvonalat, majd futtassa a `javac RecoveryModeDemo.java && java RecoveryModeDemo` parancsot.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to control how the file is opened
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Choose strict recovery – an exception is thrown if the file cannot be repaired
        loadOptions.setRecoveryMode(RecoveryMode.STRICT);
        // loadOptions.setRecoveryMode(RecoveryMode.REPAIR); // alternative: attempt repair and continue

        // Step 3: Load the possibly‑corrupted document using the configured options
        Document document = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // Step 4: Verify that the document was loaded (e.g., output its page count)
        System.out.println("Loaded successfully, page count = " + document.getPageCount());
    }
}
```

### Várható eredmény

- **Ha a fájl helyreállítható:** a konzol kiírja az oldalszámot, és biztonságosan folytathatja a `Document` objektum feldolgozását.
- **Ha a fájl javíthatatlan (STRICT mód):** `com.aspose.words.UnsupportedFileFormatException` (vagy hasonló) kerül dobásra, amelyet elkapva kedvesen kezelhet.

## Gyakori kérdések és széljegyek

### Mit tegyek, ha a pontos hiba részleteit szeretném naplózni?

Tegye a betöltő kódot egy `try‑catch` blokkba, és naplózza az `e.getMessage()`‑t. Így világos okot kap – legyen az hiányzó rész, törött kapcsolat vagy sérült adatfolyam.

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    System.out.println("Pages: " + doc.getPageCount());
} catch (Exception e) {
    System.err.println("Recovery failed: " + e.getMessage());
}
```

### Csak bizonyos részeket (pl. szöveg, de ne képeket) szeretnék helyreállítani?

Az Aspose.Words nem kínál finomhangolt helyreállítási kapcsolókat, de a betöltés után iterálhat a `NodeType` elemek felett, és eldobhatja azokat, amelyek `NodeType.SHAPE`‑ként (képek) jelennek meg, ha problémát okoznak.

### Működik ez régebbi `.doc` fájlokkal is?

Igen. A `LoadOptions` minden Word formátumra (`.doc`, `.docx`, `.dot`, `.dotx`) érvényes. Ugyanaz a helyreállítási logika alkalmazandó.

### Hogyan kezeli a könyvtár a jelszóval védett fájlokat?

Ha a fájl titkosított, a `LoadOptions` nem kerül át a jelszón. A jelszót a `loadOptions.setPassword("yourPassword")`‑vel kell megadni. A helyreállítási mód csak a sikeres dekódolás után lép életbe.

## Tippek a termelésben való használathoz

- **Naplózza a választott helyreállítási módot** – segít később visszakövetni, miért sikerült vagy miért sikertelen egy adott fájl.
- **Soha ne írja felül az eredeti fájlt** – mentse a helyreállított dokumentumot egy új helyre (`document.save("Recovered.docx")`).
- **Kombinálja validációval** – a helyreállítás után futtasson gyors helyesírás‑ vagy struktúravizsgálatot, hogy a dokumentum megfeleljen az üzleti szabályoknak.
- **Kötegelt feldolgozás** – sok fájl esetén iteráljon rajtuk, egyenként kezelje a kivételeket, és készítsen összefoglaló jelentést a sikeres és sikertelen esetekről.

## Összegzés

Most már rendelkezik egy szilárd, vég‑től‑végig tartó recepttel a **aspose words loadoptions** használatához **sérült Word** dokumentumok **helyreállításához**, a **use recovery mode** szigorú vagy engedékeny beállításának kiválasztásához, opcionálisan **repair corrupted docx** végrehajtásához, és végül a **word page count** lekérdezéséhez a helyreállított fájlban. A megközelítés determinisztikus, könnyen integrálható meglévő Java csővezetékekbe, és teljes kontrollt ad arról, mennyire agresszívan járjon el a könyvtár a hibás binárisokkal.

Készen áll a továbblépésre? Próbálja ki a `RecoveryMode.STRICT` helyett a `REPAIR`‑et egy kötegelt feladatban, vagy bővítse a példát úgy, hogy automatikusan elmentse a javított fájlt egy biztonságos mappába. A lehetőségek végtelenek, és az Aspose.Words‑szal fel van készülve a legmakacsabb Word‑fájl hibák kezelésére.

Boldog kódolást, és legyenek a dokumentumai mindig tisztán betöltve!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}