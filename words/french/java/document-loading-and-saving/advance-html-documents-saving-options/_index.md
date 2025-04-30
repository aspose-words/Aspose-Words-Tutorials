---
"description": "Dans ce tutoriel, nous avons abordé diverses options avancées d'enregistrement de documents HTML avec Aspose.Words pour Java. Ces options vous permettent de créer du HTML de haute qualité."
"linktitle": "Enregistrer des documents HTML avec"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Options avancées d'enregistrement de documents HTML avec Aspose.Words Java"
"url": "/fr/java/document-loading-and-saving/advance-html-documents-saving-options/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Options avancées d'enregistrement de documents HTML avec Aspose.Words Java


Dans ce tutoriel, nous explorerons les options avancées d'enregistrement de documents HTML offertes par Aspose.Words pour Java. Aspose.Words est une puissante API Java pour travailler avec des documents Word et offre un large éventail de fonctionnalités pour la manipulation et la conversion de documents.

## 1. Introduction
Aspose.Words pour Java vous permet de travailler avec des documents Word par programmation. Dans ce tutoriel, nous nous concentrerons sur les options avancées d'enregistrement de documents HTML, qui vous permettent de contrôler la conversion des documents Word en HTML.

## 2. Exporter les informations aller-retour
Le `exportRoundtripInformation` Cette méthode permet d'exporter des documents Word au format HTML tout en préservant les informations de retour. Ces informations peuvent être utiles pour reconvertir du HTML au format Word sans perdre les détails spécifiques du document.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Exporter les polices au format Base64
Avec le `exportFontsAsBase64` Cette méthode vous permet d'exporter les polices utilisées dans le document sous forme de données codées en Base64 dans le code HTML. Cela garantit que la représentation HTML conserve les mêmes styles de police que le document Word d'origine.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Exporter des ressources
Le `exportResources` Cette méthode vous permet de spécifier le type de feuille de style CSS et d'exporter les ressources de polices. Vous pouvez également définir un dossier de ressources et un alias pour les ressources dans le code HTML.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://exemple.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

## 5. Convertir les métafichiers en EMF ou WMF
Le `convertMetafilesToEmfOrWmf` La méthode vous permet de convertir les métafichiers du document au format EMF ou WMF, garantissant ainsi la compatibilité et un rendu fluide en HTML.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Point rouge\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Convertir les métafichiers en SVG
Utilisez le `convertMetafilesToSvg` Méthode de conversion de métafichiers au format SVG. Ce format est idéal pour afficher des graphiques vectoriels dans des documents HTML.

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

## 7. Ajouter un préfixe de nom de classe CSS
Avec le `addCssClassNamePrefix` Cette méthode vous permet d'ajouter un préfixe aux noms de classes CSS dans le code HTML exporté. Cela permet d'éviter les conflits avec les styles existants.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Exporter les URL CID pour les ressources MHTML
Le `exportCidUrlsForMhtmlResources` La méthode est utilisée lors de l'enregistrement de documents au format MHTML. Elle permet d'exporter les URL Content-ID des ressources.

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

## 9. Résoudre les noms de police
Le `resolveFontNames` La méthode permet de résoudre les noms de police lors de l'enregistrement de documents au format HTML, garantissant ainsi un rendu cohérent sur différentes plates-formes.

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

## 10. Exporter le champ de saisie de texte sous forme de texte
Le `exportTextInputFormFieldAsText` la méthode exporte les champs de formulaire sous forme de texte brut dans le HTML, les rendant ainsi facilement lisibles et modifiables.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// Le dossier spécifié doit exister et doit être vide.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Définissez une option pour exporter les champs de formulaire sous forme de texte brut et non sous forme d'éléments d'entrée HTML.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Conclusion
Dans ce tutoriel, nous avons exploré les options avancées d'enregistrement de documents HTML offertes par Aspose.Words pour Java. Ces options vous offrent un contrôle précis du processus de conversion, vous permettant de créer des documents HTML très similaires aux documents Word d'origine.

## FAQ
Voici quelques questions fréquemment posées sur l'utilisation d'Aspose.Words pour Java et les options d'enregistrement de documents HTML :

### Q1 : Comment puis-je reconvertir du HTML au format Word à l'aide d'Aspose.Words pour Java ?
Pour reconvertir du HTML au format Word, vous pouvez utiliser les API Aspose.Words `load` méthode pour charger le document HTML puis l'enregistrer au format Word.

### Q2 : Puis-je personnaliser les styles CSS lors de l’exportation vers HTML ?
Oui, vous pouvez personnaliser les styles CSS en modifiant les feuilles de style utilisées dans le HTML ou en utilisant le `addCssClassNamePrefix` méthode pour ajouter un préfixe aux noms de classe CSS.

### Q3 : Existe-t-il un moyen d’optimiser la sortie HTML pour l’affichage Web ?
Oui, vous pouvez optimiser la sortie HTML pour l'affichage Web en configurant des options telles que l'exportation de polices au format Base64 et la conversion de métafichiers en SVG.

### Q4 : Existe-t-il des limitations lors de la conversion de documents Word complexes en HTML ?
Bien qu'Aspose.Words pour Java offre de puissantes capacités de conversion, les documents Word complexes avec des mises en page complexes peuvent nécessiter un post-traitement supplémentaire pour obtenir la sortie HTML souhaitée.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}