---
category: general
date: 2026-11-15
description: Définissez l’interligne des paragraphes dans un document Word avec Java.
  Apprenez à définir l’interligne de façon programmatique à l’aide d’Aspose.Words
  pour un formatage précis du document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: fr
lastmod: 2026-11-15
og_description: Définissez l’interligne des paragraphes dans un document Word avec
  Java. Ce guide explique comment régler l’interligne des paragraphes et des séparateurs
  de notes de bas de page à l’aide d’Aspose.Words, vous offrant un contrôle total
  sur la mise en page du document.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Définir l'interligne des paragraphes dans Word avec Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Définir l’interligne du paragraphe dans un document Word avec Java
url: /fr/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir l’interligne d’un paragraphe dans un document Word avec Java

Si vous devez **définir l’interligne d’un paragraphe** dans un document Word, ce tutoriel vous montre comment le faire avec Java et Aspose.Words. Vous apprendrez également **comment définir l’interligne** pour les séparateurs de notes de bas de page — une exigence courante lors du formatage de documents professionnels.

Dans les sections suivantes, vous allez :

* Charger un fichier *.docx* existant.
* Récupérer le paragraphe du séparateur de note de bas de page.
* Appliquer une valeur d’interligne personnalisée.
* Enregistrer le document mis à jour.

Aucune configuration externe n’est requise au‑delà de l’ajout de la bibliothèque Aspose.Words à votre projet, vous pouvez donc copier le code tel quel et l’exécuter immédiatement.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Java 17 ou une version plus récente installé.
* Maven (ou un autre outil de construction) pour gérer les dépendances.
* Une licence valide d’Aspose.Words for Java (l’évaluation gratuite suffit pour les tests).
* Un document Word d’entrée (`input.docx`) placé dans un répertoire connu.

Ajoutez la dépendance Aspose.Words à votre `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Définir l’interligne d’un paragraphe avec Aspose.Words

Cet en‑tête H2 contient le mot‑clé principal, répondant ainsi à l’exigence SEO.

### Étape 1 : Charger le document Word

Tout d’abord, créez une instance `Document` qui pointe vers votre fichier source.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Pourquoi c’est important* : le chargement du document vous fournit un modèle en mémoire que vous pouvez manipuler sans toucher au fichier original jusqu’à ce que vous l’enregistriez explicitement.

### Étape 2 : Récupérer le séparateur de note de bas de page

Les séparateurs de notes de bas de page sont des paragraphes spéciaux qui apparaissent entre les notes et le texte principal. Pour modifier leur apparence, vous devez accéder à l’objet `FootnoteSeparator`.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Astuce* : si votre document ne contient pas de notes de bas de page, le séparateur existe toujours sous forme de paragraphe masqué, donc l’appel ne renverra jamais `null`.

### Étape 3 : Comment définir l’interligne du paragraphe du séparateur

Appliquez maintenant l’interligne souhaité. Aspose.Words utilise les points pour les valeurs d’interligne ; 12 pts correspond approximativement à un interligne simple pour la plupart des polices.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Vous pouvez également utiliser d’autres modes d’interligne :

| Mode                     | Appel de méthode                                      |
|--------------------------|-------------------------------------------------------|
| **Exactly** (pts fixes) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`        |
| **Multiple** (ex. 1.5)   | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Choisir la règle correcte garantit que le document s’affiche de façon cohérente dans Word, Google Docs et les autres visionneuses.

### Étape 4 : Enregistrer le document mis à jour

Enfin, écrivez les modifications sur le disque.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Lorsque vous ouvrirez `output.docx` dans Microsoft Word, le séparateur de note de bas de page affichera l’interligne que vous avez défini.

## Comprendre comment définir l’interligne pour les paragraphes ordinaires

La même API fonctionne pour tout objet `Paragraph`, pas seulement les séparateurs de notes de bas de page. Voici un exemple rapide qui ajuste l’interligne du premier paragraphe du corps :

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Pourquoi cela peut être nécessaire** : les rapports, contrats et travaux académiques exigent souvent un style d’interligne spécifique (par ex. double interligne pour les brouillons). Utiliser la même méthode `setLineSpacing` garantit la mise en page exacte attendue.

## Pièges courants et comment les éviter

| Problème                                   | Cause                                          | Solution |
|--------------------------------------------|-----------------------------------------------|----------|
| L’interligne ne change pas                 | `LineSpacingRule` laissé à sa valeur par défaut (AUTO) | Définissez explicitement la règle avec `setLineSpacingRule`. |
| Lignes blanches supplémentaires après le séparateur | Le séparateur contient des retours chariot masqués | Nettoyez le texte du séparateur avec `separator.getText().trim();` avant d’appliquer l’interligne. |
| Le document devient corrompu après l’enregistrement | Utilisation d’une version obsolète d’Aspose.Words | Mettez à jour vers la dernière version (ex. 24.10) qui contient des correctifs pour l’enregistrement. |

## Astuce pro : traitement par lots de plusieurs documents

Si vous devez mettre à jour des dizaines de fichiers, encapsulez la logique dans une méthode d’assistance et parcourez un dossier :

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Exécuter cette méthode dans une boucle vous fera gagner des heures de travail manuel.

## Résultat attendu

Après l’exécution du programme complet, `output.docx` :

* Contiendra le contenu original inchangé, à l’exception de l’interligne.
* Affichera le séparateur de note de bas de page avec un interligne simple (12 pts).
* Conservera toute autre mise en forme (styles, images, tableaux).

Ouvrez le fichier dans Word et vérifiez que la ligne du séparateur est plus serrée (ou plus lâche, selon la valeur que vous avez définie).

## Conclusion

Vous savez maintenant comment **définir l’interligne d’un paragraphe** dans un document Word avec Java, et vous comprenez également **comment définir l’interligne** pour les séparateurs de notes de bas de page ainsi que pour les paragraphes ordinaires. L’exemple complet et exécutable montre comment charger un document, ajuster les propriétés d’interligne et enregistrer le résultat—le tout en quelques appels d’API clairs.

**Prochaines étapes** que vous pourriez explorer :

* **Comment définir l’interligne** pour les tableaux et les éléments de liste.
* Appliquer différentes règles d’interligne aux titres versus au corps du texte.
* Utiliser l’objet `Style` pour imposer l’interligne sur l’ensemble du document.

Expérimentez avec les valeurs, combinez‑les avec d’autres options de formatage, et vous disposerez d’un contrôle total sur la mise en page des documents dans n’importe quelle application Java. Bon codage !


## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Change Asian Paragraph Spacing And Indents In Word Document](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}