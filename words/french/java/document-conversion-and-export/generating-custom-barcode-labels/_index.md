---
date: 2025-12-10
description: Apprenez à générer des étiquettes de codes-barres personnalisées avec
  Aspose.Words pour Java. Ce guide étape par étape vous montre comment intégrer des
  codes-barres dans des documents Word.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Générer des étiquettes de code-barres personnalisées dans Aspose.Words pour
  Java
url: /fr/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Générer des étiquettes de code‑barres personnalisées dans Aspose.Words pour Java

## Introduction à la génération de code‑barres personnalisé dans Aspose.Words pour Java

Les codes‑barres sont essentiels dans les applications modernes—que vous gériez des stocks, imprimiez des billets ou créiez des cartes d’identité. Dans ce tutoriel, vous **générerez des étiquettes de code‑barres personnalisées** et les intégrerez directement dans un document Word à l’aide de l’interface `IBarcodeGenerator`. Nous parcourrons chaque étape, de la configuration de l’environnement à l’insertion de l’image du code‑barres, afin que vous puissiez commencer à utiliser les codes‑barres dans vos projets Java dès maintenant.

## Réponses rapides
- **Que vous apprend ce tutoriel ?** Comment générer des étiquettes de code‑barres personnalisées et les intégrer dans un fichier Word avec Aspose.Words pour Java.  
- **Quel type de code‑barres est utilisé dans l’exemple ?** QR code (vous pouvez le remplacer par tout type pris en charge).  
- **Ai‑je besoin d’une licence ?** Une licence temporaire est requise pour un accès illimité pendant le développement.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur.  
- **Puis‑je modifier la taille ou les couleurs du code‑barres ?** Oui—modifiez les paramètres `BarcodeParameters` et `BarcodeGenerator`.

## Prérequis

Avant de commencer à coder, assurez‑vous de disposer de :

- Java Development Kit (JDK) : version 8 ou supérieure.  
- Bibliothèque Aspose.Words pour Java : [Download here](https://releases.aspose.com/words/java/).  
- Bibliothèque Aspose.BarCode pour Java : [Download here](https://releases.aspose.com/).  
- Environnement de développement intégré (IDE) : IntelliJ IDEA, Eclipse ou tout autre IDE de votre choix.  
- Licence temporaire : obtenez une [temporary license](https://purchase.aspose.com/temporary-license/) pour un accès illimité.

## Importer les packages

Nous utiliserons les bibliothèques Aspose.Words et Aspose.BarCode. Importez les packages suivants dans votre projet :

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Ces imports nous donnent accès à l’API de génération de code‑barres ainsi qu’aux classes de documents Word dont nous aurons besoin.

## Étape 1 : Créer une classe utilitaire pour les opérations de code‑barres

Pour garder le code principal propre, nous encapsulerons les aides communes—telles que **convertir les twips en pixels** et **la conversion hex‑color**—dans une classe utilitaire.

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

- `twipsToPixels` – Word mesure les dimensions en **twips** ; cette méthode les convertit en pixels d’écran, ce qui est pratique lorsque vous devez dimensionner précisément l’image du code‑barres.  
- `convertColor` – Transforme une chaîne hexadécimale (par ex. `"FF0000"` pour le rouge) en objet `java.awt.Color`, vous permettant de **how to insert barcode** avec des couleurs de premier plan et d’arrière‑plan personnalisées.

## Étape 2 : Implémenter le générateur de code‑barres personnalisé

Nous allons maintenant implémenter l’interface `IBarcodeGenerator`. Cette classe sera responsable de **generate qr code java**‑style images que Aspose.Words pourra intégrer.

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

- `getBarcodeImage` crée une instance de `BarcodeGenerator`, applique les couleurs fournies via `BarcodeParameters`, puis renvoie un `BufferedImage`.  
- La méthode gère également les erreurs en renvoyant une image de substitution, garantissant que la création du document Word ne plante jamais.

## Étape 3 : Générer un code‑barres et **embed barcode in Word**

Avec le générateur prêt, nous pouvons maintenant produire une image de code‑barres et **insert it into a Word document**.

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
2. **Paramètres du code‑barres** – Définit le type de code‑barres (`QR`), la valeur à encoder, ainsi que les couleurs de premier plan et d’arrière‑plan.  
3. **Insertion de l’image** – `builder.insertImage` place le code‑barres généré à la taille souhaitée (200 × 200 pixels). C’est le cœur de **how to insert barcode** dans un fichier Word.  
4. **Enregistrement** – Le document final, `CustomBarcodeLabels.docx`, contient le code‑barres intégré, prêt à être imprimé ou distribué.

## Pourquoi générer des étiquettes de code‑barres personnalisées avec Aspose.Words ?

- **Contrôle total** sur l’apparence du code‑barres (type, taille, couleurs).  
- **Intégration transparente** – aucune nécessité de fichiers image intermédiaires ; le code‑barres est généré en mémoire et inséré directement.  
- **Multiplateforme** – fonctionne sur tout OS supportant Java, ce qui le rend idéal pour la génération de documents côté serveur.  
- **Scalable** – vous pouvez parcourir une source de données pour créer des centaines d’étiquettes personnalisées en une seule exécution.

## Problèmes courants & dépannage

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Le code‑barres apparaît vide | Les couleurs `BarcodeParameters` sont identiques (ex. noir sur noir) | Vérifiez les valeurs de `foregroundColor` et `backgroundColor`. |
| L’image est déformée | Dimensions en pixels incorrectes passées à `insertImage` | Ajustez les arguments de largeur/hauteur ou utilisez la conversion `twipsToPixels` pour un dimensionnement précis. |
| Erreur de type de code‑barres non pris en charge | Utilisation d’un type non reconnu par `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Assurez‑vous que la chaîne du type de code‑barres correspond à l’un des `EncodeTypes` supportés (ex. `"QR"`, `"CODE128"`). |

## Questions fréquentes

**Q : Puis‑je utiliser Aspose.Words pour Java sans licence ?**  
R : Oui, mais certaines limitations s’appliqueront. Obtenez une [temporary license](https://purchase.aspose.com/temporary-license/) pour une fonctionnalité complète.

**Q : Quels types de code‑barres puis‑je générer ?**  
R : Aspose.BarCode prend en charge QR, Code 128, EAN‑13 et de nombreux autres formats. Consultez la [documentation](https://reference.aspose.com/words/java/) pour la liste complète.

**Q : Comment modifier la taille du code‑barres ?**  
R : Ajustez les arguments de largeur et de hauteur dans `builder.insertImage`, ou utilisez `twipsToPixels` pour convertir les unités de mesure Word en pixels.

**Q : Est‑il possible d’utiliser des polices personnalisées pour le texte du code‑barres ?**  
R : Oui, vous pouvez personnaliser la police du texte via la propriété `CodeTextParameters` du `BarcodeGenerator`.

**Q : Où puis‑je obtenir de l’aide en cas de problème ?**  
R : Visitez le [support forum](https://forum.aspose.com/c/words/8/) pour obtenir de l’assistance de la communauté Aspose et des ingénieurs.

## Conclusion

En suivant les étapes ci‑dessus, vous savez maintenant comment **générer des images de code‑barres personnalisées** et **embed barcode in Word** documents avec Aspose.Words pour Java. Cette technique est suffisamment flexible pour les étiquettes d’inventaire, les billets d’événement ou tout scénario où un code‑barres doit faire partie d’un document généré. Expérimentez avec différents types de code‑barres et options de style pour répondre à vos besoins métier spécifiques.

---

**Dernière mise à jour :** 2025-12-10  
**Testé avec :** Aspose.Words pour Java 24.12, Aspose.BarCode pour Java 24.12  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}