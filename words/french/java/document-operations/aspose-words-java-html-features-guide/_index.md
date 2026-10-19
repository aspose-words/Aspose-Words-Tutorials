---
date: '2026-02-06'
description: Apprenez à charger le VML HTML avec Aspose.Words pour Java, à chiffrer
  les fichiers HTML Java, à définir l'URI de base HTML et à configurer les options
  de contrôle HTML.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: Charger le HTML VML avec Aspose.Words pour Java – Guide complet
url: /fr/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Fonctionnalités complètes du HTML avec Aspose.Words for Java : Guide du développeur

## Introduction

Naviguer dans le monde complexe du traitement de documents peut être intimidant, surtout lorsqu’il s’agit de gérer diverses fonctionnalités HTML. Que vous manipuliez le support Vector Markup Language (VML), des documents chiffrés ou des comportements spécifiques d’importation HTML, **Aspose.Words for Java** offre une solution robuste. Dans ce guide, vous apprendrez **comment charger html vml** de manière efficace et sécurisée, tout en couvrant des tâches connexes telles que **encrypt html java**, **set html base uri**, et les options **configure html control**.

**Ce que vous allez apprendre :**
- Comment charger des documents HTML avec le support VML.
- Techniques pour gérer le HTML à page fixe et les avertissements.
- Méthodes pour chiffrer et charger des documents HTML protégés par mot de passe.
- Utilisation des URI de base dans les HtmlLoadOptions.
- Importation des éléments d’entrée HTML en tant que balises de document structuré ou champs de formulaire.
- Ignorer les éléments `<noscript>` lors du chargement HTML.
- Configuration des modes d’importation de blocs pour contrôler la préservation de la structure HTML.
- Prise en charge des règles `@font-face` pour les polices personnalisées.

## Réponses rapides
- **Quelle est la façon principale d’activer le VML lors du chargement d’un HTML ?** Définissez `loadOptions.setSupportVml(true)`.
- **Puis‑je charger des fichiers HTML protégés par mot de passe ?** Oui, transmettez le mot de passe à `HtmlLoadOptions`.
- **Comment résoudre les chemins d’image relatifs ?** Utilisez `loadOptions.setBaseUri("your/base/uri")`.
- **Est‑il possible d’importer `<select>` en tant que champ de formulaire ?** Définissez `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`.
- **Quelle classe capture les avertissements pendant le chargement ?** Implémentez `IWarningCallback` et assignez‑la à `loadOptions.setWarningCallback(...)`.

## Prérequis

Avant de commencer à implémenter les différentes fonctionnalités HTML avec Aspose.Words for Java, assurez‑vous que votre environnement est correctement configuré :

- **Bibliothèques requises :** Vous avez besoin de la bibliothèque Aspose.Words version 25.3 ou ultérieure.
- **Environnement de développement :** Ce guide suppose que vous utilisez Maven ou Gradle pour la gestion des dépendances.
- **Base de connaissances :** Une compréhension de base de Java et une familiarité avec les documents HTML seront utiles.

## Installation d’Aspose.Words

Pour commencer à travailler avec Aspose.Words, vous devez d’abord l’ajouter à votre projet. Voici les étapes pour configurer la bibliothèque avec Maven et Gradle :

### Maven

Ajoutez la dépendance suivante à votre fichier `pom.xml` :

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

Incluez ceci dans votre fichier `build.gradle` :

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Acquisition de licence

Aspose.Words nécessite une licence pour fonctionner pleinement. Vous pouvez obtenir un essai gratuit, demander une licence temporaire ou acheter une licence permanente. Consultez la [page d’achat](https://purchase.aspose.com/buy) pour plus de détails.

Pour initialiser Aspose.Words dans votre projet Java, assurez‑vous d’avoir configuré correctement la licence :

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## Guide d’implémentation

Nous allons décomposer l’implémentation en sections selon les fonctionnalités que nous souhaitons mettre en œuvre.

### Comment charger html vml avec Aspose.Words

**Vue d’ensemble :**  
Le chargement d’un document HTML avec le support VML permet un rendu polyvalent des graphiques vectoriels tels que les graphiques et les formes. C’est l’étape centrale pour le mot‑clé principal **load html vml**.

#### Étape par étape

1. **Configurer les options de chargement**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **Charger le document**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **Vérifier le type d’image**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### Charger du HTML fixe et gérer les avertissements

**Vue d’ensemble :**  
Le chargement de documents HTML à page fixe peut générer des avertissements qui doivent être gérés pour un traitement précis.

#### Étape par étape

1. **Définir le rappel d’avertissement**

```java
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import java.util.ArrayList;

private static class ListDocumentWarnings implements IWarningCallback {
    private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

    public void warning(WarningInfo info) { 
        mWarnings.add(info); 
    }

    public ArrayList<WarningInfo> warnings() { return mWarnings; }
}
```

2. **Configurer les options de chargement**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **Charger le document et vérifier les avertissements**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### Chiffrer des documents HTML

**Vue d’ensemble :**  
Le chiffrement d’un document HTML avec un mot de passe assure un accès sécurisé, ce qui est essentiel pour les informations sensibles — cela répond au scénario **encrypt html java**.

#### Étape par étape

1. **Préparer les options de signature numérique**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;

CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
SignOptions signOptions = new SignOptions();
signOptions.setComments("Comment");
signOptions.setSignTime(new Date());
signOptions.setDecryptionPassword("docPassword");
```

2. **Signer et chiffrer le document**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **Charger le document chiffré**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### URI de base pour les HtmlLoadOptions

**Vue d’ensemble :**  
Spécifier un **set html base uri** aide à résoudre les URI relatifs, notamment lorsqu’il s’agit d’images ou d’autres ressources liées.

#### Étape par étape

1. **Configurer les options de chargement avec l’URI de base**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **Charger le document et vérifier l’image**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### Importer le HTML `<select>` en tant que balise de document structuré

**Vue d’ensemble :**  
Pour **configure html control**, vous pouvez importer les éléments `<select>` en tant que Structured Document Tags, ce qui vous donne un contrôle plus fin sur les champs de formulaire dans les documents Word.

#### Étape par étape

1. **Définir le type de contrôle préféré**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **Charger le document et vérifier la structure**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.StructuredDocumentTag;

Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (!sdt.getTagName().equals("Select")) {
    throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
}
```

## Problèmes courants et solutions

| Problème | Raison | Solution |
|----------|--------|----------|
| Les graphiques VML n’apparaissent pas | Le drapeau `supportVml` laissé à sa valeur par défaut (`false`) | Assurez‑vous d’appeler `loadOptions.setSupportVml(true)` avant le chargement. |
| Images manquantes après le chargement | Les chemins relatifs ne peuvent pas être résolus | Utilisez **set html base uri** (`loadOptions.setBaseUri(...)`) pour pointer vers le bon dossier. |
| Le HTML protégé par mot de passe génère une exception | Mot de passe non fourni | Transmettez le mot de passe à `new HtmlLoadOptions("yourPassword")`. |
| Les contrôles de formulaire apparaissent en texte brut | `HtmlControlType` incorrect | Définissez `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` ou `FormField` selon le besoin. |
| Avertissements inattendus | Éléments HTML non gérés | Implémentez `IWarningCallback` pour capturer et examiner les avertissements. |

## FAQ

**Q : Puis‑je charger des fichiers HTML contenant à la fois du VML et des graphiques SVG modernes ?**  
R : Oui. Activez le VML avec `setSupportVml(true)` ; le SVG est géré automatiquement par Aspose.Words.

**Q : Comment chiffrer un document HTML sans utiliser de certificat numérique ?**  
R : Utilisez le constructeur `HtmlLoadOptions` qui accepte un mot de passe et enregistrez le document avec `Document.save(..., SaveFormat.HTML)` après avoir défini le mot de passe.

**Q : Que se passe‑t‑il si l’URI de base pointe vers un dossier inexistant ?**  
R : Aspose.Words lèvera une `FileNotFoundException` pour les ressources manquantes. Vérifiez le chemin avant le chargement.

**Q : Est‑il possible de changer le type de contrôle par défaut pour tous les éléments de formulaire HTML ?**  
R : Oui. Utilisez `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` pour l’appliquer globalement.

**Q : Les callbacks d’avertissement sont‑ils thread‑safe ?**  
R : L’implémentation du callback doit être thread‑safe si vous prévoyez de charger des documents en parallèle. Utilisez des collections synchronisées ou un stockage thread‑local.

---

**Dernière mise à jour :** 2026-02-06  
**Testé avec :** Aspose.Words for Java 25.3  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}