---
title: 'Débogage ASP.NET : Configuration requise | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a0d591c9f68e5331b2047ee749fff148c8844937
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466368"
---
# <a name="aspnet-debugging-system-requirements"></a>Débogage ASP.NET : configuration requise
Cette rubrique décrit les conditions de sécurité et les logiciels requis pour les scénarios de débogage de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] :  
  
-   Débogage local, dans lequel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et l'application Web s'exécutent sur le même ordinateur. Il y a deux versions de ce scénario :  
  
    -   Le code [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] réside sur le système de fichiers.  
  
    -   Le code de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] réside sur un site Web IIS.  
  
-   Débogage distant, dans lequel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] s'exécute sur un ordinateur client et débogue une application Web qui s'exécute sur un ordinateur de serveur distant.  
  
## <a name="security-requirements"></a>Conditions de sécurité  
 Pour le débogage distant, les ordinateurs locaux et distants doivent être sur une installation de domaine ou une installation de groupe de travail.  
  
 Pour déboguer le [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] le processus de travail (hébergé par un Pool d’applications), vous devez être autorisé à déboguer ce processus. Par défaut, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] applications IIS 6.0 avant de les exécutent en tant que le **ASPNET** utilisateur. Dans IIS 6.0 et IIS 7.0, le **SERVICE réseau** compte est la valeur par défaut. Si le processus de traitement s'exécute en tant qu' **ASPNET**ou que **SERVICE RÉSEAU**, vous devez disposer de droits d'administrateur pour le déboguer.

 > [!IMPORTANT]
 > À compter de Windows Server 2008 R2, nous recommandons l’utilisation de la [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) comme identité pour chaque pool d’applications.
  
 Le nom du processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] varie en fonction du scénario de débogage et de la version d'IIS. Pour plus d'informations, consultez [Comment : rechercher le nom du processus ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Vous pouvez changer le compte d'utilisateur sous lequel s'exécute le processus de travail [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en modifiant le fichier machine.config sur le serveur qui exécute IIS. La meilleure façon de procéder consiste à utiliser le **Gestionnaire IIS**. Pour plus d’informations, consultez [Comment : exécuter le travail processus sous un compte d’utilisateur](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Si vous modifiez le processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pour qu'il s'exécute sous votre propre compte d'utilisateur, vous n'avez pas besoin d'être administrateur sur le serveur qui exécute IIS.  
  
> [!CAUTION]
>  Avant de modifier le processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pour qu'il s'exécute sous un compte différent, envisagez les conséquences que pourrait avoir un piratage du processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] lors de son exécution sous ce compte. Les comptes d'utilisateur ASPNET et SERVICE RÉSEAU s'exécutent avec des autorisations minimales, réduisant les dommages possibles en cas de piratage du processus. Si vous devez modifier le processus de traitement [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pour qu'il s'exécute sous un compte qui a des autorisations supérieures, le risque de dommage est accru.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’Applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Guide pratique pour exécuter le processus Worker sous un compte d’utilisateur](../debugger/how-to-run-the-worker-process-under-a-user-account.md)