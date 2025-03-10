---
title: Génération de la table des matières
linktitle: Génération de la table des matières
second_title: API de traitement de documents Java Aspose.Words
description: Apprenez à créer une table des matières dynamique à l'aide d'Aspose.Words pour Java. Maîtrisez la génération de tables des matières grâce à des instructions étape par étape et à des exemples de code source.
weight: 14
url: /fr/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Génération de la table des matières

## Introduction

Vous avez déjà eu du mal à créer une table des matières dynamique et professionnelle dans vos documents Word ? Ne cherchez plus ! Avec Aspose.Words pour Java, vous pouvez automatiser l'ensemble du processus, gagner du temps et garantir l'exactitude. Que vous créiez un rapport complet ou un article universitaire, ce didacticiel vous guidera dans la génération d'une table des matières par programmation avec Java. Vous êtes prêt à vous lancer ? Commençons !

## Prérequis

Avant de commencer à coder, assurez-vous de disposer des éléments suivants :

1.  Kit de développement Java (JDK) : installé sur votre système. Vous pouvez le télécharger à partir de[Site Web d'Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
2.  Bibliothèque Aspose.Words pour Java : téléchargez la dernière version à partir du[page de sortie](https://releases.aspose.com/words/java/).
3. Environnement de développement intégré (IDE) : tel que IntelliJ IDEA, Eclipse ou NetBeans.
4.  Licence temporaire Aspose : pour éviter les limitations d'évaluation, obtenez une[permis temporaire](https://purchase.aspose.com/temporary-license/).

## Paquets d'importation

Pour utiliser efficacement Aspose.Words pour Java, assurez-vous d'importer les classes requises. Voici les importations :

```java
import com.aspose.words.*;
```

Suivez ces étapes pour générer une table des matières dynamique dans votre document Word.

## Étape 1 : Initialiser le document et DocumentBuilder

 La première étape consiste à créer un nouveau document et à utiliser le`DocumentBuilder` classe pour le manipuler.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Représente le document Word.
- `DocumentBuilder`:Une classe d'aide qui permet une manipulation facile du document.

## Étape 2 : Insérer la table des matières

Maintenant, insérons la table des matières au début du document.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: Insère un champ TOC. Les paramètres spécifient :
  - `\o "1-3"`:Inclure les titres des niveaux 1 à 3.
  - `\h`:Créer des liens hypertexte vers les entrées.
  - `\z`: Supprimer les numéros de page pour les documents Web.
  - `\u`:Conserver les styles pour les hyperliens.
- `insertBreak`: Ajoute un saut de page après la table des matières.

## Étape 3 : ajouter des titres pour remplir la table des matières

POUR remplir la table des matières, vous devez ajouter des paragraphes avec des styles de titre.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` : Définit le style de paragraphe sur un niveau de titre spécifique (par exemple,`HEADING_1`, `HEADING_2`).
- `writeln`: Ajoute du texte au document avec le style spécifié.

## Étape 4 : ajouter des titres imbriqués

Pour démontrer les niveaux de table des matières, incluez des titres imbriqués.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Ajoutez des titres de niveaux plus profonds pour afficher la hiérarchie dans la table des matières.

## Étape 5 : mettre à jour les champs de la table des matières

Le champ TOC doit être mis à jour pour afficher les derniers titres.


```java
doc.updateFields();
```

- `updateFields`: Actualise tous les champs du document, garantissant que la table des matières reflète les titres ajoutés.

## Étape 6 : Enregistrer le document

Enfin, enregistrez le document au format souhaité.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` : Exporte le document vers un`.docx` fichier. Vous pouvez spécifier d'autres formats tels que`.pdf` ou`.txt` si besoin.

## Conclusion

Félicitations ! Vous avez réussi à créer une table des matières dynamique dans un document Word à l'aide d'Aspose.Words pour Java. Avec seulement quelques lignes de code, vous avez automatisé une tâche qui pourrait autrement prendre des heures. Alors, quelle est la prochaine étape ? Essayez d'expérimenter différents styles et formats de titres pour adapter votre table des matières à des besoins spécifiques.

## FAQ

### Puis-je personnaliser davantage le format de la table des matières ?
Absolument ! Vous pouvez ajuster les paramètres de la table des matières, comme l'inclusion de numéros de page, l'alignement du texte ou l'utilisation de styles de titre personnalisés.

### Une licence est-elle obligatoire pour Aspose.Words pour Java ?
 Oui, une licence est requise pour bénéficier de toutes les fonctionnalités. Vous pouvez commencer avec une[permis temporaire](https://purchase.aspose.com/temporary-license/).

### Puis-je générer une table des matières pour un document existant ?
 Oui ! Chargez le document dans un`Document` objet et suivez les mêmes étapes pour insérer et mettre à jour la table des matières.

### Cela fonctionne-t-il pour les exportations PDF ?
 Oui, la table des matières apparaîtra dans le PDF si vous enregistrez le document dans`.pdf` format.

### Où puis-je trouver plus de documentation ?
 Découvrez le[Documentation d'Aspose.Words pour Java](https://reference.aspose.com/words/java/) pour plus d'exemples et de détails.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
