---
category: general
date: 2026-09-11
description: Apprenez à modifier le format des notes de bas de page en Java avec Aspose.Words.
  Ce guide explique comment éditer une note de bas de page, mettre à jour le style
  des notes de bas de page et modifier le séparateur de notes de bas de page.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: fr
lastmod: 2026-09-11
og_description: Modifiez le format des notes de bas de page en Java avec Aspose.Words.
  Suivez ce guide complet pour modifier la note de bas de page, mettre à jour le style
  de la note de bas de page et modifier le séparateur de note de bas de page.
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: Modifier le format des notes de bas de page en Java – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: Comment modifier le format des notes de bas de page dans un document Word avec
  Java
url: /fr/java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment modifier le format des notes de bas de page dans un document Word avec Java

Si vous devez **modifier le format des notes de bas de page** dans un document Word, ce tutoriel vous guide à travers les étapes exactes en utilisant Aspose.Words for Java. Que vous construisiez une chaîne de publication ou que vous ayez simplement besoin de **savoir comment modifier l'apparence des notes de bas de page** programmétiquement, la solution ci‑dessous couvre tout, du chargement du fichier à l'enregistrement de la version mise à jour.

Vous apprendrez comment **mettre à jour le style des notes de bas de page**, rendre le séparateur de note de bas de page en gras, et même **modifier les propriétés du séparateur de note de bas de page** telles que la taille ou la couleur de la police. Le guide part du principe que vous avez des connaissances de base en Java et une licence fonctionnelle d'Aspose.Words for Java.

## Prérequis

* Java 17 ou une version plus récente installé.
* Aspose.Words for Java (version 23.12 ou ultérieure) ajouté au classpath de votre projet.
* Un document Word (`input.docx`) contenant au moins une note de bas de page.
* Un IDE ou un outil de construction (Maven/Gradle) pour compiler et exécuter le code.

Si vous ne savez pas comment ajouter Aspose.Words à un projet Maven, incluez la dépendance suivante dans votre `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Modifier le format des notes de bas de page avec Aspose.Words for Java

Le cœur de la solution est un petit programme Java qui charge un document, accède au paragraphe du séparateur de note de bas de page, modifie son formatage et enregistre le résultat. Le code est entièrement autonome, vous pouvez donc le copier dans une nouvelle classe et l'exécuter immédiatement.

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Pourquoi chaque étape est importante

* **Chargement du document** (`new Document`) crée une représentation en mémoire que Aspose.Words peut manipuler.  
* **Récupération du séparateur de note de bas de page** (`getFootnoteSeparator`) vous donne un accès direct au paragraphe qui sépare les notes de bas de page du texte principal. C’est l’élément que vous devez cibler lorsque vous voulez **modifier le format des notes de bas de page**.  
* **Mise en forme du run** (`setBold`, `setItalic`, `setSize`, `setColor`) montre comment **modifier les propriétés du séparateur de note de bas de page**. Vous pouvez ajouter d’autres attributs de police ici, comme le soulignement ou la mise en évidence, pour contrôler entièrement l’apparence.  
* **Enregistrement du document** écrit les modifications sur le disque, produisant un nouveau fichier (`output.docx`) qui reflète le style de note de bas de page mis à jour.

> **Astuce :** Si votre document source utilise un séparateur de note de bas de page personnalisé contenant plusieurs runs (par ex., une combinaison de symboles), parcourez `footnoteSeparator.getRuns()` et appliquez les mêmes paramètres `Font` à chaque run pour un style cohérent.

## Comment modifier le séparateur de note de bas de page programmétiquement

Il arrive parfois que vous deviez modifier non seulement le séparateur mais aussi le texte de la note de bas de page lui‑-même. La même API peut être utilisée pour accéder à chaque note de bas de page, ajuster le formatage de son paragraphe ou changer le style de numérotation.

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

L’extrait ci‑dessus montre **comment modifier le corps des notes de bas de page** après avoir déjà **modifié le format des notes de bas de page** pour le séparateur. En itérant sur `doc.getFootnotes()`, vous vous assurez que chaque note de bas de page hérite du même style, ce qui est essentiel pour un document à l’aspect professionnel.

## Mettre à jour le style des notes de bas de page pour une apparence de document cohérente

Si vous préférez travailler avec des styles plutôt qu’avec des runs individuels, Aspose.Words vous permet de créer ou de modifier un objet `Style` puis de l’appliquer aux notes de bas de page et au séparateur. Cette approche est utile lorsque vous devez **mettre à jour le style des notes de bas de page** sur de nombreux documents.

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

Utiliser un style dédié facilite la maintenance future — modifiez le style une fois, et chaque note de bas de page ainsi que le séparateur se mettent à jour automatiquement. Cette technique est la méthode recommandée pour **mettre à jour le style des notes de bas de page** dans des flux de travail d’édition à grande échelle.

## Modifier le séparateur de note de bas de page pour correspondre à votre identité visuelle

Les directives de marque imposent parfois que le séparateur de note de bas de page utilise un caractère spécifique (par ex., un astérisque) ou une ligne personnalisée. Aspose.Words vous permet de remplacer entièrement le contenu du séparateur par défaut.

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

Le code ci‑dessus **modifie le séparateur de note de bas de page** en supprimant les runs existants et en insérant un nouveau run avec le texte et le formatage souhaités. Vous pouvez également utiliser des caractères Unicode tels que `\u2022` (puce) ou `\u2014` (tiret long) pour obtenir l’effet visuel exact requis par votre marque.

## Résultat attendu

Après l’exécution du programme :

* Le séparateur de note de bas de page dans `output.docx` apparaît **en gras**, **en italique**, 10 pt, et gris (ou toute couleur que vous avez définie).  
* Tous les paragraphes de notes de bas de page adoptent le style que vous avez défini, assurant une apparence uniforme dans tout le document.  
* Si vous avez remplacé le texte du séparateur, la nouvelle ligne personnalisée est visible exactement à l’endroit où se trouvait la ligne originale.

Ouvrez le fichier résultant dans Microsoft Word ou LibreOffice Writer pour vérifier les modifications. Vous devriez voir le séparateur mis à jour juste au-dessus de la première note de bas de page, et le texte de la note de bas de page devrait refléter toutes les modifications de style que vous avez appliquées.

## Pièges courants et comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| `footnoteSeparator.getRuns().getCount() == 0` lance une exception | Certains documents ont un paragraphe de séparateur vide. | Ajoutez une vérification défensive et créez un run s’il n’en existe aucun (voir l’exemple de code). |
| Les changements de police ne sont pas visibles | Le document utilise un thème qui surcharge le formatage direct. | Définissez `font.setThemeFont(null)` ou appliquez un style personnalisé au lieu du formatage direct. |
| Le fichier enregistré ne reflète pas les modifications | Le fichier original est encore ouvert dans Word, bloquant le chemin de sortie. | Fermez toutes les instances du fichier avant d’exécuter le programme, ou |

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Traitement de texte avec notes de bas de page et notes de fin](/words/english/net/working-with-footnote-and-endnote/)
- [Définir la position des notes de bas de page et des notes de fin](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Comment afficher les informations de version d’Aspose.Words en Java : guide complet](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}