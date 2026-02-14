---
date: 2026-02-14
description: Apprenez à afficher les formules mathématiques en ligne, insérer des
  équations mathématiques et manipuler les objets Office Math sans effort avec Aspose.Words
  pour Java.
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: Afficher les formules en ligne avec Office Math dans Aspose.Words pour Java
url: /fr/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Affichage des formules en ligne avec Office Math dans Aspose.Words pour Java

Dans ce tutoriel complet, vous découvrirez comment **afficher des formules en ligne** à l'aide des objets Office Math dans Aspose.Words pour Java. Que vous ayez besoin d'**insérer une équation mathématique** dans un rapport ou d'ajuster finement le formatage de formules complexes, ce guide vous accompagne à chaque étape — du chargement d'un document Word à l'enregistrement du résultat final.

## Réponses rapides
- **Que signifie « afficher les mathématiques en ligne » ?** L'équation apparaît dans le flux du texte, pas sur une ligne séparée.  
- **Quelle classe représente un objet mathématique ?** `OfficeMath` dans l'API Aspose.Words.  
- **Puis-je changer l'alignement ?** Oui, utilisez `setJustification` avec LEFT, CENTER ou RIGHT.  
- **Ai-je besoin d'une licence pour cette fonctionnalité ?** Une licence valide d'Aspose.Words pour Java est requise pour une utilisation en production.  
- **Quelle version est démontrée ?** Le code fonctionne avec la dernière version d'Aspose.Words pour Java (2026).

## Qu'est-ce que « afficher les mathématiques en ligne » ?
Afficher les mathématiques en ligne signifie que l'équation est traitée comme faisant partie du texte du paragraphe, ce qui lui permet de s'enrouler naturellement avec les mots environnants. Ceci est utile pour les formules courtes qui ne doivent pas interrompre le flux de lecture.

## Pourquoi utiliser les objets Office Math dans Aspose.Words pour Java ?
- **Contrôle précis** de la mise en page des équations (inline vs. display).  
- **Manipulation programmatique** des équations sans ouvrir Word manuellement.  
- **Rendu cohérent** sur toutes les plateformes, idéal pour la génération automatisée de rapports.

## Prérequis
Avant de commencer, assurez-vous d'avoir :

- Aspose.Words pour Java installé et référencé dans votre projet.  
- Un fichier Word contenant déjà une équation Office Math (par ex., `OfficeMath.docx`).  
- Une licence valide si vous prévoyez d'exécuter le code en dehors du mode d'évaluation.

## Guide étape par étape

### Charger le document
Tout d'abord, chargez le document qui contient l'équation Office Math que vous souhaitez manipuler :

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### Accéder à l'objet Office Math
Récupérez le premier nœud Office Math du document :

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### Définir le type d'affichage (Inline vs. Display)
Contrôlez si l'équation apparaît en ligne avec le texte environnant ou sur une ligne séparée. Pour **afficher les mathématiques en ligne**, utilisez l'énumération `INLINE` ; pour une ligne distincte, utilisez `DISPLAY` :

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*Si vous souhaitez que l'équation reste en ligne, remplacez `DISPLAY` par `INLINE`.*

### Définir la justification
Ajustez l'alignement de l'équation. Ci-dessous, nous l'alignons à gauche, mais vous pouvez également choisir `CENTER` ou `RIGHT` :

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### Enregistrer le document modifié
Enfin, écrivez les modifications dans un nouveau fichier :

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## Code source complet pour l'utilisation des objets Office Math dans Aspose.Words pour Java

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## Problèmes courants et dépannage
- **Équation non trouvée :** Assurez-vous que le document contient réellement un objet Office Math ; sinon `doc.getChild` renvoie `null`.  
- **Le type d'affichage n'a aucun effet :** Vérifiez que vous utilisez une version récente d'Aspose.Words ; les versions plus anciennes peuvent avoir un support limité de `OfficeMathDisplayType`.  
- **Exception de licence :** Si vous voyez une erreur de licence, vérifiez que votre fichier de licence est correctement chargé avant de créer l'instance `Document`.

## Questions fréquemment posées

**Q : Quel est le but des objets Office Math dans Aspose.Words pour Java ?**  
R : Les objets Office Math vous permettent de représenter et de manipuler des équations mathématiques de façon programmatique, vous offrant un contrôle total sur l'affichage et le formatage.

**Q : Puis-je aligner les équations Office Math différemment dans mon document ?**  
R : Oui, utilisez la méthode `setJustification` pour aligner à gauche, à droite ou au centre.

**Q : Aspose.Words pour Java est-il adapté à la gestion de documents mathématiques complexes ?**  
R : Absolument. La bibliothèque prend en charge pleinement les équations complexes, les fractions imbriquées, les matrices, etc.

**Q : Comment puis‑je en savoir plus sur Aspose.Words pour Java ?**  
R : Pour une documentation complète et les téléchargements, consultez [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

**Q : Où puis‑je télécharger Aspose.Words pour Java ?**  
R : Vous pouvez télécharger Aspose.Words pour Java depuis le site : [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

---

**Dernière mise à jour :** 2026-02-14  
**Testé avec :** Aspose.Words for Java 24.12 (dernière version en février 2026)  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}