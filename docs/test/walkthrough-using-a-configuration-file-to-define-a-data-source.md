---
title: "Proc&#233;dure pas &#224; pas&#160;: utilisation d&#39;un fichier de configuration pour d&#233;finir une source de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fichiers de configuration (Visual Studio ALM), définir des sources de données"
  - "sources de données, définir avec des fichiers de configuration"
  - "tests unitaires, procédure pas à pas"
ms.assetid: 95fa5214-b12e-4e1f-84e5-cc4c2d86b0d7
caps.latest.revision: 32
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 32
---
# Proc&#233;dure pas &#224; pas&#160;: utilisation d&#39;un fichier de configuration pour d&#233;finir une source de donn&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas illustre comment utiliser une source de données définie dans un fichier app.config pour des tests unitaires.  Vous apprendrez à créer un fichier app.config qui définit une source de données pouvant être utilisée par la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.  Cette procédure pas à pas illustre les tâches suivantes :  
  
-   création d'un fichier app.config ;  
  
-   définition d'une section de configuration personnalisée ;  
  
-   définition de chaînes de connexion ;  
  
-   définition des sources de données ;  
  
-   accès aux sources de données à l'aide de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Visual Studio Enterprise  
  
-   Microsoft Access ou Microsoft Excel afin de fournir des données pour au moins l'une des méthodes de test.  
  
-   Une solution Visual Studio qui contient un projet de test.  
  
## Créer le fichier app.config  
  
#### Pour ajouter un fichier app.config au projet  
  
1.  Si votre projet de test a déjà un fichier app.config, accédez à [Définir une section de configuration personnalisée](#DefineCustomConfigurationSection).  
  
2.  Cliquez avec le bouton droit sur votre projet de test dans l'**Explorateur de solutions**, pointez sur **Ajouter**, puis cliquez sur **Nouvel élément**.  
  
     La fenêtre **Ajouter un nouvel élément** s'ouvre.  
  
3.  Sélectionnez le modèle **Fichier de configuration de l'application**, puis cliquez sur **Ajouter**.  
  
##  <a name="DefineCustomConfigurationSection"></a> Définir une section de configuration personnalisée  
 Examinez le fichier app.config.  Il contient au moins la déclaration XML et un élément racine.  
  
#### Pour ajouter la section de configuration personnalisée au fichier app.config  
  
1.  L'élément racine d'app.config doit être l'élément `configuration`.  Créez un élément `configSections` dans l'élément `configuration`.  `configSections` doit être le premier élément du fichier app.config.  
  
2.  Dans l'élément `configSections`, créez un élément `section`.  
  
3.  Dans l'élément `section`, ajoutez un attribut nommé `name` et assignez\-lui une valeur égale à `microsoft.visualstudio.testtools`.  Ajoutez un autre attribut nommé `type` et assignez\-lui une valeur égale à `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
 L'élément `section` doit être similaire à ce qui suit :  
  
```  
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>  
```  
  
> [!NOTE]
>  Le nom de l'assembly doit correspondre à la version de Microsoft Visual Studio .NET Framework que vous utilisez.  Définissez la version 9.0.0.0 si vous utilisez Visual Studio .NET Framework 3.5.  Si vous utilisez Visual Studio .NET Framework 2.0, définissez la version 8.0.0.0.  
  
## Définir des chaînes de connexion  
 Les chaînes de connexion définissent des informations spécifiques au fournisseur pour accéder aux sources de données.  Les chaînes de connexion définies dans les fichiers de configuration fournissent des informations sur le fournisseur de données réutilisables dans une application.  Dans cette section, vous créez deux chaînes de connexion qui seront utilisées par des sources de données définies dans la section de configuration personnalisée.  
  
#### Pour définir des chaînes de connexion  
  
1.  Après l'élément `configSections`, créez un élément `connectionStrings`.  
  
2.  Dans l'élément `connectionStrings`, créez deux éléments `add`.  
  
3.  Dans le premier élément `add`, créez les attributs et valeurs suivants pour une connexion à une base de données Microsoft Access :  
  
|Attribut|Valeurs|  
|--------------|-------------|  
|`name`|`"MyJetConn"`|  
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|  
|`providerName`|`"System.Data.OleDb"`|  
  
 Dans le deuxième élément `add`, créez les attributs et valeurs suivants pour une connexion à une feuille de calcul Microsoft Excel :  
  
|||  
|-|-|  
|`name`|`"MyExcelConn"`|  
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|  
|`providerName`|`"System.Data.Odbc"`|  
  
 L'élément `connectionStrings` doit être similaire à ce qui suit :  
  
```  
<connectionStrings>  
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
</connectionStrings>  
```  
  
## Définir des sources de données  
 La section de sources de données contient quatre attributs utilisés par le moteur de test pour récupérer des données à partir d'une source de données.  
  
-   `name` définit l'identité utilisée par <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> pour spécifier la source de données à utiliser.  
  
-   `connectionString` identifie la chaîne de connexion créée dans la section précédente, Définir des chaînes de connexion.  
  
-   `dataTableName` définit la table ou la feuille qui contient les données à utiliser dans le test.  
  
-   `dataAccessMethod` définit la technique d'accès aux valeurs de données dans la source de données.  
  
 Dans cette section, vous définirez deux sources de données à utiliser dans un test unitaire.  
  
#### Pour définir des sources de données  
  
1.  Après l'élément `connectionStrings`, créez un élément `microsoft.visualstudio.testtools`.  Cette section a été créée dans Définir une section de configuration personnalisée.  
  
2.  Dans l'élément `microsoft.visualstudio.testtools`, créez un élément `dataSources`.  
  
3.  Dans l'élément `dataSources`, créez deux éléments `add`.  
  
4.  Dans le premier élément `add`, créez les attributs et valeurs suivants pour une source de données Microsoft Access :  
  
|Attribut|Valeurs|  
|--------------|-------------|  
|`name`|`"MyJetDataSource"`|  
|`connectionString`|`"MyJetConn"`|  
|`dataTableName`|`"MyDataTable"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 Dans le deuxième élément `add`, créez les attributs et valeurs suivants pour une source de données Microsoft Excel :  
  
|||  
|-|-|  
|`Name`|`"MyExcelDataSource"`|  
|`connectionString`|`"MyExcelConn"`|  
|`dataTableName`|`"Sheet1$"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 L'élément `microsoft.visualstudio.testtools` doit être similaire à ce qui suit :  
  
```  
<microsoft.visualstudio.testtools>  
    <dataSources>  
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
    </dataSources>  
</microsoft.visualstudio.testtools>  
```  
  
 Le fichier app.config final doit ressembler à ceci :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>   
    </configSections>  
    <connectionStrings>  
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
    </connectionStrings>  
    <microsoft.visualstudio.testtools>  
        <dataSources>  
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
        </dataSources>  
    </microsoft.visualstudio.testtools>  
</configuration>  
```  
  
## Créer un test unitaire à l'aide de sources de données définies dans app.config  
 Maintenant qu'un fichier app.config a été défini, vous allez créer un test unitaire qui utilise des données situées dans les sources de données définies dans le fichier app.config.  Dans cette section, nous allons :  
  
-   créer les sources de données du fichier app.config ;  
  
-   utiliser les sources de données dans deux méthodes de test qui comparent les valeurs dans chaque source de données.  
  
#### Pour créer une source de données Microsoft Access  
  
1.  Créez une base de données Microsoft Access nommée `testdatasource.accdb`.  
  
2.  Créez une table et nommez\-la `MyDataTable` dans `testdatasource.accdb`.  
  
3.  Créez deux champs dans `MyDataTable` nommés `Arg1` et `Arg2` à l'aide du type de données `Number`.  
  
4.  Ajoutez cinq entités à `MyDataTable` avec les valeurs suivantes pour `Arg1` et `Arg2`, respectivement : \(10,50\), \(3,2\), \(6,0\), \(0,8\) et \(12312,1000\).  
  
5.  Enregistrez et fermez la base de données.  
  
6.  Modifiez la chaîne de connexion de sorte qu'elle pointe vers l'emplacement de la base de données.  Modifiez la valeur de `Data Source` pour refléter l'emplacement de la base de données.  
  
#### Pour créer une source de données Microsoft Excel  
  
1.  Créez une feuille de calcul Microsoft Excel nommée `data.xlsx`.  
  
2.  Créez une feuille nommée `Sheet1` si elle n'existe pas déjà dans `data.xlsx`.  
  
3.  Créez deux en\-têtes de colonnes et nommez\-les `Val1` et `Val2` dans `Sheet1`.  
  
4.  Ajoutez cinq entités à `Sheet1` avec les valeurs suivantes pour `Val1` et `Val2`, respectivement : \(1,1\), \(2,2\), \(3,3\), \(4,4\) et \(5,0\).  
  
5.  Enregistrez et fermez la feuille de calcul.  
  
6.  Modifiez la chaîne de connexion de sorte qu'elle pointe vers l'emplacement de la feuille de calcul.  Modifiez la valeur de `dbq` pour refléter l'emplacement de la feuille de calcul.  
  
#### Pour créer un test unitaire à l'aide des sources de données app.config  
  
1.  Ajoutez un test unitaire au projet de test.  
  
     Pour plus d'informations, consultez [Creating and Running Unit Tests for Existing Code](http://msdn.microsoft.com/fr-fr/e8370b93-085b-41c9-8dec-655bd886f173).  
  
2.  Remplacez le contenu généré automatiquement du test unitaire par le code suivant :  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.TestTools.UnitTesting;  
  
    namespace TestProject1  
    {  
         [TestClass]  
        public class UnitTest1  
        {  
            private TestContext context;  
  
            public TestContext TestContext  
            {  
                get { return context; }  
                set { context = value; }  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]  
            [DataSource("MyJetDataSource")]  
            public void MyTestMethod()  
            {  
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());  
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());  
                Assert.AreNotEqual(a, b, "A value was equal.");  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\data.xlsx")]  
            [DataSource("MyExcelDataSource")]  
            public void MyTestMethod2()  
            {  
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);  
            }  
        }  
    }  
    ```  
  
3.  Examinez les attributs DataSource.  Notez les noms des paramètres à partir du fichier app.config.  
  
4.  Générez votre solution et exécutez les tests MyTestMethod et MyTestMethod2.  
  
> [!IMPORTANT]
>  Déployez des éléments tels que des sources de données de sorte qu'ils soient accessibles au test dans le répertoire de déploiement.  
  
## Voir aussi  
 [Tests unitaires sur votre code](../test/unit-test-your-code.md)   
 [Creating and Running Unit Tests for Existing Code](http://msdn.microsoft.com/fr-fr/e8370b93-085b-41c9-8dec-655bd886f173)   
 [Test de l'application](/devops-test-docs/test/test-apps-early-and-often)   
 [Comment : créer un test unitaire piloté par des données](../test/how-to-create-a-data-driven-unit-test.md)