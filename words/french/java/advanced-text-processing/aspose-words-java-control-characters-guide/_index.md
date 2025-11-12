---
date: '2025-11-12'
description: Apprenez pas à pas comment insérer des sauts de page, des tabulations,
  des espaces insécables et des mises en page à plusieurs colonnes avec Aspose.Words
  for Java – boostez votre automatisation de documents dès aujourd'hui.
keywords:
- how to insert control characters
- add page break java
- manage carriage return aspose
- insert non breaking space
- create multi column layout
- Aspose.Words control characters
- Java document formatting
- text layout automation
- document generation Java
- Aspose.Words API
language: fr
title: Insérer des caractères de contrôle avec Aspose.Words pour Java
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer des caractères de contrôle avec Aspose.Words pour Java

## Pourquoi les caractères de contrôle sont importants dans les documents Java
Lorsque vous générez des factures, des rapports ou des newsletters de façon programmatique, la mise en page précise du texte est incontournable. Les caractères de contrôle tels que **page breaks**, **tabs** et **non‑breaking spaces** vous permettent de déterminer exactement où le contenu apparaît sans intervention manuelle. Dans ce tutoriel, vous verrez comment gérer ces caractères avec l’API Aspose.Words for Java, afin que vos documents aient un aspect professionnel dès leur première création.

**Ce que vous allez réaliser dans ce guide**
1. Insérer et vérifier les retours chariot, sauts de ligne et sauts de page.  
2. Ajouter des espaces, des tabulations et des espaces insécables pour aligner le texte.  
3. Créer des mises en page à plusieurs colonnes à l’aide de sauts de colonne.  
4. Appliquer des conseils de performance pour les documents volumineux.

## Prérequis
Avant de commencer, assurez‑vous d’avoir les éléments suivants :

| Exigence | Détails |
|----------|---------|
| **Aspose.Words for Java** | Version 25.3 ou ultérieure (l’API est compatible rétroactivement). |
| **JDK** | 8 ou supérieur. |
| **IDE** | IntelliJ IDEA, Eclipse ou tout autre IDE Java de votre choix. |
| **Outil de construction** | Maven **ou** Gradle pour la gestion des dépendances. |
| **Licence** | Un fichier de licence Aspose.Words temporaire ou acheté (`aspose.words.lic`). |

### Checklist de configuration de l’environnement
1. Installez Maven **ou** Gradle.  
2. Ajoutez la dépendance Aspose.Words (voir la section suivante).  
3. Placez votre fichier de licence dans un emplacement sécurisé et notez le chemin d’accès.

## Ajout d’Aspose.Words à votre projet

### Maven
Insérez le fragment suivant dans votre `pom.xml` :

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle
Ajoutez cette ligne à `build.gradle` :

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Initialisation de la licence
Après avoir obtenu une licence, initialisez‑la au démarrage de votre application :

```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **Note :** Sans licence, la bibliothèque fonctionne en mode d’évaluation, ce qui ajoute des filigranes.

## Guide d’implémentation

Nous couvrirons deux fonctionnalités principales : **gestion du retour chariot** et **insertion de divers caractères de contrôle**. Chaque fonctionnalité est découpée en étapes numérotées, et un court paragraphe explicatif précède chaque bloc de code.

### Fonctionnalité 1 – Gestion du retour chariot et du saut de page
Les caractères de contrôle comme `ControlChar.CR` (retour chariot) et `ControlChar.PAGE_BREAK` définissent le flux logique d’un document. L’exemple suivant montre comment vérifier que ces caractères sont correctement placés.

#### Étape par étape

1. **Créer un nouveau Document et DocumentBuilder**  
   L’objet `Document` est le conteneur de tout le contenu ; `DocumentBuilder` fournit une API fluide pour ajouter du texte.

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **Insérer deux paragraphes simples**  
   Chaque appel à `writeln` ajoute automatiquement un saut de paragraphe.

   ```java
   builder.writeln("Hello world!");
   builder.writeln("Hello again!");
   ```

3. **Construire la chaîne attendue avec les caractères de contrôle**  
   Nous utilisons `MessageFormat` pour intégrer `ControlChar.CR` et `ControlChar.PAGE_BREAK` dans le texte attendu.

   ```java
   String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
           MessageFormat.format("Hello again!{0}", ControlChar.CR) +
           ControlChar.PAGE_BREAK;
   assert doc.getText().equals(expectedTextWithCR) :
           "Text does not match expected value with control characters.";
   ```

4. **Supprimer les espaces superflus du texte du document et re‑valider**  
   Le `trim` élimine les espaces blancs en fin de texte tout en conservant les sauts de ligne intentionnels.

   ```java
   String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
   assert doc.getText().trim().equals(expectedTrimmedText) :
           "Trimmed text does not match expected value.";
   ```

> **Résultat :** Les assertions confirment que la représentation interne du texte du document contient exactement les retours chariot et le saut de page attendus.

### Fonctionnalité 2 – Insertion de divers caractères de contrôle
Explorons maintenant comment intégrer des espaces, des tabulations, des sauts de ligne, des sauts de paragraphe et des sauts de colonne directement dans un document.

#### Étape par étape

1. **Initialiser un nouveau DocumentBuilder**  
   Partir d’un document vierge garantit que les exemples restent isolés.

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **Insérer les caractères liés aux espaces**  

   *Caractère d’espace (`ControlChar.SPACE_CHAR`)*  
   ```java
   builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
   ```

   *Espace insécable (`ControlChar.NON_BREAKING_SPACE`)*  
   ```java
   builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
   ```

   *Caractère de tabulation (`ControlChar.TAB`)*  
   ```java
   builder.write("Before tab." + ControlChar.TAB + "After tab.");
   ```

3. **Ajouter des sauts de ligne et de paragraphe**  

   *Le saut de ligne crée une nouvelle ligne au sein du même paragraphe.*  
   ```java
   // Verify that we start with a single paragraph
   Assert.assertEquals(1, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());

   builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");

   // After inserting a line feed, a second paragraph should appear
   Assert.assertEquals(2, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());
   ```

   *Saut de paragraphe (`ControlChar.PARAGRAPH_BREAK`)*  
   ```java
   builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
   Assert.assertEquals(3, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());
   ```

   *Saut de section (`ControlChar.SECTION_BREAK`)*  
   ```java
   builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
   assert doc.getSections().getCount() == 1 :
           "Section count mismatch after section break.";
   ```

4. **Créer une mise en page à plusieurs colonnes avec un saut de colonne**  

   Tout d’abord, ajoutez une seconde section et activez deux colonnes :

   ```java
   doc.appendChild(new Section(doc));
   builder.moveToSection(1);
   builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);
   ```

   Puis insérez un saut de colonne pour déplacer le contenu de la colonne 1 vers la colonne 2 :

   ```java
   builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
   ```

> **Résultat :