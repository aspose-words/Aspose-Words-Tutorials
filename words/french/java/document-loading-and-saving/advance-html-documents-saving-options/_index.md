---
date: 2025-12-19
description: Apprenez à exporter du HTML avec Aspose.Words Java, en couvrant les options
  avancées pour enregistrer Word en HTML et convertir Word en HTML efficacement.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Comment exporter du HTML avec Aspose.Words Java : options avancées'
url: /fr/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comment exporter du HTML avec Aspose.Words Java : options avancées

Dans ce tutoriel, vous découvrirez **comment exporter du HTML** à partir de documents Word en utilisant Aspose.Words for Java. Que vous ayez besoin de **sauvegarder Word en HTML** pour la publication web ou de **convertir Word en HTML** pour un traitement en aval, les options d’enregistrement avancées vous offrent un contrôle fin sur le résultat. Nous passerons en revue chaque option étape par étape, expliquerons quand l’utiliser et montrerons des scénarios concrets où ces paramètres font la différence.

## Réponses rapides
- **Quelle est la classe principale pour l’export HTML ?** `HtmlSaveOptions`  
- **Les polices peuvent‑elles être intégrées directement dans le HTML ?** Oui, définissez `exportFontsAsBase64` sur `true`.  
- **Comment conserver les données de round‑trip spécifiques à Word ?** Activez `exportRoundtripInformation`.  
- **Quel format est le meilleur pour les graphiques vectoriels ?** Utilisez `convertMetafilesToSvg` pour une sortie SVG.  
- **Est‑il possible d’éviter les collisions de noms de classes CSS ?** Oui, utilisez `addCssClassNamePrefix`.

## 1. Introduction
Aspose.Words for Java est une API robuste qui permet aux développeurs de manipuler des documents Word de façon programmatique. Ce guide se concentre sur les options avancées d’enregistrement de documents HTML qui vous permettent d’adapter le processus de conversion aux exigences spécifiques du web ou de l’intégration.

## 2. Exporter les informations de round‑trip
Conserver les informations de round‑trip vous permet de reconvertir le HTML en document Word sans perdre la mise en page ou les détails de formatage.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### Quand l’utiliser
- Lorsque vous avez besoin d’un pipeline de conversion réversible (HTML → Word → HTML).  
- Idéal pour les scénarios d’édition collaborative où la structure Word d’origine doit être conservée.

## 3. Exporter les polices en Base64
Intégrer les polices directement dans le HTML élimine les dépendances externes et garantit la fidélité visuelle sur tous les navigateurs.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Astuce pro
Utilisez cette option lorsque l’environnement cible a un accès limité aux ressources externes (par ex. newsletters par e‑mail).

## 4. Exporter les ressources
Contrôlez la façon dont les ressources CSS et de police sont émises, et spécifiez un dossier ou un alias d’URL personnalisé pour ces actifs.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

### Pourquoi c’est important
Séparer le CSS dans un fichier externe réduit la taille du HTML et permet la mise en cache pour des chargements de page plus rapides.

## 5. Convertir les métafichiers en EMF ou WMF
Les métafichiers (par ex. EMF/WMF) sont convertis vers un format que les navigateurs peuvent rendre de façon fiable.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n                    vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

### Cas d’utilisation
Choisissez EMF/WMF lorsque les navigateurs cibles supportent ces formats vectoriels et que vous avez besoin d’un redimensionnement sans perte.

## 6. Convertir les métafichiers en SVG
Le SVG offre la meilleure évolutivité et est largement supporté par les navigateurs modernes.

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

### Avantage
Les fichiers SVG sont légers et gardent le document indépendant de la résolution, parfait pour le design web réactif.

## 7. Ajouter un préfixe aux noms de classes CSS
Évitez les conflits de styles en préfixant tous les noms de classes CSS générés.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Conseil pratique
Utilisez un préfixe unique (par ex. le nom de votre projet) lors de l’insertion du HTML dans des pages existantes afin d’éviter les conflits CSS.

## 8. Exporter les URL CID pour les ressources MHTML
Lors de l’enregistrement au format MHTML, vous pouvez exporter les ressources en utilisant des URL Content‑ID pour une meilleure compatibilité e‑mail.

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

### Quand l’utiliser
Idéal pour générer un fichier HTML autonome qui peut être joint à des e‑mails.

## 9. Résoudre les noms de polices
Assure que le HTML fait référence aux bonnes familles de polices, améliorant la cohérence multiplateforme.

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

### Pourquoi c’est utile
Si le document original utilise des polices non installées sur la machine cliente, cette option les remplace par des alternatives web‑safe.

## 10. Exporter le champ de formulaire texte comme texte
Rendre les champs de formulaire sous forme de texte brut au lieu d’éléments d’entrée HTML interactifs.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// The folder specified needs to exist and should be empty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Set an option to export form fields as plain text, not as HTML input elements.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

### Cas d’utilisation
Lorsque vous avez besoin d’une représentation en lecture seule d’un formulaire à des fins d’archivage ou d’impression.

## Pièges courants & Dépannage
| Problème | Cause typique | Solution |
|----------|---------------|----------|
| Polices manquantes dans la sortie | `exportFontsAsBase64` non activé | Définir `setExportFontsAsBase64(true)` |
| CSS cassé après l’intégration | Utilisation de `EXTERNAL` sans fournir le fichier CSS | S’assurer que le fichier CSS est déployé à l’`resourceFolderAlias` indiqué |
| Taille HTML trop importante | Intégration de nombreuses images en Base64 | Passer à des ressources d’image externes via `setExportFontResources(true)` et configurer `resourceFolder` |
| SVG ne s’affiche pas dans les anciens navigateurs | Le navigateur ne supporte pas le SVG | Fournir un PNG de secours en exportant également en EMF/WMF |

## Questions fréquentes

**Q : Puis‑je à la fois intégrer les polices en Base64 et garder le CSS externe ?**  
R : Oui. Définissez `exportFontsAsBase64(true)` tout en conservant `CssStyleSheetType.EXTERNAL` pour séparer les données de police des règles de style.

**Q : Comment convertir un HTML existant en document Word ?**  
R : Chargez le HTML avec `Document doc = new Document("input.html");` puis `doc.save("output.docx");`. Conservez les données de round‑trip en utilisant `exportRoundtripInformation` lors de l’export initial.

**Q : Y a‑t‑il un impact sur les performances lors de la conversion en SVG ?**  
R : La conversion de gros métafichiers en SVG peut augmenter le temps de traitement, mais le HTML résultant est généralement plus petit et s’affiche plus rapidement dans les navigateurs.

**Q : Ces options fonctionnent‑elles également avec Aspose.Words pour .NET ?**  
R : Les mêmes concepts existent dans l’API .NET, bien que les noms de méthodes puissent différer légèrement (par ex. `HtmlSaveOptions` est partagé entre les plateformes).

**Q : Quelle option choisir pour un HTML adapté aux e‑mails ?**  
R : Utilisez `SaveFormat.MHTML` avec `exportCidUrlsForMhtmlResources` pour intégrer toutes les ressources directement dans le corps du message.

---

**Dernière mise à jour :** 2025-12-19  
**Testé avec :** Aspose.Words for Java 24.12  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}