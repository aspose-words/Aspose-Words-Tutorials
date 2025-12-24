---
date: 2025-12-24
description: Apprenez à créer un fichier texte à partir de documents Word en utilisant
  Aspose.Words pour Java. Ce guide montre comment convertir Word en txt, utiliser
  l'indentation par tabulation et enregistrer le document Word au format txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Comment créer un fichier texte brut avec Aspose.Words pour Java
url: /fr/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un fichier texte brut avec Aspose.Words pour Java

## Introduction à l'enregistrement de documents en fichiers texte avec Aspose.Words pour Java

Dans ce tutoriel, vous apprendrez **comment créer un fichier texte brut** à partir d'un document Word en utilisant la bibliothèque Aspose.Words pour Java. Que vous ayez besoin de **convertir word en txt**, d'automatiser la génération de rapports, ou simplement d'extraire du texte brut pour un traitement ultérieur, ce guide vous accompagne tout au long du processus — depuis la création du document jusqu'au réglage fin des options d'enregistrement telles que **utiliser l'indentation par tabulation** ou ajouter des marques bidi. Commençons !

## Réponses rapides
- **Quelle est la classe principale pour créer un document ?** `Document` d'Aspose.Words.  
- **Quelle option ajoute des marques bidi pour les langues de droite à gauche ?** `TxtSaveOptions.setAddBidiMarks(true)`.  
- **Comment puis‑je indenter les éléments de liste avec des tabulations ?** Définissez `ListIndentation.Character` à `'\t'`.  
- **Ai‑je besoin d'une licence pour le développement ?** Un essai gratuit suffit pour les tests ; une licence est requise en production.  
- **Puis‑je enregistrer le fichier avec un nom et un chemin personnalisés ?** Oui — transmettez le chemin complet à `doc.save()`.

## Prérequis

Avant de commencer, assurez‑vous que les prérequis suivants sont en place :

- Java Development Kit (JDK) installé sur votre système.  
- Bibliothèque Aspose.Words pour Java intégrée à votre projet. Vous pouvez la télécharger depuis [ici](https://releases.aspose.com/words/java/).  
- Connaissances de base en programmation Java.

## Étape 1 : Créer un document

Pour **enregistrer word en txt**, nous avons d'abord besoin d'une instance `Document`. Vous trouverez ci‑dessous un extrait Java simple qui crée un document et écrit quelques lignes de texte multilingue :

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Dans ce code, nous créons un nouveau document, ajoutons du texte en anglais, hébreu et arabe, et activons le formatage de droite à gauche pour le paragraphe hébreu.

## Étape 2 : Définir les options d’enregistrement du texte

Ensuite, nous configurons la façon dont le document sera enregistré en fichier texte brut. Aspose.Words fournit la classe `TxtSaveOptions`, qui vous permet de contrôler tout, des marques bidi à l'indentation des listes.

### Exemple 1 : Ajout de marques bidi (comment enregistrer txt avec un support RTL correct)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Définir `AddBidiMarks` à `true` garantit que les caractères de droite à gauche sont correctement représentés dans le **fichier texte brut** résultant.

### Exemple 2 : Utilisation du caractère de tabulation pour l'indentation des listes (utiliser l'indentation par tabulation)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Ici, nous indiquons à Aspose.Words de préfixer chaque niveau de liste avec un caractère de tabulation (`'\t'`), rendant la sortie texte plus lisible.

## Étape 3 : Enregistrer le document en texte

Maintenant que les options d’enregistrement sont prêtes, vous pouvez enregistrer le document en **fichier texte brut** :

```java
doc.save("output.txt", saveOptions);
```

Remplacez `"output.txt"` par le chemin complet où vous souhaitez stocker le fichier.

## Code source complet pour enregistrer des documents en fichiers texte avec Aspose.Words pour Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Problèmes courants et solutions

| Problème | Solution |
|----------|----------|
| **Les caractères bidi apparaissent comme du texte illisible** | Assurez‑vous que `setAddBidiMarks(true)` est activé et que le fichier de sortie est ouvert avec l'encodage UTF‑8. |
| **L'indentation de la liste semble incorrecte** | Vérifiez que `ListIndentation.Count` et `Character` sont définis aux valeurs souhaitées (tabulation `'\t'` ou espace `' '` ). |
| **Le fichier n'est pas créé** | Vérifiez que le chemin du répertoire existe et que l'application dispose des permissions d'écriture. |

## Questions fréquemment posées

### Comment ajouter des marques bidi à la sortie texte ?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Puis‑je personnaliser le caractère d'indentation des listes ?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words pour Java est‑il adapté à la gestion de texte multilingue ?

Oui, Aspose.Words pour Java prend en charge un large éventail de langues et d’encodages de caractères, ce qui le rend idéal pour extraire et enregistrer du contenu multilingue en texte brut.

### Comment accéder à plus de documentation et de ressources pour Aspose.Words pour Java ?

Vous pouvez trouver une documentation complète et des ressources sur la page Documentation Aspose.Words pour Java : [Documentation Aspose.Words pour Java](https://reference.aspose.com/words/java/).

### Où puis‑je télécharger Aspose.Words pour Java ?

Vous pouvez télécharger la bibliothèque depuis le site officiel : [Télécharger Aspose.Words pour Java](https://releases.aspose.com/words/java/).

### Que faire si je dois **convertir word en txt** dans un processus par lots ?

Enveloppez le code présenté ci‑dessus dans une boucle qui charge chaque fichier `.docx`, applique les mêmes `TxtSaveOptions` et enregistre chacun en `.txt`. Veillez à gérer les ressources en libérant les objets `Document` après chaque itération.

### L'API prend‑elle en charge l'enregistrement directement vers un flux au lieu d'un fichier ?

Oui, vous pouvez passer un `OutputStream` à `doc.save(outputStream, saveOptions)` pour un traitement en mémoire ou lors de l'intégration avec des services web.

**Dernière mise à jour :** 2025-12-24  
**Testé avec :** Aspose.Words pour Java 24.12 (dernière version)  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}