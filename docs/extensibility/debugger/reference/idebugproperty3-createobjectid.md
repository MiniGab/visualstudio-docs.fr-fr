---
title: IDebugProperty3::CreateObjectID | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: df4e45c442745652b3305fd91146bd31ffe79e4b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120973"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Crée un ID unique pour cette propriété pour vous assurer qu’il est unique parmi toutes les autres propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée lorsque le Gestionnaire de session de débogage veut s’assurer que cette propriété est identifiée de manière unique parmi toutes les autres propriétés. Le moteur de débogage (DE) prend en charge cette méthode, sauf si les propriétés qu’il traite sont déjà identifiées. Si le DE ne gère pas cette méthode, elle retourne `E_NOTIMPL`.  
  
 Un ID unique créé avec `CreateObjectID` est détruit lorsque le [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) méthode est appelée ; cela signale également à la fin de la nécessité d’identifiant de manière unique cette propriété.  
  
> [!NOTE]
>  Il n’existe aucune méthode pour récupérer cet identificateur unique, donc le DE faire quoi pour les ID uniques lors de la `CreateObjectID` méthode est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)