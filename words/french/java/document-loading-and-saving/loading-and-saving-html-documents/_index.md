---
date: 2025-12-20
description: Apprenez à charger du HTML et à convertir du HTML en DOCX avec Aspose.Words
  pour Java. Le guide étape par étape montre comment enregistrer des fichiers DOCX
  et utiliser les balises de document structurées.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Comment charger du HTML et l’enregistrer au format DOCX avec Aspose.Words pour
  Java
url: /fr/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comment charger du HTML et l’enregistrer en DOCX avec Aspose.Words for Java

## Introduction au chargement et à l’enregistrement de documents HTML avec Aspose.Words for Java

Dans cet article, nous allons explorer **comment charger du html** et l’enregistrer sous forme de fichier DOCX en utilisant la bibliothèque Aspose.Words for Java. Aspose.Words est une API puissante qui vous permet de manipuler des documents Word de façon programmatique, et elle inclut une prise en charge robuste de l’import/export HTML. Nous parcourrons l’ensemble du processus, depuis la configuration des options de chargement jusqu’à la persistance du résultat en tant que document Word.

## Réponses rapides
- **Quelle est la classe principale pour charger du HTML ?** `Document` avec `HtmlLoadOptions`.
- **Quelle option active les Structured Document Tags ?** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **Puis‑je convertir du HTML en DOCX en une seule étape ?** Oui – chargez le HTML et appelez `doc.save(...".docx")`.
- **Ai‑je besoin d’une licence pour le développement ?** Une version d’essai gratuite suffit pour les tests ; une licence commerciale est requise en production.
- **Quelle version de Java est requise ?** Java 8 ou supérieur est supporté.

## Qu’est‑ce que « how to load html » dans le contexte d’Aspose.Words ?
Charger du HTML signifie lire une chaîne ou un fichier HTML et le convertir en un objet `Document` d’Aspose.Words. Cet objet peut ensuite être édité, formaté ou enregistré dans n’importe quel format supporté par l’API, tel que DOCX, PDF ou RTF.

## Pourquoi utiliser Aspose.Words pour la conversion HTML‑vers‑DOCX ?
- **Préserve la mise en page** – les tableaux, listes et images restent intacts.
- **Prise en charge des Structured Document Tags** – idéal pour créer des contrôles de contenu dans Word.
- **Pas besoin de Microsoft Office** – fonctionne sur n’importe quel serveur ou environnement cloud.
- **Haute performance** – traite rapidement de gros fichiers HTML.

## Prérequis

1. **Bibliothèque Aspose.Words for Java** – téléchargez‑la depuis [here](https://releases.aspose.com/words/java/).
2. **Environnement de développement Java** – JDK 8+ installé et configuré.
3. **Familiarité de base avec Java I/O** – nous utiliserons `ByteArrayInputStream` pour fournir la chaîne HTML.

## Comment charger des documents HTML

Voici un exemple concis qui montre comment charger un extrait HTML tout en activant la fonctionnalité **structured document tag**.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**Explication**

- Nous créons une chaîne `HTML` contenant un simple contrôle `<select>`.
- `HtmlLoadOptions` nous permet de spécifier comment le HTML doit être interprété. Définir le type de contrôle préféré sur `STRUCTURED_DOCUMENT_TAG` indique à Aspose.Words de convertir les contrôles de formulaire HTML en contrôles de contenu Word.
- Le constructeur `Document` lit le HTML depuis un `ByteArrayInputStream` en utilisant l’encodage UTF‑8.

## Comment enregistrer en DOCX (Convertir HTML en DOCX)

Une fois le HTML chargé dans un `Document`, l’enregistrement en fichier DOCX est simple :

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

Remplacez `"Your Directory Path"` par le dossier réel où vous souhaitez que le fichier de sortie apparaisse.

## Code source complet pour charger et enregistrer des documents HTML

Voici l’exemple complet, prêt à être exécuté, qui combine les étapes de chargement et d’enregistrement. N’hésitez pas à le copier‑coller dans votre IDE.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## Pièges courants & astuces

| Problème | Pourquoi cela se produit | Comment corriger |
|----------|--------------------------|------------------|
| **Polices manquantes** | Le HTML référence des polices non installées sur le serveur. | Intégrez les polices dans le DOCX avec `FontSettings` ou assurez‑vous que les polices requises sont disponibles. |
| **Images non affichées** | Les chemins d’image relatifs ne peuvent pas être résolus. | Utilisez des URL absolues ou chargez les images dans un `MemoryStream` et définissez `HtmlLoadOptions.setImageSavingCallback`. |
| **Type de contrôle non converti** | `setPreferredControlType` non défini ou défini sur la mauvaise énumération. | Vérifiez que vous utilisez `HtmlControlType.STRUCTURED_DOCUMENT_TAG`. |
| **Problèmes d’encodage** | Chaîne HTML encodée avec un jeu de caractères différent. | Utilisez toujours `StandardCharsets.UTF_8` lors de la conversion de la chaîne en octets. |

## Questions fréquemment posées

### Comment installer Aspose.Words for Java ?
Aspose.Words for Java peut être téléchargé depuis [here](https://releases.aspose.com/words/java/). Suivez le guide d’installation sur la page de téléchargement pour ajouter les fichiers JAR à votre classpath.

### Puis‑je charger des documents HTML complexes avec Aspose.Words ?
Oui, Aspose.Words for Java peut gérer du HTML complexe, incluant des tableaux imbriqués, du CSS et des éléments interactifs sans JavaScript. Ajustez `HtmlLoadOptions` (par ex., `setLoadImages` ou `setCssStyleSheetFileName`) pour affiner l’import.

### Quels autres formats de documents Aspose.Words prend‑il en charge ?
Aspose.Words prend en charge DOC, DOCX, RTF, HTML, PDF, EPUB, XPS, et bien d’autres. L’API offre un enregistrement en une ligne vers n’importe lequel de ces formats.

### Aspose.Words convient‑il à l’automatisation de documents à l’échelle entreprise ?
Absolument. Il est utilisé par de grandes entreprises pour la génération automatisée de rapports, la conversion massive de documents et le traitement côté serveur sans dépendance à Microsoft Office.

### Où puis‑je trouver plus de documentation et d’exemples pour Aspose.Words for Java ?
Vous pouvez explorer la référence complète de l’API et des tutoriels supplémentaires sur le site de documentation d’Aspose.Words for Java : [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Dernière mise à jour :** 2025-12-20  
**Testé avec :** Aspose.Words for Java 24.12 (dernière version au moment de la rédaction)  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}