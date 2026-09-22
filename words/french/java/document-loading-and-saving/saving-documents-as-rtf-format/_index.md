---
date: 2025-12-24
description: Apprenez comment convertir Word en RTF avec Aspose.Words pour Java. Ce
  tutoriel étape par étape montre le chargement d’un DOCX, la configuration des options
  d’enregistrement RTF et l’enregistrement en texte enrichi.
linktitle: Saving Documents as RTF Format
second_title: Aspose.Words Java Document Processing API
title: Convertir Word en RTF avec le tutoriel Aspose.Words pour Java
url: /fr/java/document-loading-and-saving/saving-documents-as-rtf-format/
weight: 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Convertir Word en RTF avec Aspose.Words pour Java

Dans ce tutoriel, vous apprendrez **comment convertir Word en RTF** rapidement et de manière fiable en utilisant Aspose.Words pour Java. Convertir un DOCX au format RTF riche est une exigence courante lorsque vous avez besoin d’une large compatibilité avec les traitements de texte hérités, les clients de messagerie ou les systèmes d’archivage de documents. Nous parcourrons le chargement d’un document Word en Java, l’ajustement des options d’enregistrement RTF (y compris l’enregistrement des images au format WMF), puis l’écriture du fichier de sortie.

## Réponses rapides
- **Que signifie « convert word to rtf » ?** Cela transforme un fichier DOCX/Word en Rich Text Format tout en conservant le texte, les styles et éventuellement les images.  
- **Ai‑je besoin d’une licence ?** Un essai gratuit suffit pour le développement ; une licence commerciale est requise pour la production.  
- **Quelle version de Java est prise en charge ?** Aspose.Words pour Java prend en charge Java 8 et supérieur.  
- **Puis‑je conserver les images lors de la conversion ?** Oui – utilisez l’option `saveImagesAsWmf` pour intégrer les images au format WMF dans le RTF.  
- **Combien de temps prend la conversion ?** Généralement moins d’une seconde pour les documents standards ; les fichiers plus volumineux peuvent prendre quelques secondes.

## Qu’est‑ce que « convert word to rtf » ?
Convertir un document Word en RTF crée un fichier indépendant de la plateforme qui stocke le texte, la mise en forme et éventuellement les images dans un balisage basé sur du texte brut. Cela rend le document visible dans presque tous les traitements de texte sans perdre la mise en page.

## Pourquoi utiliser Aspose.Words pour Java pour enregistrer en texte enrichi ?
- **Fidélité totale** – Toutes les fonctionnalités Word (styles, tableaux, en‑têtes/pieds de page) sont conservées.  
- **Pas besoin de Microsoft Office** – Fonctionne sur n’importe quel serveur ou environnement cloud.  
- **Contrôle fin** – Les options d’enregistrement vous permettent de décider comment les images sont stockées, quel encodage utiliser, etc.

## Prérequis
1. **Bibliothèque Aspose.Words pour Java** – Téléchargez et ajoutez le JAR à votre projet depuis [here](https://releases.aspose.com/words/java/).  
2. **Un fichier Word source** – Par exemple, `Document.docx` que vous souhaitez enregistrer en RTF.  
3. **Environnement de développement Java** – JDK 8+ et votre IDE préféré.

## Étape 1 : Charger le document Word (load word document java)
Tout d’abord, chargez le DOCX existant dans un objet `Document`. C’est la base de toute conversion.

```java
import com.aspose.words.Document;

// Load the source document (e.g., Document.docx)
Document doc = new Document("path/to/Document.docx");
```

> **Astuce :** Utilisez des chemins absolus ou des ressources du class‑path pour éviter `FileNotFoundException`.

## Étape 2 : Configurer les options d’enregistrement RTF (save images as wmf)
Aspose.Words propose la classe `RtfSaveOptions` pour affiner la sortie. Dans cet exemple, nous activons **save images as WMF**, qui est le format préféré pour les fichiers RTF.

```java
import com.aspose.words.RtfSaveOptions;

// Create an instance of RtfSaveOptions
RtfSaveOptions saveOptions = new RtfSaveOptions();

// Set the option to save images as WMF
saveOptions.setSaveImagesAsWmf(true);
```

Vous pouvez également ajuster d’autres paramètres, comme `saveOptions.setEncoding(Charset.forName("UTF-8"))` si vous avez besoin d’un encodage de caractères spécifique.

## Étape 3 : Enregistrer le document en RTF (save docx as rtf)
Ensuite, écrivez le document en utilisant les options configurées. Cette étape **enregistre le DOCX en RTF**, produisant un fichier texte enrichi prêt à être distribué.

```java
// Save the document in RTF format

doc.save("path/to/output.rtf", saveOptions);
```

## Code source complet pour convertir Word en RTF
Voici la version compacte que vous pouvez copier‑coller dans une classe Java. Elle montre **save as rich text** avec l’option d’image WMF dans un seul bloc.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
RtfSaveOptions saveOptions = new RtfSaveOptions(); { saveOptions.setSaveImagesAsWmf(true); }
doc.save("Your Directory Path" + "WorkingWithRtfSaveOptions.SavingImagesAsWmf.rtf", saveOptions);
```

## Pièges courants et dépannage
| Problème | Raison | Solution |
|----------|--------|----------|
| Le RTF de sortie est vide | Fichier source introuvable ou non chargé | Vérifiez le chemin dans `new Document(...)` |
| Images manquantes | `saveImagesAsWmf` défini sur `false` | Activez `saveOptions.setSaveImagesAsWmf(true)` |
| Caractères illisibles | Encodage incorrect | Définissez `saveOptions.setEncoding(Charset.forName("UTF-8"))` |

## Questions fréquentes

**Q : Comment modifier d’autres options d’enregistrement RTF ?**  
R : Utilisez la classe `RtfSaveOptions` – elle fournit des propriétés pour la compression, les polices, etc. Consultez la documentation de l’API Aspose.Words Java pour la liste complète.

**Q : Puis‑je enregistrer le document RTF avec un encodage différent ?**  
R : Oui. Appelez `saveOptions.setEncoding(Charset.forName("UTF-8"))` (ou tout autre jeu de caractères supporté) avant l’enregistrement.

**Q : Est‑il possible d’enregistrer le document RTF sans images ?**  
R : Absolument. Définissez `saveOptions.setSaveImagesAsWmf(false)` pour exclure les images du résultat.

**Q : Comment gérer les exceptions pendant la conversion ?**  
R : Enveloppez les appels de chargement et d’enregistrement dans un bloc try‑catch capturant `Exception`. Enregistrez l’erreur et, si besoin, relancez une exception personnalisée pour votre application.

**Q : Cette méthode fonctionne‑t‑elle avec des fichiers Word protégés par mot de passe ?**  
R : Chargez le document avec un objet `LoadOptions` contenant le mot de passe, puis poursuivez les mêmes étapes d’enregistrement.

## Conclusion
Vous disposez maintenant d’une méthode complète, prête pour la production, pour **convertir Word en RTF** en utilisant Aspose.Words pour Java. En chargeant le DOCX, en configurant `RtfSaveOptions` (y compris **save images as WMF**), et en appelant `doc.save(...)`, vous pouvez générer des fichiers texte enrichi de haute qualité qui fonctionnent partout. N’hésitez pas à explorer d’autres options d’enregistrement pour adapter la sortie à vos besoins précis.

---

**Dernière mise à jour :** 2025-12-24  
**Testé avec :** Aspose.Words for Java 24.12  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}