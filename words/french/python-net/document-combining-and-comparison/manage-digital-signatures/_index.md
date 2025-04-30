---
"description": "Apprenez à gérer les signatures numériques et à garantir l'authenticité des documents avec Aspose.Words pour Python. Guide étape par étape avec code source."
"linktitle": "Gestion des signatures numériques et de l'authenticité"
"second_title": "API de gestion de documents Python Aspose.Words"
"title": "Gestion des signatures numériques et de l'authenticité"
"url": "/fr/python-net/document-combining-and-comparison/manage-digital-signatures/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Gestion des signatures numériques et de l'authenticité

## Introduction aux signatures numériques

Les signatures numériques sont l'équivalent électronique des signatures manuscrites. Elles permettent de vérifier l'authenticité, l'intégrité et l'origine des documents électroniques. Lorsqu'un document est signé numériquement, un hachage cryptographique est généré à partir de son contenu. Ce hachage est ensuite chiffré à l'aide de la clé privée du signataire, créant ainsi la signature numérique. Toute personne disposant de la clé publique correspondante peut vérifier la signature et s'assurer de l'authenticité du document.

## Configuration d'Aspose.Words pour Python

Pour commencer à gérer les signatures numériques à l’aide d’Aspose.Words pour Python, suivez ces étapes :

1. Installer Aspose.Words : Vous pouvez installer Aspose.Words pour Python en utilisant pip avec la commande suivante :
   
   ```python
   pip install aspose-words
   ```

2. Importez les modules requis : Importez les modules nécessaires dans votre script Python :
   
   ```python
   import aspose.words as aw
   ```

## Chargement et accès aux documents

Avant d'ajouter ou de vérifier les signatures numériques, vous devez charger le document à l'aide d'Aspose.Words :

```python
document = aw.Document("document.docx")
```

## Ajout de signatures numériques aux documents

Pour ajouter une signature numérique à un document, vous aurez besoin d'un certificat numérique :

```python
certificate_holder = aw.digitalsignatures.CertificateHolder.create("certificate.pfx", "password")
```

Maintenant, signez le document :

```python
aw.digitalsignatures.DigitalSignatureUtil.sign(MY_DIR + "Digitally signed.docx",
            ARTIFACTS_DIR + "Document.encrypted_document.docx", cert_holder, sign_options)
```

## Vérification des signatures numériques

Vérifiez l'authenticité d'un document signé à l'aide d'Aspose.Words :

```python
for signature in document.digital_signatures:
    if signature.is_valid:
        print("Signature is valid.")
    else:
        print("Signature is invalid.")
```

## Personnalisation de l'apparence de la signature numérique

Vous pouvez personnaliser l’apparence des signatures numériques :

```python
sign_options = aw.digitalsignatures.SignOptions()
sign_options.comments = 'Comment'
sign_options.sign_time = datetime.datetime.now()
```

## Conclusion

La gestion des signatures numériques et la garantie de l'authenticité des documents sont essentielles dans le paysage numérique actuel. Aspose.Words pour Python simplifie le processus d'ajout, de vérification et de personnalisation des signatures numériques, permettant ainsi aux développeurs d'améliorer la sécurité et la fiabilité de leurs documents.

## FAQ

### Comment fonctionnent les signatures numériques ?

Les signatures numériques utilisent la cryptographie pour générer un hachage unique basé sur le contenu du document, chiffré avec la clé privée du signataire.

### Un document signé numériquement peut-il être falsifié ?

Non, la falsification d’un document signé numériquement invaliderait la signature, indiquant des modifications potentiellement non autorisées.

### Plusieurs signatures peuvent-elles être ajoutées à un seul document ?

Oui, vous pouvez ajouter plusieurs signatures numériques à un même document, chacune provenant d’un signataire différent.

### Quels types de certificats sont compatibles ?

Aspose.Words prend en charge les certificats X.509, y compris les fichiers PFX, qui sont couramment utilisés pour les signatures numériques.

### Les signatures numériques sont-elles juridiquement valables ?

Oui, les signatures numériques sont juridiquement valables dans de nombreux pays et sont souvent considérées comme équivalentes aux signatures manuscrites.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}