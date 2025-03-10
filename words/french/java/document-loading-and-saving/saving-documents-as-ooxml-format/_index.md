---
title: Enregistrement de documents au format OOXML dans Aspose.Words pour Java
linktitle: Enregistrement de documents au format OOXML
second_title: API de traitement de documents Java Aspose.Words
description: Découvrez comment enregistrer des documents au format OOXML avec Aspose.Words pour Java. Sécurisez, optimisez et personnalisez vos fichiers sans effort.
weight: 20
url: /fr/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrement de documents au format OOXML dans Aspose.Words pour Java


## Introduction à l'enregistrement de documents au format OOXML dans Aspose.Words pour Java

Dans ce guide, nous allons découvrir comment enregistrer des documents au format OOXML à l'aide d'Aspose.Words pour Java. OOXML (Office Open XML) est un format de fichier utilisé par Microsoft Word et d'autres applications bureautiques. Nous aborderons différentes options et paramètres pour enregistrer des documents au format OOXML.

## Prérequis

Avant de commencer, assurez-vous que la bibliothèque Aspose.Words pour Java est configurée dans votre projet.

## Enregistrer un document avec cryptage par mot de passe

Vous pouvez crypter votre document avec un mot de passe tout en l'enregistrant au format OOXML. Voici comment procéder :

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Charger le document
Document doc = new Document("Document.docx");

// Créez OoxmlSaveOptions et définissez le mot de passe
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Enregistrer le document avec cryptage
doc.save("EncryptedDoc.docx", saveOptions);
```

## Configuration de la conformité OOXML

Vous pouvez spécifier le niveau de conformité OOXML lors de l'enregistrement du document. Par exemple, vous pouvez le définir sur ISO 29500:2008 (Strict). Voici comment procéder :

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Charger le document
Document doc = new Document("Document.docx");

// Optimiser pour Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Créez OoxmlSaveOptions et définissez le niveau de conformité
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Enregistrer le document avec le paramètre de conformité
doc.save("ComplianceDoc.docx", saveOptions);
```

## Mise à jour de la propriété Heure de la dernière sauvegarde

Vous pouvez choisir de mettre à jour la propriété « Heure de la dernière sauvegarde » du document lors de son enregistrement. Voici comment procéder :

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Charger le document
Document doc = new Document("Document.docx");

// Créez OoxmlSaveOptions et activez la mise à jour de la propriété Last Saved Time
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Enregistrez le document avec la propriété mise à jour
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Conserver les caractères de contrôle hérités

Si votre document contient des caractères de contrôle hérités, vous pouvez choisir de les conserver lors de l'enregistrement. Voici comment procéder :

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//Charger un document avec des caractères de contrôle hérités
Document doc = new Document("LegacyControlChars.doc");

// Créez OoxmlSaveOptions avec le format FLAT_OPC et activez la conservation des caractères de contrôle hérités
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Enregistrer le document avec les caractères de contrôle hérités
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Réglage du niveau de compression

Vous pouvez ajuster le niveau de compression lors de l'enregistrement du document. Par exemple, vous pouvez le régler sur SUPER_FAST pour une compression minimale. Voici comment procéder :

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Charger le document
Document doc = new Document("Document.docx");

// Créez OoxmlSaveOptions et définissez le niveau de compression
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Enregistrez le document avec le niveau de compression spécifié
doc.save("FastCompressionDoc.docx", saveOptions);
```

Voici quelques-unes des options et paramètres clés que vous pouvez utiliser lors de l'enregistrement de documents au format OOXML à l'aide d'Aspose.Words pour Java. N'hésitez pas à explorer d'autres options et à personnaliser votre processus d'enregistrement de documents selon vos besoins.

## Code source complet pour l'enregistrement de documents au format OOXML dans Aspose.Words pour Java

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

Dans ce guide complet, nous avons exploré comment enregistrer des documents au format OOXML à l'aide d'Aspose.Words pour Java. Que vous ayez besoin de crypter vos documents avec des mots de passe, de garantir la conformité avec des normes OOXML spécifiques, de mettre à jour les propriétés du document, de conserver les caractères de contrôle hérités ou d'ajuster les niveaux de compression, Aspose.Words fournit un ensemble d'outils polyvalents pour répondre à vos besoins.

## FAQ

### Comment supprimer la protection par mot de passe d’un document protégé par mot de passe ?

Pour supprimer la protection par mot de passe d'un document protégé par mot de passe, vous pouvez ouvrir le document avec le mot de passe correct, puis l'enregistrer sans spécifier de mot de passe dans les options d'enregistrement. Cela enregistrera le document sans protection par mot de passe.

### Puis-je définir des propriétés personnalisées lors de l’enregistrement d’un document au format OOXML ?

 Oui, vous pouvez définir des propriétés personnalisées pour un document avant de l'enregistrer au format OOXML. Utilisez le`BuiltInDocumentProperties` et`CustomDocumentProperties` classes pour définir diverses propriétés telles que l'auteur, le titre, les mots-clés et les propriétés personnalisées.

### Quel est le niveau de compression par défaut lors de l'enregistrement d'un document au format OOXML ?

 Le niveau de compression par défaut lors de l'enregistrement d'un document au format OOXML à l'aide d'Aspose.Words pour Java est`NORMAL` . Vous pouvez modifier le niveau de compression pour`SUPER_FAST` ou`MAXIMUM` selon les besoins.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
