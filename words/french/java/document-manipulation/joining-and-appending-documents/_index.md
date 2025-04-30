---
"description": "Apprenez à joindre et à ajouter des documents facilement avec Aspose.Words pour Java. Préservez la mise en forme, gérez les en-têtes, les pieds de page et bien plus encore."
"linktitle": "Joindre et ajouter des documents"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Joindre et ajouter des documents dans Aspose.Words pour Java"
"url": "/fr/java/document-manipulation/joining-and-appending-documents/"
"weight": 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Joindre et ajouter des documents dans Aspose.Words pour Java


## Introduction à la jonction et à l'ajout de documents dans Aspose.Words pour Java

Dans ce tutoriel, nous découvrirons comment joindre et ajouter des documents à l'aide de la bibliothèque Aspose.Words pour Java. Vous apprendrez à fusionner facilement plusieurs documents tout en préservant leur mise en forme et leur structure.

## Prérequis

Avant de commencer, assurez-vous que l’API Aspose.Words pour Java est configurée dans votre projet Java.

## Options de jonction de documents

### Ajout simple

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Ajouter avec les options de format d'importation

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Ajouter à un document vierge

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Ajouter avec conversion de numéro de page

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Convertir les champs NUMPAGES
dstDoc.updatePageLayout(); // Mettre à jour la mise en page pour une numérotation correcte
```

## Gestion des différentes configurations de page

Lors de l'ajout de documents avec des configurations de page différentes :

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Assurez-vous que les paramètres de configuration de la page correspondent au document de destination
```

## Joindre des documents avec des styles différents

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Comportement de style intelligent

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Insertion de documents avec DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Conserver la numérotation des sources

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Gestion des zones de texte

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Gestion des en-têtes et des pieds de page

### Lier les en-têtes et les pieds de page

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Dissocier les en-têtes et les pieds de page

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Conclusion

Aspose.Words pour Java offre des outils flexibles et puissants pour joindre et ajouter des documents, que vous ayez besoin de conserver la mise en forme, de gérer différentes mises en page ou de gérer les en-têtes et pieds de page. Expérimentez ces techniques pour répondre à vos besoins spécifiques en matière de traitement de documents.

## FAQ

### Comment puis-je joindre des documents avec des styles différents de manière transparente ?

Pour joindre des documents avec des styles différents, utilisez `ImportFormatMode.USE_DESTINATION_STYLES` lors de l'ajout.

### Puis-je conserver la numérotation des pages lors de l'ajout de documents ?

Oui, vous pouvez conserver la numérotation des pages en utilisant le `convertNumPageFieldsToPageRef` méthode et mise à jour de la mise en page.

### Qu'est-ce que le comportement Smart Style ?

Le comportement de style intelligent permet de maintenir des styles cohérents lors de l'ajout de documents. À utiliser avec `ImportFormatOptions` pour de meilleurs résultats.

### Comment puis-je gérer les zones de texte lors de l'ajout de documents ?

Ensemble `importFormatOptions.setIgnoreTextBoxes(false)` pour inclure des zones de texte lors de l'ajout.

### Que faire si je souhaite lier/dissocier les en-têtes et les pieds de page entre les documents ?

Vous pouvez lier les en-têtes et les pieds de page avec `linkToPrevious(true)` ou les dissocier avec `linkToPrevious(false)` selon les besoins.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}