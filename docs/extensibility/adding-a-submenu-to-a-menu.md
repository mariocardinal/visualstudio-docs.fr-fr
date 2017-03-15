---
title: "Ajout d&#39;un sous-menu &#224; un Menu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menus contextuels"
  - "sous-menus, en cascade"
  - "sous-menus en cascade"
  - "menus, création de sous-menus en cascade"
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 43
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 43
---
# Ajout d&#39;un sous-menu &#224; un Menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas s’appuie sur la démonstration de [Ajout d'un Menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) en montrant comment ajouter un sous\-menu à le **TestMenu** menu.  
  
 Un sous\-menu est un menu secondaire qui s’affiche dans un autre menu. Un sous\-menu peut être identifié par la flèche qui suit son nom. En cliquant sur le nom provoque le sous\-menu et ses commandes s’affiche.  
  
 Cette procédure pas à pas crée un sous\-menu dans un menu dans la barre de menus de Visual Studio et place une nouvelle commande dans le sous\-menu. La procédure pas à pas implémente également la nouvelle commande.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Ajout d’un sous\-menu à un Menu  
  
1.  Suivez les étapes de [Ajout d'un Menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) pour créer l’élément de menu et de projet. Les étapes de cette procédure pas à pas supposent que le nom du projet VSIX est `TopLevelMenu`.  
  
2.  Ouvrez TestCommandPackage.vsct. Dans la `<Symbols>` section, ajoutez un `<IDSymbol>` élément pour le sous\-menu, un pour le groupe de sous\-menu et un pour la commande, tout en la `<GuidSymbol>` nœud nommé « guidTopLevelMenuCmdSet ». Il s’agit du même nœud qui contient le `<IDSymbol>` élément de menu de niveau supérieur.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Ajouter le sous\-menu nouvellement créé pour le `<Menus>` section.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     La paire GUID ID du parent Spécifie le groupe de menu qui a été généré dans [Ajout d'un Menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), et est un enfant de menu de niveau supérieur.  
  
4.  Ajouter le groupe de menu défini à l’étape 2 dans la `<Groups>` section et faites\-en un enfant du sous\-menu.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Ajouter un nouveau `<Button>` élément à la `<Buttons>` section pour définir la commande créée à l’étape 2 en tant qu’élément dans le sous\-menu.  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6.  Générez la solution et démarrer le débogage. Vous devez voir l’instance expérimentale.  
  
7.  Cliquez sur **TestMenu** pour afficher un sous\-menu nommé **sous\-menu**. Cliquez sur **sous\-menu** d’une commande, ouvrez le sous\-menu **Test sous\-commande**. Notez qu’un clic sur **Test sous\-commande** n’a aucun effet.  
  
## Ajout d’une commande  
  
1.  Ouvrez TestCommand.cs et ajoutez l’ID de la commande suivante après l’ID de commande existant.  
  
    ```c#  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Ajoutez la commande secondaire. Recherchez le constructeur de la commande. Ajoutez les lignes suivantes juste après l’appel à la `AddCommand` \(méthode\).  
  
    ```c#  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     Le `SubItemCallback` Gestionnaire de commandes est défini ultérieurement. Le constructeur doit maintenant ressembler à ceci :  
  
    ```c#  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  Ajoutez SubItemCallback\(\). Il s’agit de la méthode est appelée lorsque l’utilisateur clique sur la nouvelle commande dans le sous\-menu.  
  
    ```c#  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4.  Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître.  
  
5.  Sur le **TestMenu** menu, cliquez sur **sous\-menu** puis **Test sous\-commande**. Une boîte de message doit apparaître et afficher le texte, « Test de commande à l’intérieur de TestCommand.SubItemCallback\(\) ».  
  
## Voir aussi  
 [Ajout d'un Menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md)