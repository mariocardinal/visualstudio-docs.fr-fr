---
title: "Proc&#233;dure pas &#224; pas&#160;: d&#233;boguer une feuille de style XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Proc&#233;dure pas &#224; pas&#160;: d&#233;boguer une feuille de style XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les étapes de cette procédure pas à pas montrent comment utiliser le débogueur XSLT.Elles comprennent l'affichage des variables, la définition de points d'arrêt et le parcours pas à pas du code.La feuille de style recherche tous les livres coûtant moins que le prix moyen du livre.  
  
### Pour vous préparer à cette procédure  
  
1.  Fermez les solutions ouvertes.  
  
2.  Copiez les deux fichiers exemples vers votre ordinateur local.  
  
## Lancement du débogage  
  
#### Pour lancer le débogage  
  
1.  Dans le menu **Fichier**, pointez sur **Ouvrir** et cliquez sur **Fichier**.  
  
2.  Recherchez le fichier belowAvg.xsl et cliquez sur **Ouvrir**.  
  
     La feuille de style s'ouvre dans l'éditeur XML.  
  
3.  Cliquez sur le bouton Parcourir \(**...**\) dans le champ **Entrée** de la fenêtre de propriétés du document.  
  
4.  Recherchez le fichier books.xml et cliquez sur **Ouvrir**.  
  
     Vous définissez ainsi le document source à utiliser pour la transformation XSLT.  
  
5.  Cliquez avec le bouton droit sur la balise de début `xsl:if`, pointez sur **Point d'arrêt** et cliquez sur **Insérer un point d'arrêt**.  
  
6.  Cliquez sur le bouton **Débogage XSLT** dans la barre d'outils de l'éditeur XML.  
  
 Le processus de débogage commence, ouvrant plusieurs nouvelles fenêtres utilisées par le débogueur.  
  
 Il existe deux fenêtres qui affichent le document d'entrée et la feuille de style.Le débogueur utilise ces fenêtres pour afficher l'état actuel de l'exécution.Le débogueur est positionné sur l'élément `xsl:if` de la feuille de style et sur le premier nœud book du fichier books.xml.  
  
 La fenêtre Variables locales affiche toutes les variables locales et leur valeur actuelle.Cela comprend les variables définies dans la feuille de style ainsi que celles que le débogueur utilise pour assurer le suivi des nœuds actuellement dans le contexte.  
  
 La fenêtre **Sortie XSLT** affiche la sortie de la transformation XSL.Cette fenêtre est distincte de la fenêtre **Sortie** de Visual Studio.  
  
## Fenêtre Espion  
  
#### Pour utiliser la fenêtre Espion  
  
1.  Dans le menu **Déboguer**, pointez sur **Fenêtres** et sur **Espion**, puis cliquez sur **Espion 1**.  
  
     La fenêtre Espion 1 s'affiche.  
  
2.  Entrez `$bookAverage` dans le champ **Nom** et appuyez sur ENTRÉE.  
  
     La valeur de la variable `$bookAverage` s'affiche dans la fenêtre.  
  
3.  Entrez `self::node()` dans le champ **Nom** et appuyez sur ENTRÉE.  
  
     `self::node()` est une expression XPath qui évalue le nœud de contexte actuel.La valeur de l'expression XPath `self::node()` est le premier nœud book.Cette valeur change à mesure que la transformation progresse.  
  
4.  Développez le nœud `self::node()`, puis le nœud `price`.  
  
     La valeur du prix du livre s'affiche et vous pouvez la comparer facilement à celle de `$bookAverage`.Puisque le prix du livre est inférieur à la moyenne, la condition `xsl:if` doit se vérifier.  
  
## Parcours du code pas à pas  
 Le débogueur permet d'exécuter le code ligne par ligne.  
  
#### Pour parcourir le code pas à pas  
  
1.  Appuyez sur **F5** pour continuer.  
  
     Puisque le premier nœud book répond à la condition `xsl:if`, il est ajouté à la fenêtre de sortie XSL.Le débogueur continue l'exécution jusqu'à ce qu'il se repositionne sur l'élément `xsl:if` de la feuille de style.Le débogueur est maintenant placé sur le deuxième nœud book dans le fichier books.xml.  
  
     Dans la fenêtre Espion1, la valeur `self::node()` devient le second nœud book.En examinant la valeur de l'élément price, vous pouvez constater que le prix est supérieur à la moyenne, donc la condition `xsl:if` ne doit pas se vérifier.  
  
2.  Appuyez sur **F5** pour continuer.  
  
     Puisque le second nœud book ne répond pas à la condition `xsl:if`, il n'est pas ajouté à la fenêtre de sortie XSL.Le débogueur continue l'exécution jusqu'à ce qu'il se repositionne sur l'élément `xsl:if` de la feuille de style.Le débogueur est maintenant placé sur le troisième nœud `book` dans le fichier books.xml.  
  
     Dans la fenêtre Espion1, la valeur `self::node()` devient le troisième nœud book.En examinant la valeur de l'élément `price`, vous pouvez constater que le prix est inférieur à la moyenne, donc la condition `xsl:if` doit se vérifier.  
  
3.  Appuyez sur **F5** pour continuer.  
  
     Puisque la condition `xsl:if` s'est vérifiée, le troisième livre est ajouté à la fenêtre de sortie XSL.Tous les livres du document XML ont été traités et le débogueur s'arrête.  
  
## Fichiers exemples  
 La procédure pas à pas utilise les deux fichiers suivants.  
  
### belowAvg.xsl  
  
```  
<?xml version='1.0'?>  
<xsl:stylesheet version="1.0"  
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:output method="xml" encoding="utf-8"/>  
  <xsl:template match="/">  
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>  
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>  
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>  
    <books>  
      <!--Books That Cost Below Average-->  
      <xsl:for-each select="/bookstore/book">  
        <xsl:if test="price < $bookAverage">  
          <xsl:copy-of select="."/>  
        </xsl:if>  
      </xsl:for-each>  
    </books>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### books.xml  
  
```  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database -->  
<bookstore>  
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">  
    <title>The Autobiography of Benjamin Franklin</title>  
    <author>  
      <first-name>Benjamin</first-name>  
      <last-name>Franklin</last-name>  
    </author>  
    <price>8.99</price>  
  </book>  
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">  
    <title>The Confidence Man</title>  
    <author>  
      <first-name>Herman</first-name>  
      <last-name>Melville</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">  
    <title>The Gorgias</title>  
    <author>  
      <name>Plato</name>  
    </author>  
    <price>9.99</price>  
  </book>  
</bookstore>  
```  
  
## Voir aussi  
 [Débogage XSLT](../xml-tools/debugging-xslt.md)