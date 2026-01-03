---
date: 2026-01-03
description: Apprenez à ajuster les numéros de page lors de l'insertion d'une table
  des matières avec Aspose.Words pour Java. Personnalisez les styles de la table des
  matières et créez des documents sans effort.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Ajuster les numéros de page et générer la table des matières avec Aspose.Words
  pour Java
url: /fr/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajuster les numéros de page et générer une table des matières dans Aspose.Words pour Java

Dans ce tutoriel, vous découvrirez comment **ajuster les numéros de page** et **insérer une table des matières** (TOC) avec Aspose.Words pour Java. Une TOC bien structurée rend les documents longs faciles à parcourir, et le réglage précis de l’alignement des numéros de page offre à vos lecteurs une expérience professionnelle. Nous parcourrons la création d’un document, la personnalisation des styles de la TOC, et l’ajustement des tabulations afin que les numéros de page s’alignent exactement où vous le souhaitez.

## Réponses rapides
- **Que signifie « ajuster les numéros de page » ?** Modifier les tabulations qui alignent les numéros de page dans une TOC.  
- **Puis‑je insérer automatiquement une table des matières ?** Oui – utilisez la classe `FieldToc`.  
- **Ai‑je besoin d’une licence pour exécuter le code ?** Une version d’essai gratuite suffit pour le développement ; une licence est requise en production.  
- **Quelle version d’Aspose est prise en charge ?** Les exemples fonctionnent avec la dernière version d’Aspose.Words pour Java.  
- **Est‑il possible de personnaliser les styles de la TOC ?** Absolument – vous pouvez changer les polices, le gras, etc.

## Qu’est‑ce qu’une table des matières dans Aspose.Words ?
Une TOC est un champ qui parcourt le document à la recherche de styles de titres (par ex., Heading 1, Heading 2) et génère une liste d’entrées avec les numéros de page. Aspose.Words vous permet d’insérer ce champ programmatiquement et de contrôler entièrement son apparence.

## Pourquoi ajuster les numéros de page dans une table des matières ?
L’ajustement des tabulations vous donne un contrôle précis sur l’emplacement des numéros de page, ce qui est essentiel pour :

- Maintenir une mise en page propre et alignée en colonnes.  
- Respecter les guides de style de l’entreprise.  
- Améliorer la lisibilité des documents imprimés et numériques.

## Prérequis
- Aspose.Words pour Java ajouté à votre projet (Maven/Gradle).  
- Familiarité de base avec la syntaxe Java.  

## Guide étape par étape

### Étape 1 : Créer un nouveau document
Tout d’abord, créez une instance d’un objet `Document` vide qui contiendra votre contenu et votre TOC.

```java
Document doc = new Document();
```

### Étape 2 : Personnaliser les styles de la table des matières
Vous pouvez modifier l’apparence de chaque niveau de la TOC. Dans cet exemple, nous rendons les entrées de premier niveau en gras, ce qui est une demande de formatage courante.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### Étape 3 : Ajouter du contenu à votre document
Insérez des titres (par ex., `Heading1`, `Heading2`) et des paragraphes ordinaires. Le champ TOC récupérera automatiquement ces titres plus tard. *(Code omis pour plus de concision – l’accent est mis sur la génération de la TOC.)*

### Étape 4 : Insérer le champ de table des matières
Placez la TOC à l’endroit souhaité – généralement au début du document.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### Étape 5 : Enregistrer le document
Persistez le document sur le disque. Vous pouvez choisir n’importe quel format supporté tel que DOCX, PDF ou HTML.

```java
doc.save("your_output_path_here");
```

## Personnalisation des tabulations dans la table des matières (ajustement des numéros de page)
Si la tabulation par défaut n’aligne pas les numéros de page comme vous le désirez, vous pouvez parcourir tous les paragraphes de la TOC et modifier leurs positions de tabulation.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Désormais, les entrées de la TOC affichent les numéros de page exactement où vous le souhaitez, donnant à votre document un aspect soigné.

## Problèmes courants et astuces
- **Titres manquants dans la TOC :** Assurez‑vous que vos titres utilisent les styles intégrés (`Heading1`, `Heading2`, etc.) ou mappez les styles personnalisés aux niveaux de la TOC.  
- **Tabulation non appliquée :** Vérifiez que le paragraphe appartient réellement à un style de TOC (`TOC_1`‑`TOC_9`).  
- **Performance sur de gros documents :** Appelez `doc.updateFields()` après l’insertion de la TOC pour actualiser les entrées en une seule passe.

## Questions fréquentes

**Q : Comment modifier le formatage des entrées de la table des matières ?**  
R : Utilisez `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)` où *X* représente le niveau (1‑9) et modifiez sa police, sa couleur ou ses paramètres de paragraphe.

**Q : Comment ajouter davantage de niveaux à ma TOC ?**  
R : Ajustez le commutateur `\o "1-3"` de `FieldToc` (par exemple) pour inclure des niveaux de titres supplémentaires, puis mettez à jour les styles correspondants `TOC_X`.

**Q : Puis‑je changer les positions des tabulations pour des entrées spécifiques de la TOC ?**  
R : Oui – parcourez les paragraphes comme indiqué dans la section « Personnalisation des tabulations » et modifiez chaque tabulation individuellement.

**Q : Est‑il possible de générer une TOC dans une sortie PDF ?**  
R : Absolument. Enregistrez le document au format PDF (`doc.save("output.pdf")`) après la génération de la TOC ; le champ est rendu automatiquement.

**Q : Dois‑je appeler `updateFields()` manuellement ?**  
R : Lorsque vous insérez un `FieldToc`, Aspose.Words le met à jour lors de l’enregistrement, mais appeler `doc.updateFields()` fournit des résultats immédiats pour le débogage.

## Conclusion
Vous avez appris à **ajuster les numéros de page**, **insérer une table des matières**, et **personnaliser les styles de la TOC** avec Aspose.Words pour Java. Ces techniques vous permettent de créer des documents clairs, navigables et professionnellement formatés, conformes à n’importe quelle norme de publication.

---  

**Last Updated:** 2026-01-03  
**Tested With:** Aspose.Words for Java (latest release)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}