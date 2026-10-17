---
date: 2026-02-22
description: Apprenez à enregistrer un document Word avec un mot de passe et à utiliser
  des options d’enregistrement avancées telles que la gestion des métafichiers et
  le contrôle des puces d’image avec Aspose.Words for Java.
linktitle: Saving Documents in Various Formats with
second_title: Aspose.Words Java Document Processing API
title: Enregistrer Word avec mot de passe et options avancées – Aspose.Words pour
  Java
url: /fr/java/document-loading-and-saving/advance-saving-options/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer Word avec mot de passe et options avancées – Aspose.Words for Java

Dans les applications Java modernes, **saving Word with password** protection est une exigence courante pour protéger le contenu sensible. Aspose.Words for Java vous permet non seulement de chiffrer les documents, mais aussi de contrôler finement la compression des métafichiers, les puces d'image, et de nombreuses autres fonctionnalités d'enregistrement. Dans ce tutoriel étape par étape, nous passerons en revue les options d'enregistrement *avancées* les plus utiles que vous pouvez appliquer avec l'API Aspose.Words Java.

## Réponses rapides
- **Comment ajouter un mot de passe à un fichier Word ?** Utilisez `DocSaveOptions.setPassword("yourPassword")` avant d'appeler `doc.save()`.  
- **Puis‑je empêcher la compression des métafichiers ?** Définissez `saveOptions.setAlwaysCompressMetafiles(false)`.  
- **Est‑il possible d'exclure les puces d'image ?** Oui, appelez `saveOptions.setSavePictureBullet(false)`.  
- **Ai‑je besoin d'une licence pour ces fonctionnalités ?** Un essai fonctionne pour l'évaluation ; une licence commerciale est requise pour la production.  
- **Quel produit Aspose couvre‑t‑il cela ?** Aspose.Words for Java — la bibliothèque leader pour les tâches de **aspose words document saving**.

## Qu’est‑ce que “save word with password” ?
Enregistrer un document Word avec un mot de passe signifie chiffrer le fichier afin que seuls les utilisateurs connaissant le mot de passe puissent l'ouvrir, le modifier ou l'imprimer. Cette couche de sécurité est essentielle pour les rapports confidentiels, les contrats ou toute donnée qui doit rester privée.

## Pourquoi utiliser les fonctionnalités d’enregistrement de documents Aspose.Words ?
Aspose.Words offre un ensemble complet d'options **aspose words document saving** qui vont bien au-delà d'une simple sortie de fichier. Vous pouvez contrôler la compression, la gestion des images, et même décider d'incorporer ou non des puces d'image—tout cela sans quitter votre code Java.

## Prérequis
- Java 8 ou version ultérieure installé.  
- Bibliothèque Aspose.Words for Java ajoutée à votre projet (Maven/Gradle ou JAR manuel).  
- Familiarité de base avec les IDE Java (IntelliJ, Eclipse, etc.).

## Guide étape par étape

### Étape 1 : Créer un document simple
Tout d'abord, nous créons un nouveau `Document` et ajoutons du texte. Ce sera le fichier de base que nous protégerons ensuite avec un mot de passe.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Hello world!");
```

### Étape 2 : Enregistrer Word avec mot de passe
Maintenant nous chiffrons le document. L'objet `DocSaveOptions` nous permet de spécifier le mot de passe ainsi que d'autres préférences d'enregistrement.

```java
DocSaveOptions saveOptions = new DocSaveOptions();
{
    saveOptions.setPassword("password");
}
doc.save("Your Directory Path" + "EncryptedDocument.docx", saveOptions);
```

> **Astuce :** Stockez les mots de passe de manière sécurisée (par ex., en utilisant un coffre) et ne les codez jamais en dur dans le code de production.

### Étape 3 : Ne pas compresser les petits métafichiers
Si votre document contient des graphiques vectoriels (par ex., des objets d'équation), vous pouvez préférer les laisser non compressés pour une meilleure qualité. L'exemple suivant désactive la compression automatique.

```java
@Test
public void doNotCompressSmallMetafiles() throws Exception {
    Document doc = new Document("Your Directory Path" + "Microsoft equation object.docx");
    DocSaveOptions saveOptions = new DocSaveOptions();
    {
        saveOptions.setAlwaysCompressMetafiles(false);
    }
    doc.save("Your Directory Path" + "NotCompressedMetafiles.docx", saveOptions);
}
```

### Étape 4 : Exclure les puces d'image du fichier enregistré
Les puces d'image peuvent augmenter la taille du fichier. Si vous n'en avez pas besoin, désactivez‑les avec `setSavePictureBullet(false)`.

```java
@Test
public void doNotSavePictureBullet() throws Exception {
    Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
    DocSaveOptions saveOptions = new DocSaveOptions();
    {
        saveOptions.setSavePictureBullet(false);
    }
    doc.save("Your Directory Path" + "NoPictureBullet.docx", saveOptions);
}
```

### Étape 5 : Code source complet à titre de référence
Ci-dessous se trouve le code complet et exécutable qui montre les trois options d'enregistrement avancées ensemble.

```java
public void encryptDocumentWithPassword() throws Exception {
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.write("Hello world!");
	DocSaveOptions saveOptions = new DocSaveOptions();
	{
		saveOptions.setPassword("password");
	}
	doc.save("Your Directory Path" + "WorkingWithDocSaveOptions.EncryptDocumentWithPassword.docx", saveOptions);
}
@Test
public void doNotCompressSmallMetafiles() throws Exception {
	Document doc = new Document("Your Directory Path" + "Microsoft equation object.docx");
	DocSaveOptions saveOptions = new DocSaveOptions();
	{
		saveOptions.setAlwaysCompressMetafiles(false);
	}
	doc.save("Your Directory Path" + "WorkingWithDocSaveOptions.NotCompressSmallMetafiles.docx", saveOptions);
}
@Test
public void doNotSavePictureBullet() throws Exception {
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	DocSaveOptions saveOptions = new DocSaveOptions();
	{
		saveOptions.setSavePictureBullet(false);
	}
	doc.save("Your Directory Path" + "WorkingWithDocSaveOptions.DoNotSavePictureBullet.docx", saveOptions);
}
```

## Problèmes courants et astuces
| Problème | Cause | Solution |
|----------|-------|----------|
| **Le document s'ouvre mais le mot de passe est ignoré** | Utilisation de `saveOptions` avec un `SaveFormat` différent | Assurez‑vous de passer la même instance `DocSaveOptions` à `doc.save()` et que l'extension du fichier correspond au format (par ex., `.docx`). |
| **Les métafichiers restent compressés** | `setAlwaysCompressMetafiles` n'affecte que les métafichiers *petits* | Vérifiez la taille du métafichier ; les gros sont toujours compressés selon la spécification DOCX. |
| **Les puces d'image apparaissent toujours** | Le document contient des images en ligne utilisées comme puces | Convertissez ces puces en styles de liste standard avant l'enregistrement, ou supprimez‑les manuellement via l'API. |

## Questions fréquemment posées

**Q : Aspose.Words for Java est‑il une bibliothèque gratuite ?**  
R : Non, Aspose.Words for Java est une bibliothèque commerciale. Vous pouvez trouver les détails de licence [ici](https://purchase.aspose.com/buy).

**Q : Comment obtenir un essai gratuit d'Aspose.Words for Java ?**  
R : Vous pouvez obtenir un essai gratuit d'Aspose.Words for Java [ici](https://releases.aspose.com/).

**Q : Où puis‑je trouver du support pour Aspose.Words for Java ?**  
R : Pour le support et les discussions communautaires, visitez le [forum Aspose.Words for Java](https://forum.aspose.com/).

**Q : Puis‑je utiliser Aspose.Words for Java avec d'autres bibliothèques Java ?**  
R : Oui, Aspose.Words for Java est compatible avec diverses bibliothèques et frameworks Java.

**Q : Existe‑t‑il une option de licence temporaire ?**  
R : Oui, vous pouvez obtenir une licence temporaire [ici](https://purchase.aspose.com/temporary-license/).

## Questions fréquentes supplémentaires

**Q : La protection par mot de passe affecte‑t‑elle la taille du document ?**  
R : Le fichier chiffré est légèrement plus volumineux en raison de la surcharge du chiffrement, mais l'augmentation est généralement négligeable.

**Q : Puis‑je définir différents mots de passe pour la lecture seule et les permissions de modification ?**  
R : Aspose.Words prend en charge un seul mot de passe pour ouvrir le document. Pour des permissions plus granulaires, envisagez d'utiliser la conversion PDF avec des paramètres de protection séparés.

**Q : Ces options d'enregistrement sont‑elles disponibles pour tous les formats Word (DOC, DOCX, RTF) ?**  
R : Oui, `DocSaveOptions` fonctionne avec tous les formats pris en charge par Aspose.Words, bien que certaines options soient spécifiques à un format (par ex., les puces d'image ne concernent que le DOCX).

**Dernière mise à jour** : 2026-02-22  
**Testé avec** : Aspose.Words for Java 24.12  
**Auteur** : Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}