---
title: METADATA_ADDRESS_LOCAL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 720f150be1b7cf992f0949750dd52218939c7d2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125516"
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL
Cette structure représente l’adresse d’une variable locale dans une portée (généralement une fonction ou méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## <a name="terms"></a>Termes  
 tokMethod  
 L’ID de la méthode ou la fonction de la variable locale fait partie.  
  
 (C++) `_mdToken` est un `typedef` pour 32 bits `int`.  
  
 pLocal  
 Le jeton dont l’adresse de cette structure représente.  
  
 dwIndex  
 Peut être l’index de cette variable locale dans la méthode, une fonction ou une autre valeur (spécifique à la langue).  
  
## <a name="remarks"></a>Notes  
 Cette structure est la partie de l’union dans la [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lors de la structure la `dwKind` champ le `DEBUG_ADDRESS_UNION` structure est définie sur `ADDRESS_KIND_LOCAL` (une valeur à partir de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).  
  
 `Warning:` (C++ uniquement)  Si `pLocal` n’est pas null, vous devez l’appeler `Release` sur le pointeur de jeton (`addr` est un champ dans le [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure) :  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)