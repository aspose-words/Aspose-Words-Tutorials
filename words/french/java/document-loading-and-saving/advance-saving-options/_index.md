---
date: 2025-12-19
description: Apprenez comment enregistrer Word avec un mot de passe, contrôler la
  compression des métafichiers et gérer les puces d’image à l’aide d’Aspose.Words
  pour Java.
linktitle: Saving Documents in Various Formats with
second_title: Aspose.Words Java Document Processing API
title: Enregistrer le document Word avec un mot de passe à l'aide d'Aspose.Words pour
  Java
url: /fr/java/document-loading-and-saving/advance-saving-options/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer Word avec mot de passe et options avancées avec Aspose.Words for Java

## Guide de tutoriel étape par étape : Enregistrer Word avec mot de passe et autres options d’enregistrement avancées

Dans le monde numérique d'aujourd'hui, les développeurs doivent souvent protéger les fichiers Word, contrôler la façon dont les objets incorporés sont enregistrés, ou supprimer les puces d'image indésirables. **Enregistrer un document Word avec un mot de passe** est une méthode simple mais puissante pour sécuriser les données sensibles, et Aspose.Words for Java le rend sans effort. Dans ce guide, nous parcourrons le chiffrement d'un document, la prévention de la compression des petits métafichiers, et la désactivation des puces d'image — afin que vous puissiez ajuster précisément la façon dont vos fichiers Word sont enregistrés.

## Réponses rapides
- **Comment enregistrer un document Word avec un mot de passe ?** Utilisez `DocSaveOptions.setPassword()` avant d'appeler `doc.save()`.  
- **Puis‑je empêcher la compression des petits métafichiers ?** Oui, définissez `saveOptions.setAlwaysCompressMetafiles(false)`.  
- **Est‑il possible d'exclure les puces d'image du fichier enregistré ?** Absolument — utilisez `saveOptions.setSavePictureBullet(false)`.  
- **Ai‑je besoin d'une licence pour utiliser ces fonctionnalités ?** Une licence valide d'Aspose.Words for Java est requise pour une utilisation en production.  
- **Quelle version de Java est prise en charge ?** Aspose.Words fonctionne avec Java 8 et versions ultérieures.

## Qu’est‑ce que « enregistrer Word avec mot de passe » ?

Enregistrer un document Word avec un mot de passe chiffre le contenu du fichier, nécessitant le mot de passe correct pour l'ouvrir dans Microsoft Word ou tout visualiseur compatible. Cette fonctionnalité est essentielle pour protéger les rapports confidentiels, les contrats ou toute donnée qui doit rester privée.

## Pourquoi utiliser Aspose.Words for Java pour cette tâche ?

- **Contrôle complet** – Vous pouvez définir les mots de passe, les options de compression et la gestion des puces en un seul appel d'API.  
- **Pas besoin de Microsoft Office** – Fonctionne sur n'importe quelle plateforme supportant Java.  
- **Haute performance** – Optimisé pour les gros documents et le traitement par lots.

## Prérequis
- Java 8 ou version plus récente installé.  
- Bibliothèque Aspose.Words for Java ajoutée à votre projet (Maven/Gradle ou JAR manuel).  
- Une licence valide d'Aspose.Words pour la production (essai gratuit disponible).

## Guide étape par étape

### 1. Créer un document simple
Tout d'abord, créez un nouveau `Document` et ajoutez du texte. Ce sera le fichier que nous protégerons ensuite avec un mot de passe.

```java
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.write("Hello world!");
```

### 2. Chiffrer le document – **enregistrer Word avec mot de passe**
Nous configurons maintenant `DocSaveOptions` pour intégrer un mot de passe. Lorsque le fichier est ouvert, Word demandera ce mot de passe.

```java
DocSaveOptions saveOptions = new DocSaveOptions();
{
    saveOptions.setPassword("password");
}
doc.save("Your Directory Path" + "EncryptedDocument.docx", saveOptions);
```

### 3. Ne pas compresser les petits métafichiers
Les métafichiers (comme EMF/WMF) sont souvent compressés automatiquement. Si vous avez besoin de la qualité originale, désactivez la compression :

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

### 4. Exclure les puces d'image du fichier enregistré
Les puces d'image peuvent augmenter la taille du fichier. Utilisez l'option suivante pour les omettre lors de l'enregistrement :

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

### 5. Code source complet à titre de référence
Ci-dessous se trouve l'exemple complet, prêt à l'exécution, qui démontre les trois options d'enregistrement avancées ensemble.

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
```

## Problèmes courants et dépannage
- **Mot de passe non appliqué** – Assurez‑vous d'utiliser `DocSaveOptions` *au lieu de* `PdfSaveOptions` ou d'autres options spécifiques à un format.  
- **Métafichiers toujours compressés** – Vérifiez que le fichier source contient réellement de petits métafichiers ; l'option ne concerne que ceux en dessous d'un certain seuil de taille.  
- **Les puces d'image apparaissent toujours** – Certaines versions anciennes de Word ignorent le drapeau ; envisagez de convertir les puces en styles de liste standard avant l'enregistrement.

## Questions fréquemment posées

**Q : Aspose.Words for Java est‑il une bibliothèque gratuite ?**  
R : Non, Aspose.Words for Java est une bibliothèque commerciale. Vous pouvez consulter les détails de licence [ici](https://purchase.aspose.com/buy).

**Q : Comment obtenir un essai gratuit d'Aspose.Words for Java ?**  
R : Vous pouvez obtenir un essai gratuit [ici](https://releases.aspose.com/).

**Q : Où puis‑je trouver du support pour Aspose.Words for Java ?**  
R : Pour le support et les discussions communautaires, visitez le [forum Aspose.Words for Java](https://forum.aspose.com/).

**Q : Puis‑je utiliser Aspose.Words for Java avec d'autres frameworks Java ?**  
R : Oui, il s'intègre facilement avec Spring, Hibernate, Android et la plupart des conteneurs Java EE.

**Q : Existe‑t‑il une option de licence temporaire pour l'évaluation ?**  
R : Oui, une licence temporaire est disponible [ici](https://purchase.aspose.com/temporary-license/).

## Conclusion
Vous savez maintenant comment **enregistrer Word avec mot de passe**, contrôler la compression des métafichiers et exclure les puces d'image en utilisant Aspose.Words for Java. Ces options d'enregistrement avancées vous offrent un contrôle précis sur la taille finale du fichier, la sécurité et l'apparence — parfait pour les rapports d'entreprise, l'archivage de documents ou tout scénario où l'intégrité du document est cruciale.

---

**Dernière mise à jour :** 2025-12-19  
**Testé avec :** Aspose.Words for Java 24.12 (dernière version au moment de la rédaction)  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}