---
title: "CreateItem, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
caps.latest.revision: 15
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: a9eb48e8c695c92a68e75f17cea31d887dfb439d
ms.lasthandoff: 02/22/2017

---
# <a name="createitem-task"></a>CreateItem, tâche
Remplit des collections d’éléments avec les éléments d’entrée. Cela permet de copier des éléments d’une liste à une autre.  
  
> [!NOTE]
>  Cette tâche est dépréciée. À compter du .NET Framework 3.5, les groupes d’éléments peuvent être placés dans des éléments [Target](../msbuild/target-element-msbuild.md). Pour plus d’informations, consultez l’article [Éléments MSBuild](../msbuild/msbuild-items.md).  
  
## <a name="attributes"></a>Attributs  
 Le tableau ci-dessous décrit les paramètres de la tâche `CreateItem`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AdditionalMetadata`|Paramètres de tableau `String` facultatif.<br /><br /> Spécifie des métadonnées supplémentaires à attacher aux éléments de sortie.  Spécifiez le nom et la valeur des métadonnées de l’élément avec la syntaxe suivante :<br /><br /> *nom_métadonnées* `=` *valeur_métadonnées*<br /><br /> Plusieurs paires nom/valeur de métadonnées doivent être séparées par un point-virgule. Si le nom ou la valeur contient un point-virgule ou tout autre caractère spécial, ils doivent être échappés. Pour plus d’informations, consultez [Guide pratique pour utiliser des caractères spéciaux d’échappement dans MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les éléments à exclure de la collection d’éléments de sortie. Ce paramètre peut contenir des spécifications de caractères génériques. Pour plus d’informations, consultez [Éléments](../msbuild/msbuild-items.md) et [Guide pratique pour exclure des fichiers de la build](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les éléments à inclure dans la collection d’éléments de sortie. Ce paramètre peut contenir des spécifications de caractères génériques.|  
|`PreserveExistingMetadata`|Paramètre `Boolean` facultatif.<br /><br /> Si `True`, appliquer uniquement les métadonnées supplémentaires si elles n’existent pas.|  
  
## <a name="remarks"></a>Notes  
 Outre les paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle-même de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez l’article [TaskExtension Base Class (Classe de base TaskExtension)](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant crée une collection d’éléments nommée `MySourceItemsWithMetadata` à partir de la collection d’éléments `MySourceItems`. La tâche `CreateItem` remplit la nouvelle collection d’éléments avec les éléments contenus dans l’élément `MySourceItems`. Elle ajoute ensuite une entrée de métadonnées supplémentaire nommée `MyMetadata` avec la valeur `Hello` à chaque élément de la nouvelle collection.  
  
 Une fois la tâche exécutée, la collection d’éléments `MySourceItemsWithMetadata` contient les éléments `file1.resx` et `file2.resx`, tous deux avec des entrées de métadonnées pour `MyMetadata`. La collection d’éléments `MySourceItems` est inchangée.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceItems Include="file1.resx;file2.resx" />  
    </ItemGroup>  
  
    <Target Name="NewItems">  
        <CreateItem  
            Include="@(MySourceItems)"  
            AdditionalMetadata="MyMetadata=Hello">  
           <Output  
               TaskParameter="Include"  
               ItemName="MySourceItemsWithMetadata"/>  
        </CreateItem>  
  
    </Target>  
  
</Project>  
```  
  
 Le tableau suivant décrit la valeur de l’élément de sortie après l’exécution de la tâche. Les métadonnées de l’élément sont affichées entre parenthèses après l’élément.  
  
|Collection d'éléments.|Sommaire|  
|---------------------|--------------|  
|`MySourceItemsWithMetadata`|`file1.resx` (`MyMetadata="Hello"`)<br /><br /> `file2.resx` (`MyMetadata="Hello"`)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des tâches](../msbuild/msbuild-task-reference.md)   
 [Tâches](../msbuild/msbuild-tasks.md)