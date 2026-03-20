---
date: '2026-03-20'
description: Apprenez à créer des signets imbriqués et à générer des PDF avec des
  signets à l'aide d'Aspose.Words pour Java, améliorant la lisibilité et la navigation.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Créer des signets imbriqués dans les PDF avec Aspose.Words Java
url: /fr/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Créer des signets imbriqués dans les PDF avec Aspose.Words Java

## Introduction
Si vous avez déjà eu du mal à garder les signets PDF organisés après avoir converti un document Word, vous n'êtes pas seul. Dans ce tutoriel, vous **créerez des signets imbriqués** et apprendrez à **générer un PDF avec des signets** faciles à parcourir. Nous passerons en revue la configuration d'Aspose.Words, la construction d'une hiérarchie de signets, l'attribution de niveaux de plan, et enfin l'exportation d'un PDF propre.

**Ce que vous apprendrez**
- Comment configurer Aspose.Words pour Java
- Comment **créer des signets imbriqués** dans un document Word
- Comment configurer les niveaux de plan des signets pour une navigation PDF claire
- Comment **générer un PDF avec des signets** qui reflètent la hiérarchie que vous avez définie

### Réponses rapides
- **Quelle est la classe principale pour créer des documents ?** `DocumentBuilder`
- **Quelle méthode ajoute un signet ?** `startBookmark(String name)`
- **Comment définir un niveau de plan pour un signet ?** `outlineLevels.add(name, level)`
- **Ai-je besoin d'une licence pour la production ?** Oui, une licence achetée débloque toutes les fonctionnalités.
- **Puis-je l'utiliser avec Maven ou Gradle ?** Absolument – les deux sont pris en charge.

### Prérequis
- **Aspose.Words pour Java** (version 25.3 ou ultérieure).  
- Un JDK installé et un IDE tel qu'IntelliJ IDEA ou Eclipse.  
- Connaissances de base en Java et familiarité avec Maven ou Gradle.

## Qu’est‑ce que « créer des signets imbriqués » ?
Créer des signets imbriqués signifie placer un signet à l'intérieur d'un autre, formant une hiérarchie parent‑enfant. Lorsque le document est enregistré au format PDF, ces relations apparaissent comme des entrées réductibles dans le volet des signets du PDF, rendant les documents volumineux beaucoup plus faciles à explorer.

## Pourquoi utiliser les niveaux de plan lors de la génération d'un PDF avec des signets ?
Les niveaux de plan définissent la hiérarchie visuelle des signets dans le visualiseur PDF. Un signet de niveau 1 apparaît comme une entrée de niveau supérieur, le niveau 2 comme un enfant, etc. Des niveaux de plan appropriés transforment une liste plate de signets en une table des matières structurée, ce qui est particulièrement utile pour les contrats juridiques, les rapports techniques et les livres numériques.

## Configuration d'Aspose.Words
Ajoutez la bibliothèque à votre projet en utilisant Maven ou Gradle.

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Acquisition de licence
Aspose.Words est un produit commercial, mais vous pouvez commencer avec un essai gratuit.

1. **Essai gratuit** – Téléchargez depuis la [page de diffusion d'Aspose](https://releases.aspose.com/words/java/) pour tester toutes les capacités.  
2. **Licence temporaire** – Postulez sur la [page de licence temporaire d'Aspose](https://purchase.aspose.com/temporary-license/) pour une évaluation à court terme.  
3. **Achat** – Obtenez une licence permanente depuis le [portail d'achat d'Aspose](https://purchase.aspose.com/buy).

Après avoir obtenu le fichier `.lic`, chargez‑le dans votre code pour débloquer toutes les fonctionnalités.

## Guide d'implémentation
Voici un guide pas à pas pour créer un document, ajouter des signets imbriqués, attribuer des niveaux de plan, et enregistrer le résultat au format PDF.

### Étape 1 : Initialiser le Document et le Builder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Cela crée un document Word vide et un objet builder que vous utiliserez pour insérer du texte et des signets.

### Étape 2 : Créer le premier signet (parent)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
L’appel `startBookmark` ouvre un nouveau signet nommé **Bookmark 1**. Tout ce que vous écrivez après cet appel appartiendra à ce signet jusqu’à ce que vous le fermiez.

### Étape 3 : Imbriquer un deuxième signet à l'intérieur du premier
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
Comme ce signet est démarré **après** le premier et fermé **avant** le premier, il devient un enfant de **Bookmark 1**.

### Étape 4 : Fermer le signet parent
```java
builder.endBookmark("Bookmark 1");
```
La hiérarchie ressemble maintenant à :

- Bookmark 1 (niveau 1)  
  - Bookmark 2 (niveau 2)

### Étape 5 : Ajouter un troisième signet indépendant
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```
Ce signet se trouve au niveau supérieur, séparé des deux premiers.

### Étape 6 : Configurer les niveaux de plan pour l'exportation PDF
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
L’objet `PdfSaveOptions` vous permet de contrôler la façon dont les signets apparaissent dans le PDF final.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 1);
```
Ici nous attribuons le niveau 1 aux signets de niveau supérieur et le niveau 2 au signet imbriqué.

### Étape 7 : Enregistrer le document au format PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
Le PDF résultant affichera un volet de signets propre et réductible qui reflète la hiérarchie que vous avez définie.

## Problèmes courants et solutions
- **Signets manquants** – Chaque `startBookmark` doit avoir un `endBookmark` correspondant. En oublier un entraînera l'ignorance du signet dans le PDF.  
- **Niveaux de plan incorrects** – Vérifiez deux fois les noms que vous passez à `outlineLevels.add`. Une faute de frappe signifie que le niveau ne sera pas appliqué.  
- **Documents volumineux** – Pour des fichiers très gros, appelez `doc.removeMacros()` ou supprimez les styles inutilisés avant d’enregistrer afin de garder une taille de PDF raisonnable.

## Applications pratiques
1. **Contrats juridiques** – Passez rapidement d’une clause à une sous‑clause.  
2. **Rapports techniques** – Naviguez entre les sections, tableaux et figures sans faire défiler.  
3. **Matériel d’e‑learning** – Fournissez une table des matières cliquable pour les étudiants.

## Conseils de performance
- Supprimez les ressources inutilisées (images, styles) avant d’enregistrer.  
- Utilisez les API de streaming si vous traitez des PDF de plus de 100 Mo afin de maintenir une faible consommation de mémoire.

## Conclusion
Vous savez maintenant comment **créer des signets imbriqués**, attribuer des niveaux de plan, et **générer un PDF avec des signets** à la fois fonctionnels et conviviaux. Expérimentez avec des hiérarchies plus profondes ou intégrez cette logique dans votre pipeline de génération de documents pour une automatisation encore plus poussée.

## Questions fréquentes

**Q : Comment installer Aspose.Words pour Java ?**  
R : Ajoutez la dépendance Maven ou Gradle indiquée ci‑dessus, puis chargez votre fichier de licence à l’exécution.

**Q : Puis‑je utiliser les signets sans définir de niveaux de plan ?**  
R : Oui, mais le PDF affichera une liste plate, ce qui peut être difficile à parcourir dans des documents complexes.

**Q : Y a‑t‑il une limite à la profondeur d’imbrication des signets ?**  
R : Techniquement non, mais gardez la hiérarchie raisonnable (3‑4 niveaux) pour maintenir la lisibilité.

**Q : Comment Aspose gère‑t‑il les très gros documents ?**  
R : Il diffuse le contenu et propose des utilitaires de gestion de la mémoire ; toutefois, vous devez toujours éliminer les éléments inutilisés.

**Q : Puis‑je modifier les signets après la création du PDF ?**  
R : Absolument – utilisez Aspose.PDF pour Java afin de modifier les titres des signets, leurs destinations ou les niveaux de plan après la génération.

## Ressources
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)
- [Download Latest Releases](https://releases.aspose.com/words/java/)
- [Purchase a License](https://purchase.aspose.com/buy)
- [Free Trial](https://releases.aspose.com/words/java/)
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Dernière mise à jour :** 2026-03-20  
**Testé avec :** Aspose.Words for Java 25.3  
**Auteur :** Aspose