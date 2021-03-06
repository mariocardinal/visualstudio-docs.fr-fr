---
title: "ResumeProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ResumeProfile"
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ResumeProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La méthode `ResumeProfile` décrémente le compteur de Suspend\/Resume pour le niveau de profilage spécifié.  
  
## Syntaxe  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### Paramètres  
 `Level`  
  
 Indique le niveau de profil auquel la collection de données de performance peut être appliquée.  Les énumérateurs **PROFILE\_CONTROL\_LEVEL** suivants permettent d'indiquer l'un des trois niveaux auxquels la collection des données de performance peut être appliquée :  
  
|Enumerator|Description|  
|----------------|-----------------|  
|PROFILE\_GLOBALLEVEL|Le paramètre de niveau global affecte tous les processus et threads dans l'exécution du profilage.|  
|PROFILE\_PROCESSLEVEL|Le paramètre au niveau du processus affecte tous les threads qui font partie du processus spécifié.|  
|PROFILE\_THREADLEVEL|Le paramètre au niveau du profilage du thread affecte le thread spécifié.|  
  
 `dwId`  
  
 Identificateur de processus ou de thread généré par le système.  
  
## Valeur de propriété\/valeur de retour  
 La fonction indique la réussite ou l'échec en utilisant l'énumération **PROFILE\_COMMAND\_STATUS**.  La valeur de retour peut être l'une des suivantes :  
  
|Enumerator|Description|  
|----------------|-----------------|  
|PROFILE\_ERROR\_ID\_NOEXIST|L'ID de l'élément de profilage n'existe pas.|  
|PROFILE\_ERROR\_LEVEL\_NOEXIST|Le niveau de profilage spécifié n'existe pas.|  
|PROFILE\_ERROR\_MODE\_NEVER|La valeur NEVER a été affectée au mode de profilage lors de l'appel à la fonction.|  
|PROFILE\_ERROR\_NOT\_YET\_IMPLEMENTED|L'appel de la fonction de profilage, le niveau de profilage ou une combinaison de l'appel et du niveau n'est pas encore implémenté.|  
|PROFILE\_OK|L'appel a réussi.|  
  
## Notes  
 La valeur initiale du compteur Suspend\/Resume est 0.  Chaque appel à SuspendProfile ajoute 1 au nombre de Suspend\/Resume ; chaque appel à ResumeProfile enlève 1.  
  
 Lorsque le nombre de Suspend\/Resume est supérieur ou égal à 0, l'état Suspend\/Resume du niveau est OFF.  Lorsque le nombre est inférieur ou égal à 0, l'état de Suspend\/Resume est ON.  
  
 Lorsque l'état Start\/Stop et l'état Suspend\/Resume sont tous deux ON, l'état de profilage du niveau est ON.  Pour qu'un thread soit profilé, les états au niveau global, du processus et du thread doivent être ON.  
  
## Équivalent .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Informations sur la fonction  
 En\-tête : déclaré dans VSPerf.h  
  
 Importez la bibliothèque : VSPerf.lib  
  
## Exemple  
 L'exemple suivant illustre la fonction ResumeProfile.  L'exemple suppose qu'un appel à la méthode SuspendProfile a été effectué pour le même thread ou processus identifié par [PROFILE\_CURRENTID](../profiling/profile-currentid.md).  
  
```  
void ExerciseResumeProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.   
    // Each call to SuspendProfile adds 1 to the Suspend/Resume   
    // count; each call to ResumeProfile subtracts 1.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call to ResumeProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = ResumeProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("ResumeProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## Voir aussi  
 [Référence des API du profileur Visual Studio \(Native\)](../profiling/visual-studio-profiler-api-reference-native.md)