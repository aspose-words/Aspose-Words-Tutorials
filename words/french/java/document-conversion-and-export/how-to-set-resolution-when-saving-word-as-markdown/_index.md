---
category: general
date: 2026-05-04
description: Comment définir la résolution pour l’exportation Markdown depuis Word.
  Apprenez la résolution des images Markdown, comment exporter les équations et enregistrer
  Word au format Markdown en Java.
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: fr
og_description: Comment définir la résolution pour l'exportation Markdown depuis Word.
  Ce guide montre la résolution des images en markdown, l'exportation des équations
  et la sauvegarde de Word au format markdown.
og_title: Comment définir la résolution lors de l’enregistrement de Word en Markdown
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: Comment définir la résolution lors de l’enregistrement de Word en Markdown
url: /fr/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir la résolution lors de l'enregistrement de Word en Markdown

Vous vous êtes déjà demandé **comment définir la résolution** pour les images qui apparaissent dans un fichier Markdown généré à partir d'un document Word ? Vous n'êtes pas le seul. De nombreux développeurs rencontrent un problème lorsque les images mathématiques rasterisées par défaut sont floues, surtout sur les écrans à haute résolution (DPI).  

Dans ce tutoriel, nous parcourrons les étapes exactes pour contrôler *la résolution des images Markdown* tout en montrant **comment exporter les équations** en LaTeX, et enfin comment **enregistrer Word en markdown** à l'aide d'Aspose.Words for Java. À la fin, vous disposerez d'un fichier Markdown net et prêt pour la production, qui rend les équations proprement et les images avec la qualité requise.

## Prérequis

- Java 17 (ou tout JDK récent)  
- Aspose.Words for Java 23.6 ou plus récent – vous pouvez le récupérer depuis Maven Central  
- Un document Word (`.docx`) contenant des objets OfficeMath (équations) et éventuellement des images raster  
- Une connaissance de base de Maven/Gradle et d'un IDE (IntelliJ IDEA, Eclipse, VS Code, etc.)

Aucune bibliothèque supplémentaire n'est requise ; tout le reste est géré par Aspose.Words.

---

## Comment définir la résolution pour l'exportation Markdown

> **Astuce :** La résolution que vous choisissez influence directement la taille du fichier des images générées. Une valeur de **300 dpi** est un bon compromis pour la plupart des visionneuses Markdown basées sur le web.

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

L'appel `setImageResolution(int dpi)` est le cœur de **comment définir la résolution**. Il indique à Aspose.Words de rasteriser toutes les images de secours (par ex., lorsqu'une équation ne peut pas être représentée en LaTeX pur) au nombre de points par pouce spécifié. Si vous omettez cette ligne, la bibliothèque revient à son défaut de 220 dpi, ce qui peut apparaître flou sur les écrans Retina.

### Pourquoi utiliser LaTeX pour les équations ?

Lorsque vous exportez les équations en LaTeX (`OfficeMathExportMode.LATEX`), le Markdown résultant contient du code LaTeX brut entouré de `$…$` ou `$$…$$`. La plupart des rendus Markdown modernes (GitHub, GitLab, MkDocs avec MathJax) afficheront cela comme des graphiques vectoriels nets et évolutifs—aucun souci de résolution à ce niveau. Le paramètre de résolution ne concerne que **la résolution des images Markdown** pour les images raster de secours, telles que les graphiques ou images intégrés qui ne sont pas pris en charge nativement par le Markdown.

---

## Comment utiliser efficacement la résolution des images Markdown

Si vous devez intégrer des images classiques (par ex., des captures d'écran) dans votre fichier Word, elles seront converties en PNG par Aspose.Words. La même méthode `setImageResolution` s'applique, garantissant que ces PNG héritent du DPI que vous spécifiez. Voici une petite checklist :

1. **Choisissez un DPI qui correspond à votre plateforme cible** – 72 dpi pour le web hérité, 150 dpi pour les écrans standards, 300 dpi pour les PDF de qualité impression.  
2. **Testez le résultat** – ouvrez le fichier `.md` généré dans votre visionneuse préférée et zoomez pour vérifier la netteté.  
3. **Prenez en compte la taille du fichier** – un DPI plus élevé produit des PNG plus volumineux ; si la bande passante est un problème, expérimentez avec 200 dpi et comparez.

---

## Comment exporter les équations en LaTeX

La ligne `saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` indique à Aspose.Words de traduire chaque objet OfficeMath en LaTeX. C'est l'approche recommandée parce que :

- **Scalabilité** – LaTeX s'affiche à n'importe quelle taille sans perte de qualité.  
- **Éditabilité** – Vous pouvez ensuite ajuster le LaTeX directement dans le fichier Markdown.  
- **Compatibilité** – La plupart des générateurs de sites statiques et des outils de documentation supportent déjà le rendu LaTeX.

Si vous avez besoin de l'ancienne méthode de secours basée sur les images, il suffit de passer à `OfficeMathExportMode.IMAGE`. Dans ce cas, la résolution que vous définissez devient encore plus cruciale.

---

## Enregistrer Word en Markdown – Exemple complet de bout en bout

Ci-dessous se trouve un extrait complet et exécutable d'un projet Maven qui démontre le flux complet, de la déclaration des dépendances à l'exécution.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**Résultat attendu :** `MathExport.md` contiendra des blocs LaTeX pour chaque équation, et toutes les images intégrées apparaîtront comme des liens PNG dont le DPI est de 300. Ouvrez le fichier dans un visualiseur Markdown qui supporte MathJax (par ex., VS Code avec l'extension Markdown Preview Enhanced) et vous devriez voir des équations et des images parfaitement nettes.

---

## Questions fréquentes & cas particuliers

### Et si j'ai besoin d'un DPI différent pour une seule image ?

Aspose.Words applique le DPI globalement via `setImageResolution`. Pour gérer un DPI par image, vous devrez post‑traiter le Markdown généré : remplacer les fichiers PNG par des versions à plus haute résolution et ajuster manuellement les liens d'image. Ce n'est pas idéal, mais faisable pour quelques cas particuliers.

### Cela fonctionne-t-il sur Linux/macOS ?

Absolument. La bibliothèque est pure Java, donc le même code fonctionne partout où le JDK fonctionne. Assurez‑vous simplement que les chemins de fichiers utilisent des barres obliques (`/`) ou `Paths.get(...)` pour une gestion indépendante de la plateforme.

### Qu'en est‑il de la sortie SVG ?

Si vous préférez des images vectorielles pour les graphiques, vous pouvez définir `saveOptions.setExportImagesAsSvg(true);`. Les SVG ignorent le DPI, donc le problème de **résolution des images Markdown** disparaît. Cependant, tous les rendus Markdown ne gèrent pas les SVG correctement, il faut donc tester votre plateforme cible d'abord.

### Puis‑je intégrer le Markdown généré dans un générateur de site statique ?

Oui. La sortie est un simple `.md` avec la syntaxe Markdown standard plus les délimiteurs LaTeX. La plupart des générateurs (Jekyll, Hugo, MkDocs) l'accepteront tel quel. N'oubliez pas d'activer MathJax ou KaTeX dans la configuration de votre site.

---

## Conclusion

Nous avons couvert **comment définir la résolution** pour les images lorsque vous **enregistrez Word en markdown**, exploré les subtilités de **la résolution des images Markdown**, démontré **comment exporter les équations** en LaTeX, et présenté l'implémentation Java complète. En ajustant `setImageResolution` et en choisissant le bon `OfficeMathExportMode`, vous obtenez un contrôle précis à la fois sur la fidélité visuelle et la taille du fichier.

Prêt pour l'étape suivante ? Essayez de combiner cette approche avec Aspose.PDF pour convertir la même source Word directement en PDF, ou expérimentez `setExportImagesAsSvg(true)` pour des graphiques vectoriels. Les techniques que vous avez apprises ici sont des blocs de construction pour tout pipeline de documentation automatisé.

Si vous avez trouvé ce guide utile, donnez‑lui une étoile sur GitHub, partagez‑le avec vos collègues, ou laissez un commentaire ci‑dessous avec vos propres astuces. Bon codage !  

![Exemple de réglage de résolution](resolution.png "Comment définir la résolution lors de l'enregistrement de Word en Markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}