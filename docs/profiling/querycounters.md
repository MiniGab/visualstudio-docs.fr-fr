---
title: QueryCounters | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f3c3176ea0b865ecf4a433a7a0a22a316720229
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257707"
---
# <a name="querycounters"></a>QueryCounters
L’option **/QueryCounters** répertorie les compteurs de performances (matériels) de l’UC qui sont disponibles sur l’ordinateur.  
  
 **QueryCounters** doit être la seule option sur la ligne de commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 Quand vous utilisez la méthode d’instrumentation, le profileur peut collecter les valeurs d’un ou plusieurs compteurs de performances de l’UC à chaque événement de collecte de données. Quand vous utilisez la méthode de profilage par échantillonnage, vous pouvez spécifier un événement de compteur et le nombre d’occurrences de l’événement à utiliser comme intervalle d’échantillonnage.  
  
 Les différents processeurs exposent des compteurs de performances d’UC différents. Le profileur définit un ensemble de compteurs génériques qui peuvent être utilisés sur presque tous les processeurs. L’option **QueryCounters** répertorie les noms des compteurs génériques et les noms des compteurs qui sont spécifiques au processeur.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profiler des services](../profiling/command-line-profiling-of-services.md)