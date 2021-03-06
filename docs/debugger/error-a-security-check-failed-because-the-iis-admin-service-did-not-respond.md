---
title: 'Erreur : Une vérification de sécurité a échoué, car le Service IIS Admin n’a pas répondu | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f307e84f5267036e480ab1ec8118c32ee632bff
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058059"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Erreur : une vérification de la sécurité a échoué, car le service de l'administration IIS n'a pas répondu
Cette erreur se produit lorsque le service IIS Admin ne répond pas. Il s'agit généralement d'un problème relatif à l'installation IIS. Tout d’abord, vérifiez que le service est en cours d’exécution à l’aide de la **Services** à partir de l’outil **outils d’administration**.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Réinstallez IIS, à l’aide de la **Ajout / Suppression de programmes** le panneau de configuration.  
  
-   - ou -  
  
-   Supprimez IIS de votre ordinateur, à l’aide de l’application Ajout/Suppression de programmes du Panneau de configuration. Si vous avez supprimé IIS et que les problèmes persistent, examinez le Registre et assurez-vous que cette clé n'existe plus :  
  
    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`  
  
     - ou -  
  
-   Désactivez le service de l’administration IIS, à l’aide du panneau de configuration Outils d’administration. Cela permet de désactiver IIS sur votre ordinateur.  
  
     Après avoir exécuté l'une de ces trois opérations, redémarrez votre ordinateur.  
  
     Pour plus d'informations, consultez la documentation IIS.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)