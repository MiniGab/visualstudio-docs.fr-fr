---
title: IDiaStackWalkHelper::symbolForVA | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e70dac639f18f934bb997cc4979bdbe6a7d8c4c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31467535"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
Récupère le symbole qui contient l’adresse virtuelle spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `va`  
 [in] L’adresse virtuelle qui est contenue dans le symbole demandé. Le symbole doit être un `SymTagFunctionType` (une valeur à partir de la [symtagenum, énumération](../../debugger/debug-interface-access/symtagenum.md) énumération).  
  
 `ppSymbol`  
 [out] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objet qui représente le symbole à l’adresse spécifiée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)