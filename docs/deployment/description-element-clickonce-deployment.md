---
title: '&lt;Description&gt; , élément (déploiement ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8985bc83299f55cec3c5f41fd3d76c8801fdf34
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079808"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Description&gt; , élément (déploiement ClickOnce)
Identifie les informations de l’application utilisées pour créer la présence d’un shell et un **Ajout / Suppression de programmes** élément dans le panneau de configuration.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `description` est obligatoire et se trouve dans l’espace de noms `urn:schemas-microsoft-com:asm.v1`. Il ne contient aucun élément enfant et a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`publisher`|Obligatoire. Identifie le nom de société utilisé pour la sélection élective d’icône dans le Windows **Démarrer** menu et le **Ajout / Suppression de programmes** élément dans le panneau de configuration, lorsque le déploiement est configuré pour l’installation.|  
|`product`|Obligatoire. Identifie le nom de produit complet. Utilisé en tant que le titre de l’icône installée dans le Windows **Démarrer** menu.|  
|`suiteName`|Facultatif. Identifie un sous-dossier dans le `publisher` dossier dans le Windows **Démarrer** menu.|  
|`supportUrl`|Facultatif. Spécifie une URL de prise en charge qui est indiquée dans le **Ajout / Suppression de programmes** élément dans le panneau de configuration. Un raccourci vers cette URL est également créé pour la prise en charge de l’application dans le Windows **Démarrer** menu, lorsque le déploiement est configuré pour l’installation.|  
  
## <a name="remarks"></a>Notes  
 L’élément description est requis dans toutes les configurations de déploiement.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre un `description` élément dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste de déploiement. Cet exemple de code fait partie d’un exemple plus complet fourni pour le [du manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md) rubrique.  
  
```xml  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)