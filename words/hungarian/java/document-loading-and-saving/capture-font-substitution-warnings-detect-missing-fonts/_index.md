---
category: general
date: 2026-04-04
description: Rögzítse a betűtípuscsere‑figyelmeztetéseket a Word‑dokumentumok betöltésekor
  az Aspose.Words for Java használatával, és automatikusan észlelje a hiányzó betűtípusokat.
  Kövesse ezt a lépésről‑lépésre útmutatót.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: hu
og_description: Rögzítse a betűtípus-helyettesítési figyelmeztetéseket Word-dokumentumok
  betöltésekor az Aspose.Words for Java-val, és néhány egyszerű lépésben észlelje
  a hiányzó betűtípusokat.
og_title: Betűkészlet-helyettesítési figyelmeztetések rögzítése – Hiányzó betűkészletek
  felderítése
tags:
- Aspose.Words
- Java
- Document Processing
title: Betűtípus‑helyettesítési figyelmeztetések rögzítése – Hiányzó betűtípusok felderítése
url: /hu/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Betűkészlet helyettesítési figyelmeztetések rögzítése – Hiányzó betűkészletek észlelése

Valaha is szükséged volt **betűkészlet helyettesítési figyelmeztetések rögzítésére** egy Word fájl megnyitásakor, csak hogy rájöjj, hogy egy fontos betűtípus hiányzik? Nem vagy egyedül. Sok vállalati munkafolyamatban egy hiányzó betűkészlet tökéletesen formázott jelentést is összezavarhat, és az egyetlen jelzés egy csendes figyelmeztetés, amit a legtöbb fejlesztő soha nem lát.

A jó hír, hogy az Aspose.Words for Java lehetővé teszi, hogy beavatkozz a betöltési folyamatba, és **hiányzó betűkészleteket észlelj**, mielőtt később problémát okoznának. Ebben az útmutatóban egy teljes, futtatható példán keresztül vezetünk, amely minden helyettesítési figyelmeztetést közvetlenül a konzolra ír, így eldöntheted, hogy beágyazod a megfelelő betűtípust, lecseréled, vagy értesíted a felhasználót.

A végére a következőket fogod tudni:

* Beállíts egy `LoadOptions` objektumot egy egyedi figyelmeztetési visszahívással.
* Szűrd a visszahívást, hogy csak a betűkészlet‑helyettesítési eseményekre reagáljon.
* Tölts be bármilyen `.docx` fájlt, és azonnal lásd a figyelmeztetéseket.
* Bővítsd a megoldást, hogy naplózza a figyelmeztetéseket, kivételt dobjon, vagy akár automatikusan telepítse a hiányzó betűkészleteket.

Nem szükséges külső dokumentáció – csak néhány Java sor és az Aspose.Words JAR.

## Előkövetelmények

Mielőtt belemerülnénk, győződj meg róla, hogy a következők rendelkezésre állnak:

* Telepített Java 8 vagy újabb (a legújabb LTS verzió a legjobb).
* Aspose.Words for Java 23.11 vagy újabb – letöltheted a Maven artefaktust vagy a sima JAR-t az Aspose weboldaláról.
* Egy Word dokumentum, amely olyan betűkészletet hivatkozik, ami nincs a fejlesztői gépedre telepítve (pl. „MyFancyFont”).
* Egy általad választott IDE vagy szövegszerkesztő – én az IntelliJ IDEA-t használom, de az Eclipse vagy a VS Code is megfelelő.

Ha bármelyik ismeretlennek tűnik, állj meg és telepítsd előbb; a többi útmutató feltételezi, hogy készen állnak.

---

## Betűkészlet helyettesítési figyelmeztetések rögzítése az Aspose.Words segítségével

A megoldás központja egy `LoadOptions` példányban rejlik. Egy `IWarningCallback` hozzárendelésével elkapjuk a könyvtár által a betöltési fázis során kibocsátott minden figyelmeztetést.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Miért működik ez:**  
`LoadOptions` megmondja az Aspose.Words-nek, hogyan kezelje a bejövő fájlt. Az `IWarningCallback` interfész egy horgot biztosít, amely *minden* figyelmeztetéshez egy `WarningInfo` objektumot kap. Az `info.getWarningType()` ellenőrzésével kiszűrjük mindent, kivéve a `SUBSTITUTED_FONT` típusút. A `description` tulajdonság emberi olvasásra alkalmas üzenetet tartalmaz, például: “Font 'MyFancyFont' was substituted with 'Arial'”.

### Várható konzolkimenet

Ha a forrásdokumentum olyan betűkészletet hivatkozik, amely nincs telepítve, valami ilyesmit látsz:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Ha a dokumentum csak olyan betűkészleteket használ, amelyek a gépen telepítve vannak, a visszahívás csendben marad, és csak a végső “Document loaded successfully.” sor jelenik meg.

---

## Hiányzó betűkészletek észlelése a dokumentumban

Elgondolkodhatsz, *„Ugyanaz a helyettesítési figyelmeztetés, mint a hiányzó betűkészlet?”* A legtöbb esetben igen – az Aspose.Words egy hiányzó betűkészletet helyettesítő betűtípussal helyettesít, és ezt a `SUBSTITUTED_FONT` segítségével jelzi. Vannak azonban olyan szélhelyzetek, amikor a betűkészlet jelen van, de a pontos stílus (félkövér‑dőlt, specifikus OpenType funkciók) nem, ami finom helyettesítést eredményez.

Ahhoz, hogy teljesen biztos legyél benne, hogy minden hiányt elkaptál, kombinálhatod a figyelmeztetési visszahívást egy betöltés utáni ellenőrzéssel:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Pro tipp:** Ha találsz olyan futásokat, amelyek még mindig a hiányzó betűkészletre hivatkoznak, helyben kicserélheted őket:

```java
font.setName("Arial"); // fallback
```

Így garantálod a konzisztens vizuális eredményt, még akkor is, ha az eredeti figyelmeztetés el lett nyomva.

---

## Gyakori buktatók és hogyan kerüld el őket

| Buktató | Miért fordul elő | Megoldás |
|---------|------------------|----------|
| **Elfelejtett visszahívás beállítása** | `LoadOptions` alapértelmezés szerint egy üres visszahívást használ, ezért a figyelmeztetések eltűnnek. | Mindig hívd meg a `loadOptions.setWarningCallback(...)` metódust a betöltés előtt. |
| **Rossz figyelmeztetéstípus használata** | `WarningType.SUBSTITUTED_FONT` az egyetlen enum, amely a hiányzó betűkészleteket jelzi. | Szűrd pontosan a `WarningType.SUBSTITUTED_FONT` értékre; a többi típus (pl. `UNKNOWN_FILE_FORMAT`) nem kapcsolódik. |
| **Fájlutak keménykódolása** | Helyben működik, de CI/CD csővezetékekben hibát okoz. | Használj relatív útvonalat, vagy add át a fájl helyét parancssori argumentumként. |
| **Unicode betűkészletek figyelmen kívül hagyása** | Néhány hiányzó betűkészlet csak bizonyos karaktereknél jelent problémát. | Tesztelj egy olyan dokumentummal, amely a támogatni kívánt teljes karakterkészletet tartalmazza. |
| **Fej nélküli szerveren futtatás betűkészlet-konfiguráció nélkül** | A szerveren előfordulhat, hogy nincs semmilyen tartalék betűkészlet, ami váratlan helyettesítéseket eredményez. | Telepíts egy minimális, gyakori betűkészletet (Arial, Times New Roman) a szerverre. |

---

## A megoldás bővítése

Most, hogy **rögzíted a betűkészlet helyettesítési figyelmeztetéseket**, szeretnéd:

* **Figyelmeztetések naplózása fájlba** – cseréld le a `System.out.println`-t egy naplózóval, például SLF4J-re.
* **Kivétel dobása** – hasznos automatizált csővezetékekben, ahol a hiányzó betűkészletnek a buildet kell hibára állítania:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Hiányzó betűkészletek automatikus telepítése** – a szükséges TTF/OTF letöltése futásidőben, és hozzáadása a Java `GraphicsEnvironment`-hez. Ez egy fejlettebb forgatókönyv, de teljesen megvalósítható.

---

## Diagram (opcionális)

![Betűkészlet helyettesítési figyelmeztetések folyamatábra, amely a LoadOptions → WarningCallback → Konzol kimenetet mutatja](capture-font-substitution-warnings-diagram.png)

*Alt text:* “Betűkészlet helyettesítési figyelmeztetések folyamatábra, amely bemutatja, hogyan irányítja az Aspose.Words a hiányzó betűkészlet figyelmeztetéseket egy egyedi visszahívásba.”

---

## Összegzés

Most bemutattuk, hogyan **rögzítsd a betűkészlet helyettesítési figyelmeztetéseket** és **észleld a hiányzó betűkészleteket** a Word dokumentumok Java‑os Aspose.Words‑szel történő betöltésekor. Egy `LoadOptions` objektum konfigurálásával és egy apró `IWarningCallback` megvalósításával teljes rálátást kapsz a betűkészlet‑tartalék folyamatára, lehetővé téve a naplózást, cserét vagy a hiányzó betűtípusok esetén a folyamat megszakítását.

Röviden: állítsd be a visszahívást, szűrd a `SUBSTITUTED_FONT` típusra, töltsd be a dokumentumot, és kezeld a kimenetet a saját alkalmazásod igényei szerint. Innen tovább bővítheted naplózási keretrendszerekre, CI ellenőrzésekre vagy akár automatikus betűkészlet‑ellátásra.

Szeretnél továbbmenni? Próbáld ki:

* **Betűkészletek beágyazása** közvetlenül a mentett dokumentumba (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` a `FontEmbeddingMode.EMBED_ALL` használatával).
* **PDF generálása** a betűkészletek javítása után, biztosítva, hogy a végső kimenet pontosan úgy nézzen ki, ahogy szeretnéd.
* **Egy teljes mappát átvizsgálni** a dokumentumokban a hiányzó betűkészletekért, és egy összefoglaló jelentést készíteni.

Ez egyelőre minden—boldog kódolást, és legyenek a dokumentumaid mindig a megfelelő betűtípussal megjelenítve!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}