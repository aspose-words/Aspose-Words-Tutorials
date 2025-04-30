---
"description": "Apprenez à utiliser les objets OLE et les contrôles ActiveX dans Aspose.Words pour Java. Créez facilement des documents interactifs. Commencez dès maintenant !"
"linktitle": "Utilisation d'objets OLE et de contrôles ActiveX"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Utilisation des objets OLE et des contrôles ActiveX dans Aspose.Words pour Java"
"url": "/fr/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilisation des objets OLE et des contrôles ActiveX dans Aspose.Words pour Java

Dans ce tutoriel, nous découvrirons comment utiliser les objets OLE (Object Linking and Embedding) et les contrôles ActiveX dans Aspose.Words pour Java. Les objets OLE et les contrôles ActiveX sont des outils puissants qui vous permettent d'améliorer vos documents en intégrant ou en liant du contenu externe, comme des feuilles de calcul, des fichiers multimédias ou des contrôles interactifs. Suivez-nous pour explorer les exemples de code et apprendre à utiliser efficacement ces fonctionnalités.

### Prérequis

Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :

1. Aspose.Words pour Java : Assurez-vous que la bibliothèque Aspose.Words est installée dans votre projet Java. Vous pouvez la télécharger ici. [ici](https://releases.aspose.com/words/java/).

2. Environnement de développement Java : vous devez disposer d’un environnement de développement Java fonctionnel configuré sur votre système.

### Insertion d'un objet OLE

Commençons par insérer un objet OLE dans un document Word. Nous allons créer un document Word simple, puis insérer un objet OLE représentant une page web.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlfile", vrai, vrai, nul);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

Dans ce code, nous créons un nouveau document et insérons un objet OLE affichant le site web Aspose. Vous pouvez remplacer l'URL par le contenu souhaité.

### Insertion d'un objet OLE avec OlePackage

Voyons maintenant comment insérer un objet OLE à l'aide d'un OlePackage. Cela vous permet d'intégrer des fichiers externes sous forme d'objets OLE dans votre document.

```java
@Test
public void insertOleObjectWithOlePackage() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    byte[] bs = FileUtils.readFileToByteArray(new File("Your Directory Path" + "Zip file.zip"));
    try (ByteArrayInputStream stream = new ByteArrayInputStream(bs))
    {
        Shape shape = builder.insertOleObject(stream, "Package", true, null);
        OlePackage olePackage = shape.getOleFormat().getOlePackage();
        olePackage.setFileName("filename.zip");
        olePackage.setDisplayName("displayname.zip");
        doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
    }
}
```

Dans cet exemple, nous insérons un objet OLE à l'aide d'un OlePackage, vous permettant d'inclure des fichiers externes en tant qu'objets incorporés.

### Insertion d'un objet OLE en tant qu'icône

Voyons maintenant comment insérer un objet OLE comme icône. Ceci est utile pour afficher une icône représentant un fichier incorporé.

```java
@Test
public void insertOleObjectAsIcon() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObjectAsIcon("Your Directory Path" + "Presentation.pptx", false, getImagesDir() + "Logo icon.ico", "My embedded file");
    doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
}
```

Dans ce code, nous insérons un objet OLE sous forme d’icône, offrant une représentation visuellement plus attrayante du contenu intégré.

### Lecture des propriétés du contrôle ActiveX

Passons maintenant aux contrôles ActiveX. Nous allons apprendre à lire les propriétés des contrôles ActiveX dans un document Word.

```java
@Test
public void readActiveXControlProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "ActiveX controls.docx");
    String properties = "";
    for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true))
    {
        if (shape.getOleFormat() == null) break;
        OleControl oleControl = shape.getOleFormat().getOleControl();
        if (oleControl.isForms2OleControl())
        {
            Forms2OleControl checkBox = (Forms2OleControl) oleControl;
            properties = properties + "\nCaption: " + checkBox.getCaption();
            properties = properties + "\nValue: " + checkBox.getValue();
            properties = properties + "\nEnabled: " + checkBox.getEnabled();
            properties = properties + "\nType: " + checkBox.getType();
            if (checkBox.getChildNodes() != null)
            {
                properties = properties + "\nChildNodes: " + checkBox.getChildNodes();
            }
            properties += "\n";
        }
    }
    properties = properties + "\nTotal ActiveX Controls found: " + doc.getChildNodes(NodeType.SHAPE, true).getCount();
    System.out.println("\n" + properties);
}
```

Dans ce code, nous parcourons les formes d’un document Word, identifions les contrôles ActiveX et récupérons leurs propriétés.

### Conclusion

Félicitations ! Vous avez appris à utiliser les objets OLE et les contrôles ActiveX dans Aspose.Words pour Java. Ces fonctionnalités ouvrent un monde de possibilités pour la création de documents dynamiques et interactifs.

### FAQ

### Quel est le but des objets OLE dans un document Word ? 
   - Les objets OLE vous permettent d'intégrer ou de lier du contenu externe, tel que des fichiers ou des pages Web, dans un document Word.

### Puis-je personnaliser l’apparence des objets OLE dans mon document ? 
   - Oui, vous pouvez personnaliser l’apparence des objets OLE, y compris la définition des icônes et des noms de fichiers.

### Que sont les contrôles ActiveX et comment peuvent-ils améliorer mes documents ? 
   - Les contrôles ActiveX sont des éléments interactifs qui peuvent ajouter des fonctionnalités à vos documents Word, tels que des contrôles de formulaire ou des lecteurs multimédias.

### Aspose.Words pour Java est-il adapté à l’automatisation des documents au niveau de l’entreprise ? 
   - Oui, Aspose.Words pour Java est une bibliothèque puissante pour automatiser la génération et la manipulation de documents dans les applications Java.

### Où puis-je accéder à Aspose.Words pour Java ? 
   - Vous pouvez télécharger Aspose.Words pour Java à partir de [ici](https://releases.aspose.com/words/java/).

Commencez dès aujourd’hui avec Aspose.Words pour Java et exploitez tout le potentiel de l’automatisation et de la personnalisation des documents !



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}