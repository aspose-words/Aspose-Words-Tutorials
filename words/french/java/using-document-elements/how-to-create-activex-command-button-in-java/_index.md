---
category: general
date: 2026-10-07
description: Créer un bouton de commande ActiveX en Java et ajouter programmatiquement
  le bouton de commande aux documents Word. Apprenez comment définir les positions
  gauche et haut du bouton.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: fr
lastmod: 2026-10-07
og_description: Créez un bouton de commande ActiveX en Java pour intégrer des contrôles
  interactifs dans vos documents Word. Apprenez à ajouter de façon programmatique
  un bouton de commande, à définir sa position et à personnaliser son apparence.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Créer un bouton de commande ActiveX en Java – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Comment créer un bouton de commande ActiveX en Java
url: /fr/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un bouton de commande ActiveX en Java

Si vous devez **créer un bouton de commande ActiveX** dans un document Word en utilisant Java, ce guide vous montre exactement comment. Vous verrez un exemple complet et exécutable qui **ajoute programmétiquement un bouton de commande**, le positionne avec `setLeft` et `setTop`, et enregistre le résultat sous forme de fichier `.docx`.

Intégrer un bouton interactif vous permet de créer des formulaires, d'automatiser des flux de travail ou de collecter des saisies utilisateur directement dans un fichier Word. Les étapes ci‑dessous couvrent tout, de la configuration du projet à la vérification finale, afin que vous puissiez copier le code dans votre propre projet sans manquer aucun détail.

## Prérequis

- JDK 17 ou version plus récente installé  
- Maven 3.8+ (ou votre outil de construction préféré)  
- Aspose.Words for Java 23.9 ou ultérieur – la bibliothèque qui fournit `DocumentBuilder` et la prise en charge des contrôles OLE  
- Familiarité de base avec la syntaxe Java et les concepts orientés objet  

Si vous utilisez Maven, ajoutez la dépendance à votre `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Astuce :** Utilisez la dernière version d'Aspose.Words pour bénéficier des corrections de bugs et des nouvelles fonctionnalités OLE.

## Étape 1 : Créer un nouveau document vide et un DocumentBuilder

La première étape pour **créer un bouton de commande ActiveX** consiste à instancier un `Document` vierge et un `DocumentBuilder`. Le builder vous fournit une API fluide pour insérer du contenu, y compris des contrôles OLE.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` représente le fichier Word en mémoire, tandis que `DocumentBuilder` agit comme un curseur qui vous permet de placer les éléments précisément où vous le souhaitez.

## Étape 2 : Insérer un contrôle de bouton de commande OLE

Les contrôles ActiveX sont insérés en tant qu'objets OLE. Aspose.Words fournit la classe `Forms2OleControl` à cet effet.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

Lorsque vous appelez `insertForms2OleControl()`, Aspose crée automatiquement une forme de remplacement qui hébergera le bouton ActiveX.

## Étape 3 : Configurer les propriétés du bouton

Vous **ajoutez maintenant programmétiquement les détails du bouton de commande** tels que son ProgID, sa légende et sa taille. Le ProgID le plus courant pour un bouton de commande est `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Comment définir la position gauche/haut du bouton

Le positionnement du bouton est l'endroit où le mot‑clé secondaire **how to set button left top** devient pertinent. Les méthodes `setLeft` et `setTop` acceptent des valeurs mesurées en points (1 point = 1/72 pouce).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Ajustez ces nombres pour correspondre à votre mise en page. Par exemple, pour aligner le bouton avec une cellule de tableau, calculez les coordonnées de la cellule et transmettez‑les à `setLeft`/`setTop`.

## Étape 4 : Enregistrer le document

Enfin, écrivez le document sur le disque. Le fichier contiendra le bouton ActiveX prêt à être utilisé lorsqu'il sera ouvert dans Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

L'exécution de la méthode `main` produit `CommandButton.docx`. Ouvrez le fichier dans Word, activez le contenu si cela vous est demandé, et vous verrez un bouton cliquable intitulé **Click Me** positionné aux coordonnées que vous avez spécifiées.

![Créer un bouton de commande ActiveX en Java](/images/activex-button-screenshot.png){.center width=600 alt="Capture d'écran du bouton de commande ActiveX en Java montrant le bouton dans le document Word"}

## Variations courantes et cas limites

### Ajouter plusieurs boutons

Si vous avez besoin de plusieurs boutons, répétez **l’étape 2** et **l’étape 3** pour chaque contrôle. N'oubliez pas d'ajuster `setLeft` et `setTop` afin que les boutons ne se chevauchent pas.

### Modifier le comportement du bouton

Les boutons ActiveX peuvent exécuter des macros VBA lorsqu'ils sont cliqués. Pour associer une macro, définissez la propriété `setOnAction` avec le nom de la macro :

```java
commandButton.setOnAction("MyMacro");
```

Assurez‑vous que le document cible contient le module VBA correspondant ; sinon Word affichera une erreur.

### Notes de compatibilité

- Le bouton ne fonctionne que dans les versions de bureau de Word qui prennent en charge ActiveX (par ex., Word pour Windows). Il apparaîtra comme une image statique dans Word pour Mac ou les éditeurs en ligne.  
- Si vous ciblez un environnement mixte, envisagez d'utiliser un **contrôle de contenu** (`RichTextContentControl`) à la place d'un contrôle ActiveX.

## Code source complet à titre de référence

Voici l'exemple complet et autonome que vous pouvez copier dans un nouveau projet Maven et exécuter immédiatement.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Sortie attendue :** Après exécution, vous trouverez `CommandButton.docx` dans le répertoire de travail de votre projet. L'ouverture du fichier dans Microsoft Word affiche un bouton à l'emplacement spécifié avec la légende « Click Me ».

## Conclusion

Vous savez maintenant comment **créer un bouton de commande ActiveX** en Java, **ajouter programmétiquement un bouton de commande** à un document Word, et contrôler précisément sa mise en page à l'aide des méthodes **how to set button left top**. Cette technique ouvre la porte à des formulaires Word riches et interactifs qui peuvent déclencher des macros, lancer des applications externes ou collecter des saisies utilisateur directement dans le document.

### Prochaines étapes

- Explorez d'autres contrôles ActiveX tels que `Forms.TextBox.1` ou `Forms.CheckBox.1`.  
- Combinez plusieurs contrôles avec un module VBA pour implémenter des formulaires complets.  
- Remplacez ActiveX par des contrôles de contenu si vous avez besoin d'une compatibilité multiplateforme.  

N'hésitez pas à expérimenter avec la taille, la légende et le positionnement pour correspondre à votre conception UI. Si vous rencontrez des problèmes, revérifiez que la version d'Aspose.Words que vous utilisez prend en charge les contrôles OLE, et assurez‑vous que les paramètres de sécurité de Word autorisent l'exécution d'ActiveX. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Intégration d'objets OLE et de contrôles ActiveX dans les documents Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Créer une forme rectangulaire dans Word avec Java – Guide complet](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}