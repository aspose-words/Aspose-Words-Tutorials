---
"date": "2025-03-29"
"description": "Leer hoe u documenten optimaal kunt opslaan met Aspose.Words voor Python met behulp van XAML-stroomopmaak en voortgangscallbacks. Verbeter de efficiëntie van documentbeheer."
"title": "Optimaliseren van het opslaan van documenten in Python&#58; Aspose.Words XAML-stroom en voortgangscallbacks"
"url": "/nl/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---
{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
# Hoe u het opslaan van documenten in Python kunt optimaliseren met Aspose.Words: XAML-flow- en voortgangscallbacks

## Invoering

Wilt u documentconversies efficiënt beheren met Python? Heeft u moeite met het verwerken van afbeeldingen en het bijhouden van de voortgang tijdens het opslaan van documenten? Deze tutorial begeleidt u bij het optimaliseren van het opslaan van documenten met Aspose.Words voor Python, met de nadruk op twee krachtige functies: `XamlFlowSaveOptions` met terugbelfunctie voor de voortgang van het opslaan van afbeeldingen en documenten.

Deze uitgebreide handleiding is perfect voor ontwikkelaars die hun documentverwerkingsworkflows willen verbeteren met behulp van de Aspose.Words-bibliotheek.

**Wat je leert:**
- Hoe u een document in XAML-stroomformaat kunt opslaan en tegelijkertijd de afbeeldingsbronnen kunt beheren.
- Implementeer voortgangs-callbacks tijdens het opslaan van documenten om langdurige bewerkingen te voorkomen.
- Aspose.Words voor Python installeren en configureren in uw ontwikkelomgeving.
- Toepassingen van deze functies in de praktijk in documentbeheersystemen.

Laten we eens kijken naar de vereisten voordat we beginnen met coderen!

## Vereisten

Voordat u begint, moet u ervoor zorgen dat u over het volgende beschikt:

### Vereiste bibliotheken en versies
- **Aspose.Words voor Python**: Zorg ervoor dat u versie 23.3 of hoger hebt.
- **Python**: Versie 3.6 of hoger wordt aanbevolen.

### Vereisten voor omgevingsinstellingen
- Een code-editor zoals VSCode of PyCharm.
- Basiskennis van Python-programmering.

### Kennisvereisten
- Kennis van concepten voor documentverwerking.
- Kennis van bestandsbeheer en directorybeheer in Python.

## Aspose.Words instellen voor Python

Om Aspose.Words te gebruiken, moet je het via pip installeren. Open je terminal of opdrachtprompt en voer het volgende uit:

```bash
pip install aspose-words
```

### Stappen voor het verkrijgen van een licentie
1. **Gratis proefperiode**: Toegang tot een tijdelijke licentie [hier](https://purchase.aspose.com/temporary-license/) voor testdoeleinden.
2. **Aankoop**: Voor langdurig gebruik, koop een licentie [hier](https://purchase.aspose.com/buy).
3. **Basisinitialisatie en -installatie**:
   - Laad uw document met behulp van `aw.Document()`.
   - Configureer indien nodig opslagopties.

## Implementatiegids

In deze sectie wordt u stapsgewijs begeleid bij het implementeren van de twee belangrijkste functies uit deze tutorial: XamlFlowSaveOptions met Image Folder en Document Saving Progress Callback.

### Functie 1: XamlFlowSaveOptions met afbeeldingsmap

#### Overzicht
Met deze functie kunt u een document opslaan in XAML-stroomformaat en daarbij een afbeeldingsmap en alias opgeven. Dit is ideaal voor het efficiënt beheren van grote documenten met ingesloten afbeeldingen.

#### Implementatiestappen

##### Stap 1: Importeer de benodigde bibliotheken
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### Stap 2: Definieer de ImageUriPrinter Callback-klasse
Deze klasse telt afbeeldingsstromen en leidt deze om naar een opgegeven aliasmap tijdens de conversie.

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # type: Lijst[str]

        def image_saving(self, args: aw.saving.ImageSavingArgs):
            self.resources.append(args.image_file_name)
            with open(f"{self.images_folder_alias}/{args.image_file_name}", "wb") as image_stream:
                args.image_stream = image_stream
            args.keep_image_stream_open = False

    def test_image_folder(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Rendering.docx")
        callback = self.ImageUriPrinter(YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias")

        options = aw.saving.XamlFlowSaveOptions()
        options.images_folder = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolder"
        options.images_folder_alias = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias"
        options.image_saving_callback = callback

        os.makedirs(options.images_folder_alias, exist_ok=True)
        
        doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.image_folder.xaml", options)

        for resource in callback.resources:
            print(f"{callback.images_folder_alias}/{resource}")
```
**Belangrijkste configuratieopties:**
- `images_folder`: Geeft de map aan waar afbeeldingen worden opgeslagen.
- `images_folder_alias`: Hiermee stelt u een aliaspad in dat wordt gebruikt tijdens de documentconversie.

##### Tips voor probleemoplossing
- Controleer of alle mappen bestaan voordat u de code uitvoert. Zo voorkomt u fouten doordat het bestand niet is gevonden.
- Controleer de schrijfrechten in uw uitvoermap.

### Functie 2: Terugbelfunctie voor de voortgang van het opslaan van documenten

#### Overzicht
Met deze functie wordt het opslagproces beheerd met behulp van een voortgangs-callback, zodat u langdurige opslagbewerkingen kunt annuleren.

#### Implementatiestappen

##### Stap 1: Definieer de SavingProgressCallback-klasse
De klasse bewaakt de duur van het opslaan van het document en annuleert het opslaan als een bepaalde tijdslimiet wordt overschreden.

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # Maximale toegestane duur in sec.

        def notify(self, args: aw.saving.DocumentSavingArgs):
            canceled_at = datetime.now()
            elapsed_seconds = (canceled_at - self.saving_started_at).total_seconds()
            if elapsed_seconds > self.max_duration:
                raise OperationCanceledException(f"estimated_progress = {args.estimated_progress}; canceled_at = {canceled_at}")

    def test_progress_callback(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        parameters = [
            (aw.SaveFormat.XAML_FLOW, "xamlflow"),
            (aw.SaveFormat.XAML_FLOW_PACK, "xamlflowpack"),
        ]

        for save_format, ext in parameters:
            doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Big document.docx")
            save_options = aw.saving.XamlFlowSaveOptions(save_format)
            save_options.progress_callback = self.SavingProgressCallback()

            try:
                doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.progress_callback.{ext}", save_options)
            except OperationCanceledException as e:
                print(e)
```
**Belangrijkste configuratieopties:**
- `save_format`: Kies tussen XAML_FLOW en XAML_FLOW_PACK.
- `progress_callback`: Controleert de voortgang van het opslaan, zodat langdurige bewerkingen kunnen worden afgehandeld.

##### Tips voor probleemoplossing
- Aanpassen `max_duration` gebaseerd op de grootte en complexiteit van het document.
- Ga op een elegante manier om met uitzonderingen, zodat er informatieve foutmeldingen worden weergegeven.

## Praktische toepassingen

Hier zijn enkele praktijkvoorbeelden van deze functies:
1. **Documentbeheersystemen**: Beheer grote documenten met ingesloten afbeeldingen efficiënt door afbeeldingsmappen op te geven, waardoor de prestaties en organisatie worden verbeterd.
2. **Geautomatiseerde rapportagetools**: Gebruik voortgangs-callbacks om ervoor te zorgen dat rapporten binnen acceptabele tijdsbestekken worden gegenereerd en zo de gebruikerservaring te verbeteren.
3. **Contentdistributienetwerken**: Stroomlijn de conversie van documenten voor distributie via internet en beheer tegelijkertijd uw middelen effectief.

## Prestatieoverwegingen

Om de prestaties te optimaliseren bij het gebruik van Aspose.Words met Python:
- **Geheugenbeheer**: Controleer het resourcegebruik en beheer het geheugen efficiënt door objecten na gebruik weg te gooien.
- **Bestand I/O-bewerkingen**: Minimaliseer lees-/schrijfbewerkingen om de snelheid te verbeteren.
- **Batchverwerking**: Verwerk documenten waar mogelijk in batches om overheadkosten te beperken.

## Conclusie

In deze tutorial hebben we onderzocht hoe je het opslaan van documenten kunt optimaliseren met Aspose.Words voor Python met behulp van XAML Flow en voortgangscallbacks. Door deze functies te implementeren, kun je de efficiëntie van je documentverwerkingsworkflows verbeteren, resources effectief beheren en tijdige processen garanderen.
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}