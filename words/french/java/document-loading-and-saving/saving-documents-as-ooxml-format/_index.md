---
date: 2026-01-09
description: Apprenez comment chiffrer les fichiers docx avec un mot de passe et modifier
  le niveau de compression lors de l’enregistrement des documents au format OOXML
  à l’aide d’Aspose.Words pour Java.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Chiffrer un docx avec un mot de passe – Enregistrement OOXML avec Aspose.Words
  Java
url: /fr/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chiffrer un docx avec un mot de passe – Enregistrement OOXML avec Aspose.Words Java

## Introduction à l'enregistrement des documents au format OOXML avec Aspose.Words pour Java

Dans ce guide, vous apprendrez comment **chiffrer un docx avec un mot de passe** et enregistrer des documents au format OOXML en utilisant Aspose.Words pour Java. OOXML (Office Open XML) est le format de fichier moderne utilisé par Microsoft Word et de nombreuses autres applications bureautiques. Nous passerons en revue les options les plus courantes — protection par mot de passe, niveaux de conformité, mise à jour des propriétés, gestion des caractères hérités, et **comment changer le niveau de compression** — afin que vous puissiez adapter la sortie à vos besoins précis.

## Quick Answers
- **Comment puis‑je protéger un fichier Word ?** Utilisez `OoxmlSaveOptions.setPassword("yourPassword")` avant d’enregistrer.  
- **Quel niveau de conformité OOXML devrais‑je choisir ?** ISO 29500 2008 Strict pour une compatibilité maximale avec les versions modernes d’Office.  
- **Puis‑je conserver les caractères de contrôle hérités ?** Oui, activez `setKeepLegacyControlChars(true)`.  
- **Comment changer le niveau de compression ?** Définissez `setCompressionLevel(CompressionLevel.SUPER_FAST)` ou `MAXIMUM` selon les besoins.  
- **Ces options affectent‑elles la taille du fichier ?** Le niveau de compression et la gestion des caractères hérités peuvent modifier de façon notable la taille finale du .docx.

## What is “encrypt docx with password”?
Chiffrer un fichier DOCX signifie que le document est enregistré avec un chiffrement AES‑256, nécessitant un mot de passe pour l’ouvrir dans Word ou tout visualiseur compatible. Cela est essentiel pour protéger les informations confidentielles lorsque les fichiers sont partagés par e‑mail, stockage cloud ou portails intranet.

## Why use OOXML saving options?
- **Sécurité :** La protection par mot de passe empêche l’accès non autorisé.  
- **Compatibilité :** Les paramètres de conformité garantissent que le fichier fonctionne sur différentes versions de Word.  
- **Performance :** Ajuster la compression peut accélérer l’enregistrement ou réduire la taille du fichier.  
- **Préservation :** Conserver les caractères de contrôle hérités maintient la fidélité lors de la conversion de documents anciens.

## Prerequisites
- Bibliothèque Aspose.Words pour Java ajoutée à votre projet (Maven/Gradle ou JAR manuel).  
- Java 8 ou supérieur.  
- Un document source (`.docx` ou `.doc`) que vous souhaitez traiter.

## Saving a Document with Password Encryption

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

> **Astuce :** Choisissez un mot de passe robuste et conservez‑le en lieu sûr ; le mot de passe ne peut pas être récupéré à partir du fichier chiffré.

## Setting OOXML Compliance

Vous pouvez spécifier le niveau de conformité OOXML lors de l’enregistrement du document. Par exemple, vous pouvez le définir sur ISO 29500:2008 (Strict). Voici comment :

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

## Updating Last Saved Time Property

Vous pouvez choisir de mettre à jour la propriété « Last Saved Time » du document lors de son enregistrement. Voici comment :

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

## Keeping Legacy Control Characters

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

## How to Change Compression Level When Saving OOXML

Vous pouvez ajuster le niveau de compression lors de l’enregistrement du document. Par exemple, vous pouvez le définir sur `SUPER_FAST` pour une compression minimale ou `MAXIMUM` pour la plus petite taille de fichier. Voici comment :

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

Voici quelques-unes des options et paramètres clés que vous pouvez utiliser lors de l’enregistrement de documents au format OOXML avec Aspose.Words pour Java. N’hésitez pas à explorer davantage d’options et à personnaliser votre processus d’enregistrement de documents selon vos besoins.

## Complete Source Code For Saving Documents as OOXML Format in Aspose.Words for Java

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

Dans ce guide complet, nous avons exploré comment **chiffrer un docx avec un mot de passe** et enregistrer des documents au format OOXML en utilisant Aspose.Words pour Java. Que vous ayez besoin de protéger vos fichiers, d’assurer une conformité OOXML stricte, de mettre à jour les propriétés du document, de préserver les caractères de contrôle hérités, ou de **modifier le niveau de compression**, Aspose.Words offre un ensemble d’outils polyvalents pour répondre à vos exigences.

## Frequently Asked Questions

**Q: Comment supprimer la protection par mot de passe d’un document protégé ?**  
R: Ouvrez le document avec le mot de passe correct, puis enregistrez‑le sans spécifier de mot de passe dans `OoxmlSaveOptions`. Cela crée une copie non protégée.

**Q: Puis‑je définir des propriétés personnalisées lors de l’enregistrement d’un document au format OOXML ?**  
R: Oui. Utilisez `BuiltInDocumentProperties` et `CustomDocumentProperties` sur l’objet `Document` avant d’appeler `save()`.

**Q: Quel est le niveau de compression par défaut lors de l’enregistrement d’un document au format OOXML ?**  
R: Le défaut est `CompressionLevel.NORMAL`. Vous pouvez passer à `SUPER_FAST` pour la rapidité ou à `MAXIMUM` pour la plus petite taille de fichier.

**Q: L’activation de `keepLegacyControlChars` affectera‑t‑elle la compatibilité avec les versions modernes de Word ?**  
R: Word moderne peut ouvrir les fichiers contenant des caractères de contrôle hérités, mais certaines fonctionnalités anciennes peuvent s’afficher différemment. Utilisez cette option uniquement lorsque vous devez préserver le contenu original exact.

**Q: Est‑il possible de combiner plusieurs options d’enregistrement (par ex., mot de passe + compression) en un seul appel ?**  
R: Absolument. Configurez toutes les propriétés souhaitées sur une seule instance de `OoxmlSaveOptions` avant de la passer à `doc.save()`.

---

**Last Updated:** 2026-01-09  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}