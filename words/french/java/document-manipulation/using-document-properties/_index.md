---
"description": "Optimisez la gestion de vos documents avec Aspose.Words pour Java. Apprenez à gérer les propriétés des documents, à ajouter des métadonnées personnalisées et bien plus encore dans ce tutoriel complet."
"linktitle": "Utilisation des propriétés du document"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Utilisation des propriétés de document dans Aspose.Words pour Java"
"url": "/fr/java/document-manipulation/using-document-properties/"
"weight": 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilisation des propriétés de document dans Aspose.Words pour Java


## Introduction aux propriétés du document

Les propriétés d'un document sont essentielles. Elles fournissent des informations supplémentaires sur le document lui-même, telles que son titre, son auteur, son sujet, ses mots-clés, etc. Dans Aspose.Words pour Java, vous pouvez manipuler les propriétés de document intégrées et personnalisées.

## Énumération des propriétés du document

### Propriétés intégrées

Pour récupérer et utiliser les propriétés de document intégrées, vous pouvez utiliser l'extrait de code suivant :

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

Ce code affichera le nom du document et les propriétés intégrées, y compris des propriétés telles que « Titre », « Auteur » et « Mots-clés ».

### Propriétés personnalisées

Pour travailler avec des propriétés de document personnalisées, vous pouvez utiliser l'extrait de code suivant :

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

Cet extrait de code montre comment ajouter des propriétés de document personnalisées, notamment une valeur booléenne, une chaîne, une date, un numéro de révision et une valeur numérique.

## Suppression des propriétés du document

Pour supprimer des propriétés spécifiques du document, vous pouvez utiliser le code suivant :

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Ce code supprime la propriété personnalisée « Date d'autorisation » du document.

## Configuration du lien vers le contenu

Dans certains cas, vous souhaiterez peut-être créer des liens dans votre document. Voici comment procéder :

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

    // Ajouter un lien vers la propriété de contenu.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Cet extrait de code montre comment créer un signet dans votre document et ajouter une propriété de document personnalisée qui renvoie à ce signet.

## Conversion entre les unités de mesure

Dans Aspose.Words pour Java, vous pouvez facilement convertir des unités de mesure. Voici un exemple :

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Définissez les marges en pouces.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Cet extrait de code définit différentes marges et distances en pouces en les convertissant en points.

## Utilisation des caractères de contrôle

Les caractères de contrôle peuvent être utiles dans le traitement du texte. Voici comment remplacer un caractère de contrôle dans votre texte :

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Remplacez le caractère de contrôle « \r » par « \r\n ».
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

Dans cet exemple, nous remplaçons le retour chariot (`\r`) avec un retour chariot suivi d'un saut de ligne (`\r\n`).

## Conclusion

Les propriétés de document jouent un rôle essentiel dans la gestion et l'organisation efficaces de vos documents dans Aspose.Words pour Java. Qu'il s'agisse de propriétés intégrées, de propriétés personnalisées ou d'utilisation de caractères de contrôle, vous disposez d'une gamme d'outils pour améliorer vos capacités de gestion documentaire.

## FAQ

### Comment accéder aux propriétés de document intégrées ?

Pour accéder aux propriétés de document intégrées dans Aspose.Words pour Java, vous pouvez utiliser le `getBuiltInDocumentProperties` méthode sur le `Document` objet. Cette méthode renvoie une collection de propriétés intégrées que vous pouvez parcourir.

### Puis-je ajouter des propriétés de document personnalisées à un document ?

Oui, vous pouvez ajouter des propriétés de document personnalisées à un document à l'aide de l' `CustomDocumentProperties` collection. Vous pouvez définir des propriétés personnalisées avec différents types de données, notamment des chaînes, des booléens, des dates et des valeurs numériques.

### Comment puis-je supprimer une propriété de document personnalisée spécifique ?

Pour supprimer une propriété de document personnalisée spécifique, vous pouvez utiliser le `remove` méthode sur le `CustomDocumentProperties` collection, en passant le nom de la propriété que vous souhaitez supprimer en paramètre.

### Quel est le but de créer un lien vers le contenu d’un document ?

Créer des liens vers le contenu d'un document permet de créer des références dynamiques vers des parties spécifiques du document. Cela peut être utile pour créer des documents interactifs ou des références croisées entre sections.

### Comment puis-je convertir entre différentes unités de mesure dans Aspose.Words pour Java ?

Vous pouvez convertir entre différentes unités de mesure dans Aspose.Words pour Java en utilisant le `ConvertUtil` classe. Il fournit des méthodes pour convertir des unités telles que des pouces en points, des points en centimètres, etc.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}