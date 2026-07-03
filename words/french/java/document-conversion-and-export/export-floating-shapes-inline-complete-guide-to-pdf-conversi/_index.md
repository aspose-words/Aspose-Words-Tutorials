---
category: general
date: 2026-07-03
description: Exportez les formes flottantes en ligne lors de la conversion de Word
  en PDF en ligne. Apprenez comment définir les options PDF et enregistrer les options
  de conversion de Word en PDF en Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: fr
og_description: Exporter les formes flottantes en ligne lors de la conversion d’un
  document Word en PDF. Ce tutoriel montre comment définir les options PDF et enregistrer
  les options Word en PDF.
og_title: Exporter des formes flottantes en ligne – Guide de conversion PDF Java
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Exporter les formes flottantes en ligne – Guide complet de la conversion PDF
url: /fr/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exporter les formes flottantes en ligne – Guide complet de conversion PDF

Vous avez déjà eu besoin d'**exporter les formes flottantes en ligne** lors de la conversion d'un document Word en PDF ? Vous n'êtes pas seul — de nombreux développeurs rencontrent ce problème lorsque leurs diagrammes ou icônes se déplacent mystérieusement vers des calques séparés. La bonne nouvelle, c’est qu’une seule option PDF peut garder ces formes bien à l'intérieur des balises `<span>`, préservant la mise en page exactement comme vous la voyez dans Word.

Dans ce tutoriel, nous allons parcourir **comment définir les options PDF** en Java, vous montrer le code exact pour **enregistrer Word en PDF avec des options**, et expliquer pourquoi vous pourriez vouloir **convertir Word en PDF en ligne** plutôt que d’utiliser l’exportation par défaut au niveau du bloc. À la fin, vous disposerez d’un extrait prêt à l’emploi que vous pourrez intégrer à n’importe quel projet Maven ou Gradle.

## Ce que vous allez apprendre

- La différence entre l'exportation en ligne `<span>` et en bloc `<div>` pour les formes flottantes.  
- Comment configurer `PdfSaveOptions` pour forcer le rendu en ligne.  
- Un code pas à pas qui charge un `.docx`, applique l’option et génère un PDF.  
- Les pièges courants (polices manquantes, formes non prises en charge) et comment les éviter.  
- Des astuces pour tester le résultat et étendre l’approche à d’autres éléments du document.

**Prérequis** – vous aurez besoin de Java 8 ou plus récent, de la bibliothèque Aspose.Words for Java (ou de toute API qui reproduit sa classe `PdfSaveOptions`), et d’un fichier Word d’exemple contenant des formes flottantes (le tutoriel utilise `FloatingShapes.docx`). Aucun autre outil externe n’est requis.

---

## Étape 1 : Charger le document Word source

La première chose à faire est d’ouvrir le `.docx` que vous souhaitez transformer. C’est simple, mais assurez‑vous que le chemin soit absolu ou correctement résolu depuis votre classpath.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Pourquoi c’est important :*  
Si le document n’est pas chargé correctement, la conversion PDF suivante lèvera une `FileNotFoundException`. L’utilisation de `Document` garantit que le modèle d’objet interne est entièrement peuplé, y compris toutes les formes flottantes présentes sur la page.

---

## Étape 2 : Créer les options d’enregistrement PDF et définir les formes flottantes en ligne

C’est ici que la magie opère. Par défaut, Aspose.Words exporte les formes flottantes sous forme d’éléments `<div>` de niveau bloc, ce qui peut rompre le flux dans les PDF basés sur HTML. L’appel à `setExportFloatingShapesAsInlineTag(true)` indique au moteur d’envelopper chaque forme dans une balise `<span>` en ligne.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Pourquoi c’est important :*  
- **Fidélité de la mise en page** – Les balises en ligne maintiennent la forme alignée avec le texte environnant, évitant les espaces indésirables.  
- **Recherchabilité** – Les éléments en ligne sont plus susceptibles d’être correctement indexés par les lecteurs PDF.  
- **Contrôle du style** – Vous pouvez cibler le `<span>` avec du CSS si vous reconvertissez plus tard le PDF en HTML.

> **Astuce :** Si vous avez besoin du comportement en bloc ancien pour un document spécifique, passez simplement `false` ou omettez l’appel.

---

## Étape 3 : Enregistrer le document en PDF en utilisant les options configurées

Vous combinez maintenant le `Document` chargé avec le `PdfSaveOptions` et écrivez le fichier. Cette ligne unique fait le gros du travail.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Pourquoi c’est important :*  
La méthode `save` respecte chaque drapeau que vous avez défini sur `pdfOptions`. Omettre de passer les options reviendra à l’exportation par défaut en bloc, annulant l’objectif d’**exporter les formes flottantes en ligne**.

---

## Exemple complet fonctionnel

En réunissant le tout, voici un programme compact que vous pouvez compiler et exécuter immédiatement. Remplacez `YOUR_DIRECTORY` par un chemin réel sur votre machine.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Résultat attendu** – Après l’exécution du programme, ouvrez `FloatingShapes.pdf`. Vous devriez voir les formes collées au texte, sans espace blanc supplémentaire, et la représentation HTML (si vous inspectez la structure interne du PDF) contiendra des balises `<span>` autour de chaque forme.

![Exemple d'exportation de formes flottantes en ligne](https://example.com/export-inline.png "Capture d'écran montrant les formes flottantes rendues en ligne dans le PDF")

*Texte alternatif de l’image :* **export floating shapes inline** capture d’écran du PDF avec des formes en ligne.

---

## Questions fréquentes & cas limites

### 1. « Et si mon document contient du SmartArt complexe ? »

Le SmartArt est traité comme un objet de dessin. Le drapeau en ligne fonctionne pour la plupart des formes vectorielles, mais un SmartArt très détaillé peut encore être rendu sous forme d’image. Dans ces cas, pensez à aplatir le SmartArt dans Word avant la conversion, ou utilisez `pdfOptions.setExportSmartArtAsImage(true)` pour forcer l’exportation en image.

### 2. « Puis‑je combiner des exportations en ligne et en bloc dans le même document ? »

Malheureusement, l’API applique le paramètre globalement. Si vous avez besoin d’un comportement mixte, divisez le document en sections, exportez chaque section séparément avec des options différentes, puis fusionnez les PDF à l’aide de `PdfMerger`.

### 3. « Cela affecte‑t‑il l’inclusion des polices ? »

Non. L’inclusion des polices est contrôlée par `pdfOptions.setEmbedFullFonts(true)` (par défaut). Vous pouvez l’activer ou la désactiver sans toucher au drapeau des formes en ligne.

### 4. « Comment vérifier que les formes sont réellement des `<span>` ? »

Ouvrez le PDF résultant avec un outil comme **PDF.js** ou **Adobe Acrobat** → **Modifier le PDF** → **Inspecteur d’objets**. Vous verrez la forme enveloppée dans un élément `<span>` dans le XML sous‑jacent. Si vous voyez `<div>`, l’option n’a pas été appliquée.

---

## Extension de l’approche – Options connexes

Puisque vous êtes ici, vous pourriez également explorer d’autres paramètres de conversion PDF :

| Option | Ce qu’elle fait | Cas d’utilisation typique |
|--------|----------------|---------------------------|
| `setCompressImages(true)` | Réduit la taille des images | Téléchargements plus rapides |
| `setUseHighQualityRendering(true)` | Améliore le rendu vectoriel | PDF prêts à l’impression |
| `setExportDocumentStructure(true)` | Ajoute des balises structurelles pour l’accessibilité | Conformité WCAG |
| `setSaveFormat(SaveFormat.PDF)` | Définit explicitement le format (rarement nécessaire) | Pipelines multi‑format |

Ces réglages se marient bien avec les scénarios **convertir Word en PDF en ligne** où vous avez besoin à la fois de fidélité de mise en page et de performance.

---

## Tester votre conversion

1. **Vérification visuelle** – Ouvrez le PDF dans deux visionneurs (Chrome et Adobe Reader) pour vous assurer que les formes sont alignées.  
2. **Différence automatisée** – Utilisez une bibliothèque comme `pdfbox` pour extraire le XML et vérifier la présence de balises `<span>`.  
3. **Benchmark de performance** – Mesurez le temps d’exécution avec et sans `setCompressImages` pour observer le compromis.

Un exemple JUnit rapide :

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Conclusion

Vous disposez maintenant d’une solution solide, de bout en bout, pour **exporter les formes flottantes en ligne** lorsque vous **convertissez Word en PDF en ligne**. En configurant `PdfSaveOptions`, vous contrôlez la balise HTML utilisée pour chaque forme, gardant vos PDF propres et recherchables. N’oubliez pas de tester le résultat, d’ajuster les options connexes comme la compression d’images, et de gérer les cas particuliers tels que le SmartArt complexe.

Prêt pour l’étape suivante ? Essayez d’appliquer la même technique pour **exporter les tableaux flottants en ligne** ou expérimentez les PDF stylisés avec CSS en utilisant les `HtmlSaveOptions` d’Aspose. Le même schéma — charger, configurer, enregistrer — s’applique à presque tous les scénarios de document‑vers‑PDF.

Vous avez d’autres questions sur **comment définir les options PDF** ou besoin d’aide avec **enregistrer Word en PDF avec des options** pour une bibliothèque différente ? Laissez un commentaire, et bon codage !


## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Convertir Word en PDF avec Aspose.Words for Java](/words/english/java/document-converting/)
- [Comment enregistrer un document en PDF avec Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Exporter la structure d’un document Word vers un document PDF](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}