---
date: 2025-12-14
description: Apprenez comment **insérer une forme d'image** avec Aspose.Words pour
  Java. Ce guide vous montre comment ajouter des formes, créer des formes de zone
  de texte, placer des formes dans des tableaux, définir le rapport d’aspect des formes
  et ajouter des formes d’appel.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Utilisation des formes de document dans Aspose.Words pour Java
url: /fr/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comment **insérer une forme d'image** avec Aspose.Words for Java

Dans ce tutoriel complet, vous découvrirez comment **insérer des formes d'image** dans des documents Word à l'aide d'Aspose.Words for Java. Que vous créiez des rapports, du matériel marketing ou des formulaires interactifs, les formes vous permettent d'ajouter des bulles d'appel, des boutons, des zones de texte, des filigranes et même du SmartArt. Nous parcourrons chaque étape, expliquerons pourquoi utiliser une forme particulière et fournirons des extraits de code prêts à l'exécution.

## Réponses rapides
- **Quelle est la façon principale d'ajouter une forme ?** Utilisez `DocumentBuilder.insertShape` ou créez une instance `Shape` et ajoutez‑la à l'arbre du document.  
- **Puis‑je insérer une image sous forme de forme ?** Oui – appelez `builder.insertImage` puis traitez le `Shape` retourné comme n'importe quel autre.  
- **Comment conserver le ratio d'aspect d'une forme ?** Définissez `shape.setAspectRatioLocked(true)` ou `false` selon vos besoins.  
- **Est‑il possible de regrouper des formes ?** Absolument – encapsulez‑les dans un `GroupShape` et insérez le groupe comme un seul nœud.  
- **Les diagrammes SmartArt fonctionnent‑ils avec Aspose.Words ?** Oui, vous pouvez détecter et mettre à jour les SmartArt programmatiquement.

## Qu'est‑ce que **insérer une forme d'image** ?
Une *forme d'image* est un élément visuel qui contient des graphiques raster ou vectoriels à l'intérieur d'un document Word. Dans Aspose.Words, une image est représentée par un objet `Shape`, vous offrant un contrôle complet sur la taille, la position, la rotation et l'habillage.

## Pourquoi utiliser des formes dans vos documents ?
- **Impact visuel :** Les formes attirent l'attention sur les informations clés.  
- **Interactivité :** Les boutons et les bulles d'appel peuvent être liés à des URL ou des signets.  
- **Flexibilité de mise en page :** Positionnez les graphiques avec précision grâce à des coordonnées absolues ou relatives.  
- **Automatisation :** Générez des mises en page complexes sans édition manuelle.

## Prérequis
- Java Development Kit (JDK 8 ou supérieur)  
- Bibliothèque Aspose.Words for Java (téléchargement depuis le site officiel)  
- Connaissances de base en Java et en programmation orientée objet  

Vous pouvez télécharger la bibliothèque ici : [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Comment **ajouter une forme** – Insertion d'un GroupShape
Un `GroupShape` vous permet de traiter plusieurs formes comme une seule unité. Cela est utile pour déplacer ou mettre en forme plusieurs éléments ensemble.

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

## Créer une **forme de zone de texte**
Une zone de texte est un conteneur pouvant contenir du texte formaté. Vous pouvez également la faire pivoter pour un rendu dynamique.

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

## Définir le **ratio d'aspect de la forme**
Parfois, vous avez besoin qu'une forme s'étire librement, d'autres fois vous souhaitez conserver ses proportions d'origine. Le contrôle du ratio d'aspect est simple.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Placer une **forme dans un tableau**
Intégrer une forme dans une cellule de tableau peut être pratique pour les mises en page de rapports. L'exemple ci‑dessous crée un tableau puis insère une forme de type filigrane qui s'étend sur toute la page.

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

## Ajouter une **forme d'appel**
Une forme d'appel est parfaite pour mettre en évidence des notes ou des avertissements. Bien que le code ci‑dessus montre déjà un `ACCENT_BORDER_CALLOUT_1`, vous pouvez remplacer le `ShapeType` par n'importe quelle variante d'appel pour correspondre à votre conception.

## Travailler avec les formes SmartArt

### Détecter les formes SmartArt
Les diagrammes SmartArt peuvent être identifiés programmatiquement, vous permettant de les traiter ou de les remplacer selon les besoins.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Mettre à jour les dessins SmartArt
Une fois détectés, vous pouvez actualiser les graphiques SmartArt pour refléter les changements de données.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Problèmes courants & conseils
- **Forme non affichée :** Assurez‑vous que la forme est insérée après le nœud cible en utilisant `builder.insertNode`.  
- **Rotation inattendue :** Souvenez‑vous que la rotation s'applique autour du centre de la forme ; ajustez `setLeft`/`setTop` si nécessaire.  
- **Ratio d'aspect verrouillé :** Par défaut, de nombreuses formes verrouillent leur ratio d'aspect ; appelez `setAspectRatioLocked(false)` pour les étirer librement.  
- **Échec de la détection SmartArt :** Vérifiez que vous utilisez une version d'Aspose.Words qui prend en charge SmartArt (v24+).

## Questions fréquemment posées

**Q : Qu’est‑ce qu’Aspose.Words for Java ?**  
R : Aspose.Words for Java est une bibliothèque Java qui permet aux développeurs de créer, modifier et convertir des documents Word programmatiquement. Elle offre un large éventail de fonctionnalités et d’outils pour travailler avec des documents dans divers formats.

**Q : Comment puis‑je télécharger Aspose.Words for Java ?**  
R : Vous pouvez télécharger Aspose.Words for Java depuis le site Aspose en suivant ce lien : [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q : Quels sont les avantages d’utiliser des formes de document ?**  
R : Les formes de document ajoutent des éléments visuels et de l’interactivité à vos documents, les rendant plus attrayants et informatifs. Avec les formes, vous pouvez créer des bulles d’appel, des boutons, des images, des filigranes, etc., améliorant l’expérience utilisateur globale.

**Q : Puis‑je personnaliser l’apparence des formes ?**  
R : Oui, vous pouvez personnaliser l’apparence des formes en ajustant leurs propriétés telles que la taille, la position, la rotation et la couleur de remplissage. Aspose.Words for Java offre de nombreuses options de personnalisation des formes.

**Q : Aspose.Words for Java est‑il compatible avec SmartArt ?**  
R : Oui, Aspose.Words for Java prend en charge les formes SmartArt, vous permettant de travailler avec des diagrammes et graphiques complexes dans vos documents.

---

**Dernière mise à jour :** 2025-12-14  
**Testé avec :** Aspose.Words for Java 24.12 (dernière version)  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}