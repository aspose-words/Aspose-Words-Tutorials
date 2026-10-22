---
category: general
date: 2026-08-07
description: Comment modifier une note de bas de page en Java avec Aspose.Words –
  ajouter un tiret personnalisé, modifier la ligne de la note de bas de page et définir
  l’alignement du paragraphe pour des documents soignés.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: fr
lastmod: 2026-08-07
og_description: Comment modifier une note de bas de page en Java avec Aspose.Words.
  Apprenez à ajouter un tiret personnalisé, à changer la ligne de la note de bas de
  page et à définir l’alignement du paragraphe en quelques étapes seulement.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Comment modifier la note de bas de page en Java – ajouter un tiret, changer
  de ligne, définir l’alignement
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Comment modifier une note de bas de page en Java avec Aspose.Words
url: /fr/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment modifier une note de bas de page en Java avec Aspose.Words

Si vous devez **comment modifier une note de bas de page** dans un document Word en utilisant Java, ce guide présente le flux de travail complet. Vous apprendrez à ajouter un tiret personnalisé, à modifier la ligne de la note de bas de page et à définir l’alignement du paragraphe afin que le séparateur de note de bas de page ait un aspect professionnel.

La modification des notes de bas de page est une exigence courante lors de la préparation de contrats juridiques, de travaux académiques ou de brochures marketing. Les étapes ci‑dessous couvrent tout ce dont vous avez besoin — du chargement du document à l’enregistrement du fichier final — sans nécessiter d’outils supplémentaires.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Java 17 ou une version plus récente installé.
* Aspose.Words for Java (dernière version) ajouté au classpath de votre projet.
* Un fichier DOCX (`input.docx`) contenant au moins une note de bas de page.

Ces éléments garantissent que le code s’exécute sans erreurs d’exécution.

## Comment modifier le séparateur et la ligne de la note de bas de page

Le séparateur de note de bas de page est le paragraphe qui apparaît entre le texte principal et la liste des notes de bas de page. Modifier son apparence améliore la lisibilité et correspond à l’image de marque de l’entreprise.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Pourquoi chaque ligne est importante

1. **Chargement du document** – `new Document(...)` lit le fichier DOCX en mémoire, vous donnant accès à tous ses nœuds.  
2. **Récupération du séparateur** – `getFootnoteSeparator()` renvoie le paragraphe spécial qu’Aspose.Words considère comme la ligne de note de bas de page. Cet objet est le seul endroit où vous pouvez modifier le séparateur en toute sécurité.  
3. **Définition de l’alignement du paragraphe** – `setAlignment(ParagraphAlignment.CENTER)` change l’alignement de la ligne. Le mot‑clé *set paragraph alignment* est appliqué directement au séparateur, assurant un tiret centré.  
4. **Ajout d’un tiret personnalisé** – En supprimant les runs existants et en ajoutant un nouveau `Run` contenant le caractère tiret cadratin (`—`), vous obtenez l’effet *add custom dash* tout en *change footnote line* selon le style souhaité.  
5. **Enregistrement du document** – `doc.save(...)` écrit les modifications sur le disque, produisant un fichier de sortie qui reflète toutes les modifications.

## Ajouter un tiret personnalisé au séparateur de la note de bas de page

Le code de **l’étape 4** illustre la technique *add custom dash*. Vous pouvez remplacer le tiret cadratin par n’importe quelle chaîne, telle que `"***"` ou `"---"`, pour correspondre au style visuel de votre document.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Utiliser un tiret personnalisé est particulièrement utile lorsque la ligne fine par défaut ne respecte pas les directives de marque.

## Modifier le style de la ligne de la note de bas de page

Si vous préférez une ligne solide plutôt qu’un tiret, vous pouvez insérer un caractère Unicode de dessin de boîte ou un soulignement répété.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

L’étape *change footnote line* fonctionne de la même manière quel que soit le caractère choisi, car le paragraphe séparateur ne fait qu’afficher le texte qu’il contient.

## Définir l’alignement du paragraphe pour le séparateur de la note de bas de page

L’opération *set paragraph alignment* n’est pas limitée à l’alignement centré. Vous pouvez aligner à gauche, à droite ou justifier selon les besoins de votre mise en page.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Aligner le séparateur à droite peut être utile pour les documents qui utilisent des notes de bas de page alignées à droite, comme les publications bilingues.

## Exemple complet et exécutable

Voici le programme complet qui intègre tous les concepts — chargement d’un document, modification du séparateur de note de bas de page, ajout d’un tiret personnalisé, changement du style de ligne et définition de l’alignement.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Résultat attendu :** Le fichier `output.docx` contient un tiret cadratin centré à la place de la ligne fine d’origine. Toutes les notes de bas de page restent intactes, et la mise en page du document reflète le nouveau style de séparateur.

## Pièges courants et comment les éviter

| Problème | Raison | Solution |
|----------|--------|----------|
| Séparateur introuvable | Le document ne contient aucune note de bas de page ou utilise un style de note de bas de page personnalisé | Vérifiez que le DOCX source contient au moins une note de bas de page avant d’appeler `getFootnoteSeparator()` |
| Tiret personnalisé invisible | La police ne prend pas en charge le caractère choisi | Utilisez un caractère Unicode supporté par la police par défaut du document, ou intégrez une police compatible |
| Alignement inchangé | Le format du paragraphe est écrasé plus tard dans le code | Appliquez l’alignement **après** tout autre appel de formatage susceptible de le réinitialiser |

Traiter ces points évite les erreurs d’exécution et garantit que le processus *how to edit footnote* fonctionne de manière fiable.

## Prochaines étapes

Maintenant que vous savez **comment modifier une note de bas de page**, vous pouvez explorer des tâches connexes :

* **Ajouter un style de référence de note de bas de page personnalisé** – modifiez les nœuds `FootnoteReference` pour changer la numérotation ou les symboles.  
* **Insérer des notes de bas de page de façon programmatique** – utilisez `DocumentBuilder.insertFootnote()` pour du contenu dynamique.  
* **Appliquer un formatage conditionnel** – changez l’apparence des notes de bas de page en fonction du style de paragraphe ou de la longueur du contenu.

Chacune de ces extensions s’appuie sur la même surface d’API que vous avez utilisée pour *add custom dash*, *change footnote line* et *set paragraph alignment*.

---

*Bon codage ! Si le tutoriel vous a aidé à maîtriser la modification des notes de bas de page, pensez à le partager avec votre équipe ou à soumettre une pull request pour améliorer davantage l’exemple.*

## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Set Footnote And End Note Position](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}