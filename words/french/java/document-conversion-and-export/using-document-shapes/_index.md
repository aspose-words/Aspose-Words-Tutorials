---
date: 2026-02-16
description: Apprenez à créer une zone de texte, ajouter un filigrane de texte, regrouper
  plusieurs formes, définir le rapport d’aspect d’une forme et placer une forme dans
  une cellule de tableau en utilisant Aspose.Words pour Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Comment créer une zone de texte et utiliser les formes de document dans Aspose.Words
  pour Java
url: /fr/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilisation des formes de document dans Aspose.Words for Java

## Introduction à l'utilisation des formes de document dans Aspose.Words for Java

Dans ce guide complet, **vous apprendrez à create text box** des objets et d'autres formes puissantes avec Aspose.Words for Java. Les formes vous permettent d'enrichir les documents Word avec des bulles d'appel, des boutons, des filigranes, SmartArt, et plus encore—les rendant visuellement attrayants et interactifs. Nous parcourrons des exemples concrets, depuis l'insertion d'une simple zone de texte jusqu'au groupement de plusieurs formes, à la définition des rapports d'aspect, et au placement des formes à l'intérieur des cellules de tableau.

## Réponses rapides
- **Quelle est la façon principale d'ajouter une text box ?** Utilisez `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Puis-je regrouper des formes ensemble ?** Oui – créez un `GroupShape` et ajoutez des formes enfants.
- **Comment verrouiller ou déverrouiller le rapport d'aspect d'une forme ?** Appelez `shape.setAspectRatioLocked(true/false)`.
- **Est-il possible d'ajouter un filigrane avec une forme ?** Absolument – insérez un `Shape` avec `TEXT_PLAIN_TEXT` et définissez son remplissage/contour.
- **Les diagrammes SmartArt fonctionnent-ils avec Aspose.Words ?** Oui – détectez avec `shape.hasSmartArt()` et mettez à jour via `shape.updateSmartArtDrawing()`.

## Qu'est-ce qu'une text box et pourquoi créer des formes de text box ?

Une text box est un conteneur qui peut contenir du texte formaté, des images ou d'autres formes. Utiliser **create text box** dans votre automatisation vous permet de placer du contenu flottant n'importe où sur une page, idéal pour les annotations, les bulles d'appel ou les éléments décoratifs sans modifier le flux principal du document.

## Comment ajouter une forme

Avant de plonger dans le code, assurez-vous qu'Aspose.Words for Java est référencé dans votre projet. Si vous ne l'avez pas encore ajouté, téléchargez la bibliothèque depuis le site officiel :

[Télécharger Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Ajout de formes aux documents

## Comment regrouper plusieurs formes

Un `GroupShape` vous permet de traiter plusieurs formes individuelles comme une seule unité—utile pour les déplacer ou les faire pivoter ensemble.

### Insertion d'un GroupShape

Voici un exemple complet qui crée un groupe, ajoute deux formes différentes, et insère le groupe dans le document.

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

## Comment créer une text box (create text box)

### Insertion d'une forme Text Box

La méthode `insertShape` facilite l'ajout d'une text box. L'exemple ci-dessous montre deux façons de positionner et de faire pivoter une text box.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Comment définir le rapport d'aspect d'une forme

### Gestion du rapport d'aspect

Parfois, vous avez besoin qu'une forme s'étire sans conserver ses proportions d'origine. Le fragment suivant montre comment déverrouiller le rapport d'aspect d'une forme image.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Comment placer une forme dans une cellule de tableau

### Placement d'une forme à l'intérieur d'une cellule de tableau

Voici un exemple étape par étape qui crée un tableau, puis insère une forme de filigrane positionnée par rapport à la page mais pouvant également être placée à l'intérieur d'une cellule.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## Travail avec les formes SmartArt

### Détection des formes SmartArt

Vous pouvez trouver de manière programmatique les objets SmartArt dans un document en utilisant la méthode `hasSmartArt()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Mise à jour des dessins SmartArt

Une fois que vous avez localisé les formes SmartArt, vous pouvez rafraîchir leurs données de dessin internes avec `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Conclusion

Dans ce guide, nous avons couvert comment **create text box** des objets, regrouper plusieurs formes, ajuster les rapports d'aspect, intégrer des formes dans des cellules de tableau, ajouter des filigranes, et travailler avec des diagrammes SmartArt en utilisant Aspose.Words for Java. Ces techniques vous permettent de créer des documents Word richement formatés et interactifs de manière programmatique.

## FAQ

### Qu'est-ce qu'Aspose.Words for Java ?

Aspose.Words for Java est une bibliothèque Java qui permet aux développeurs de créer, modifier et convertir des documents Word de manière programmatique. Elle offre un large éventail de fonctionnalités et d'outils pour travailler avec des documents dans divers formats.

### Comment puis‑je télécharger Aspose.Words for Java ?

Vous pouvez télécharger Aspose.Words for Java depuis le site Aspose en suivant ce lien : [Télécharger Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Quels sont les avantages d'utiliser les formes de document ?

Les formes de document ajoutent des éléments visuels et de l'interactivité à vos documents, les rendant plus attrayants et informatifs. Avec les formes, vous pouvez créer des bulles d'appel, des boutons, des images, des filigranes, et plus encore, améliorant l'expérience utilisateur globale.

### Puis‑je personnaliser l'apparence des formes ?

Oui, vous pouvez personnaliser l'apparence des formes en ajustant leurs propriétés telles que la taille, la position, la rotation et la couleur de remplissage. Aspose.Words for Java offre de nombreuses options pour la personnalisation des formes.

### Aspose.Words for Java est‑il compatible avec SmartArt ?

Oui, Aspose.Words for Java prend en charge les formes SmartArt, vous permettant de travailler avec des diagrammes et graphiques complexes dans vos documents.

## Questions fréquemment posées

**Q : Puis‑je combiner une text box avec une image à l'intérieur de la même forme ?**  
R : Oui. Insérez une image dans la forme text box en utilisant `builder.insertImage()` après avoir créé la forme, puis ajustez sa mise en page selon les besoins.

**Q : Comment garantir qu'un filigrane apparaît derrière tout le contenu du document ?**  
R : Définissez le `WrapType` de la forme sur `NONE` et ajustez son `RelativeHorizontalPosition` et `RelativeVerticalPosition` sur `PAGE`. Cela place le filigrane derrière le flux principal.

**Q : Est‑il possible d'animer une forme groupée dans Word ?**  
R : Bien qu'Aspose.Words puisse créer et regrouper des formes, les fonctionnalités d'animation ne sont pas prises en charge car elles dépendent des capacités de l'interface utilisateur de Word.

**Q : Quelle version d'Aspose.Words est requise pour la prise en charge de SmartArt ?**  
R : La détection et la mise à jour de SmartArt sont disponibles à partir d'Aspose.Words 20.9 pour Java et versions ultérieures.

**Q : La bibliothèque gère‑t‑elle efficacement les gros documents contenant de nombreuses formes ?**  
R : Oui. Utilisez `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` ou une version supérieure pour améliorer les performances sur les documents contenant de nombreuses formes.

---

**Dernière mise à jour :** 2026-02-16  
**Testé avec :** Aspose.Words for Java 24.12  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}