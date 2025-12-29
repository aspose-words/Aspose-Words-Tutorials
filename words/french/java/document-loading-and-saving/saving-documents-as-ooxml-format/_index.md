---
date: 2025-12-29
description: Apprenez à chiffrer les fichiers docx avec un mot de passe en utilisant
  les options d’enregistrement d’Aspose.Words pour Java. Sécurisez, optimisez et personnalisez
  vos fichiers OOXML sans effort.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Comment chiffrer un DOCX avec un mot de passe en utilisant Aspose.Words pour
  Java
url: /fr/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comment chiffrer un DOCX avec un mot de passe à l'aide d'Aspose.Words pour Java

Dans ce guide, vous découvrirez **comment chiffrer un docx avec un mot de passe** lors de l’enregistrement de documents au format OOXML avec Aspose.Words pour Java. Que vous protégiez des rapports confidentiels ou sécurisiez des projets de contrat, les étapes ci‑dessous montrent exactement comment appliquer la protection par mot de passe et affiner d’autres options d’enregistrement OOXML.

## Réponses rapides
- **Puis‑je chiffrer un fichier DOCX avec un mot de passe ?** Oui, utilisez `OoxmlSaveOptions.setPassword()` avant d’enregistrer.  
- **Quelle classe contrôle les paramètres d’enregistrement OOXML ?** `OoxmlSaveOptions` (fait partie d’Aspose.Words).  
- **Ai‑je besoin d’une licence pour la protection par mot de passe ?** Une licence valide d’Aspose.Words est requise pour une utilisation en production.  
- **Puis‑je combiner le chiffrement avec les paramètres de conformité ?** Absolument – définissez à la fois `setPassword` et `setCompliance` sur la même instance de `OoxmlSaveOptions`.  
- **Quels niveaux de compression sont disponibles ?** `NORMAL`, `SUPER_FAST` et `MAXIMUM` via `CompressionLevel`.

## Qu’est‑ce que « encrypt docx with password » ?
Chiffrer un fichier DOCX signifie que le contenu du fichier est stocké sous forme cryptée et ne peut être ouvert qu’après avoir fourni le mot de passe correct. Cela protège les informations sensibles contre tout accès non autorisé tout en permettant aux outils Word standards d’ouvrir le fichier une fois le mot de passe saisi.

## Pourquoi utiliser les options d’enregistrement d’Aspose.Words pour le chiffrement ?
Aspose.Words propose un ensemble riche d’**aspose words save options** qui vous permettent de contrôler non seulement le chiffrement, mais aussi les niveaux de conformité, la compression et la gestion des caractères de contrôle hérités – le tout depuis le code Java. Cela élimine le besoin de post‑traitement manuel ou d’outils tiers.

## Prérequis
- Java Development Kit (JDK 8 ou supérieur)  
- Bibliothèque Aspose.Words pour Java ajoutée à votre projet (Maven/Gradle ou JAR)  
- Une licence valide d’Aspose.Words pour la production (facultatif pour l’évaluation)

## Enregistrement d’un document avec chiffrement par mot de passe

Vous pouvez chiffrer votre document avec un mot de passe lors de son enregistrement au format OOXML. Voici comment procéder :

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

## Définir la conformité OOXML

Vous pouvez spécifier le niveau de conformité OOXML lors de l’enregistrement du document. Par exemple, vous pouvez le régler sur ISO 29500:2008 (Strict). Voici comment :

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## Mettre à jour la propriété « Last Saved Time »

Vous pouvez choisir de mettre à jour la propriété « Last Saved Time » du document lors de l’enregistrement. Voici comment :

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Conserver les caractères de contrôle hérités

Si votre document contient des caractères de contrôle hérités, vous pouvez choisir de les conserver lors de l’enregistrement. Voici comment :

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Définir le niveau de compression

Vous pouvez ajuster le niveau de compression lors de l’enregistrement du document. Par exemple, vous pouvez le régler sur **SUPER_FAST** pour une compression minimale. Voici comment :

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

Voici quelques‑unes des options clés que vous pouvez utiliser lors de l’enregistrement de documents au format OOXML avec Aspose.Words pour Java. N’hésitez pas à explorer d’autres options et à personnaliser votre processus d’enregistrement selon vos besoins.

## Code source complet pour enregistrer des documents au format OOXML avec Aspose.Words pour Java

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## Conclusion

Dans ce guide complet, nous avons exploré comment **encrypt docx with password** et affiné une gamme d’options d’enregistrement OOXML à l’aide d’Aspose.Words pour Java. Que vous ayez besoin de protéger du contenu confidentiel, de respecter une conformité ISO stricte, de préserver des caractères hérités ou de contrôler la compression, la bibliothèque vous offre un contrôle granulaire via la même API `OoxmlSaveOptions`.

## Questions fréquentes

**Q : Comment supprimer la protection par mot de passe d’un document protégé ?**  
R : Ouvrez le document avec le mot de passe correct, puis enregistrez‑le à nouveau sans appeler `setPassword`. Le nouveau fichier sera non protégé.

**Q : Puis‑je définir des propriétés personnalisées lors de l’enregistrement d’un document au format OOXML ?**  
R : Oui. Utilisez `BuiltInDocumentProperties` ou `CustomDocumentProperties` sur l’objet `Document` avant d’appeler `save`.

**Q : Quel est le niveau de compression par défaut lors de l’enregistrement d’un document au format OOXML ?**  
R : Le défaut est `NORMAL`. Vous pouvez passer à `SUPER_FAST` pour la rapidité ou à `MAXIMUM` pour réduire la taille du fichier.

**Q : Les aspose words save options fonctionnent‑elles avec les anciennes versions de Word ?**  
R : Oui. En ajustant `MsWordVersion` et les paramètres de conformité, vous pouvez cibler Word 2007‑2019 et garantir la compatibilité.

**Q : Est‑il possible de combiner plusieurs options d’enregistrement en une seule opération ?**  
R : Absolument. Créez une instance `OoxmlSaveOptions`, définissez toutes les propriétés souhaitées (mot de passe, conformité, compression, etc.) et transmettez‑la à `doc.save()`.

---

**Dernière mise à jour :** 2025-12-29  
**Testé avec :** Aspose.Words pour Java 24.12  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}