---
category: general
date: 2026-09-27
description: Créer un docx contenant ActiveX en Java avec Aspose.Words. Apprenez à
  insérer un bouton de commande ActiveX étape par étape.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: fr
lastmod: 2026-09-27
og_description: Créez un fichier docx contenant ActiveX en Java avec Aspose.Words.
  Suivez ce guide pour insérer un bouton de commande ActiveX et enregistrer le document.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Créer un docx contenant ActiveX en Java – guide complet
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Comment créer un docx contenant ActiveX avec Java et Aspose.Words
url: /fr/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un docx contenant ActiveX avec Java et Aspose.Words

Si vous devez **créer un docx contenant ActiveX**, ce guide vous propose une solution complète. Vous apprendrez comment **insérer un bouton de commande ActiveX** dans un fichier Word à l’aide d’Aspose.Words pour Java, puis enregistrer le résultat au format .docx pouvant être ouvert dans Microsoft Word.

Générer un document Word de façon programmatique vous évite les éditions manuelles et garantit la cohérence des rapports, contrats ou modèles de formulaires. Les étapes ci‑dessous couvrent tout, de la configuration du projet à la gestion des problèmes courants, afin que vous puissiez intégrer la technique dans n’importe quelle application Java.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Java Development Kit (JDK) 8 ou supérieur installé.  
* Maven 3.6+ (ou tout autre outil de construction que vous préférez).  
* Un fichier de licence Aspose.Words pour Java (l’évaluation gratuite suffit pour les tests).  
* Microsoft Word installé sur la machine cible si vous souhaitez vérifier visuellement le contrôle ActiveX.

Ces éléments sont nécessaires parce qu’Aspose.Words fournit l’API qui crée le document, tandis que Word est requis pour rendre le contrôle ActiveX.

## Étape 1 : Configurer le projet Maven

Créez un nouveau projet Maven ou ajoutez la dépendance Aspose.Words à un `pom.xml` existant :

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Astuce :** Gardez la version d’Aspose.Words synchronisée avec les notes de version officielles pour bénéficier des corrections de bugs et des nouvelles fonctionnalités ActiveX.

## Étape 2 : Écrire le code Java qui crée le document

Créez une classe nommée `ActiveXDocxCreator`. Le code ci‑dessous comprend tous les imports requis, une méthode `main`, et des commentaires détaillés expliquant chaque opération.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Pourquoi chaque ligne est importante

* `Document` est le conteneur de tout le contenu Word. Créer une nouvelle instance vous donne une toile vierge.  
* `DocumentBuilder` fournit une API fluide pour insérer des éléments ; il suit automatiquement le point d’insertion.  
* `insertForms2OleControl()` crée un espace réservé générique pour un contrôle OLE. Aspose.Words le traite comme un conteneur ActiveX.  
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` indique à Word que l’espace réservé doit être rendu comme un CommandButton.  
* `setCaption("Click Me")` définit le texte affiché sur le bouton.  
* `setLeft` et `setTop` placent le bouton par rapport aux marges de la page. Ajustez ces valeurs selon votre mise en page.  
* `setWidth` et `setHeight` sont optionnels mais améliorent l’apparence du bouton, surtout lorsque la taille par défaut est trop petite.  
* `doc.save` écrit la structure en mémoire dans un fichier .docx physique que Word peut ouvrir.

## Étape 3 : Vérifier le document généré

Ouvrez `output/ActiveXCommandButton.docx` dans Microsoft Word :

1. Le document doit afficher une seule page avec un bouton libellé **Click Me** positionné près du coin supérieur gauche.  
2. Si le bouton n’apparaît pas, vérifiez que **les contrôles ActiveX sont activés** dans le Centre de gestion de la confidentialité de Word (Fichier → Options → Centre de gestion de la confidentialité → Paramètres du Centre de gestion de la confidentialité → Paramètres ActiveX).  
3. Le bouton ne fonctionne que sur les versions Windows de Word qui prennent en charge ActiveX. Sous macOS ou Word en ligne, le contrôle sera affiché comme une image statique.

## Étape 4 : Gestion des cas limites courants

| Situation | Raison | Action recommandée |
|-----------|--------|--------------------|
| Le bouton est absent après l’ouverture du fichier | Les paramètres de sécurité de Word bloquent ActiveX | Activez « Exécuter tous les contrôles sans restrictions » pour les emplacements de confiance. |
| Le .docx généré ne peut pas être ouvert | Version d’Aspose.Words incompatible | Mettez à jour vers la dernière version d’Aspose.Words ; les versions plus anciennes peuvent ne pas intégrer correctement les parties OLE requises. |
| Vous avez besoin que le bouton exécute une macro | ActiveX seul ne contient pas de code macro | Combinez le contrôle ActiveX avec une macro VBA qui gère l’événement `Click`. Utilisez la méthode `DocumentBuilder.insertOleObject` pour intégrer un modèle activé par macro. |
| La mise en page est décalée sur des tailles de page différentes | Les coordonnées sont en points absolus | Utilisez `builder.getPageSetup().setPageWidth` et `setPageHeight` pour standardiser la taille de la page avant de positionner le contrôle. |

## Étape 5 : Étendre la solution

Vous pouvez insérer d’autres contrôles ActiveX en modifiant l’énumération `ControlType` :

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words prend également en charge l’insertion de **boîtes de texte ActiveX**, **list boxes** et **combo boxes**. Les mêmes méthodes de positionnement (`setLeft`, `setTop`, `setWidth`, `setHeight`) s’appliquent.

Si vous devez placer plusieurs contrôles, appelez `builder.insertForms2OleControl()` à plusieurs reprises et ajustez les coordonnées de chaque contrôle en conséquence.

## Fichier source complet

Voici le fichier complet `ActiveXDocxCreator.java` prêt à être copié‑collé :

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

L’exécution de ce programme produit un **docx contenant ActiveX** que vous pouvez distribuer aux utilisateurs finaux ayant besoin de formulaires interactifs.

## Conclusion

Vous savez maintenant comment **créer un docx contenant ActiveX** avec Java et Aspose.Words, et comment **insérer un bouton de commande ActiveX** de façon programmatique. Le tutoriel a couvert la configuration du projet, le code complet, les étapes de vérification et les stratégies pour gérer les problèmes typiques.

À partir d’ici, vous pourriez explorer :

* Ajouter des macros VBA pour répondre au clic du bouton.  
* Intégrer d’autres contrôles ActiveX tels que des cases à cocher ou des listes déroulantes.  
* Automatiser la génération de formulaires multi‑pages avec des données dynamiques.

Expérimentez avec différentes coordonnées, tailles et types de contrôles pour adapter votre mise en page spécifique. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos projets.

- [Utilisation des objets OLE et des contrôles ActiveX dans Aspose.Words pour Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words pour Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Créer une forme rectangulaire dans Word avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}