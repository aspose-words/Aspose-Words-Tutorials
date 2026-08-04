---
category: general
date: 2026-08-04
description: Chargez le soulignement Markdown en Java et préservez le formatage Markdown
  lors du chargement du Markdown dans le document. Suivez ce tutoriel étape par étape.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: fr
lastmod: 2026-08-04
og_description: Chargez le markdown avec soulignement en Java et préservez le formatage
  markdown. Apprenez comment charger le markdown dans un document avec un support
  complet du soulignement.
og_image_alt: Diagram showing load markdown underline process
og_title: Charger le soulignement Markdown en Java – guide étape par étape
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: Charger le soulignement Markdown en Java – guide complet de programmation
url: /fr/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Charger le soulignement markdown en Java – guide complet de programmation

Si vous devez **charger le soulignement markdown** lors de la conversion d’un fichier Markdown en objet `Document`, ce guide vous montre exactement comment le faire. Vous apprendrez également comment **charger le markdown dans le document** sans perdre le style de soulignement, en garantissant que le formatage Markdown original est entièrement préservé.

Le tutoriel couvre tout ce que vous devez savoir : bibliothèques requises, chaque étape de configuration, et comment vérifier que le formatage du soulignement a survécu à l’importation. À la fin, vous disposerez d’un extrait de code réutilisable que vous pourrez intégrer à n’importe quel projet Java.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

- Java 17 ou version ultérieure installé (l’exemple utilise le système de modules moderne)
- La dernière version de **GroupDocs.Viewer** (ou une bibliothèque compatible qui fournit `LoadOptions` et `Document`)
- Un fichier Markdown (`sample.md`) contenant du texte souligné, par ex. `<u>underlined</u>` ou la syntaxe GitHub‑flavored `__underlined__`
- Un IDE tel qu’IntelliJ IDEA ou VS Code, bien que tout éditeur de texte fonctionne

Ces exigences garantissent que le code s’exécute sans configuration supplémentaire.

## Charger le soulignement markdown – guide étape par étape

Le processus se compose de trois actions principales : créer une instance de `LoadOptions`, activer la détection du soulignement, puis charger le fichier Markdown avec ces options. Chaque étape est expliquée ci‑dessous.

### Étape 1 : Créer `LoadOptions` pour le document

`LoadOptions` vous permet de personnaliser la façon dont la bibliothèque analyse le fichier source. Créer une nouvelle instance vous donne une base propre pour les réglages ultérieurs.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

L’objet `LoadOptions` est le point d’entrée pour toutes les personnalisations liées à l’importation. Vous l’utiliserez à l’étape suivante pour activer la détection du soulignement.

### Étape 2 : Activer la détection du formatage de soulignement lors du chargement

Par défaut, le visualiseur peut ignorer les balises de soulignement car elles sont moins courantes en Markdown. Activer ce drapeau indique à l’analyseur de conserver les segments de soulignement intacts.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

Le réglage `setImportUnderlineFormatting(true)` garantit que toute balise HTML `<u>` ou toute syntaxe de soulignement GitHub‑flavored est traduite dans le modèle `Document` sous forme de style souligné. C’est l’action clé qui fait fonctionner **load markdown underline** comme prévu.

### Étape 3 : Charger le fichier Markdown en utilisant les options configurées

Vous pouvez maintenant charger le fichier. Passez l’objet `loadOptions` au constructeur `Document` afin que l’analyseur respecte le drapeau de soulignement.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

Lorsque le constructeur se termine, `markdownDoc` contient une représentation complète en mémoire du source Markdown, avec les passages soulignés.

### Étape 4 : Vérifier que le formatage de soulignement est préservé

Une vérification rapide vous aide à confirmer que **preserve markdown formatting** a fonctionné. L’extrait suivant imprime le texte de chaque paragraphe et marque les fragments soulignés avec un tilde (`~`) pour plus de visibilité.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**Sortie attendue** (en supposant que `sample.md` contient `This is __underlined__ text`) :

```
This is ~underlined~ text
```

Les tildes indiquent que le style de soulignement a survécu à l’importation, confirmant que l’opération **load markdown into document** a préservé le formatage original.

## Pièges courants et comment les éviter

| Symptom | Cause | Fix |
|---|---|---|
| Le soulignement disparaît après le chargement | `setImportUnderlineFormatting` laissé à sa valeur par défaut `false` | Assurez‑vous d’appeler `loadOptions.setImportUnderlineFormatting(true)` avant de créer le `Document`. |
| Seule une partie du texte est soulignée | Syntaxe Markdown mixte (ex. HTML `<u>` mélangé avec `__underline__`) | La bibliothèque supporte les deux ; vérifiez que le fichier source utilise un marqueur de soulignement cohérent. |
| Le document ne se charge pas | Chemin de fichier incorrect ou dépendances de bibliothèque manquantes | Utilisez un chemin absolu ou placez `sample.md` relatif au répertoire de travail ; incluez les JARs du viewer dans le classpath. |

**Astuce :** Si vous devez également conserver les styles gras ou italique, activez‑les avec `setImportBoldFormatting(true)` et `setImportItalicFormatting(true)` respectivement. Combiner ces drapeaux vous donne une importation totalement fidèle des styles Markdown les plus courants.

## Exemple complet exécutable

Voici un programme Java autonome qui réunit tous les éléments. Copiez le code dans un fichier nommé `LoadMarkdownUnderlineDemo.java`, ajustez le chemin du fichier, puis exécutez‑le avec `java LoadMarkdownUnderlineDemo`.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

L’exécution du programme affiche le contenu du document avec des marqueurs de soulignement, prouvant que la fonctionnalité **load markdown underline** fonctionne et que vous pouvez **preserve markdown formatting** tout au long du pipeline d’importation.

## Conclusion

Vous savez maintenant comment **load markdown underline** en Java, comment **load markdown into document** tout en conservant le style original, et comment vérifier que le formatage du soulignement reste intact. Cette approche fonctionne avec les dernières versions de GroupDocs.Viewer et peut être étendue pour prendre en charge des fonctionnalités Markdown supplémentaires telles que le gras, l’italique et les tableaux.

Ensuite, explorez des sujets connexes comme **preserve markdown formatting for tables**, **render Markdown to PDF**, ou **custom styling of imported Markdown elements**. Ajustez les drapeaux `LoadOptions` pour correspondre exactement aux exigences de formatage de votre application, et vous disposerez d’un contrôle granulaire sur chaque étape d’importation. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Maîtriser les options de chargement Markdown avec Aspose.Words pour Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Maîtriser les options de chargement Markdown Aspose Words Java](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}