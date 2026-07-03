---
category: general
date: 2026-07-03
description: Créez une forme rectangulaire en Java et apprenez comment ajouter une
  ombre à la forme, appliquer l’effet d’ombre, régler la transparence de la forme
  et créer rapidement un document vierge.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: fr
og_description: Créez une forme rectangulaire en Java avec ombre, transparence et
  un document vierge. Suivez ce guide pour maîtriser la gestion des formes.
og_title: Créer une forme rectangulaire en Java – Tutoriel complet de programmation
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Créer une forme de rectangle en Java – Guide complet étape par étape
url: /fr/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire en Java – Guide complet étape par étape

Vous êtes-vous déjà demandé comment **créer une forme rectangulaire** dans un document Word en Java ? Vous n'êtes pas le seul — les développeurs ont souvent besoin d’ajouter rapidement des graphiques géométriques, puis de leur appliquer une ombre subtile pour que la mise en page paraisse plus soignée. Dans ce tutoriel, nous parcourrons l’ensemble du processus : de la création d’un **document vierge** à **l’ajout d’une ombre à la forme**, **l’application de l’effet d’ombre**, et même **la définition de la transparence de la forme** pour un rendu professionnel.

L’extrait de code ci‑dessous est un exemple fonctionnel complet que vous pouvez copier‑coller dans votre projet. Aucun document externe n’est requis — suivez simplement les étapes, comprenez le « pourquoi », et vous générerez des rectangles ombrés en quelques secondes.

## Ce que vous allez apprendre

- Comment **créer une forme rectangulaire** programmatique avec Aspose.Words for Java.
- Les appels exacts nécessaires pour **ajouter une ombre à la forme** et configurer ses propriétés visuelles.
- Les manières d’**appliquer un effet d’ombre** et d’ajuster des paramètres comme le décalage, le rayon de flou et la couleur.
- Les techniques pour **définir la transparence de la forme** afin d’obtenir un rendu plus subtil.
- Comment **créer un document vierge**, insérer la forme et enregistrer le résultat.

> **Astuce :** Toutes ces actions sont effectuées sur une seule instance `Document`, ce qui signifie que vous pouvez les chaîner sans vous soucier d’opérations intermédiaires d’E/S de fichiers.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

- Java 17 (ou tout JDK récent) installé.
- La bibliothèque Aspose.Words for Java ajoutée à votre projet (coordonnées Maven : `com.aspose:aspose-words:23.12`).
- Un IDE Java ou un simple éditeur de texte — rien de sophistiqué, juste un endroit pour compiler et exécuter.

Si l’un de ces éléments vous manque, téléchargez le JDK depuis Oracle et ajoutez la dépendance Aspose via Maven ou Gradle. Une fois cela fait, vous êtes prêt à démarrer.

## Étape 1 : **Créer un document vierge** – la toile pour tout

La toute première chose dont vous avez besoin est un objet `Document` vide. Pensez‑y comme à une feuille blanche ; sans elle, il n’y a nulle part où placer votre rectangle.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Pourquoi commencer par un document vierge ? Parce que chaque forme vit à l’intérieur d’une `Section`, et un `Document` nouvellement instancié contient déjà une section par défaut avec un corps prêt à recevoir des nœuds. Ignorer cette étape vous obligerait à créer manuellement des sections plus tard, ce qui ajoute une complexité inutile.

## Étape 2 : **Créer une forme rectangulaire** et définir sa taille

Maintenant que nous avons une toile, créons **une forme rectangulaire**. La classe `Shape` prend la référence du document et un `ShapeType`. Ici nous choisissons `RECTANGLE` et définissons la largeur/hauteur en points (1 pt ≈ 1/72 pouce).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Pourquoi définir `WrapType.INLINE` ? L’enveloppement en ligne fait que la forme se comporte comme un caractère dans le paragraphe, garantissant qu’elle se déplace avec le texte environnant. Si vous avez besoin d’un comportement flottant, passez à `WrapType.SQUARE` ou `WrapType.TOP_BOTTOM`.

## Étape 3 : **Appliquer l’effet d’ombre** – donner de la profondeur au rectangle

Un rectangle plat paraît… plat. Ajouter une ombre le fait ressortir. Nous allons **appliquer l’effet d’ombre** en créant une instance `ShadowEffect`, puis en ajustant ses propriétés visuelles.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Décomposons cela :

- **Color** – `Color.getGray(0.5)` renvoie un gris à 50 %, neutre et fonctionnant sur la plupart des arrière‑plans.
- **OffsetX/Y** – Des valeurs positives déplacent l’ombre vers la droite et le bas ; des valeurs négatives la déplaceraient vers la gauche/haut.
- **BlurRadius** – Des valeurs plus élevées créent une ombre plus douce et diffuse.
- **Transparency** – Varie de `0` (opaque) à `1` (totalement transparent). Ici nous avons choisi `0.3` pour un effet subtil.

## Étape 4 : **Ajouter l’ombre à la forme** – lier l’effet

Créer l’effet ne suffit pas ; nous devons **ajouter l’ombre à la forme** en assignant l’objet `ShadowEffect` au rectangle.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

En coulisses, cet appel met à jour le balisage OpenXML sous‑jacent (`<w:shdw>`) que Word utilise pour rendre les ombres. Si vous inspectez le `.docx` enregistré, vous verrez un élément `<w:effect>` rempli avec les paramètres que nous avons définis.

## Étape 5 : **Définir la transparence de la forme** – optionnel mais souvent utile

Parfois, vous voulez que le rectangle lui‑même soit semi‑transparent, laissant le texte d’arrière‑plan transparaître. La classe `Shape` expose `setFillColor` et `setFillTransparency`. Voici un exemple rapide qui rend le rectangle 40 % transparent :

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Pourquoi faire cela ? Imaginez un filigrane ou une annotation mise en évidence où le contenu sous‑jacent doit rester lisible. Ajustez la valeur de transparence selon votre charte graphique.

## Étape 6 : Insérer la forme dans le document

Nous avons construit le rectangle, ajouté une ombre et (optionnellement) défini sa transparence. L’étape finale consiste à **ajouter la forme à la première section du document**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Ajouter la forme au corps la place à la fin du premier paragraphe. Si vous avez besoin d’un point d’insertion précis, récupérez le `Paragraph` cible et utilisez `insertBefore` ou `insertAfter`.

## Étape 7 : Enregistrer le document – voir le résultat

Tout ce travail se résume à un seul appel `save`. Choisissez un chemin qui a du sens dans votre environnement.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Ouvrez le `ShadowShape.docx` résultant dans Microsoft Word ou LibreOffice, et vous verrez un rectangle net avec une douce ombre grise, légèrement transparent si vous avez conservé l’étape optionnelle. Le rendu visuel correspond aux paramètres que nous avons définis programmatique­ment.

---

![create rectangle shape with shadow in a Word document](https://example.com/images/rectangle-shadow.png "create rectangle shape with shadow")

*Texte alternatif de l’image :* **créer une forme rectangulaire avec ombre** – représentation visuelle du résultat final.

## Questions fréquentes & cas particuliers

### Et si je veux une couleur d’ombre différente ?

Il suffit de modifier l’appel `setColor` :

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Rappelez‑vous que des ombres trop vives peuvent paraître non professionnelles ; des tons subtils fonctionnent généralement mieux.

### Puis‑je appliquer la même ombre à plusieurs formes ?

Oui. Créez une instance `ShadowEffect`, configurez‑la, puis réutilisez‑la :

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Évitez simplement de muter le `ShadowEffect` après l’avoir attaché à d’autres formes, sauf si vous avez l’intention de les mettre à jour toutes simultanément.

### Comment changer dynamiquement le flou de l’ombre ?

Exposez un curseur UI qui mappe à `setBlurRadius`. Des valeurs entre `2` et `12` sont typiques ; des nombres plus grands produisent un « halo » plutôt qu’une ombre nette.

### Et si la forme doit flotter plutôt qu’être en ligne ?

Changez le type d’enveloppe :

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Les formes flottantes offrent plus de liberté de mise en page mais nécessitent une logique de positionnement supplémentaire.

## Exemple complet fonctionnel

Voici le programme complet, prêt à être copié‑collé, qui intègre toutes les étapes abordées. Exécutez‑le comme une application Java classique.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Sortie attendue :** Lorsque vous ouvrez `ShadowShape.docx`, vous verrez un rectangle blanc, 200 × 100 pt, centré dans le premier paragraphe, avec une ombre gris‑moyen décalée de 5 pt, floutée avec un rayon de 8, et 30 % transparente. Le rectangle lui‑même est 40 % transparent, laissant le texte sous‑jacent entrevoir.

## Conclusion

Nous venons de **créer une forme rectangulaire** à partir de zéro, **ajouter une ombre à la forme**, **appliquer l’effet d’ombre**, et même **définir la transparence de la forme**—tout en **créant un document vierge** comme base. L’approche est simple, repose sur l’API fluide d’Aspose.Words, et peut être étendue aux cercles, étoiles ou polygones personnalisés.

Quelles sont vos prochaines étapes ? Essayez de remplacer `ShapeType.RECTANGLE` par `ShapeType.OVAL` pour générer des cercles ombrés, ou expérimentez les remplissages en dégradé pour


## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}