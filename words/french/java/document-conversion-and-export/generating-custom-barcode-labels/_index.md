---
date: 2026-02-09
description: Générez des étiquettes de code‑barres personnalisées avec Aspose Barcode
  Java dans Aspose.Words for Java. Apprenez à intégrer un code‑barres dans des documents
  Word et à créer des exemples Java de codes QR.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Générer des étiquettes de code-barres personnalisées avec Aspose Barcode Java
url: /fr/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Générer des étiquettes de codes-barres personnalisées avec Aspose Barcode Java

## Introduction à la génération d'étiquettes de codes-barres personnalisées dans Aspose.Words pour Java

Les codes-barres sont essentiels dans les applications modernes, et **Aspose Barcode Java** simplifie leur création directement dans les documents Word. Que vous ayez besoin d'**intégrer un code-barres dans Word**, de générer un QR code pour une URL, ou de convertir des unités de mesure, ce tutoriel vous guide à travers tout ce qu'il faut savoir. Prêt à plonger ? C’est parti !

## Réponses rapides
- **Quelle bibliothèque crée des codes-barres en Java ?** Aspose Barcode Java associé à Aspose.Words pour Java.  
- **Quel type de code-barres est démontré ?** QR code (generate qr code java).  
- **Comment convertir les twips en pixels ?** Utilisez la méthode utilitaire `twipsToPixels` fournie.  
- **Puis-je ajouter un code-barres à un fichier Word existant ?** Oui – utilisez simplement la méthode `DocumentBuilder.insertImage`.  
- **Ai-je besoin d'une licence ?** Une licence temporaire supprime les limites d'évaluation.

## Qu'est-ce qu'Aspose Barcode Java ?
Aspose Barcode Java est une API puissante qui permet aux développeurs de générer une large gamme de codes-barres 1D et 2D (y compris les QR codes) de façon programmatique. Lorsqu'elle est combinée avec Aspose.Words pour Java, vous pouvez **intégrer un code-barres dans Word** sans quitter votre environnement Java.

## Pourquoi utiliser Aspose Barcode Java avec Aspose.Words ?
- **Contrôle total** sur l'apparence du code-barres (couleurs, taille, format).  
- **Intégration transparente** – l'image du code-barres peut être insérée directement dans un document Word.  
- **Multi‑plateforme** – fonctionne sur toute plateforme compatible Java.  
- **Extensible** – vous pouvez créer des classes utilitaires pour réutiliser la logique du code-barres dans plusieurs projets.

## Prérequis

Avant de commencer à coder, assurez‑vous de disposer de :

- Kit de développement Java (JDK) : version 8 ou supérieure.  
- Bibliothèque Aspose.Words pour Java : [Télécharger ici](https://releases.aspose.com/words/java/).  
- Bibliothèque Aspose.BarCode pour Java : [Télécharger ici](https://releases.aspose.com/).  
- Environnement de développement intégré (IDE) : IntelliJ IDEA, Eclipse ou tout IDE de votre choix.  
- Licence temporaire : obtenez une [licence temporaire](https://purchase.aspose.com/temporary-license/) pour un accès illimité.

## Importer les packages

Nous utiliserons les bibliothèques Aspose.Words et Aspose.BarCode. Importez les packages suivants dans votre projet :

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Ces imports nous permettent d'exploiter les fonctionnalités de génération de codes-barres et de les intégrer aux documents Word.

Décomposons cette tâche en étapes gérables.

## Étape 1 : Créer une classe utilitaire pour les opérations de code‑barres

Pour simplifier les opérations liées aux codes‑barres, nous créerons une classe utilitaire avec des méthodes d’aide pour les tâches courantes comme la conversion de couleur et **convertir les twips en pixels**.

### Code :

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

- `twipsToPixels` convertit l’unité de mesure utilisée par Word (twips) en pixels d’écran – une aide pratique lorsque vous avez besoin d’une taille précise.  
- `convertColor` traduit une chaîne de couleur hexadécimale (par ex., “FF0000”) en un objet Java `Color`, vous permettant de personnaliser le premier plan et l’arrière‑plan du code‑barres.

## Étape 2 : Implémenter le générateur de code‑barres personnalisé

Nous implémenterons l’interface `IBarcodeGenerator` afin qu’Aspose.Words puisse demander une image de code‑barres chaque fois qu’il rencontre un champ de code‑barres.

### Code :

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

- `getBarcodeImage` crée un `BarcodeGenerator` en utilisant le type **generate qr code java** que vous spécifiez (QR dans notre exemple).  
- Il applique les couleurs de premier plan et d’arrière‑plan via les méthodes utilitaires, puis renvoie l’image rendue.  
- L’image de secours garantit que le programme continue même si la création du code‑barres échoue.

## Étape 3 : Générer un code‑barres et l’ajouter à un document Word

Nous réunissons maintenant tous les éléments : créer un document, générer un code‑barres, et **comment ajouter un code‑barres** au fichier Word.

### Code :

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

1. **Initialisation du document** – crée un nouveau `Document` (ou vous pouvez charger un .docx existant).  
2. **Paramètres du code‑barres** – définissent le type (`QR`), la valeur et les couleurs, illustrant l’utilisation de **generate qr code java**.  
3. **Insertion de l’image** – `builder.insertImage` place le code‑barres à l’endroit souhaité, montrant concrètement **comment ajouter un code‑barres** à un fichier Word.  
4. **Enregistrement** – le document final (`CustomBarcodeLabels.docx`) contient le code‑barres intégré, prêt à être imprimé ou distribué.

## Problèmes courants et solutions

| Problème | Cause | Solution |
|----------|-------|----------|
| Le code‑barres apparaît vide | Chaîne de couleur invalide ou type de code‑barres non pris en charge | Vérifiez le format hexadécimal de la couleur et utilisez un type pris en charge (par ex., QR, Code128). |
| La taille de l'image est incorrecte | Conversion de pixels incorrecte | Utilisez `twipsToPixels` pour calculer les dimensions exactes en fonction de la mise en page de Word. |
| Exception de licence | Aucune licence Aspose valide | Appliquez une licence temporaire ou achetée avant d'exécuter le code. |

## Questions fréquentes

**Q : Puis-je utiliser Aspose.Words pour Java sans licence ?**  
R : Oui, mais vous rencontrerez des limitations d'évaluation. Obtenez une [licence temporaire](https://purchase.aspose.com/temporary-license/) pour une fonctionnalité complète.

**Q : Quels types de codes‑barres puis‑je générer ?**  
R : Aspose.BarCode prend en charge QR, Code 128, EAN‑13, et bien d’autres. Consultez la [documentation officielle](https://reference.aspose.com/words/java/) pour la liste complète.

**Q : Comment puis‑je modifier la taille du code‑barres ?**  
R : Ajustez les paramètres de largeur/hauteur dans `builder.insertImage` ou modifiez les propriétés `XDimension` et `BarHeight` de l’objet `BarcodeGenerator`.

**Q : Puis‑je utiliser des polices personnalisées pour la partie lisible du code‑barres ?**  
R : Absolument. Utilisez la propriété `CodeTextParameters` pour définir la famille, la taille et le style de la police.

**Q : Où puis‑je obtenir de l’aide pour Aspose.Words ?**  
R : Visitez le [forum de support](https://forum.aspose.com/c/words/8/) pour obtenir de l’assistance communautaire et le support officiel.

---

**Dernière mise à jour** : 2026-02-09  
**Testé avec** : Aspose.Words pour Java 24.12, Aspose.BarCode pour Java 24.12  
**Auteur** : Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}