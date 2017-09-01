---
title: "Procédure pas à pas : Création d’un kit de développement à l’aide de C++ | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 32
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d4458cb2cf0f3f198b2931beec15f8eead446ba6
ms.openlocfilehash: 3baf914755f0cdd4e0aa0a6c1405126faeec0364
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Procédure pas à pas : Création d’un kit de développement à l’aide de C++
Cette procédure pas à pas montre comment créer une bibliothèque C++ native mathématiques SDK, le package du Kit de développement logiciel comme un Visual Studio Extension (VSIX) et utilisez-le pour créer une application. La procédure pas à pas est divisée en comme suit :  
  
-   [Pour créer les natif et les bibliothèques Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Pour créer le projet d’extension NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Pour créer un exemple d’application qui utilise la bibliothèque de classes](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="a-namecreateclasslibrarya-to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Pour créer les natif et les bibliothèques Windows Runtime  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans la liste des modèles, développez **Visual C++**, **du Windows Store**, puis sélectionnez le **DLL (applications du Windows Store)** modèle. Dans le **nom** , spécifiez `NativeMath`, puis choisissez le **OK** bouton.  
  
3.  Mettre à jour NativeMath.h pour faire correspondre le code suivant.  
  
     [!code-cpp[CreatingAnSDKUsingCpp n °&1;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  NativeMath.cpp de mise à jour pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCpp n °&2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **Solution 'NativeMath'**, puis choisissez **ajouter**, **nouveau projet**.  
  
6.  Dans la liste des modèles, développez **Visual C++**, puis sélectionnez le **composant Windows Runtime** modèle. Dans le **nom** , spécifiez `NativeMathWRT`, puis choisissez le **OK** bouton.  
  
7.  Class1.h de mise à jour pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCpp n °&3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Class1.cpp de mise à jour pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCpp n °&4;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
##  <a name="a-namecreatevsixa-to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>Pour créer le projet d’extension NativeMathVSIX  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **Solution 'NativeMath'**, puis choisissez **ajouter**, **nouveau projet**.  
  
2.  Dans la liste des modèles, développez **Visual C#**, **extensibilité**, puis sélectionnez **Package VSIX**. Dans le **nom** , spécifiez **NativeMathVSIX**, puis choisissez le **OK** bouton.  
  
3.  Lorsque le Concepteur de manifeste VSIX apparaît, fermez-la.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **source.extension.vsixmanifest**, puis choisissez **afficher le Code**.  
  
5.  Utilisez le code XML suivant pour remplacer le document XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp n °&6;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

6.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **NativeMathVSIX** de projet, puis choisissez **ajouter**, **un nouvel élément**.  
  
7.  Dans la liste des **éléments Visual c#**, développez **données**, puis sélectionnez **fichier XML**. Dans le **nom** , spécifiez `SDKManifest.xml`, puis choisissez le **OK** bouton.  
  
8.  Utilisez ce code XML pour remplacer le contenu du fichier :  
  
     [!code-xml[CreatingAnSDKUsingCpp n °&5;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
9. Dans **l’Explorateur de solutions**, dans le **NativeMathVSIX** de projet, créez cette structure de dossiers :  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
10. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **Solution 'NativeMath'**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.  
  
11. Dans **Explorateur de fichiers**, copiez \NativeMath\NativeMath.h, puis dans **l’Explorateur de solutions**, dans le **NativeMathVSIX** project, collez-le dans le dossier \DesignTime\CommonConfiguration\Neutral\Include\.  
  
     Copiez \Debug\NativeMath\NativeMath.lib et collez-le dans le dossier \DesignTime\Debug\x86\.  
  
     Copiez \Debug\NativeMath\NativeMath.dll et collez-le dans le dossier \Redist\Debug\x86\.  
  
     Copiez DebugNativeMathWRTNativeMathWRT.dll et collez-le dans le dossier RedistDebugx86.  
  
     Copiez DebugNativeMathWRTNativeMathWRT.winmd et collez-le dans le dossier ReferencesCommonConfigurationNeutral.  
  
     Copiez DebugNativeMathWRTNativeMathWRT.pri et collez-le dans le dossier ReferencesCommonConfigurationNeutral.  
  
12. Dans le dossier \DesignTime\Debug\x86\, créez un fichier texte nommé NativeMathSDK.props, puis collez-y le contenu suivant :  
  
    [!code-xml[CreatingAnSDKUsingCpp&#7;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Dans la barre de menus, choisissez **affichage**, **autres fenêtres**, **fenêtre Propriétés** (clavier : appuyez sur la touche F4).  
  
14. Dans **l’Explorateur de solutions**, sélectionnez le **NativeMathWRT.winmd** fichier. Dans le **propriétés** fenêtre, modifier la **Action de génération** propriété **contenu**, puis modifiez le **inclure dans VSIX** propriété **True**.  
  
     Répétez ce processus pour le **SimpleMath.pri** fichier.  
  
     Répétez ce processus pour le **NativeMath.Lib** fichier.  
  
     Répétez ce processus pour le **NativeMathSDK.props** fichier.  
  
15. Dans **l’Explorateur de solutions**, sélectionnez le **NativeMath.h** fichier. Dans le **propriétés** fenêtre, modifier la **inclure dans VSIX** propriété **True**.  
  
     Répétez ce processus pour le **NativeMath.dll** fichier.  
  
     Répétez ce processus pour le **NativeMathWRT.dll** fichier.  
  
     Répétez ce processus pour le **SDKManifest.xml** fichier.  
  
16. Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
17. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **NativeMathVSIX** de projet, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.  
  
18. Dans **Explorateur de fichiers**, accédez au dossier \bin\Debug\, puis exécutez NativeMathVSIX.vsix pour commencer l’installation.  
  
19. Choisissez le **installer** bouton, attendez que l’installation se termine, puis redémarrez Visual Studio.  
  
##  <a name="a-namecreatesamplea-to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Pour créer un exemple d’application qui utilise la bibliothèque de classes  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans la liste des modèles, développez **Visual C++**, **du Windows Store**, puis sélectionnez **application vide**. Dans le **nom** , spécifiez **NativeMathSDKSample**, puis choisissez le **OK** bouton.  
  
3.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **NativeMathSDKSample** de projet, puis choisissez **ajouter**, **référence**.  
  
4.  Sur le **propriétés communes**, **structure et références** page de propriétés, dans la liste des types référence, développez **Windows**, puis sélectionnez **Extensions**. Dans le volet détails, sélectionnez le **natif mathématiques SDK** extension, puis choisissez le **ajouter une nouvelle référence** bouton.  
  
5.  Dans le **ajouter une référence** boîte de dialogue, sélectionnez le **natif mathématiques SDK** case à cocher, puis choisissez le **OK** bouton.  
  
6.  Afficher les propriétés du projet pour NativeMathSDKSample.  
  
     Les propriétés que vous avez définie dans NativeMathSDK.props ont été appliquées lorsque vous avez ajouté la référence. Vous pouvez le vérifier en examinant le **répertoires VC ++** propriété du projet **propriétés de Configuration**.  
  
7.  Dans **l’Explorateur de solutions**, ouvrez MainPage.xaml et utilisez le code XAML suivant pour remplacer son contenu :  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp n °&1;](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
8.  Mainpage.xaml.h de mise à jour pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp n °&2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
9. MainPage.xaml.cpp de mise à jour pour correspondre à ce code :  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp n °&3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
10. Appuyez sur la touche F5 pour exécuter l’application.  
  
11. Dans l’application, entrez les deux numéros, sélectionnez une opération, puis le ** = ** bouton.  
  
     Le résultat correct apparaît.  
  
 Cette procédure pas à pas vous a montré comment créer et utiliser un SDK d’Extension pour appeler un [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] bibliothèque et non -[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] bibliothèque.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création d’un kit de développement à l’aide de c# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Création d’un Kit de développement logiciel](../extensibility/creating-a-software-development-kit.md)