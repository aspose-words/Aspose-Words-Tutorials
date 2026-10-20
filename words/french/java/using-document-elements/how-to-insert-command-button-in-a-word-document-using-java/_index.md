---
category: general
date: 2026-08-23
description: Apprenez comment insérer un bouton de commande dans un document Word
  en utilisant Java et Aspose.Words. Ce guide montre comment ajouter un contrôle de
  formulaire, définir le nom du bouton et intégrer un bouton ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: fr
lastmod: 2026-08-23
og_description: Insérer un bouton de commande dans un document Word à l'aide de Java.
  Suivez ce guide pour ajouter un contrôle de formulaire, définir le nom du bouton
  et intégrer un bouton ActiveX avec Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Insérer un bouton de commande dans Word avec Java – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Comment insérer un bouton de commande dans un document Word avec Java
url: /fr/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment insérer un bouton de commande dans un document Word avec Java

Si vous devez **insérer un bouton de commande** dans un fichier Word, ce tutoriel vous présente une solution complète avec Aspose.Words for Java. Vous verrez comment ajouter un contrôle de formulaire, configurer sa légende et définir le nom du bouton sans quitter votre IDE.

Le guide couvre tout ce dont vous avez besoin pour créer un `.docx` contenant un bouton ActiveX prêt à être utilisé dans Microsoft Word. Aucun outil supplémentaire n'est requis, et l'exemple fonctionne avec Java 8+.

## Ce que vous apprendrez

* Comment ajouter un contrôle de formulaire de type **CommandButton** à un document Word.  
* Les étapes exactes pour **set button name** et **add activex button**.  
* Comment enregistrer le document afin que le bouton apparaisse correctement lorsqu'il est ouvert dans Word.  

Vous devez disposer d'un environnement de développement Java de base ainsi qu'un projet Maven ou Gradle capable d'importer la bibliothèque Aspose.Words.

## Prérequis

| Requirement | Reason |
|-------------|--------|
| Java 8 ou version ultérieure | Aspose.Words for Java fonctionne avec Java 8+. |
| Outil de construction Maven ou Gradle | Simplifie l'ajout de la dépendance Aspose.Words. |
| Licence Aspose.Words for Java (ou version d'essai gratuite) | Nécessaire pour l'ensemble complet des fonctionnalités ; l'API fonctionne en mode évaluation. |
| Un IDE tel qu'IntelliJ IDEA ou Eclipse | Facilite l'édition et l'exécution de l'exemple. |

## Étape 1 : Ajouter Aspose.Words à votre projet

Si vous utilisez Maven, ajoutez la dépendance suivante à `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Pour Gradle, placez cette ligne dans `build.gradle` :

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Une fois la dépendance résolue, vous pouvez importer les classes de la bibliothèque dans votre fichier source Java.

## Étape 2 : Insérer le bouton de commande – le code principal

Créez une nouvelle classe Java nommée `InsertCommandButtonDemo`. Le code ci‑dessous effectue les quatre actions nécessaires pour **insert command button** :

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Pourquoi chaque ligne est importante

* **Document & DocumentBuilder** – Ils fournissent la représentation en mémoire d'un fichier Word et l'API permettant de modifier son contenu.  
* **insertForms2OleControl** – Cette méthode **adds form control** de type `COMMAND_BUTTON`. L'objet `Forms2OleControl` retourné représente le contrôle ActiveX.  
* **setName** – Assigne un identifiant programmatique (`btnSubmit`). Les macros Word ou VBA peuvent référencer ce nom ultérieurement.  
* **setCaption** – Définit le texte que l'utilisateur voit sur le bouton, répondant à la question « comment ajouter un bouton ».  
* **save** – Enregistre le `.docx` sur le disque, en conservant le bouton ActiveX intégré.  

L'exécution du programme crée `CommandButtonDemo.docx` dans le répertoire de travail. L'ouverture du fichier dans Microsoft Word affiche un bouton libellé **Submit** que vous pouvez cliquer (il affichera une boîte de dialogue ActiveX par défaut en mode évaluation).

## Étape 3 : Vérifier le bouton inséré dans Word

1. Ouvrez `CommandButtonDemo.docx` avec Microsoft Word (2016 ou version ultérieure).  
2. Le bouton **Submit** apparaît à l'endroit où le curseur était positionné lors de l'insertion.  
3. Faites un clic droit sur le bouton et choisissez **Properties** pour voir que le champ **Name** contient `btnSubmit`.  

Si le bouton n'apparaît pas, assurez‑vous que les **ActiveX controls** sont activés dans les paramètres du Centre de confiance de Word.

## Étape 4 : Personnaliser le bouton (facultatif)

Vous pouvez personnaliser davantage le bouton en ajustant sa taille, sa position ou en ajoutant une macro VBA. La classe `Forms2OleControl` expose des propriétés supplémentaires telles que `setWidth`, `setHeight` et `setLeft`. Voici un exemple qui agrandit le bouton :

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Ces lignes peuvent être placées après l'appel à `setCaption`. Elles illustrent la personnalisation **add activex button** au‑delà de l'insertion de base.

## Problèmes courants et comment les éviter

| Symptom | Cause | Fix |
|---------|-------|-----|
| Le bouton n'apparaît pas dans Word | Document enregistré avant que le contrôle ne soit ajouté | Assurez‑vous que `insertForms2OleControl` est appelé avant `doc.save`. |
| La légende du bouton est vide | `setCaption` non appelé ou appelé avec une chaîne vide | Fournissez une chaîne non vide, par ex., `"Submit"`. |
| VBA ne trouve pas le bouton | Incohérence de nom entre le code VBA et la valeur de `setName` | Conservez le même nom ; utilisez `setName("btnSubmit")` et référencez `btnSubmit` dans VBA. |
| Avertissement de sécurité à l'ouverture du fichier | La sécurité des macros de Word bloque les contrôles ActiveX | Modifiez Centre de confiance > Paramètres des macros, ou signez le document avec un certificat de confiance. |

## Exemple complet et exécutable

Voici le fichier source complet, prêt à être copié‑collé dans votre IDE. Il comprend les déclarations d'importation, la gestion des exceptions et un bloc de commentaires qui explique chaque étape majeure.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Résultat attendu :** Après l'exécution du programme, `CommandButtonDemo.docx` contient un seul bouton **Submit**. L'ouverture du fichier dans Word affiche le bouton exactement à l'endroit où le curseur `DocumentBuilder` était positionné.

## Prochaines étapes

* **Add more form controls** – Utilisez `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` ou `TEXT_BOX` pour créer des formulaires Word complets.  
* **Combine with mail merge** – Insérez des boutons dans un document de publipostage afin de créer des formulaires interactifs personnalisés.  
* **Attach VBA macros** – Intégrez programmatique du VBA qui réagit à l'événement `Click` du bouton pour une automatisation avancée.  

Ces sujets prolongent naturellement la technique **add form control** que vous venez de maîtriser.

---

### Récapitulatif

Vous savez maintenant comment **insert command button** dans un document Word avec Java, comment **add form control**, comment **set button name**, et comment personnaliser **add activex button**. L'exemple complet fonctionne immédiatement, et vous pouvez l'adapter à tout flux de génération de documents. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques présentées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insérer un champ de formulaire Combo Box dans un document Word](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Insérer un champ de formulaire Check Box dans un document Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}