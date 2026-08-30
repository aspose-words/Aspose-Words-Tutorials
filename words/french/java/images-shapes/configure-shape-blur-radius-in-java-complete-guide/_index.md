---
category: general
date: 2026-06-27
description: Apprenez à configurer le rayon de flou d’une forme avec Aspose.Words
  for Java. Ce tutoriel pas à pas couvre également les paramètres d’ombre, la transparence
  et l’enregistrement du document.
draft: false
keywords:
- configure shape blur radius
- Aspose.Words shape shadow
- Java shadow format
- Word document shape manipulation
- set blur radius
language: fr
og_description: Configurez le rayon de flou de la forme dans un document Word en Java.
  Suivez ce tutoriel détaillé pour maîtriser les paramètres d’ombre des formes Aspose.Words.
og_title: Configurer le rayon de flou de forme en Java – Guide complet
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  headline: Configure Shape Blur Radius in Java – Complete Guide
  type: TechArticle
- description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  name: Configure Shape Blur Radius in Java – Complete Guide
  steps:
  - name: Understanding the Numbers
    text: '- **Blur radius** (`setBlurRadius`) controls how fuzzy the shadow looks.
      A value of `0` gives a crisp edge, while `10` or higher yields a dreamy glow.
      - **DistanceX / DistanceY** shift the shadow relative to the shape. Positive
      X moves it right; positive Y moves it down. - **Transparency** makes the'
  - name: Targeting a Specific Shape by Name
    text: 'If your document contains many shapes, rely on the shape’s **name** (set
      in Word’s layout options) instead of index:'
  - name: Applying Different Blur Radii
    text: 'You might want a stronger blur for background graphics and a subtle one
      for icons. Loop through all shapes:'
  - name: Compatibility Notes
    text: '- **Units:** Aspose.Words uses points (1 pt = 1/72 inch). If you work with
      millimeters, convert accordingly. - **Version:** The API shown works with Aspose.Words
      for Java 24.9 and later. Older versions may use `setBlurRadius(double)` but
      lack some newer shadow properties.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Configurer le rayon de flou de forme en Java – Guide complet
url: /fr/java/images-shapes/configure-shape-blur-radius-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configurer le rayon de flou de forme dans Java – Guide complet

Vous avez déjà eu besoin de **configurer le rayon de flou d’une forme** dans un document Word en travaillant avec Java ? Vous n’êtes pas le seul à vous creuser la tête à ce sujet. Que vous peaufiniez un rapport d’entreprise ou ajoutiez une touche visuelle subtile à un flyer, maîtriser ce paramètre peut rendre vos documents beaucoup plus professionnels.

Dans ce tutoriel, nous parcourrons l’ensemble du processus — du chargement du fichier `.docx` à l’ajustement du flou de l’ombre, puis à l’enregistrement du résultat. En chemin, nous aborderons également des sujets connexes comme **Aspose.Words shape shadow**, **Java shadow format** et la **manipulation générale des formes dans un document Word**. À la fin, vous disposerez d’un extrait de code prêt à l’emploi et d’une compréhension claire de l’importance de chaque ligne.

## Ce que vous allez apprendre

- Comment charger un document Word avec Aspose.Words for Java.  
- Comment localiser le premier objet `Shape` dans le corps du document.  
- Les étapes exactes pour **configurer le rayon de flou de forme** et d’autres propriétés d’ombre telles que la distance et la transparence.  
- Comment persister les modifications dans un nouveau fichier `.docx`.  

Aucune bibliothèque externe autre qu’Aspose.Words n’est requise, et le code fonctionne avec Java 8 et plus ainsi que toute version récente d’Aspose.Words for Java (par ex., 24.9). Si vous êtes à l’aise avec la syntaxe Java de base, vous serez fine.

---

## Étape 1 : Charger le document Word

Avant de pouvoir toucher à une forme, il faut que le document soit chargé en mémoire. Aspose.Words rend cela possible en une seule ligne.

```java
// Load the source .docx file
com.aspose.words.Document document = new com.aspose.words.Document("YOUR_DIRECTORY/input.docx");
```

**Pourquoi c’est important :**  
Créer un objet `Document` analyse le fichier complet, vous donnant accès aux sections, paragraphes, tableaux **et formes**. Ignorer cette étape vous laisserait sans contexte pour appliquer le rayon de flou.

> **Astuce :** Si vous traitez de gros fichiers, envisagez d’utiliser `LoadOptions` pour ne charger que les parties nécessaires. Cela peut réduire considérablement l’utilisation de la mémoire.

---

## Étape 2 : Récupérer la forme cible

Les formes peuvent se trouver n’importe où — en-têtes, pieds de page, tableaux, etc. Pour simplifier, nous récupérerons la première forme trouvée dans le corps principal de la première section.

```java
// Navigate to the first shape in the document body
com.aspose.words.Shape shape = (com.aspose.words.Shape) document
        .getFirstSection()
        .getBody()
        .getChild(com.aspose.words.NodeType.SHAPE, 0, true);
```

**Pourquoi c’est important :**  
L’appel `getChild` parcourt l’arbre des nœuds en profondeur, renvoyant la *première* forme qui correspond à `NodeType.SHAPE`. Si votre document contient plusieurs formes, vous pouvez ajuster l’indice (`0`) ou itérer sur `document.getChildNodes(NodeType.SHAPE, true)`.

> **Cas particulier :** Si le document ne contient aucune forme, `shape` sera `null` et la ligne suivante déclenchera un `NullPointerException`. Pensez toujours à vérifier cela dans le code de production.

---

## Étape 3 : Configurer l’ombre de la forme – Définir le rayon de flou

Voici le cœur du sujet : ajuster le rayon de flou. Cela se trouve dans l’objet `ShadowFormat` attaché à la forme.

```java
// Access the shadow format of the shape
com.aspose.words.ShadowFormat shadow = shape.getShadowFormat();

// Set the blur radius (in points). Larger values produce a softer edge.
shadow.setBlurRadius(5.0);

// Optional: fine‑tune other shadow attributes
shadow.setDistanceX(3.0);          // Horizontal offset
shadow.setDistanceY(3.0);          // Vertical offset
shadow.setTransparency(0.3);      // 0 = fully opaque, 1 = fully transparent
```

### Comprendre les valeurs

- **Rayon de flou** (`setBlurRadius`) contrôle la douceur de l’ombre. Une valeur de `0` donne un bord net, tandis que `10` ou plus produit une lueur onirique.  
- **DistanceX / DistanceY** déplacent l’ombre par rapport à la forme. Un X positif la décale vers la droite ; un Y positif la décale vers le bas.  
- **Transparency** rend l’ombre translucide. Utile lorsque vous voulez un effet subtil plutôt qu’un bloc noir opaque.

> **Pourquoi configurer le rayon de flou ?**  
> Dans de nombreux modèles d’entreprise, un léger flou ajoute de la profondeur sans distraire le lecteur. C’est un petit réglage visuel qui peut améliorer considérablement la qualité perçue.

---

## Étape 4 : Enregistrer le document modifié

Tout le travail lourd est terminé ; il ne reste plus qu’à écrire les changements sur le disque.

```java
// Persist the modified document
document.save("YOUR_DIRECTORY/output.docx");
```

**Pourquoi c’est important :**  
Appeler `save` écrit l’ensemble du document, y compris le `ShadowFormat` mis à jour. Si vous avez seulement besoin de la forme sous forme d’image, vous pouvez l’exporter via `shape.getImageData().save(...)` à la place.

---

## Exemple complet fonctionnel

Voici le programme complet, autonome, que vous pouvez copier‑coller dans n’importe quel IDE Java. Assurez‑vous d’avoir le JAR Aspose.Words for Java dans votre classpath.

```java
import com.aspose.words.*;

public class ConfigureShapeBlurRadius {
    public static void main(String[] args) throws Exception {
        // 1. Load the document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Get the first shape (add null‑check for safety)
        Shape shape = (Shape) document.getFirstSection()
                .getBody()
                .getChild(NodeType.SHAPE, 0, true);
        if (shape == null) {
            System.out.println("No shape found in the document.");
            return;
        }

        // 3. Configure shadow – focus on blur radius
        ShadowFormat shadow = shape.getShadowFormat();
        shadow.setBlurRadius(5.0);          // Soft blur
        shadow.setDistanceX(3.0);           // Horizontal offset
        shadow.setDistanceY(3.0);           // Vertical offset
        shadow.setTransparency(0.3);        // Slightly transparent

        // 4. Save the result
        document.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved with configured shape blur radius.");
    }
}
```

**Résultat attendu :**  
L’exécution du programme crée un nouveau `output.docx` où la première forme possède désormais une ombre douce, semi‑transparente avec un rayon de flou de `5` points. Ouvrez le fichier dans Word, sélectionnez la forme, puis sous **Format de forme → Effets d’ombre → Options d’ombre**, vous verrez les valeurs que vous avez définies reflétées dans l’interface.

---

## Gestion de plusieurs formes & scénarios avancés

### Cibler une forme spécifique par son nom

Si votre document contient de nombreuses formes, utilisez le **nom** de la forme (défini dans les options de mise en page de Word) plutôt que l’indice :

```java
Shape target = (Shape) document.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getName().equals("MyLogo"))
        .findFirst()
        .orElse(null);
```

### Appliquer différents rayons de flou

Vous pourriez vouloir un flou plus fort pour les graphiques d’arrière‑plan et un plus subtil pour les icônes. Parcourez toutes les formes :

```java
for (Node node : document.getChildNodes(NodeType.SHAPE, true)) {
    Shape s = (Shape) node;
    ShadowFormat sf = s.getShadowFormat();
    sf.setBlurRadius(s.getName().contains("Background") ? 10.0 : 3.0);
}
```

### Notes de compatibilité

- **Unités :** Aspose.Words utilise les points (1 pt = 1/72 pouce). Si vous travaillez en millimètres, convertissez en conséquence.  
- **Version :** L’API présentée fonctionne avec Aspose.Words for Java 24.9 et versions ultérieures. Les versions antérieures pouvaient utiliser `setBlurRadius(double)` mais ne prenaient pas en charge certaines propriétés d’ombre plus récentes.

---

## Pièges courants & comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| `NullPointerException` sur `shape` | Le document n’a aucune forme ou l’index de requête est hors limites | Ajouter une vérification de null avant d’accéder à `ShadowFormat`. |
| Ombre non visible dans Word | La couleur de l’ombre est transparente par défaut ou les valeurs de distance la déplacent hors de la page | Définir une `ShadowColor` visible (`shadow.setColor(Color.BLACK)`) et garder `DistanceX/Y` modestes. |
| Le rayon de flou ne change pas | Utilisation d’une version obsolète d’Aspose.Words qui ignore la propriété | Mettre à jour vers la dernière bibliothèque ; la propriété a été introduite dans la version 20.5. |
| Ralentissement des performances sur de gros documents | Ré‑enregistrement du document entier après chaque modification de forme | Regrouper toutes les modifications, puis appeler `save` une seule fois. |

---

## Conclusion

Vous savez maintenant **comment configurer le rayon de flou d’une forme** dans un document Word en utilisant Java et Aspose.Words. Du chargement du fichier, à la récupération de la bonne `Shape`, en passant par le réglage du `ShadowFormat`, jusqu’à la persistance des changements — chaque étape est détaillée avec explications et conseils pratiques.

La technique ne se limite pas à une seule forme ; vous pouvez l’étendre à l’ensemble du document, appliquer différents niveaux de flou ou la combiner avec d’autres attributs d’ombre comme **shadow transparency Java**. Les prochaines étapes logiques sont d’explorer **set blur radius** pour les images, d’expérimenter le **Java shadow format** sur les graphiques, ou d’approfondir la **manipulation des formes dans un document Word** pour la génération dynamique de rapports.

Vous avez un scénario qui n’est pas couvert ici ? Laissez un commentaire ou consultez la documentation Aspose.Words for Java pour des effets d’ombre plus avancés. Bon codage !

---

<img src="configure-shape-blur-radius.png" alt="Configure shape blur radius using Aspose.Words Java example" style="max-width:100%;">

---


## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches alternatives dans vos projets.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}