---
date: 2026-02-19
description: Apprenez à créer un document avec filigrane en utilisant Aspose.Words
  pour Java et à ajouter un filigrane image en Java pour des documents à l’aspect
  professionnel.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Créer un document avec filigrane en utilisant Aspose.Words pour Java
url: /fr/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document avec filigrane en utilisant Aspose.Words pour Java

Dans ce tutoriel, vous **créerez un document avec filigrane** en utilisant l'API Aspose.Words pour Java. Les filigranes—qu'ils soient texte ou image—vous aident à marquer un fichier comme confidentiel, brouillon ou approuvé, et ils peuvent être appliqués programmatiquement à tout document Word. Nous parcourrons la configuration de la bibliothèque, l'ajout de filigranes texte et image, la personnalisation de leur apparence, et même leur suppression lorsqu'ils ne sont plus nécessaires.

## Réponses rapides
- **Que fait un filigrane ?** Il superpose du texte ou une image sur chaque page pour indiquer un statut ou une marque.  
- **Quelle bibliothèque ajoute des filigranes en Java ?** Aspose.Words pour Java fournit une prise en charge intégrée des filigranes.  
- **Puis-je ajouter un filigrane image ?** Oui—utilisez la classe `Shape` et l'approche `add image watermark java`.  
- **Le filigrane est‑il semi‑transparent ?** Vous pouvez contrôler l'opacité via `setSemitransparent` pour les filigranes texte.  
- **Ai‑je besoin d'une licence ?** Un essai gratuit fonctionne pour les tests ; une licence commerciale est requise pour la production.

## Qu'est‑ce qu'un filigrane et pourquoi l'utiliser ?

Un filigrane est une superposition légère—textuelle ou graphique—ajoutée à chaque page d'un document. Il est couramment utilisé pour indiquer la **confidentialité**, le **statut de brouillon**, ou la **marque** sans modifier le contenu sous‑jacent. Ajouter des filigranes programmatiquement garantit la cohérence sur de grands lots de fichiers et fait gagner du temps comparé à l'édition manuelle.

## Configuration d'Aspose.Words pour Java

Avant de commencer à ajouter des filigranes, assurez‑vous que la bibliothèque est prête dans votre projet :

1. Téléchargez Aspose.Words pour Java depuis [ici](https://releases.aspose.com/words/java/).  
2. Ajoutez le JAR téléchargé (ou la dépendance Maven/Gradle) au classpath de votre projet.  
3. Importez les classes requises dans votre fichier source Java :

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Maintenant que la bibliothèque est configurée, plongeons dans le code réel du filigrane.

## Comment ajouter un filigrane texte

Les filigranes texte sont idéaux pour marquer un document comme « CONFIDENTIEL » ou « BROUILLON ». Le fragment suivant montre une façon claire de **créer un document avec filigrane** en utilisant `TextWatermarkOptions`.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

### Personnaliser le filigrane texte
- **Famille et taille de police** – modifiez `setFontFamily` et `setFontSize`.  
- **Couleur** – utilisez n'importe quel `java.awt.Color`.  
- **Disposition** – choisissez `HORIZONTAL`, `DIAGONAL`, etc.  
- **Transparence** – activez `setSemitransparent(true)` pour un aspect plus léger.

## Comment ajouter un filigrane image (add image watermark java)

Les filigranes image sont parfaits pour les logos ou les graphiques personnalisés. Ci‑dessous se trouve l'exemple **add image watermark java** qui insère un PNG au centre de chaque page.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

### Conseils pour les filigranes image
- **Redimensionner** en utilisant `setWidth` / `setHeight` pour adapter à la page.  
- **Position** peut être centrée ou alignée à n'importe quelle marge en utilisant `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Transparence** peut être appliquée en ajustant le canal alpha de l'image avant le chargement.

## Comment supprimer les filigranes

Lorsqu'un document n'a plus besoin d'un filigrane, vous pouvez le supprimer programmatiquement. Le code ci‑dessous parcourt toutes les formes et supprime celles qui contiennent « Watermark » dans leur nom.

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Problèmes courants et dépannage

- **Filigrane manquant après l'enregistrement** – assurez‑vous d'appeler `doc.save()` après avoir défini le filigrane.  
- **Image non affichée** – vérifiez que le chemin de l'image est correct et que le fichier est dans un format supporté (PNG, JPEG, BMP).  
- **Transparence non appliquée** – `setSemitransparent(true)` ne fonctionne que pour les filigranes texte ; pour les images, modifiez le canal alpha du PNG.  
- **Sections multiples** – si votre document comporte plusieurs sections, ajoutez le filigrane au corps de chaque section ou utilisez `doc.getWatermark().setText(...)` qui s'applique globalement.

## Questions fréquemment posées

**Q : Comment puis‑je changer la police d'un filigrane texte ?**  
R : Modifiez la propriété `setFontFamily` dans `TextWatermarkOptions`, par exemple `options.setFontFamily("Times New Roman");`.

**Q : Puis‑je ajouter plusieurs filigranes à un même document ?**  
R : Oui. Créez plusieurs objets `Shape` (pour les images) ou appelez `doc.getWatermark().setText(...)` avec différentes options pour chaque filigrane.

**Q : Est‑il possible de faire pivoter un filigrane ?**  
R : Pour les filigranes image, définissez la rotation sur l'objet `Shape` avec `watermark.setRotation(angle)`. Pour les filigranes texte, utilisez la propriété `setLayout` (par ex., `WatermarkLayout.DIAGONAL`).

**Q : Comment rendre un filigrane semi‑transparent ?**  
R : Définissez `options.setSemitransparent(true)` dans `TextWatermarkOptions`. Pour les images, ajustez l'opacité de l'image avant le chargement.

**Q : Puis‑je ajouter des filigranes à des sections spécifiques d'un document ?**  
R : Oui. Parcourez `doc.getSections()` et ajoutez le filigrane uniquement aux sections souhaitées.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Dernière mise à jour :** 2026-02-19  
**Testé avec :** Aspose.Words for Java 24.12 (latest)  
**Auteur :** Aspose