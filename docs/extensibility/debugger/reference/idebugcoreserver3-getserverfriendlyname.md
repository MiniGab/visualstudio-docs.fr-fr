---
title: IDebugCoreServer3::GetServerFriendlyName | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 811292ff5f7dd95e127e63d30bf14ee06269ff7d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107788"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Récupère un nom convivial pour le serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbstrName`  
 [out] Retourne un nom convivial pour le serveur.  
  
> [!NOTE]
>  L’appelant est responsable de la libération de la chaîne.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Pour les serveurs de l’utilisateur a lancé, le nom retourné par cette méthode est le nom complet du serveur. Pour les serveurs lancé automatiquement, le nom est que de l’ordinateur, le serveur s’exécute sur.  
  
 Pour un nom orientés machine, appelez le [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)