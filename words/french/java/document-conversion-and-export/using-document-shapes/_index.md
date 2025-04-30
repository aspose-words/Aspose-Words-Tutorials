---
"description": "Exploitez la puissance des formes de documents dans Aspose.Words pour Java. Apprenez à créer des documents visuellement attrayants grâce à des exemples détaillés."
"linktitle": "Utilisation des formes de document"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Utilisation des formes de document dans Aspose.Words pour Java"
"url": "/fr/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilisation des formes de document dans Aspose.Words pour Java


## Introduction à l'utilisation des formes de document dans Aspose.Words pour Java

Dans ce guide complet, nous explorerons l'univers des formes de documents dans Aspose.Words pour Java. Les formes sont essentielles à la création de documents attrayants et interactifs. Que vous ayez besoin d'ajouter des légendes, des boutons, des images ou des filigranes, Aspose.Words pour Java fournit les outils nécessaires. Voyons comment utiliser ces formes étape par étape avec des exemples de code source.

## Premiers pas avec les formes de documents

Avant de passer au code, configurons notre environnement. Assurez-vous d'avoir intégré Aspose.Words pour Java à votre projet. Si ce n'est pas déjà fait, vous pouvez le télécharger depuis le site web d'Aspose. [Télécharger Aspose.Words pour Java](https://releases.aspose.com/words/java/)

## Ajout de formes aux documents

### Insertion d'une GroupShape

UN `GroupShape` permet de regrouper plusieurs formes. Voici comment créer et insérer un `GroupShape`:

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

### Insertion d'une forme de zone de texte

Pour insérer une forme de zone de texte, vous pouvez utiliser le `insertShape` méthode comme indiqué dans l'exemple ci-dessous :

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

## Manipulation des propriétés de forme

### Gestion du rapport hauteur/largeur

Vous pouvez contrôler si le rapport hauteur/largeur d'une forme est verrouillé ou non. Voici comment déverrouiller le rapport hauteur/largeur d'une forme :

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Placer une forme dans une cellule de tableau

Si vous devez placer une forme à l'intérieur d'une cellule de tableau, vous pouvez y parvenir avec le code suivant :

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
watermark.isLayoutInCell(true); // Affichez la forme en dehors de la cellule du tableau si elle doit être placée dans une cellule.
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

## Travailler avec des formes SmartArt

### Détection des formes SmartArt

Vous pouvez détecter des formes SmartArt dans un document à l’aide du code suivant :

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Mise à jour des dessins SmartArt

Pour mettre à jour les dessins SmartArt dans un document, utilisez le code suivant :

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Conclusion

Dans ce guide, nous avons exploré l'univers des formes de documents dans Aspose.Words pour Java. Vous avez appris à ajouter diverses formes à vos documents, à manipuler leurs propriétés et à utiliser des formes SmartArt. Grâce à ces connaissances, vous pouvez créer facilement des documents attrayants et interactifs.

## FAQ

### Qu'est-ce qu'Aspose.Words pour Java ?

Aspose.Words pour Java est une bibliothèque Java permettant aux développeurs de créer, modifier et convertir des documents Word par programmation. Elle offre un large éventail de fonctionnalités et d'outils pour travailler avec des documents de différents formats.

### Comment puis-je télécharger Aspose.Words pour Java ?

Vous pouvez télécharger Aspose.Words pour Java depuis le site Web d'Aspose en suivant ce lien : [Télécharger Aspose.Words pour Java](https://releases.aspose.com/words/java/)

### Quels sont les avantages de l’utilisation de formes de documents ?

Les formes ajoutent des éléments visuels et interactifs à vos documents, les rendant plus attrayants et informatifs. Elles vous permettent de créer des légendes, des boutons, des images, des filigranes et bien plus encore, améliorant ainsi l'expérience utilisateur.

### Puis-je personnaliser l’apparence des formes ?

Oui, vous pouvez personnaliser l'apparence des formes en ajustant leurs propriétés telles que la taille, la position, la rotation et la couleur de remplissage. Aspose.Words pour Java offre de nombreuses options de personnalisation.

### Aspose.Words pour Java est-il compatible avec SmartArt ?

Oui, Aspose.Words pour Java prend en charge les formes SmartArt, vous permettant de travailler avec des diagrammes et des graphiques complexes dans vos documents.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}