---
category: general
date: 2026-06-17
description: Naplózza a betűkészlet-helyettesítési figyelmeztetéseket Java-ban az
  Aspose.Words használatával – rögzítse a hiányzó betűkészleteket a dokumentum betöltésekor,
  és tartsa konzisztensnek a kimenetet.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: hu
og_description: Regisztrálja a betűtípus‑helyettesítési figyelmeztetéseket Java‑ban
  az Aspose.Words segítségével. Tanulja meg, hogyan rögzítse a hiányzó betűtípusok
  figyelmeztetéseit a dokumentum betöltésekor, és tartsa PDF‑jeit hibátlanul.
og_title: Betűtípus-helyettesítési figyelmeztetések naplózása Java-ban – Teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Betűtípus-helyettesítési figyelmeztetések naplózása Java-ban az Aspose.Words
  használatával
url: /hu/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Betűkészlet helyettesítési figyelmeztetések naplózása Java‑ban – Teljes útmutató

Gondolkodtál már azon, hogyan **naplózhatod a betűkészlet helyettesítési figyelmeztetéseket**, amikor egy Word‑dokumentum olyan betűtípust tölt be, amely nincs a szerveren? Nem vagy egyedül, aki a csendben helyettesített hiányzó betűtípusok miatt vakargatja a fejét. A jó hír? Az Aspose.Words for Java tiszta módot biztosít arra, hogy a betöltés pillanatában elkapd ezeket a helyettesítéseket.

Ebben a bemutatóban egy gyakorlati példán keresztül mutatjuk be, hogyan regisztrálj egy figyelmeztetési visszahívást, szűrd le a betűkészlet‑helyettesítési riasztásokat, és írd ki őket a konzolra (vagy bármely általad preferált naplózóba). A végére egy újrahasználható kódrészletet kapsz, amelyet bármely Java‑projektbe beilleszthetsz, amely **Aspose.Words Java**‑t használ.

## Amit megtanulsz

- Hogyan konfiguráld a **LoadOptions**‑t a figyelmeztetések rögzítéséhez.
- Hogyan valósíts meg egy **IWarningCallback**‑et, amely csak a **font substitution** eseményekre reagál.
- Hogyan tölts be egy dokumentumot biztonságosan, miközben tiszta audit nyomot hagysz a hiányzó betűtípusokról.
- Tippek a megoldás kiterjesztésére fájl‑alapú naplók vagy felügyeleti rendszerek felé.

### Előfeltételek

- Java 8 vagy újabb (a kód Java 11‑tel is működik).
- Aspose.Words for Java könyvtár (ajánlott a 23.10 vagy újabb verzió).
- Egy minta `.docx`, amely olyan betűtípust hivatkozik, amely nincs telepítve a gépeden (pl. `MissingFont.docx`).

Nem szükséges további keretrendszer – csak tiszta Java és az Aspose.JAR‑ok.

---

## 1. lépés: LoadOptions konfigurálása Aspose.Words Java‑hoz

Mielőtt bármilyen figyelmeztetést el tudnál kapni, szükséged van egy **LoadOptions** példányra. Ez az objektum azt mondja meg az Aspose.Words‑nek, hogyan viselkedjen a bejövő fájl feldolgozása során.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Miért kritikus ez a lépés? `LoadOptions` objektum nélkül a könyvtár csendben helyettesíti a hiányzó betűtípusokat, és te sosem látsz semmilyen nyomot. Ha explicit módon létrehozod, megnyílik a lehetőség egy egyedi **warning callback** használatára, amely pontosan azt naplózza, ami számodra fontos.

> **Pro tipp:** Ha sok dokumentumot töltesz be kötegelt módon, használd újra ugyanazt a `LoadOptions` példányt, hogy elkerüld a felesleges objektum‑létrehozást.

---

## 2. lépés: Figyelmeztetési visszahívás megvalósítása betűkészlet‑helyettesítéshez

Az Aspose.Words a `IWarningCallback` interfészt biztosítja. Ennek megvalósításával eldöntheted, mit tegyél, amikor a motor `WarningInfo`‑t generál. Ebben az esetben csak a `WarningType.FONT_SUBSTITUTION`‑ra szeretnénk reagálni.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Néhány fontos megjegyzés:

1. **Szűrés** – Az `if` utasítás biztosítja, hogy a nem releváns figyelmeztetéseket (például elrendezési problémákat) figyelmen kívül hagyjuk, és a napló rendezett maradjon.
2. **Szálbiztonság** – A visszahívás ugyanazon a szálon fut, amely a dokumentumot betölti, így egyszerű konzol‑kimenet esetén nincs szükség extra szinkronizációra. Ha közös naplóba írsz, győződj meg róla, hogy az szálbiztos.
3. **Bővíthetőség** – Szeretnél fájlba írni? Cseréld le a `System.out.println`‑t `java.util.logging.Logger`‑re vagy egy harmadik‑fél logolási keretrendszerre.

---

## 3. lépés: Dokumentum betöltése a konfigurált beállításokkal

Most, hogy a visszahívás be van állítva, töltsd be a Word‑fájlt. Amint az Aspose.Words feldolgozza a dokumentumot, minden hiányzó betűtípus aktiválja a fent definiált visszahívást.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Ha a forrásfájl olyan betűtípust hivatkozik, amely nincs telepítve, a kimenet hasonló lesz ehhez:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Ez a sor a **log font substitution warnings**, amelyet kerestél. Most már cselekedhetsz – például felhívhatod a felhasználó figyelmét, átválthatsz egy tartalék stíluslapra, vagy egyszerűen nyilvántarthatod a megfelelőség érdekében.

---

## 4. lépés: Normál feldolgozás folytatása

A betöltés után a dokumentum úgy viselkedik, mint bármely más `Document` objektum. Nyugodtan vizsgáld meg a szekciókat, extraháld a szöveget, vagy konvertáld PDF‑be. A figyelmeztetések naplózása automatikusan megtörténik a betöltési lépés során, így nincs szükség extra kódra.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

A konzol most már megjeleníti a betűkészlet‑helyettesítési figyelmeztetést (ha van) **és** a szekciók számát, ezzel megerősítve, hogy a dokumentum teljesen funkcionális.

---

## Haladó tippek és szélhelyzetek

### Naplózás fájlba a konzol helyett

Ha tartós naplót szeretnél, cseréld le a `System.out.println` hívást egy `FileWriter`‑re:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Ne felejtsd el a `IOException`‑t megfelelően kezelni a produkciós kódban.

### Több dokumentum feldolgozása ciklusban

Mappában lévő dokumentumok feldolgozásakor újra felhasználhatod ugyanazt a visszahívást:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Mivel a visszahívás a `loadOptions`‑hoz van csatolva, minden iteráció automatikusan naplózza a betűkészlet‑helyettesítési eseményeket.

### Beágyazott betűtípusok kezelése

Az Aspose.Words képes beágyazni a hiányzó betűtípusokat, ha engedélyezed:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Még a beágyazás bekapcsolt állapotában is a figyelmeztetési visszahívás aktiválódik, így láthatóvá válik, mi lett helyettesítve.

---

## Teljes működő példa

Az alábbiakban a kész, futtatható program látható. Másold be egy `FontSubstitutionDiagnostics.java` nevű osztályba, állítsd be a fájlútvonalat, és futtasd.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Várható kimenet** (feltételezve, hogy a forrásdokumentum hiányzó betűtípust hivatkozik):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

A konzol és a `font_substitution_log.txt` egyaránt tartalmazni fogja a figyelmeztetést, megbízható audit nyomot biztosítva.

---

## Következtetés

Most megmutattuk, hogyan **naplózhatod a betűkészlet helyettesítési figyelmeztetéseket** Java‑ban az Aspose.Words segítségével. A `LoadOptions` konfigurálásával, egy `IWarningCallback` bekötésével és a dokumentum betöltésével teljes rálátást kapsz minden hiányzó betűtípus‑eseményre, amely egyébként észrevétlen maradhatna. Innen tovább:

- Figyelmeztetéseket irányíthatsz egy központi naplózási szolgáltatás felé.
- Riasztásokat indíthatsz minőség‑ellenőrző folyamatokhoz.
- Kombinálhatod ezt a technikát más **document loading** stratégiákkal, például PDF‑konverzióval vagy levél‑összevonással.

Nyugodtan kísérletezz – cseréld le a konzol‑naplózót SLF4J‑ra, adj hozzá időbélyeget, vagy küldj riasztásokat egy felügyeleti műszerfalra. A fő minta változatlan marad, és most már szilárd alapod van a robusztus betűkészlet‑kezeléshez bármely Java‑alapú dokumentum‑munkafolyamatban.

Van egy saját trükköd, amit megosztanál? Lehet, hogy már integráltad ezt Spring Boot‑tal vagy egy felhő‑funkcióval. Írj egy megjegyzést alább, és tartsuk fenn a beszélgetést. Boldog kódolást!

## Mit tanulj meg legközelebb?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek további API‑funkciók elsajátításában és alternatív megvalósítási megközelítések felfedezésében saját projektjeidben.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}