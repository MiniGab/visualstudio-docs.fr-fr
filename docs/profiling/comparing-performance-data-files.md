---
title: "Comparaison des fichiers de données de performances | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9a0b4dcb86aa4241d223dd4a1172267dd8ec20da
ms.lasthandoff: 02/22/2017

---
# <a name="comparing-performance-data-files"></a>Comparaison des fichiers de données de performances
La fonctionnalité de comparaison de fichiers de données des outils de profilage permet de sélectionner deux fichiers de rapport (.VSP et/ou .VSP) et de générer un rapport montrant les différences, les régressions de performances et les améliorations qui se sont produites entre deux sessions de profilage.  
  
 Dans un rapport de comparaison de fichiers de données des outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], les résultats d’une analyse d’un fichier de données de profilage sont comparés aux résultats d’une analyse de base de référence d’un autre fichier de données. Les deux fichiers de données doivent avoir été générés à l’aide de la même méthode de profilage. Le rapport des comparaisons analysées est enregistré dans un fichier .vsps.  
  
 La vue du rapport de comparaison présente les données modifiées sous la forme d’un tableau. Le tableau présente les données delta, c’est-à-dire ce qui a été modifié par rapport à la base de référence. Les données delta sont calculées en déterminant la différence entre l’ancienne valeur, la valeur de base de référence et la valeur résultant de la nouvelle analyse.  
  
 Les comparaisons des données du profileur peuvent être basées sur les fonctions du code, les modules de l’application, les lignes, les pointeurs d’instruction et les types.  
  
 Les données de profilage qui peuvent être utilisées pour la comparaison comprennent des informations qui sont affichées dans les colonnes. Pour plus d’informations sur les définitions de ces noms de colonnes, consultez [Vues Rapport de performances](../profiling/performance-report-views.md).  
  
 Vous pouvez définir un seuil pour réduire le bruit et exclure de l’affichage les lignes du tableau de comparaison dont la valeur n’a pas changé de manière significative.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour comparer des fichiers de données de performances](../profiling/how-to-compare-performance-data-files.md)