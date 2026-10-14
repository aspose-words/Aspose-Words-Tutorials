---
category: general
date: 2026-10-13
description: Créer un bouton de champ de formulaire dans Word avec Aspose.Words pour
  Java. Apprenez à insérer des champs de formulaire Word de type bouton de commande
  et à définir la légende du bouton de commande en quelques étapes simples.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: fr
lastmod: 2026-10-13
og_description: Créer un bouton de champ de formulaire dans Word avec Aspose.Words
  pour Java. Ce tutoriel montre comment insérer des champs de bouton de commande Word
  et définir rapidement la légende du bouton de commande.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Créer un bouton de champ de formulaire dans Word – Guide Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Créer un bouton de champ de formulaire dans Word avec Aspose.Words Java
url: /fr/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un bouton de champ de formulaire dans Word avec Aspose.Words Java

Si vous devez **create form field button** dans un document Word, ce guide vous accompagne à travers le processus complet en utilisant Aspose.Words for Java. Que vous créiez un modèle de formulaire à remplir ou ajoutiez des contrôles interactifs à un rapport, vous apprendrez comment **insert command button word** form fields et **set command button caption** avec un minimum de code.

Le tutoriel couvre tout, de la configuration de Maven à un exemple entièrement exécutable, afin que vous puissiez copier‑coller le code, l’exécuter, et voir un fichier `.docx` contenant un bouton cliquable prêt à être personnalisé davantage.

## Prérequis

- Java 17 (ou plus récent) installé et configuré sur votre machine.
- Maven 3.6+ pour la gestion des dépendances.
- Un IDE ou éditeur de texte de votre choix (par ex., IntelliJ IDEA, VS Code).
- Une licence valide d’Aspose.Words for Java (l’essai gratuit fonctionne pour l’évaluation).

## Étape 1 : Ajouter Aspose.Words à votre projet Maven

Créez un `pom.xml` (ou modifiez celui existant) et incluez la dépendance Aspose.Words :

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Astuce :** Gardez le numéro de version à jour. Les nouvelles versions ajoutent la prise en charge des dernières fonctionnalités Word et améliorent les performances.

## Étape 2 : Initialiser un document vierge et un `DocumentBuilder`

La classe `DocumentBuilder` fournit une API fluide pour éditer un document Word. Dans cette étape, nous créons un `Document` vide et y attachons un builder.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Créer le document constitue la base pour les objets **create form field button** plus tard dans le tutoriel.

## Étape 3 : Insérer un champ de bouton de commande

Aspose.Words expose la classe `Forms2OleControl` pour les contrôles de formulaire OLE. Pour **insert command button word** form fields, appelez `insertForms2OleControl` avec la valeur d’énumération `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

La méthode renvoie une instance de `Forms2OleControl` que nous pouvons configurer avant l’enregistrement.

## Étape 4 : Définir la taille et la position du bouton

Un bouton de commande nécessite des dimensions et un placement explicites sur la page. Ajustez la largeur, la hauteur et les coordonnées selon votre mise en page.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Un réglage fin de ces valeurs garantit que le bouton apparaît exactement où vous le souhaitez dans le document final.

## Étape 5 : **Set command button caption**

Le texte visible sur le bouton est contrôlé par la méthode `setCaption`. C’est ici que nous **set command button caption** pour guider l’utilisateur.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Vous pouvez remplacer `"Click Me"` par n’importe quel libellé correspondant à l’intention de votre formulaire, comme `"Submit"` ou `"Approve"`.

## Étape 6 : Enregistrer le document

Enfin, écrivez le document sur le disque. Le fichier résultant contient le bouton interactif et peut être ouvert dans Microsoft Word ou LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

L’exécution du programme produit `CommandButtonDemo.docx`. L’ouvrir dans Word affiche un bouton libellé **Click Me** positionné à 50 pts du bord gauche et 100 pts du bord supérieur de la page.

### Résultat attendu

- Un fichier `.docx` nommé `CommandButtonDemo.docx`.
- Le document contient une page unique avec un champ de bouton de commande.
- Le bouton affiche la légende que vous avez définie (par ex., **Click Me**).

## Variantes courantes et cas limites

| Situation | Comment adapter |
|-----------|-----------------|
| **Multiple buttons** | Appelez `insertForms2OleControl` à plusieurs reprises, en ajustant `setLeft`/`setTop` pour chaque nouveau bouton. |
| **Different caption per button** | Utilisez `setCaption` avec une chaîne unique après chaque insertion. |
| **Button inside a table cell** | Déplacez le curseur dans la cellule souhaitée avec `builder.moveTo(cell.getFirstParagraph())` avant d’insérer le contrôle. |
| **Legacy Word formats (.doc)** | Enregistrez avec `doc.save("Demo.doc", SaveFormat.DOC);` – le bouton de commande est conservé. |
| **Read‑only forms** | Après insertion, définissez `commandButton.setEnabled(false);` pour empêcher l’interaction de l’utilisateur. |

## Conseils pour une implémentation robuste

- **Validate dimensions** : Des largeurs extrêmement grandes peuvent faire déborder le bouton hors de la marge de la page.
- **License enforcement** : Sans licence valide, Aspose.Words ajoute un filigrane au document généré. Appliquez votre licence tôt avec `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Testing** : Ouvrez le fichier généré dans Word et activez le **Design Mode** (Developer → Design Mode) pour voir les propriétés du bouton.

## Récapitulatif du code source complet

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Copiez le code dans un fichier nommé `InsertCommandButtonDemo.java`, compilez avec Maven (`mvn compile`), et exécutez (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). Le document généré apparaîtra dans le dossier racine de votre projet.

## Conclusion

Vous savez maintenant comment **create form field button** dans Word en utilisant Aspose.Words for Java, comment **insert command button word** form fields, et comment **set command button caption** de manière programmatique. Cet exemple complet vous fournit une base solide pour créer des documents Word plus riches et interactifs—que vous ayez besoin d’un seul bouton de soumission ou d’une suite complète de contrôles de formulaire.

### Et après ?

- Explorez d’autres contrôles de formulaire tels que les cases à cocher (`Forms2OleControlType.CHECKBOX`) et les zones de texte (`Forms2OleControlType.TEXTBOX`).
- Combinez les champs de formulaire avec la fusion et publipostage pour générer des questionnaires personnalisés.
- Utilisez l’API `FormField` d’Aspose.Words pour lire les données saisies par l’utilisateur après que le document a été rempli.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Ajouter un champ de formulaire Combo Box à un document Word avec Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Ajouter un champ de formulaire Check Box à un document Word avec Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}