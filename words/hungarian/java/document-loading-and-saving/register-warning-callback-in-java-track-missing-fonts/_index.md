---
category: general
date: 2026-05-30
description: Regisztrálja a figyelmeztető visszahívást Java-ban a hiányzó betűtípusok
  nyomon követéséhez, és testreszabja a dokumentum betöltését az Aspose.Words segítségével.
  Ismerje meg a teljes lépésről‑lépésre megoldást.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: hu
og_description: Regisztrálj figyelmeztető visszahívást Java-ban a hiányzó betűtípusok
  nyomon követéséhez és a dokumentum betöltés testreszabásához. Teljes útmutató kóddal
  és magyarázatokkal.
og_title: Figyelmeztető visszahívás regisztrálása Java-ban – Hiányzó betűtípusok nyomon
  követése
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Figyelmeztető visszahívás regisztrálása Java-ban – Hiányzó betűtípusok nyomon
  követése
url: /hu/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Regisztrálja a figyelmeztető visszahívást Java‑ban – Hiányzó betűtípusok nyomon követése

Gondolkodtál már azon, hogyan **követhesd a hiányzó betűtípusokat** egy Word dokumentum betöltésekor az Aspose.Words for Java‑val? Lehet, hogy láttad már azokat a csendes betűtípus‑helyettesítéseket, és azt kérdezted: „Mi történt a elrendezéssel?” A jó hír, hogy nem kell találgatnod. **Figyelmeztető visszahívás regisztrálásával** minden betűtípus‑helyettesítési eseményt el tudsz kapni a dokumentum beolvasásakor, és **testreszabhatod a dokumentum betöltését** is, hogy illeszkedjen a folyamatodba.

Ebben az útmutatóban egy valós példán keresztül mutatjuk be, hogyan állítsd be a visszahívást, miért fontos, és hogyan tartsd tisztán a további feldolgozási lépéseket. A végére egy kész, futtatható Java osztályt kapsz, amely kiírja minden hiányzó betűtípusra vonatkozó figyelmeztetést, és elment egy feldolgozott példányt a dokumentumból. Nem szükséges külső hivatkozás – csak tiszta, futtatható kód.

> **Mit kapsz majd:**  
> • Egy komplett Java program az Aspose.Words‑szal  
> • Lépés‑ről‑lépésre magyarázat minden sorhoz  
> • Tippek a szélhelyzetek kezeléséhez, például titkosított fájlok vagy nagy kötegek esetén  
> • Egy gyors ellenőrzés, amelyet bármelyik `.docx` fájlon futtathatsz

## Előfeltételek

Mielőtt belevágnánk, győződj meg róla, hogy:

- **Java 17** (vagy bármely friss JDK) telepítve van, és a `JAVA_HOME` be van állítva.  
- **Aspose.Words for Java** JAR a classpath‑ban. A legújabb verziót a Maven Central tárolóból szerezheted be:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Egy minta Word dokumentum (`input.docx`), amelyben gyanítod, hogy hiányzó betűtípusok vannak.  
- Egy IDE vagy parancssori build eszköz (Maven/Gradle), amivel kényelmesen dolgozol.

Ennyi. Nincs szükség extra betűtípusokra, extra szolgáltatásokra – csak tiszta Java és Aspose.Words.

## Miért regisztráljunk figyelmeztető visszahívást?

Gondolj a **figyelmeztető visszahívásra** úgy, mint egy biztonsági kamerára a dokumentum betöltési folyamatában. Amikor az Aspose.Words hiányzó glifet talál, nem dob kivételt, hanem csendben egy tartalék betűtípust használ. Ez a hallgató helyettesítés tönkreteheti az elrendezést, különösen márkakritikus PDF‑ek vagy számlák esetén. A visszahívás regisztrálásával:

1. **Valós‑időben nyerhetsz betekintést** – minden `FONT_SUBSTITUTION` figyelmeztetés azonnal megérkezik.  
2. **Naplózhatsz vagy reagálhatsz** – fájlba írhatsz, riasztást küldhetsz, vagy akár programból is kicserélheted a betűtípust.  
3. **Tiszta kimenetet biztosítasz** – ha tudod, mely betűtípusok hiányoznak, javíthatod a forrásdokumentumot a közzététel előtt.

Röviden, a visszahívás egy rejtett problémát láthatóvá tesz, és sokkal megbízhatóbbá teszi a dokumentum‑feldolgozó csővezetékedet.

## 1. lépés – Hozd létre a `LoadOptions`‑t a dokumentum betöltésének testreszabásához

Az első dolog, amit megteszünk, a `LoadOptions` példányosítása. Ez az objektum a kapu minden betöltési finomhangoláshoz, a jelszókezeléstől a **figyelmeztető visszahívás regisztrálása** funkcióig.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

Miért ne hívnád egyszerűen a `new Document("file.docx")`‑t? Mert `LoadOptions` nélkül elveszíted a lehetőséget, hogy beavatkozz a betöltési eseményekbe. A `LoadOptions` az egyetlen hely, ahol az Aspose.Words lehetővé teszi a **dokumentum betöltésének testreszabását**.

## 2. lépés – Regisztrálj egy figyelmeztető visszahívást a hiányzó betűtípusok nyomon követéséhez

Most jön a főszereplő: **regisztrálunk egy figyelmeztető visszahívást**, amely implementálja az `IWarningCallback` interfészt. A `warning` metódusban szűrünk a `WarningType.FONT_SUBSTITUTION` típusra, és egy hasznos üzenetet írunk ki.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Néhány fontos megjegyzés:

- **Miért `IWarningCallback`?** Ez az interfész az Aspose.Words által minden figyelmeztetéstípushoz használt, így egyetlen belépési pontot kapsz a lehetséges problémákhoz.  
- **A szűrés elengedhetetlen** – a `if` ellenőrzés nélkül a hiányzó képekről, elavult funkciókról stb. is figyelmeztetéseket látnál, ami csak elárasztaná a naplódat.  
- **Szálbiztonság** – a visszahívás ugyanazon a szálon fut, amely a dokumentumot betölti, így biztonságosan frissítheted a megosztott struktúrákat, ha később aggregálni szeretnéd az eredményeket.

Ez a kódrészlet **regisztrálja a figyelmeztető visszahívást**, és ettől kezdve minden hiányzó betűtípus‑esemény ki lesz írva a `stdout`‑ra. Ez a **hiányzó betűtípusok nyomon követése** magja.

## 3. lépés – Töltsd be a dokumentumot a konfigurált `LoadOptions`‑szal

Miután a visszahívás be van állítva, végül betöltjük a fájlt. Ha a dokumentum olyan betűtípust hivatkozik, amely nálad nincs, a visszahívás a `Document` objektum teljes felépítése előtt aktiválódik.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Cseréld le a `YOUR_DIRECTORY`‑t a saját géped tényleges elérési útjára. A `Document` konstruktor beolvassa a fájlt, alkalmazza a jelszót (ha a `loadOptions`‑ban beállítottad), és minden hiányzó betűtípusra meghívja a figyelmeztető visszahívást. A kimenet valahogy így néz majd ki:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Ez a sor bizonyítja, hogy sikeresen **nyomon követted a hiányzó betűtípusokat**.

## 4. lépés – Folytasd a dokumentum feldolgozását (opcionális)

Ebben a szakaszban tetszés szerint módosíthatod a dokumentumot – szöveget cserélhetsz, képeket illeszthetsz, vagy akár programból is kicserélheted a helyettesített betűtípusokat. A visszahívás már megadta a problémás betűtípusok listáját, így például beágyazhatsz egy tartalék betűtípust:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Nyugodtan hagyd ki ezt a blokkot, ha csak a **hiányzó betűtípusok nyomon követésére** van szükséged. A lényeg, hogy most már megvan az információ, amivel megalapozott döntést hozhatsz.

## 5. lépés – Mentsd el a feldolgozott dokumentumot

Végül persze el kell menteni a dokumentumot. Felülírhatod az eredetit, menthetsz egy új helyre, vagy exportálhatod PDF‑be – mindezt anélkül, hogy elveszítenéd a korábban rögzített figyelmeztetéseket.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Az egész osztály futtatása minden hiányzó betűtípusra kiírja a konzolt, és egy új `processed.docx` nevű fájlt hoz létre ugyanabban a mappában.

## Teljes működő példa

Az alábbiakban megtalálod a teljes Java osztályt, amelyet egyszerűen bemásolhatsz az IDE‑dbe. Tartalmazza a korábban bemutatott összes elemet, valamint egy apró `main` metódus burkolót.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Várt kimenet

Amikor a programot egy olyan dokumentummal futtatod, amely olyan betűtípust használ, amely nincs telepítve a rendszeredre, valami ilyesmit látsz majd:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Ha a dokumentum **nem tartalmaz hiányzó betűtípusokat**, a konzol csendben marad, amíg meg nem jelenik a végső „Document saved successfully.” sor – pontosan azt, amit egy jól működő **figyelmeztető visszahívás regisztrálása** implementációtól vársz.

## Profi tippek és gyakori buktatók

- **Több visszahívás?** Az Aspose.Words csak egy figyelmeztető kezelőt engedélyez. Ha egyszerre fájlba és a konzolra is szeretnél naplózni, valósíts meg egy kompozit visszahívást, amely továbbítja a figyelmeztetéseket több célpont felé.  
- **Nagy kötegek** – több száz fájl feldolgozásakor érdemes egyetlen `LoadOptions` példányt újrahasználni; minden fájlhoz új példány létrehozása felesleges terhelést jelent.  
- **Titkosított dokumentumok** – a jelszót állítsd be a `LoadOptions`‑ban a betöltés előtt, különben `IncorrectPasswordException` keletkezik, mielőtt a visszahívás egyáltalán lefutna.  
- **Teljesítmény** – a visszahívás szinkron módon fut. Ha távoli szolgáltatásba logolsz, puffereld az üzeneteket, és a betöltés befejezése után írd ki őket, hogy elkerüld az I/O szűk keresztmetszetet.  
- **Betűtípus‑fallback** – megadhatsz egy egyedi `FontSource` gyűjteményt is, ha saját, proprietás betűtípusokat szeretnél, amelyeket az Aspose.Words a rendszerbetűtípusok előtt vizsgál meg.

## Összegzés

Most már tudod, hogyan **regisztrálj figyelmeztető visszahívást** Java‑ban, hatékonyan **kövesd a hiányzó betűtípusokat**, és **testreszabhatod a dokumentum betöltését** az Aspose.Words‑szal. A megoldás önálló, egyetlen `main` metódussal futtatható, és azonnali láthatóságot biztosít minden olyan betűtípus‑helyettesítéshez, amely egyébként észrevétlen maradna.

Mi a következő lépés? Próbáld meg a visszahívást úgy kibővíteni, hogy a figyelmeztetéseket CSV fájlba írja audit célokra, vagy kombináld egy kötegfeldolgozóval, amely automatikusan beágyazza a hiányzó betűtípusokat. Felfedezheted továbbá a `IMAGE_SUBSTITUTION` vagy `DEPRECATED_FEATURE` típusú figyelmeztetéseket is – ugyanaz a minta alkalmazandó.

Boldog kódolást, és legyenek a dokumentumaid mindig úgy megjelenítve, ahogy eltervezted!

![Regisztrálja a figyelmeztető visszahívás diagramja](register-warning-callback.png "Regisztrálja a figyelmeztető visszahívás folyamata")


## Mit érdemes legközelebb megtanulni?

- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Customize Theme Colors & Fonts in Aspose.Words Java: A Comprehensive Guide](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}