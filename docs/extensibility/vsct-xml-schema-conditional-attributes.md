---
title: Attributs conditionnels du schéma XML VSCT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b31b99e38eeec2ff1e5e31bc6bdaeed3d3be3d83
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586819"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Attributs conditionnels du schéma XML VSCT
Vous pouvez appliquer des attributs conditionnels pour toutes les listes et les éléments. Opérateurs logiques et les expressions d’expansion symbole équivalente à true ou false. Si la valeur est true, la liste associée ou l’élément est inclus dans la sortie résultante.  
  
 Vous pouvez tester les expansions de jeton par rapport à d’autres extensions de jeton ou des constantes. La fonction `Defined()` teste si un nom particulier a été défini, même si elle n’a aucune valeur.  
  
 Lorsqu’un attribut Condition est appliqué à une liste, la condition est appliquée à chaque élément enfant dans la liste. Si un élément enfant lui-même contient un attribut de Condition, sa condition est combinée avec l’expression parent par une opération AND.  
  
 Les valeurs 1, « 1 » et « trues » sont évaluées comme true et 0, '0' et 'false' sont évaluées comme false.  
  
## <a name="operators"></a>Opérateurs  
 Utilisez les opérateurs suivants pour évaluer des expressions conditionnelles.  
  
|Opérateur|Définition|  
|--------------|----------------|  
|(,)|Regroupement|  
|!|Opérateur NOT logique|  
|\<, >, \<=, >=, ==, !=|Opérateurs relationnels et opérateurs d'égalité|  
|et|Booléen|  
|ou|Booléen|  
  
## <a name="examples"></a>Exemples  
  
```xml  
<Menu Condition="Defined(DEBUG)" ...  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" ...  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu ...  
        </Menu>  
    </Menus>  
  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Table de commande Visual Studio (. Fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)