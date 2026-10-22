---
category: general
date: 2026-07-20
description: Comment ajouter un bouton à un document Word en utilisant Aspose.Words.
  Apprenez à insérer un bouton Forms2OleControl avec DocumentBuilder en quelques minutes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: fr
lastmod: 2026-07-20
og_description: Comment ajouter un bouton à un document Word avec Aspose.Words. Suivez
  ce guide pratique pour intégrer un bouton CommandButton Forms2OleControl en Java.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Comment ajouter un bouton à un document Word – Tutoriel complet Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Comment ajouter un bouton à un document Word – Guide étape par étape
url: /fr/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter un bouton à un document Word – Tutoriel complet Aspose.Words

Vous vous êtes déjà demandé **comment ajouter un bouton à un document Word** sans ouvrir l'interface utilisateur et cliquer partout ? Vous n'êtes pas le seul. De nombreux développeurs doivent intégrer de façon programmatique des contrôles interactifs — pensez à un bouton « Submit » dans un modèle qui sera ensuite rempli par un utilisateur final. Bonne nouvelle ? Avec Aspose.Words for Java, vous pouvez le faire en quelques lignes.

Dans ce tutoriel, nous parcourrons les étapes exactes pour insérer un `Forms2OleControl` de type **CommandButton** à l'aide du `DocumentBuilder`. À la fin, vous disposerez d'un fichier `.docx` prêt à l'emploi affichant un bouton cliquable libellé « Click Me ». Pas de mystère, juste du code clair et la logique derrière chaque ligne.

## Ce que vous apprendrez

- Comment créer un nouveau document Word à partir de zéro.  
- Comment utiliser **DocumentBuilder** pour placer un **Forms2OleControl**.  
- Pourquoi vous devez définir la légende du bouton et sa taille comme nous le faisons.  
- Comment enregistrer et vérifier le résultat.  
- Pièges courants (par ex., bibliothèques manquantes, types de contrôles non pris en charge) et comment les éviter.  

**Prérequis** – Vous avez besoin de Java 8+ (ou plus récent) et de la bibliothèque Aspose.Words for Java (version 23.12 ou ultérieure). Un IDE tel qu'IntelliJ IDEA ou Eclipse facilitera les choses, mais tout éditeur de texte fonctionne.

---

## Étape 1 : Configurez votre projet et importez les dépendances

Avant que le code ne s’exécute, Maven (ou Gradle) doit savoir où récupérer Aspose.Words. Ajoutez cet extrait à votre `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Si vous préférez Gradle, l’équivalent est :

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Astuce pro :** Utilisez la dernière version ; les versions plus anciennes peuvent ne pas contenir l’API `Forms2OleControl`.

Une fois la dépendance résolue, vous êtes prêt à écrire du code Java.

---

## Étape 2 : Créez un nouveau document et obtenez un DocumentBuilder

La classe `Document` représente l’ensemble du package `.docx`, tandis que `DocumentBuilder` est le pinceau que vous utilisez pour y peindre du contenu. Pensez à `DocumentBuilder` comme le « curseur » qui sait où placer le prochain élément.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Pourquoi c’est important :** Initialiser un `Document` vierge vous donne une toile propre. Le builder pointe automatiquement sur le premier paragraphe, vous n’avez donc pas à gérer manuellement les sections ou les pages.

---

## Étape 3 : Insérez un Forms2OleControl de type CommandButton

Voici la star du spectacle : `insertForms2OleControl`. Cette méthode crée un contrôle OLE (Object Linking and Embedding) que Word traite comme un élément de formulaire. Nous passerons trois arguments :

1. `Forms2OleControlType.COMMANDBUTTON` – indique à Word que nous voulons un bouton.  
2. `100` – largeur en points (≈1,39 pouces).  
3. `30` – hauteur en points (≈0,42 pouces).  

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**Comment ça fonctionne :** En coulisses, Aspose.Words génère le XML approprié dans la partie `word/document.xml`, en référant l’objet OLE. Les dimensions que vous fournissez sont respectées par le moteur de mise en page de Word, de sorte que le bouton apparaît exactement à l’endroit où le curseur du builder est positionné.

---

## Étape 4 : Définissez la légende (texte) du bouton

Un bouton sans libellé est déroutant — imaginez un bouton d’ascenseur muet. La méthode `setCaption` définit le texte visible :

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Vous pouvez changer la légende à votre guise : « Submit », « Approve », ou même une chaîne localisée. La légende est stockée dans les propriétés de l’objet OLE, ainsi Word l’affichera nativement.

---

## Étape 5 : Enregistrez le document et vérifiez le résultat

Enfin, écrivez le fichier sur le disque. Choisissez un dossier où vous avez les droits d’écriture ; sinon vous obtiendrez une `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Ouvrez `button-demo.docx` dans Microsoft Word. Vous devriez voir un bouton libellé **Click Me** placé en haut du document. Cliquer dessus dans Word déclenchera le comportement OLE par défaut (généralement un message d’espace réservé, à moins que vous ne liiez une macro).

---

## Cas limites courants et comment les gérer

| Situation | Pourquoi cela se produit | Solution |
|-----------|--------------------------|----------|
| **Type `Forms2OleControl` manquant** | Les versions plus anciennes d'Aspose.Words n'exposaient pas cet enum. | Mettez à jour vers la version 23.12+ ou ultérieure. |
| **Le bouton apparaît comme une image** | Les paramètres de sécurité de Word bloquent les contrôles OLE. | Activez « Faire confiance à l'accès au modèle d'objet du projet VBA » dans le Centre de confiance, ou utilisez un fichier macro‑activé `.docm`. |
| **Taille incorrecte** | Confusion entre points et pixels. | Rappelez‑vous que 1 point = 1/72 pouce. Ajustez les nombres en conséquence. |
| **Enregistrement génère `FileNotFoundException`** | Le chemin n'existe pas. | Assurez‑vous que le répertoire (`output/`) est créé avant `doc.save`. Utilisez `new File("output").mkdirs();`. |

---

## Extension de l’exemple : ajouter plusieurs boutons ou d’autres contrôles

Si vous avez besoin de plusieurs boutons, déplacez simplement le curseur du builder avec `builder.moveTo` ou `builder.writeln()` avant d’appeler à nouveau `insertForms2OleControl`.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Vous pouvez également insérer une **CheckBox**, **ComboBox** ou **ListBox** en remplaçant `Forms2OleControlType.COMMANDBUTTON` par la valeur d’enum appropriée (`CHECKBOX`, `COMBOBOX`, etc.). Les mêmes paramètres de largeur/hauteur s’appliquent.

---

## Comment cela s’intègre dans des flux de travail d’automatisation Word plus larges

- **Génération de modèles :** Créez un modèle de contrat incluant un bouton « Approve » pour la validation en aval.  
- **Reporting :** Générez un rapport quotidien avec un bouton « Refresh Data » qui déclenche une macro.  
- **Distribution de formulaires :** Expédiez un questionnaire avec des contrôles interactifs pré‑remplis.  

Tous ces scénarios bénéficient de l’**automatisation Word** démontrée ici. En intégrant les contrôles par programme, vous éliminez les éditions manuelles et réduisez les erreurs humaines.

---

## Code source complet (prêt à copier‑coller)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Résultat attendu :** Lorsque vous ouvrez `output/button-demo.docx` dans Microsoft Word, vous verrez deux boutons — « Click Me » et « Submit » — empilés verticalement en haut du fichier.

---

## Conclusion

Nous avons répondu à **comment ajouter un bouton à un document Word** en utilisant Aspose.Words for Java, étape par étape. En partant d’un `Document` vierge, nous avons exploité **DocumentBuilder** pour insérer un `Forms2OleControl` de type **CommandButton**, défini une légende conviviale et enregistré le résultat. L’approche s’étend à plusieurs contrôles et s’intègre proprement aux pipelines d’**automatisation Word** plus larges.

Prêt pour le prochain défi ? Essayez de remplacer le bouton par une **CheckBox**, ou liez une macro pour réagir lorsque l’utilisateur clique sur le bouton dans un fichier `.docm`. Le même schéma s’applique — il suffit de changer l’enum et d’ajuster la légende.

Si vous rencontrez des difficultés, revérifiez la version de votre bibliothèque et les permissions du dossier de sortie. N’hésitez pas à laisser un commentaire ci‑dessous avec vos questions ou à partager votre propre cas d’utilisation. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words pour Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insérer une image en ligne dans un document Word avec Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Créer une forme groupée dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}