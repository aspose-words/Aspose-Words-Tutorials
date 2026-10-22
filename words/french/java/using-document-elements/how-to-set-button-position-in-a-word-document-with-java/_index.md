---
category: general
date: 2026-09-24
description: Définissez la position d’un bouton dans un document Word à l’aide de
  Java et Aspose.Words. Apprenez comment insérer un bouton, ajouter un contrôle ActiveX
  et créer un document Word à la manière de Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: fr
lastmod: 2026-09-24
og_description: Définir la position du bouton dans un document Word avec Java. Ce
  guide montre comment insérer un bouton, ajouter un contrôle ActiveX et créer un
  document Word en Java avec Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Définir la position du bouton dans un document Word avec Java – guide complet
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Comment définir la position d’un bouton dans un document Word avec Java
url: /fr/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir la position d'un bouton dans un document Word avec Java

Si vous devez **set button position** à l'intérieur d'un fichier Word, ce guide vous montre une solution complète et exécutable. Que vous construisiez un modèle nécessitant une interaction utilisateur ou que vous automatisiez un formulaire, vous apprendrez exactement **how to insert button** en utilisant Aspose.Words for Java et contrôlerez son placement.

Le tutoriel couvre tout ce dont vous avez besoin pour **add ActiveX control** à un document Word, explique comment **add button to Word**, et démontre le processus complet pour **create Word document java**. Aucun référentiel externe n'est requis — copiez, exécutez et vérifiez le résultat.

## Prérequis

* Java 17 (ou tout environnement d'exécution Java 8+) installé.
* Maven ou Gradle pour gérer les dépendances.
* Une licence Aspose.Words for Java (l'essai gratuit fonctionne pour l'évaluation).
* Une compréhension de base de la syntaxe Java.

> **Conseil pro** : Conservez vos JAR Aspose.Words dans un dossier `libs/` et ajoutez‑les au classpath de votre projet pour éviter les conflits de version.

## Étape 1 : Configurer le projet Maven

Créez un projet Maven simple (ou utilisez Gradle) et ajoutez la dépendance Aspose.Words :

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

L'exécution de `mvn clean compile` télécharge la bibliothèque et prépare le chemin de construction.

## Étape 2 : Créer un nouveau document Word

La première opération consiste à **create Word document java** style. Vous instanciez un objet `Document` et un `DocumentBuilder` qui vous permet d'éditer le fichier.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

La classe `Document` représente le fichier .docx complet, tandis que `DocumentBuilder` fournit une API fluide pour insérer du contenu.

## Étape 3 : Comment insérer un bouton – ajouter un contrôle ActiveX

Aspose.Words expose la classe `Forms2OleControl` pour insérer des contrôles ActiveX hérités tels qu'un CommandButton. Cette étape montre la façon exacte de **how to insert button** dans le document.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

La méthode `insertForms2OleControl` renvoie une instance `Forms2OleControl` que vous pouvez configurer. C’est le cœur du processus **add ActiveX control**.

## Étape 4 : Définir la position du bouton

Now we actually **set button position**. The control’s `setLeft` and `setTop` methods accept values in points (1 pt = 1/72 in). To align the button with typical screen coordinates, you can convert pixels to points (1 px ≈ 0.75 pt). In the example we place the button 100 px from the left edge and 150 px from the top edge.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Comme la logique **set button position** est encapsulée ici, vous pouvez réutiliser ces lignes chaque fois que vous devez déplacer un contrôle. Ajustez les nombres selon les exigences de votre mise en page.

## Étape 5 : Définir la taille et la légende

Un bouton sans libellé est déroutant. Utilisez `setWidth`, `setHeight` et `setCaption` pour lui donner une apparence visible.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

La taille est également exprimée en points, nous convertissons donc depuis les pixels pour plus de cohérence.

## Étape 6 : Enregistrer le document – compléter le flux **create Word document java**

Enfin, persistez le fichier sur le disque. Le chemin peut être absolu ou relatif à la racine du projet.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

L'exécution du programme produit `CommandButtonDemo.docx` dans le dossier `output`. L'ouverture du fichier dans Microsoft Word montre un bouton cliquable positionné exactement où vous l'avez défini.

### Résultat attendu

* Un fichier `.docx` nommé **CommandButtonDemo.docx**.
* À l'intérieur du document, un **CommandButton** libellé « Click Me » apparaît à 100 px du bord gauche et à 150 px du bord supérieur.
* Le bouton répond aux clics lorsque le document est ouvert dans Word (il affichera un message ActiveX par défaut à moins que vous n'ajoutiez du code VBA personnalisé).

## Étape 7 : Variations courantes et cas limites

### Ajouter plusieurs boutons

If you need to **add button to Word** more than once, repeat steps 3‑5 with a new `Forms2OleControl` instance each time. Remember to adjust the `setTop` value so buttons don’t overlap.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Travailler sans licence

Aspose.Words adds a watermark when used without a license. For production code, purchase a license and apply it at the start of `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Compatibilité avec les versions Office plus anciennes

ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To create a legacy file, change the save format:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Code source complet (exécutable)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Enregistrez le fichier sous `src/main/java/CommandButtonDemo.java`, exécutez `mvn exec:java -Dexec.mainClass=CommandButtonDemo`, et ouvrez le document généré pour voir le résultat.

## Questions fréquemment posées

**Q : Cette solution fonctionne‑t‑elle avec OpenJDK ?**  
R : Oui. Aspose.Words est purement Java et fonctionne sur toute implémentation JDK 8+ , y compris OpenJDK.

**Q : Puis‑je modifier la police ou la couleur du bouton ?**  
R : L'apparence du bouton ActiveX est contrôlée par l'application hôte (Word). Vous pouvez attacher du code VBA pour modifier les propriétés à l'exécution, mais l'apparence statique est limitée au style par défaut.

**Q : Que faire si je dois placer le bouton à l'intérieur d'une cellule de tableau ?**  
R : Déplacez le curseur du `DocumentBuilder` dans la cellule avant d'appeler `insertForms2OleControl`. Le contrôle héritera de la mise en page de la cellule, et vous pourrez toujours utiliser `setLeft`/`setTop` pour un réglage fin.

## Conclusion

Vous savez maintenant comment **set button position** dans un document Word en Java, comment **how to insert button**, comment **add ActiveX control**, et comment **add button to Word** tout en suivant les meilleures pratiques pour les projets **create Word document java**. L'exemple complet montre l'ensemble du flux — de la configuration du projet à un fichier `.docx` enregistré contenant un CommandButton fonctionnel.

### Prochaines étapes

* Explorez d'autres valeurs `Forms2OleControl.ControlType` (par ex., `CHECKBOX`, `TEXTBOX`) pour créer des formulaires plus riches.
* Combinez le bouton avec des macros VBA pour gérer les clics personnalisés.
* Utilisez la fonctionnalité de publipostage d’Aspose.Words pour générer des documents personnalisés contenant déjà des contrôles interactifs.

Bon codage, et profitez de l'automatisation des documents Word avec Java !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Ajouter un champ de formulaire Combo Box à un document Word avec Aspose.Words pour .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Comment charger des documents Word avec Aspose.Words Java : guide complet](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}