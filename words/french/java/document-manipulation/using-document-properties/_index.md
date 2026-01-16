---
date: 2026-01-16
description: Apprenez à convertir les pouces en points, à lire les métadonnées d’un
  document en Java, à ajouter des propriétés personnalisées en Java et à définir les
  marges de page en Java avec Aspose.Words pour Java.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Convertir les pouces en points – Utilisation des propriétés du document dans
  Aspose.Words pour Java
url: /fr/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Convertir les pouces en points – Utilisation des propriétés de document dans Aspose.Words pour Java

Dans ce tutoriel, vous découvrirez comment **convertir les pouces en points** lors de la définition des marges de page, lire les métadonnées d'un document en Java, ajouter des propriétés personnalisées en Java, et travailler avec les propriétés de document intégrées à l'aide d'Aspose.Words pour Java. Que vous génériez des rapports, des factures ou des documents juridiques, maîtriser ces techniques vous donne un contrôle précis sur l'apparence et les métadonnées de vos fichiers Word.

## Réponses rapides
- **Comment convertir les pouces en points ?** Utilisez `ConvertUtil.inchToPoint(value)` d'Aspose.Words.
- **Puis-je lire les métadonnées d'un document en Java ?** Oui – appelez `doc.getBuiltInDocumentProperties()` ou `doc.getCustomDocumentProperties()`.
- **Comment ajouter une propriété personnalisée en Java ?** Utilisez `doc.getCustomDocumentProperties().add(name, value)`.
- **Quelle méthode définit les marges de page en points ?** `PageSetup.setTopMargin`, `setBottomMargin`, etc., acceptent des valeurs en points.
- **Le lien vers un signet est‑il pris en charge ?** Oui – utilisez `addLinkToContent` sur la collection des propriétés personnalisées.

## Introduction aux propriétés de document

Les propriétés de document sont une partie essentielle de tout fichier Word. Elles stockent des informations telles que le titre, l'auteur, le sujet, les mots‑clés, ainsi que toute métadonnée personnalisée dont vous avez besoin pour le traitement en aval. Dans Aspose.Words pour Java, vous pouvez manipuler à la fois les propriétés intégrées et personnalisées d'un document, et vous pouvez également contrôler les détails de mise en page comme les marges en convertissant les unités de mesure (par exemple **convertir les pouces en points**).

## Qu’est‑ce que « convertir les pouces en points » ?

Dans Word, les mesures de mise en page sont exprimées en points (1 point = 1/72 de pouce). Convertir les pouces en points vous permet de définir les marges, les retraits et les espacements en utilisant des unités impériales familières, tandis que l'API travaille en interne avec des points.

## Pourquoi gérer les métadonnées de document en Java ?

Intégrer des métadonnées facilite la recherche, la catégorisation et l'automatisation des flux de travail. Par exemple, vous pouvez marquer un contrat avec un indicateur « Autorisé » ou stocker un numéro de révision pour les pistes d'audit. Lire et écrire ces informations de façon programmatique garantit la cohérence sur de grands lots de documents.

## Prérequis
- Java 17+ (ou JDK compatible)
- Bibliothèque Aspose.Words pour Java ajoutée à votre projet (Maven/Gradle)
- Un fichier `.docx` d'exemple (par ex., `Properties.docx`) placé dans un répertoire accessible

## Guide étape par étape

### Énumération des propriétés de document intégrées

Voici un test simple qui ouvre un document et affiche toutes les propriétés intégrées telles que Titre, Auteur et Mots‑clés.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Astuce :** Utilisez cet extrait pour vérifier que vos métadonnées ont été correctement écrites lors des étapes précédentes.

### Ajout de propriétés de document personnalisées (add custom properties java)

Les propriétés personnalisées vous permettent de stocker tout type de données dont vous avez besoin — booléen, chaîne, date, nombre, etc.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Pourquoi c’est important :** Ajouter un indicateur comme **Authorized** peut piloter les flux d'approbation en aval sans modifier le contenu du document.

### Suppression d’une propriété personnalisée

Si une propriété n'est plus nécessaire, vous pouvez la supprimer proprement.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Configuration d’un lien vers le contenu (liaison de signet)

Vous pouvez créer un signet puis ajouter une propriété personnalisée qui pointe vers ce signet, permettant des références croisées dynamiques.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Conversion entre unités de mesure (set page margins java)

C’est ici que le mot‑clé principal brille. Nous définissons les marges en pouces, puis **convertissons les pouces en points** à l’aide de `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Remarque :** `ConvertUtil` fournit également `pointToInch`, `mmToPoint`, etc., pour une gestion flexible de la mise en page.

### Utilisation des caractères de contrôle (read document metadata java)

Les caractères de contrôle vous aident à nettoyer les flux de texte. Cet exemple remplace un retour chariot (`\r`) par la séquence de saut de ligne Windows (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Problèmes courants et solutions

| Problème | Cause | Solution |
|----------|-------|----------|
| Les marges sont incorrectes après conversion | Utilisation de la mauvaise unité (par ex., cm au lieu de pouces) | Vérifiez que vous appelez `ConvertUtil.inchToPoint` pour les valeurs en pouces |
| La propriété personnalisée n'apparaît pas | Propriété ajoutée après l'enregistrement du document | Appelez `doc.save(...)` après avoir ajouté les propriétés |
| Le lien du signet est cassé | Erreur de frappe du nom du signet | Assurez‑vous que le nom du signet correspond exactement dans `addLinkToContent` |

## FAQ

### Comment accéder aux propriétés de document intégrées ?

Pour accéder aux propriétés de document intégrées dans Aspose.Words pour Java, vous pouvez utiliser la méthode `getBuiltInDocumentProperties` sur l'objet `Document`. Cette méthode renvoie une collection de propriétés intégrées que vous pouvez parcourir.

### Puis‑je ajouter des propriétés de document personnalisées à un document ?

Oui, vous pouvez ajouter des propriétés de document personnalisées à un document en utilisant la collection `CustomDocumentProperties`. Vous pouvez définir des propriétés personnalisées avec divers types de données, y compris des chaînes, des booléens, des dates et des valeurs numériques.

### Comment supprimer une propriété de document personnalisée spécifique ?

Pour supprimer une propriété de document personnalisée spécifique, vous pouvez utiliser la méthode `remove` sur la collection `CustomDocumentProperties`, en passant le nom de la propriété à supprimer comme paramètre.

### Quel est le but du lien vers le contenu à l'intérieur d'un document ?

Lier du contenu à l'intérieur d'un document vous permet de créer des références dynamiques vers des parties spécifiques du document. Cela peut être utile pour créer des documents interactifs ou des références croisées entre les sections.

### Comment convertir entre différentes unités de mesure dans Aspose.Words pour Java ?

Vous pouvez convertir entre différentes unités de mesure dans Aspose.Words pour Java en utilisant la classe `ConvertUtil`. Elle fournit des méthodes pour convertir des unités telles que pouces en points, points en centimètres, etc.

## Questions fréquemment posées

**Q : Comment lire les métadonnées d'un document Java sans charger le fichier complet ?**  
R : Utilisez `DocumentInfo` pour récupérer les propriétés de base sans charger entièrement le contenu du document.

**Q : Puis‑je définir les marges de page en Java de façon programmatique pour des documents existants ?**  
R : Oui — ouvrez le document, modifiez les marges de `PageSetup` (convertissez les pouces en points si nécessaire), puis enregistrez.

**Q : Est‑il possible d'exporter les propriétés personnalisées vers les métadonnées PDF ?**  
R : Lors de l'enregistrement au format PDF, Aspose.Words mappe automatiquement les propriétés de document personnalisées aux métadonnées personnalisées du PDF.

**Q : Les caractères de contrôle affectent‑ils la conversion PDF ?**  
R : Ils sont conservés pendant la conversion ; cependant, vous pouvez vouloir normaliser les fins de ligne pour plus de cohérence.

**Q : Quelle version d'Aspose.Words est requise pour `ConvertUtil` ?**  
R : `ConvertUtil` est disponible depuis Aspose.Words 16.5 ; toute version récente le prend en charge.

## Conclusion

En maîtrisant **convertir les pouces en points**, la lecture des métadonnées de document en Java et l'ajout de propriétés personnalisées en Java, vous obtenez un contrôle complet à la fois sur la mise en page visuelle et les données cachées de vos fichiers Word. Ces capacités vous permettent de créer des pipelines de documents automatisés, d'assurer la conformité et de générer des rapports richement formatés — le tout avec Aspose.Words pour Java.

---

**Dernière mise à jour :** 2026-01-16  
**Testé avec :** Aspose.Words for Java 24.11  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}