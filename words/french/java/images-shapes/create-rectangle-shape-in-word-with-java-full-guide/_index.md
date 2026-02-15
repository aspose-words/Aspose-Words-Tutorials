---
category: general
date: 2026-02-15
description: Créer une forme rectangulaire dans un document Word en utilisant Java.
  Apprenez comment ajouter une ombre à la forme, enregistrer le document Word et ajouter
  une forme rectangulaire avec Aspose.Words.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: fr
og_description: Créer une forme rectangulaire dans un fichier Word avec Java. Ce guide
  montre comment ajouter une ombre à la forme, enregistrer le document Word et ajouter
  une forme rectangulaire étape par étape.
og_title: Créer une forme rectangulaire – Tutoriel Java Aspose.Words
tags:
- Aspose.Words
- Java
- Document Automation
title: Créer une forme rectangulaire dans Word avec Java – Guide complet
url: /fr/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

3" etc not bold.

Make sure we kept code block placeholders unchanged.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire dans Word avec Java – Guide complet

Vous avez déjà eu besoin de **créer une forme rectangulaire** dans un fichier Word mais vous ne saviez pas par où commencer ? Vous n'êtes pas le seul — de nombreux développeurs rencontrent ce problème lorsqu'ils automatisent des rapports ou des factures. La bonne nouvelle ? Avec Aspose.Words for Java, vous pouvez créer un rectangle, lui ajouter une belle ombre, et enregistrer le document Word en quelques lignes.

## Prérequis

- Java 8 ou supérieur (l'API fonctionne également avec Java 11+).  
- Bibliothèque Aspose.Words for Java (version 23.9 ou ultérieure).  
- Un IDE comme IntelliJ IDEA ou Eclipse — cela convient.  
- Familiarité de base avec la syntaxe Java.

> **Astuce pro :** Si vous utilisez Maven, ajoutez la dépendance Aspose.Words à votre `pom.xml` et laissez l'IDE gérer le reste.

---

## Étape 1 : Initialiser un nouveau document – Comment **créer une forme rectangulaire**

Tout d'abord : vous avez besoin d'une toile vierge. Dans Aspose.Words, cette toile est un objet `Document`.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

La classe `Document` représente le fichier .docx complet. Considérez‑la comme le cahier où vous ajouterez plus tard **une forme rectangulaire** et son ombre.

## Étape 2 : Construire le rectangle – **Ajouter une forme rectangulaire**

Nous allons maintenant réellement construire le rectangle. Nous définirons sa taille, sa mise en page et sa couleur de remplissage.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

Pourquoi un enrobage `INLINE` ? Parce que nous voulons que la forme se comporte comme un paragraphe — idéal pour des rapports simples. Vous pouvez le changer en `TOPBOTTOM` si vous avez besoin que le texte s'écoule autour de la forme plus tard.

## Étape 3 : Appliquer une ombre – **Comment ajouter une ombre à une forme**

Un rectangle plat semble un peu fade. Ajouter une ombre lui donne de la profondeur et rend le document plus soigné. C’est ici que nous répondons à la question « **comment ajouter une ombre à une forme** » en pratique.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

Chaque propriété fait quelque chose de spécifique :

- `setVisible(true)` active l'ombre.  
- `setColor` choisit un gris foncé pour un effet subtil.  
- `setBlurRadius` contrôle la douceur des bords.  
- `setOffsetX/Y` déplace l'ombre vers la droite et le bas, imitant une source de lumière.  
- `setTransparency` la rend légèrement transparente, afin que la forme reste la vedette.

> **Note :** Si vous avez besoin d'une ombre colorée, il suffit de passer un autre `java.awt.Color` à `setColor`.

## Étape 4 : Insérer la forme dans le document

Avec le rectangle et son ombre prêts, nous l'insérons dans la première section du document.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

L'ajout à la fin du corps place la forme à l'endroit où un nouveau paragraphe serait inséré. Si vous souhaitez placer le rectangle à un emplacement précis, vous pouvez utiliser `insertBefore` ou manipuler la collection `Paragraph`.

## Étape 5 : **Enregistrer le document Word** – Conservez votre travail

La dernière étape consiste à écrire le fichier sur le disque. C’est le moment où vous **enregistrez le document Word** réellement.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Remplacez `YOUR_DIRECTORY` par un chemin absolu ou relatif sur votre machine. Après avoir exécuté le programme, ouvrez `ShadowShape.docx` dans Microsoft Word — vous devriez voir un rectangle gris clair avec une ombre sombre et douce.

![Diagramme montrant une forme rectangulaire avec ombre créée avec Aspose.Words](https://example.com/rectangle-shadow.png "créer une forme rectangulaire avec ombre")

---

## Questions fréquentes & cas particuliers  

### Et si j’ai besoin de plusieurs rectangles ?

Répétez simplement **l’Étape 2** et **l’Étape 3** dans une boucle, en ajustant `setWidth`, `setHeight` ou `setFillColor` à chaque itération. N'oubliez pas d'attribuer à chaque forme un nom de variable unique ou de les stocker dans une liste.

### Puis‑je exporter en PDF au lieu de DOCX ?

Absolument. Après avoir ajouté la forme, appelez `document.save("output.pdf")`. Aspose.Words gérera la conversion, en préservant l'ombre.

### Qu’en est‑il des versions plus anciennes de Word ?

Utilisez la surcharge `document.save("file.doc", SaveFormat.DOC)`. L'API rétrograde automatiquement les fonctionnalités, mais notez que certains styles d'ombre peuvent apparaître légèrement différents dans les formats hérités.

### Comment modifier la direction de l'ombre ?

Manipulez `setOffsetX` et `setOffsetY`. Un X positif déplace l'ombre vers la droite, un X négatif vers la gauche. Un Y positif déplace l'ombre vers le bas, un Y négatif vers le haut. Expérimentez avec ces valeurs pour simuler une source de lumière sous n'importe quel angle.

---

## Conseils pour travailler avec les formes  

- **Regrouper les formes** : Si vous avez besoin d'une étiquette à côté du rectangle, créez un `GroupShape` et ajoutez à la fois le rectangle et une `TextBox`.  
- **L'ordre Z compte** : Utilisez `shape.moveToFront()` ou `shape.moveToBack()` pour contrôler quelle forme apparaît au premier plan.  
- **Performance** : Ajouter des centaines de formes peut être lent. Regroupez‑les dans une seule section, puis appelez `document.updatePageLayout()` une fois à la fin.

## Récapitulatif  

Nous avons vu comment **créer une forme rectangulaire** dans un document Word avec Java, comment **ajouter une ombre à la forme**, et comment **enregistrer le document Word** avec le résultat. Le code complet et exécutable se trouve dans les extraits ci‑dessus, et vous comprenez maintenant le « pourquoi » de chaque propriété — ainsi vous pouvez ajuster les couleurs, le flou et les décalages selon n'importe quel design.

Prêt pour le prochain défi ? Essayez de combiner le rectangle avec un graphique, ou exportez le fichier en PDF et observez le rendu de l'ombre. Vous pouvez également explorer **ajouter une forme rectangulaire** à l'intérieur des tableaux pour des mises en page de rapports sophistiquées.

Bon codage, et que vos documents soient toujours aussi impeccables que votre code !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}