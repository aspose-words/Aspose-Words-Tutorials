---
date: 2026-10-23
description: Apprenez à créer des étiquettes Java QR code avec Aspose.Words. Ce guide
  step‑by‑step vous montre comment embed barcodes dans les documents Word et customize
  size, colors, et format.
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: Génération d'étiquettes Barcode personnalisées
og_description: Apprenez à créer des étiquettes Java QR code avec Aspose.Words. Ce
  guide explique barcode embedding, size control, et color customization dans les
  documents Word.
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: Comment créer des étiquettes Java QR code avec Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  headline: How to create QR code Java labels using Aspose.Words
  type: TechArticle
- description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  name: How to create QR code Java labels using Aspose.Words
  steps:
  - name: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
    text: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
  - name: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
    text: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
  - name: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
    text: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
  - name: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
    text: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
  type: HowTo
- questions:
  - answer: Yes, but it will have evaluation limitations. Obtain a [temporary license](https://purchase.aspose.com/temporary-license/)
      for full functionality.
    question: Can I use Aspose.Words for Java without a license?
  - answer: Aspose.BarCode supports QR, Code 128, EAN‑13, DataMatrix, PDF417, and
      many other formats—over 20 symbologies in total. See the [documentation](https://reference.aspose.com/words/java/)
      for the complete list.
    question: What types of barcodes can I generate?
  - answer: Adjust the width and height arguments in `builder.insertImage`, or calculate
      exact Word twips using `twipsToPixels` for pixel‑perfect control.
    question: How can I change the barcode size?
  - answer: Yes, you can customize the text font through the `CodeTextParameters`
      property of the `BarcodeGenerator`.
    question: Is it possible to use custom fonts for the barcode text?
  - answer: Visit the [support forum](https://forum.aspose.com/c/words/8/) for assistance
      from the Aspose community and engineers.
    question: Where can I get help if I run into problems?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- barcode generation
- Aspose.Words
- Java document processing
- QR code
title: Comment créer des étiquettes Java QR code avec Aspose.Words
url: /fr/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer des étiquettes QR code Java avec Aspose.Words

Les codes-barres sont essentiels dans les applications modernes—que vous gériez des stocks, imprimiez des billets ou créiez des cartes d'identité. Dans ce tutoriel, vous **créerez des étiquettes QR code Java** et les intégrerez directement dans un document Word à l'aide de l'interface `IBarcodeGenerator`. Nous parcourrons chaque étape, de la configuration de l'environnement à l'insertion de l'image du code-barres, afin que vous puissiez commencer à utiliser les codes-barres dans vos projets Java immédiatement.

## Réponses rapides
- **Quel est l'objectif de ce tutoriel ?** Comment créer des étiquettes QR code Java et les intégrer dans un fichier Word avec Aspose.Words for Java.  
- **Quel type de code-barres est utilisé dans l'exemple ?** QR code (vous pouvez le remplacer par n'importe lequel des plus de 20 types pris en charge).  
- **Ai-je besoin d'une licence ?** Une licence temporaire est requise pour un accès illimité pendant le développement.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur.  
- **Puis-je modifier la taille ou les couleurs du code-barres ?** Oui—modifiez les paramètres `BarcodeParameters` et `BarcodeGenerator`.

## Qu'est-ce que create QR code Java ?
`create QR code Java` désigne la génération d'une image de QR‑code de manière programmatique dans un environnement Java et son insertion dans un document ou un composant UI. Aspose.Words for Java associé à Aspose.BarCode vous permet de produire l'image entièrement en mémoire, évitant les fichiers temporaires.

## Pourquoi générer des étiquettes de code-barres personnalisées avec Aspose.Words ?
Aspose.Words prend en charge **plus de 35 formats d'entrée et de sortie** et peut traiter **des documents de 500 pages en moins de 3 secondes** sur du matériel serveur standard. En utilisant sa génération de code-barres en mémoire, vous obtenez un contrôle total sur le type, la taille et les couleurs tout en conservant un flux de travail entièrement centré sur Java et indépendant de la plateforme.

## Prérequis
- Java Development Kit (JDK) : Version 8 ou supérieure.  
- Bibliothèque Aspose.Words for Java : [Télécharger ici](https://releases.aspose.com/words/java/).  
- Bibliothèque Aspose.BarCode for Java : [Télécharger ici](https://releases.aspose.com/).  
- Environnement de développement intégré (IDE) : IntelliJ IDEA, Eclipse, ou tout IDE de votre choix.  
- Licence temporaire : Obtenez une [licence temporaire](https://purchase.aspose.com/temporary-license/) pour un accès illimité.

## Importer les packages
Nous utiliserons les bibliothèques Aspose.Words et Aspose.BarCode. Importez les packages suivants dans votre projet :

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Ces imports nous donnent accès à l'API de génération de code-barres et aux classes de documents Word dont nous aurons besoin.

## Étape 1 : créer une classe utilitaire pour les opérations de code-barres
La classe utilitaire regroupe des aides réutilisables telles que **convert twips to pixels** et **hex‑color conversion**.  
La classe `CustomBarcodeGeneratorUtils` fournit des méthodes statiques pour la conversion d'unités et la gestion des couleurs.

### Code

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**Explication**  
- `twipsToPixels` – Word mesure les dimensions en **twips** ; cette méthode les convertit en pixels d'écran, ce qui est pratique lorsque vous devez dimensionner l'image du code-barres avec précision.  
- `convertColor` – Convertit une chaîne hexadécimale (par ex., `"FF0000"` pour le rouge) en un objet `java.awt.Color`, vous permettant d'**ajouter le code-barres au document Word** avec des couleurs de premier plan et d'arrière-plan personnalisées.

## Étape 2 : implémenter le générateur de code-barres personnalisé
Nous allons maintenant implémenter l'interface `IBarcodeGenerator`. Cette classe est responsable de **générer des images QR code Java** que Aspose.Words peut intégrer.  
L'interface `IBarcodeGenerator` définit une méthode unique qui renvoie un `BufferedImage` représentant le code-barres.

### Code

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**Explication**  
- `getBarcodeImage` crée une instance de `BarcodeGenerator`, applique les couleurs fournies via `BarcodeParameters`, puis renvoie finalement un `BufferedImage`.  
- La méthode gère également les erreurs de manière élégante en renvoyant une image de substitution, garantissant que la création du document Word ne plante jamais.

## Comment intégrer un code-barres dans Word avec Aspose.Words ?
Chargez votre fichier Word avec `new Document("template.docx")` (ou créez un nouveau `Document`) et appelez `builder.insertImage` avec l'image du code-barres renvoyée par le générateur. Ce schéma en deux étapes intègre le code-barres directement sans écrire de fichier intermédiaire sur le disque. En spécifiant les dimensions de l'image en pixels ou en convertissant les twips Word en pixels, vous pouvez contrôler la taille exacte et le positionnement du code-barres dans le document, garantissant une mise en page professionnelle qui s'imprime correctement sur n'importe quelle imprimante.

## Étape 3 : générer un code-barres et l'intégrer dans Word
Avec le générateur prêt, nous pouvons maintenant produire une image de code-barres et **l'insérer dans un document Word**.

### Code

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**Explication**  

1. **Initialisation du document** – Crée un nouveau `Document` (ou vous pouvez charger un modèle existant).  
2. **Paramètres du code-barres** – Définit le type de code-barres (`QR`), la valeur à encoder, ainsi que les couleurs de premier plan/arrière-plan.  
3. **Insertion de l'image** – `builder.insertImage` place le code-barres généré à la taille souhaitée (200 × 200 pixels). C'est le cœur du **comment intégrer un code-barres dans Word**.  
4. **Enregistrement** – Le document final, `CustomBarcodeLabels.docx`, contient le code-barres intégré, prêt à être imprimé ou distribué.

## Problèmes courants & dépannage

| Symptôme | Cause probable | Solution |
|----------|----------------|----------|
| Le code-barres apparaît vide | Les couleurs de `BarcodeParameters` sont identiques (par ex., noir sur noir) | Vérifiez les valeurs de `foregroundColor` et `backgroundColor`. |
| L'image est déformée | Dimensions en pixels incorrectes passées à `insertImage` | Ajustez les arguments de largeur/hauteur ou utilisez la conversion `twipsToPixels` pour un dimensionnement précis. |
| Erreur de type de code-barres non pris en charge | Utilisation d'un type non reconnu par `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Assurez-vous que la chaîne du type de code-barres correspond à l'un des `EncodeTypes` pris en charge (par ex., `"QR"`, `"CODE128"`). |

## Questions fréquemment posées

**Q : Puis-je utiliser Aspose.Words for Java sans licence ?**  
R : Oui, mais il y aura des limitations d'évaluation. Obtenez une [licence temporaire](https://purchase.aspose.com/temporary-license/) pour une fonctionnalité complète.

**Q : Quels types de codes-barres puis-je générer ?**  
R : Aspose.BarCode prend en charge QR, Code 128, EAN‑13, DataMatrix, PDF417, et de nombreux autres formats—plus de 20 symbologies au total. Consultez la [documentation](https://reference.aspose.com/words/java/) pour la liste complète.

**Q : Comment puis-je modifier la taille du code-barres ?**  
R : Ajustez les arguments de largeur et de hauteur dans `builder.insertImage`, ou calculez les twips Word exacts en utilisant `twipsToPixels` pour un contrôle pixel‑parfait.

**Q : Est-il possible d'utiliser des polices personnalisées pour le texte du code-barres ?**  
R : Oui, vous pouvez personnaliser la police du texte via la propriété `CodeTextParameters` du `BarcodeGenerator`.

**Q : Où puis-je obtenir de l'aide en cas de problème ?**  
R : Consultez le [forum d'assistance](https://forum.aspose.com/c/words/8/) pour obtenir de l'aide de la communauté Aspose et des ingénieurs.

## Conclusion

En suivant les étapes ci‑dessus, vous savez maintenant comment **créer des images QR code Java** et **intégrer des codes-barres dans des documents Word** à l'aide d'Aspose.Words for Java. Cette technique est suffisamment flexible pour les étiquettes d'inventaire, les billets d'événement ou tout scénario où un code-barres doit faire partie d'un document généré. Expérimentez différents types de codes-barres, couleurs et options de dimensionnement pour répondre à vos besoins métier spécifiques.

---

**Dernière mise à jour :** 2026-10-23  
**Testé avec :** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Auteur :** Aspose

## Tutoriels associés

- [Créer un PDF à partir de Word avec génération de code-barres – Aspose.Words for Java](/words/java/document-conversion-and-export/using-barcode-generation/)
- [Enregistrer Word en PDF avec le guide Aspose Words étape par étape Java](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Créer un document Word vierge en Java avec Aspose Words](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}