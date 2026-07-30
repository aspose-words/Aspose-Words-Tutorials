---
date: 2025-12-27
description: Apprenez à définir les LoadOptions dans Aspose.Words pour Java, y compris
  comment spécifier le dossier temporaire, définir la version de Word, convertir les
  métafichiers en PNG et convertir les formes en équations pour un traitement de documents
  flexible.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Comment définir les LoadOptions dans Aspose.Words pour Java
url: /fr/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir LoadOptions dans Aspose.Words pour Java

Dans ce tutoriel, nous allons parcourir **comment définir LoadOptions** pour divers scénarios réels lors de l’utilisation d’Aspose.Words pour Java. LoadOptions vous offrent un contrôle fin sur la façon dont un document est ouvert — que vous ayez besoin de mettre à jour les champs sales, de travailler avec des fichiers chiffrés, de convertir des formes en Office Math, ou d’indiquer à la bibliothèque où stocker les données temporaires. À la fin, vous pourrez personnaliser le comportement de chargement pour répondre exactement aux exigences de votre application.

## Réponses rapides
- **Qu’est‑ce que LoadOptions ?** Un objet de configuration qui influence la façon dont Aspose.Words charge un document.  
- **Puis‑je mettre à jour les champs lors du chargement ?** Oui — définissez `setUpdateDirtyFields(true)`.  
- **Comment ouvrir un fichier protégé par mot de passe ?** Passez le mot de passe au constructeur de `LoadOptions`.  
- **Est‑il possible de changer le dossier temporaire ?** Utilisez `setTempFolder("path")`.  
- **Quelle méthode convertit les formes en Office Math ?** `setConvertShapeToOfficeMath(true)`.

## Pourquoi utiliser LoadOptions ?
LoadOptions vous permettent d’éviter les étapes de post‑traitement, de réduire la consommation de mémoire et de garantir que le document est interprété exactement comme vous le souhaitez. Par exemple, convertir les métafichiers en PNG pendant le chargement empêche les problèmes de rasterisation ultérieurs, et spécifier la version de MS Word aide à maintenir la fidélité de mise en page lors du traitement de fichiers anciens.

## Prérequis
- Java 17 ou version ultérieure  
- Aspose.Words pour Java (dernière version)  
- Une licence Aspose valide pour une utilisation en production  

## Guide étape par étape

### Mettre à jour les champs sales

Lorsqu’un document contient des champs qui ont été modifiés mais pas rafraîchis, vous pouvez demander à Aspose.Words de les mettre à jour automatiquement pendant le chargement.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*L’appel `setUpdateDirtyFields(true)` garantit que tous les champs sales sont recalculés dès que le document est ouvert.*

### Charger un document chiffré

Si votre fichier source est protégé par un mot de passe, fournissez‑le lors de la création de l’instance `LoadOptions`. Vous pouvez également définir un nouveau mot de passe lors de l’enregistrement dans un format différent.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Convertir une forme en Office Math

Certains documents anciens stockent les équations sous forme de formes dessinées. Activer cette option convertit ces formes en objets Office Math natifs, plus faciles à modifier par la suite.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### Définir la version de MS Word

Spécifier la version cible de Word aide la bibliothèque à choisir les règles de rendu appropriées, notamment lorsqu’il s’agit de formats de fichiers plus anciens.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Utiliser un dossier temporaire

Les documents volumineux peuvent générer des fichiers temporaires (par ex., lors de l’extraction d’images). Vous pouvez diriger ces fichiers vers un dossier de votre choix, ce qui est utile dans des environnements sandboxés.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Callback d’avertissement

Lors du chargement, Aspose.Words peut émettre des avertissements (par ex., fonctionnalités non prises en charge). Implémenter un callback vous permet de consigner ou de réagir à ces événements.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Convertir les métafichiers en PNG

Les métafichiers tels que WMF peuvent être rasterisés en PNG pendant le chargement, assurant un rendu cohérent sur toutes les plateformes.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Code source complet pour travailler avec LoadOptions dans Aspose.Words pour Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		// Prints warnings and their details as they arise during document loading.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Cas d’utilisation courants & astuces

- **Pipelines de conversion par lots** – Combinez `setTempFolder` avec un job planifié pour traiter des centaines de fichiers sans saturer le répertoire temporaire du système.  
- **Migration de documents anciens** – Utilisez `setMswVersion` conjointement avec `setConvertShapeToOfficeMath` pour faire passer d’anciens documents d’ingénierie vers un format moderne tout en conservant les équations.  
- **Gestion sécurisée des documents** – Associez `loadEncryptedDocument` à `OdtSaveOptions` pour re‑chiffrer les fichiers avec un nouveau mot de passe dans un format différent.  

## FAQ

**Q : Comment gérer les avertissements lors du chargement d’un document ?**  
R : Implémentez une interface personnalisée `IWarningCallback` (comme montré dans l’exemple *Callback d’avertissement*) et enregistrez‑la via `loadOptions.setWarningCallback(...)`. Cela vous permet de consigner, ignorer ou interrompre le processus selon la gravité de l’avertissement.

**Q : Puis‑je convertir des formes en objets Office Math lors du chargement d’un document ?**  
R : Oui—appelez `loadOptions.setConvertShapeToOfficeMath(true)` avant de créer le `Document`. La bibliothèque remplacera automatiquement les formes compatibles par des objets Office Math natifs.

**Q : Comment spécifier la version de MS Word pour le chargement d’un document ?**  
R : Utilisez `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (ou toute autre valeur de l’énumération) pour indiquer à Aspose.Words les règles de rendu de la version de Word souhaitée.

**Q : Quel est le rôle de la méthode `setTempFolder` dans LoadOptions ?**  
R : Elle dirige tous les fichiers temporaires générés pendant le chargement (comme les images extraites) vers un dossier que vous contrôlez, ce qui est essentiel dans les environnements où l’accès au répertoire temporaire système est limité.

**Q : Est‑il possible de convertir des métafichiers comme WMF en PNG pendant le chargement ?**  
R : Absolument—activez‑le avec `loadOptions.setConvertMetafilesToPng(true)`. Cela garantit que les images raster sont stockées au format PNG, améliorant la compatibilité avec les visionneuses modernes.

## Conclusion

Nous avons couvert les techniques essentielles pour **définir LoadOptions** dans Aspose.Words pour Java, de la mise à jour des champs sales à la gestion des fichiers chiffrés, en passant par la conversion des formes, la spécification de la version Word, la direction du stockage temporaire, et bien plus encore. En tirant parti de ces options, vous pouvez créer des pipelines de traitement de documents robustes et performants qui s’adaptent à une large gamme de scénarios d’entrée.

---

**Dernière mise à jour :** 2025-12-27  
**Testé avec :** Aspose.Words pour Java 24.11  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}