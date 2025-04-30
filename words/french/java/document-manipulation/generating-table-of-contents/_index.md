---
"description": "Apprenez à générer et personnaliser une table des matières (TOC) avec Aspose.Words pour Java. Créez facilement des documents organisés et professionnels."
"linktitle": "Génération de la table des matières"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Génération d'une table des matières dans Aspose.Words pour Java"
"url": "/fr/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Génération d'une table des matières dans Aspose.Words pour Java


## Introduction à la génération de tables des matières dans Aspose.Words pour Java

Dans ce tutoriel, nous vous expliquerons comment générer une table des matières (TOC) avec Aspose.Words pour Java. La TOC est une fonctionnalité essentielle pour créer des documents organisés. Nous verrons comment personnaliser son apparence et sa mise en page.

## Prérequis

Avant de commencer, assurez-vous qu'Aspose.Words pour Java est installé et configuré dans votre projet Java.

## Étape 1 : Créer un nouveau document

Commençons par créer un nouveau document avec lequel travailler.

```java
Document doc = new Document();
```

## Étape 2 : Personnaliser les styles de table des matières

Pour personnaliser l'apparence de votre table des matières, vous pouvez modifier les styles qui lui sont associés. Dans cet exemple, nous allons mettre les entrées de premier niveau de la table des matières en gras.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Étape 3 : Ajoutez du contenu à votre document

Vous pouvez ajouter votre contenu au document. Ce contenu servira à générer la table des matières.

## Étape 4 : Générer la table des matières

Pour générer la table des matières, insérez un champ « Table des matières » à l'emplacement souhaité dans votre document. Ce champ sera automatiquement renseigné en fonction des titres et des styles de votre document.

```java
// Insérez un champ TOC à l’emplacement souhaité dans votre document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Étape 5 : Enregistrer le document

Enfin, enregistrez le document avec la table des matières.

```java
doc.save("your_output_path_here");
```

## Personnalisation des taquets de tabulation dans la table des matières

Vous pouvez également personnaliser les taquets de tabulation dans votre table des matières pour contrôler la disposition des numéros de page. Voici comment modifier les taquets de tabulation :

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Obtenez le premier onglet utilisé dans ce paragraphe, qui aligne les numéros de page.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Retirez l'ancienne languette.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insérez un nouvel onglet à une position modifiée (par exemple, 50 unités à gauche).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Vous disposez désormais d'une table des matières personnalisée dans votre document avec des tabulations ajustées pour l'alignement des numéros de page.


## Conclusion

Dans ce tutoriel, nous avons découvert comment générer une table des matières (TOC) avec Aspose.Words pour Java, une puissante bibliothèque permettant de travailler avec des documents Word. Une table des matières bien structurée est essentielle pour organiser et parcourir de longs documents, et Aspose.Words fournit les outils nécessaires pour créer et personnaliser facilement des tables des matières.

## FAQ

### Comment modifier la mise en forme des entrées de la table des matières ?

Vous pouvez modifier les styles associés aux niveaux de table des matières en utilisant `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, où X est le niveau TOC.

### Comment puis-je ajouter plus de niveaux à ma table des matières ?

Pour inclure plus de niveaux dans votre table des matières, vous pouvez modifier le champ Table des matières et spécifier le nombre de niveaux souhaité.

### Puis-je modifier les positions des taquets de tabulation pour des entrées de table des matières spécifiques ?

Oui, comme indiqué dans l'exemple de code ci-dessus, vous pouvez modifier les positions des taquets de tabulation pour des entrées de table des matières spécifiques en parcourant les paragraphes et en modifiant les taquets de tabulation en conséquence.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}