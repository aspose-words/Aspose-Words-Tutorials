---
category: general
date: 2026-08-07
description: Aspose.Words ActiveX‑tutorial laat zien hoe je een CommandButton‑besturingselement
  toevoegt aan een Word‑document met Java. Leer de volledige code, configuratie en
  opslaanstappen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: nl
lastmod: 2026-08-07
og_description: De Aspose.Words ActiveX‑tutorial legt uit hoe je een CommandButton
  ActiveX‑besturingselement in een Word‑document kunt insluiten met Java. Volg het
  volledige voorbeeld om het document te maken, te configureren en op te slaan.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Aspose.Words ActiveX-tutorial – Java stap‑voor‑stapgids
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Aspose.Words ActiveX‑tutorial – een CommandButton invoegen met Java
url: /nl/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX‑tutorial – een CommandButton invoegen met Java

Als je een ActiveX‑besturingselement in een Word‑bestand wilt insluiten, leidt deze **Aspose.Words ActiveX‑tutorial** je door het volledige proces. Je ziet hoe je een leeg document maakt, een CommandButton invoegt, de eigenschappen instelt en het resultaat opslaat – allemaal met gewone Java‑code.

Het voorbeeld maakt gebruik van de Aspose.Words for Java‑API, waardoor Microsoft Office niet nodig is op de build‑server. Aan het einde van deze gids kun je .docx‑bestanden genereren die volledig functionele CommandButton‑besturingselementen bevatten, klaar voor gebruik in Windows‑omgevingen.

## Vereisten

Zorg er voordat je begint voor dat je het volgende hebt:

- Java Development Kit (JDK) 8 of nieuwer geïnstalleerd.
- Maven of een ander build‑tool om afhankelijkheden te beheren.
- Een Aspose.Words for Java‑licentie (of een tijdelijke evaluatiesleutel) om evaluatiewatermerken te vermijden.
- Basiskennis van Java‑syntaxis en object‑georiënteerd programmeren.

> **Pro tip:** Voeg de Aspose.Words Maven‑dependency toe aan je `pom.xml` zodat de IDE de klassen automatisch kan vinden:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Stap 1: Maak een nieuw leeg document en een `DocumentBuilder`

De `Document`‑klasse vertegenwoordigt het Word‑bestand in het geheugen, terwijl `DocumentBuilder` een vloeiende API biedt voor het bewerken van het document. Het initialiseren van beide objecten maakt het document klaar voor verdere aanpassingen.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Waarom dit belangrijk is:**  
`DocumentBuilder` houdt de huidige cursorpositie bij, zodat elke daaropvolgende invoegbewerking – zoals het toevoegen van een besturingselement – precies op de gewenste plaats verschijnt.

## Stap 2: Een CommandButton ActiveX‑besturingselement invoegen

Aspose.Words biedt `Forms2OleControl` voor ActiveX‑objecten. De methode `insertForms2OleControl` vereist het type besturingselement, dat je opgeeft via de enumeratie `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Uitleg:**  
Het ingevoegde besturingselement is een COM‑gebaseerd object dat Word zal weergeven als een klikbare knop wanneer het document wordt geopend in een Windows‑omgeving.

## Stap 3: De eigenschappen van de knop configureren

Na het invoegen kun je de naam, bijschrift, grootte en positie van de knop aanpassen. Deze eigenschappen bepalen hoe het besturingselement eruitziet en zich gedraagt binnen Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Waarom deze instellingen belangrijk zijn:**  

- **Name** – Maakt het mogelijk dat VBA‑macro's naar het besturingselement verwijzen (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Bepaalt het zichtbare label waarop gebruikers klikken.
- **Left / Top** – Regelt de plaatsing ten opzichte van de paginamarges.
- **Width / Height** – Zorgt voor een consistente visuele grootte op verschillende schermresoluties.

## Stap 4: Het document opslaan

Het aanroepen van `save` schrijft de in‑memory‑representatie naar een fysiek bestand. Je kunt elk ondersteund formaat kiezen (`.docx`, `.doc`, `.pdf`, enz.). Voor deze tutorial houden we het bij het native Word‑formaat.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Resultaat:**  
Het openen van `ActiveXDemo.docx` in Microsoft Word toont een CommandButton met het label **Submit** op de opgegeven coördinaten. Klikken op de knop activeert het standaardgedrag (er is standaard geen VBA‑code gekoppeld).

## Volledige broncode

Als je de onderdelen samenvoegt, ziet het complete, uitvoerbare programma er als volgt uit:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Verwachte output

- Een bestand met de naam **ActiveXDemo.docx** in de map `output`.
- Wanneer geopend in Microsoft Word (Windows), toont het document een klikbare **Submit**‑knop op de gedefinieerde positie.
- De knop kan worden geselecteerd, verplaatst of via de Word‑UI (Developer → Properties) aan VBA‑code gekoppeld.

## Veelvoorkomende variaties behandelen

| Scenario | Aanpassing |
|----------|------------|
| **Opslaan als .doc** (oud formaat) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Een gebeurtenis‑handler toevoegen** | Word stelt geen ActiveX‑gebeurtenissen beschikbaar via Aspose.Words. Je moet handmatig VBA‑code toevoegen nadat het document is gegenereerd. |
| **Meerdere besturingselementen** | Herhaal het invoeg‑/configuratie‑blok met verschillende `setName`‑ en `setCaption`‑waarden. |
| **Ander besturingselementtype (bijv. CheckBox)** | Gebruik `Forms2OleControlType.CHECKBOX` in de `insertForms2OleControl`‑aanroep. |
| **Niet‑Windows‑platforms** | ActiveX‑besturingselementen worden alleen gerenderd in Word op Windows. Voor cross‑platformoplossingen, overweeg content controls (`StructuredDocumentTag`). |

## Best practices en valkuilen

- **Licentie vroegtijdig** – Registreer je Aspose.Words‑licentie vóór het aanmaken van het `Document` om evaluatie‑prompts te vermijden.
- **Coördinatensysteem** – Posities worden gemeten in points (1 pt = 1/72 in). Converteer van pixels of centimeters als je UI‑ontwerp die eenheden gebruikt.
- **Bestandspaden** – Gebruik absolute paden of de Java `Paths`‑API om `FileNotFoundException` te voorkomen wanneer de output‑directory niet bestaat.
- **Thread‑veiligheid** – `Document` en `DocumentBuilder` zijn niet thread‑safe. Maak aparte instanties per thread als je documenten parallel genereert.
- **Testen** – Controleer het gegenereerde document op de doel‑Word‑versie (bijv. Word 2016, Word 365) omdat oudere versies ActiveX‑besturingselementen anders kunnen weergeven.

## Conclusie

Deze **Aspose.Words ActiveX‑tutorial** laat zien hoe je programmatically een CommandButton‑besturingselement toevoegt aan een Word‑document met Java. Je hebt geleerd hoe je:

1. Een `Document` en `DocumentBuilder` initialiseert.
2. Een `Forms2OleControl` van het type `COMMAND_BUTTON` invoegt.
3. De naam, het bijschrift, de grootte en de positie van de knop instelt.
4. Het document opslaat als een .docx‑bestand dat het ActiveX‑besturingselement bevat.

Vanaf hier kun je extra besturingselementtypen verkennen, VBA‑macro‑injectie automatiseren, of ActiveX‑besturingselementen combineren met andere Aspose.Words‑functies zoals mail‑merge en content controls. Experimenteer met verschillende lay-outs en integreer de gegenereerde documenten in je grotere Java‑gebaseerde rapportage‑pipeline.

---


## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Convert Word to RTF with Aspose.Words for Java Tutorial](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}