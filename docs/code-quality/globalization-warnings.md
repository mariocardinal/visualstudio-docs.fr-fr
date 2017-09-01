---
title: "Avertissements li&#233;s &#224; la globalisation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.globalizationrules"
helpviewer_keywords: 
  - "globalisation (Visual Studio), avertissements"
  - "avertissements liés à la globalisation"
  - "avertissements liés à l'analyse du code managé, avertissements liés à la globalisation"
  - "avertissements, globalisation"
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# Avertissements li&#233;s &#224; la globalisation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les avertissements liés à la globalisation prennent en charge des bibliothèques et des applications prêtes à la mise en pratique.  
  
## Dans cette section  
  
|Règle|Description|  
|-----------|-----------------|  
|[CA1300 : Spécifier MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md)|Pour afficher correctement une boîte de message pour les cultures qui utilisent un sens de lecture de droite à gauche, les membres RightAlign et RtlReading de l'énumération MessageBoxOptions doivent être passés à la méthode Show.|  
|[CA1301 : Éviter les accélérateurs en double](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|Une touche d'accès rapide, également connue sous le nom d'accélérateur, autorise l'accès à un contrôle par le biais du clavier, à l'aide de la touche ALT.  Lorsque plusieurs contrôles présentent des touches d'accès rapide en doublon, le comportement de ces dernières n'est pas correctement défini.|  
|[CA1302 : Ne pas coder en dur les chaînes spécifiques aux paramètres régionaux](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|L'énumération System.Environment.SpecialFolder contient des membres qui font référence à des dossiers système spéciaux.  Les emplacements de ces dossiers peuvent avoir des valeurs distinctes selon le système d'exploitation ; l'utilisateur peut modifier certains des emplacements, et ces derniers sont localisés.  La méthode Environment.GetFolderPath retourne les emplacements associés à l'énumération Environment.SpecialFolder, localisés et appropriés pour l'ordinateur en cours d'exécution.|  
|[CA1303 : Ne pas transmettre des littéraux en tant que paramètres localisés](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Une méthode visible de l'extérieur passe un littéral de chaîne en tant que paramètre à un constructeur ou une méthode dans la bibliothèque de classes du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ; en outre, cette chaîne doit être localisable.|  
|[CA1304 : Spécifier CultureInfo](../Topic/CA1304:%20Specify%20CultureInfo.md)|Une méthode ou un constructeur appelle un membre présentant une surcharge qui accepte un paramètre System.Globalization.CultureInfo, et la méthode ou le constructeur n'appelle pas la surcharge qui prend le paramètre CultureInfo.  Lorsqu'un objet CultureInfo ou System.IFormatProvider n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté selon les différents paramètres régionaux.|  
|[CA1305 : Spécifier IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)|Une méthode ou un constructeur appelle un ou plusieurs membres présentant des surcharges qui acceptent un paramètre System.IFormatProvider, et la méthode ou le constructeur n'appelle pas la surcharge qui prend le paramètre IFormatProvider.  Lorsqu'un objet System.Globalization.CultureInfo ou IFormatProvider n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté selon les différents paramètres régionaux.|  
|[CA1306 : Définir les paramètres régionaux pour les types de données](../code-quality/ca1306-set-locale-for-data-types.md)|Les paramètres régionaux déterminent des éléments de présentation des données spécifiques à la culture, telles que la mise en forme utilisée pour les valeurs numériques, les symboles monétaires et l'ordre de tri.  Lorsque vous créez un DataTable ou un DataSet, vous devez définir les paramètres régionaux explicitement.|  
|[CA1307 : Spécifier StringComparison](../code-quality/ca1307-specify-stringcomparison.md)|Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas de paramètre StringComparison.|  
|[CA1308 : Normaliser les chaînes en majuscules](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Les chaînes doivent être normalisées en majuscules.  En cas de conversion en minuscules, un petit groupe de caractères ne peut pas faire un aller\-retour.|  
|[CA1309 : Utiliser StringComparison avec la valeur Ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Opération de comparaison de chaînes non linguistique qui n'affecte pas la valeur Ordinal ou OrdinalIgnoreCase au paramètre StringComparison.  En affectant explicitement au paramètre la valeur StringComparison.Ordinal ou StringComparison.OrdinalIgnoreCase, votre code gagne souvent en rapidité, tout en devenant plus correct et plus fiable.|  
|[CA2101 : Spécifiez le marshaling pour les arguments de chaîne P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Un membre d'appel de code non managé autorise les appelants dotés d'un niveau de confiance partielle, présente un paramètre de chaîne et ne marshale pas explicitement la chaîne.  Cela peut provoquer une faille de sécurité potentielle.|