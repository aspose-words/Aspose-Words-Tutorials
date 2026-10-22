---
category: general
date: 2026-10-16
description: Créez un document Word vierge avec Java et apprenez comment ajouter un
  bouton ActiveX, définir sa légende et ajuster ses dimensions à l'aide d'Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: fr
lastmod: 2026-10-16
og_description: Créez un document Word vierge avec Java, puis ajoutez un bouton ActiveX,
  définissez sa légende et spécifiez ses dimensions à l'aide d'Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Créer un document Word vierge et intégrer un bouton ActiveX – Guide Java
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Créer un document Word vierge et ajouter un bouton ActiveX (Java)
url: /fr/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge et ajouter un bouton ActiveX (Java)

Si vous devez **créer un document Word vierge** de manière programmatique, ce guide vous montre comment le faire avec Java et Aspose.Words. Vous apprendrez également comment **ajouter un bouton ActiveX**, **définir la légende du bouton**, et **définir les dimensions du bouton** afin que le contrôle apparaisse exactement comme vous l’attendez.

Ce tutoriel couvre :

* Initialiser un fichier Word vide avec Aspose.Words for Java.  
* Insérer un contrôle ActiveX `CommandButton`.  
* Configurer la légende et la taille du bouton.  
* Enregistrer le fichier final `.docx`.

Vous devez posséder des connaissances de base en Java et une version récente de la bibliothèque Aspose.Words for Java (le code fonctionne avec la version 23.9 et ultérieure). Aucune dépendance supplémentaire n’est requise.

![Create a blank Word document with an ActiveX button](/images/activex-button-example.png){: .align-center alt="Créer un document Word vierge avec un bouton ActiveX"}

## Créer un document Word vierge avec Aspose.Words

La première étape consiste à instancier un objet `Document` vide. Cet objet représente l’ensemble du fichier Word en mémoire et fournit la classe `DocumentBuilder` pour l’édition.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Pourquoi c’est important :**  
Créer un document vierge vous offre une toile propre, évitant tout style ou section caché(e) qui pourrait interférer avec les calculs de mise en page ultérieurs.

## Ajouter un bouton ActiveX au document

Aspose.Words vous permet d’intégrer des contrôles ActiveX hérités via la classe `Forms2OleControl`. Le code suivant insère un contrôle `CommandButton` à la position actuelle du curseur.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Astuce :** La valeur `setOleClassName` `"Forms.CommandButton.1"` est le ProgID du bouton standard Microsoft Forms. Utiliser un ProgID différent (par ex., `"Forms.CheckBox.1"`) insérerait un type de contrôle différent.

## Définir la légende du bouton

Une légende est le texte qui apparaît sur la face du bouton. Vous pouvez la modifier à tout moment avant d’enregistrer le document.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Pourquoi c’est nécessaire :** Les utilisateurs ne comprennent un contrôle que lorsque son objectif est clair. Définir une légende significative améliore l’utilisabilité, surtout lorsque le document est ouvert dans Word sous Windows.

## Définir les dimensions du bouton

La position et la taille sont spécifiées en points (1 point = 1/72 pouce). Ajustez les valeurs pour correspondre à votre mise en page.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Variations courantes :**

| Scénario | Ajustement |
|----------|------------|
| Bouton plus grand pour les écrans tactiles | Augmenter `setWidth` et `setHeight` proportionnellement |
| Bouton centré sur la page | Calculer `left = (pageWidth - width) / 2` |
| Plusieurs boutons dans une colonne | Incrémenter `setTop` pour chaque nouveau bouton |

## Enregistrer le document contenant le bouton ActiveX

Enfin, écrivez le document sur le disque. Le format `.docx` préserve le contrôle ActiveX pour les versions Windows de Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Résultat attendu :** L’ouverture de `ActiveXCommandButton.docx` dans Word (Windows) affiche une page blanche avec un bouton cliquable libellé **Click Me** positionné à 100 pt du bord gauche et à 200 pt du bord supérieur.

## Exemple complet et exécutable

Copiez la classe complète ci‑dessous dans votre IDE, ajoutez le JAR Aspose.Words for Java au classpath du projet, puis exécutez‑la.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

L’exécution du programme génère `ActiveXCommandButton.docx` dans le répertoire de travail. Ouvrez‑le avec Microsoft Word (Windows) pour vérifier que le bouton apparaît exactement comme configuré.

## Pourquoi cette approche est recommandée

* **Simplicité :** Seule l’API principale d’Aspose.Words est utilisée ; aucune interop COM ou bibliothèque supplémentaire n’est requise.  
* **Portabilité :** Le code s’exécute sur n’importe quelle plateforme supportant Java, bien que le contrôle ActiveX lui‑même ne fonctionne que sur les versions Windows de Word.  
* **Maintenabilité :** Toutes les propriétés (légende, dimensions, position) sont définies via des méthodes claires et auto‑documentées, rendant les ajustements futurs simples.

## Pièges courants et comment les éviter

| Piège | Solution |
|---------|------------|
| Le bouton n’apparaît pas dans Word sous macOS ou Linux | Les contrôles ActiveX sont réservés à Windows. Utilisez un autre contrôle (par ex., un contrôle de contenu) pour les documents multiplateformes. |
| La légende est tronquée | Assurez‑vous que la largeur du bouton est suffisante pour le texte ; augmentez `setWidth` ou utilisez une légende plus courte. |
| Le bouton chevauche d’autres contenus | Ajustez les valeurs `setTop` et `setLeft`, ou insérez un nouveau paragraphe avant le contrôle pour lui donner son propre espace. |

## Prochaines étapes

Maintenant que vous pouvez **créer un document Word vierge**, **ajouter un bouton ActiveX**, **définir la légende du bouton** et **définir les dimensions du bouton**, vous pourriez explorer :

* Ajouter du code de gestion d’événements via des macros VBA (nécessite l’intégration d’un module macro).  
* Insérer plusieurs contrôles dans une disposition tableau pour des documents de type formulaire.  
* Utiliser les API **FormField** d’Aspose.Words pour des solutions de formulaire multiplateformes.

Expérimentez avec différentes tailles, positions et légendes pour adapter à votre conception de document spécifique. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word Java – Ajouter une forme rectangle avec effet d’ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Ajouter un filigrane à un document avec Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}