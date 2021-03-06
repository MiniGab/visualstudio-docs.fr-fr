---
title: 'Comment : accéder au jeu de couleurs et polices intégrées | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 180dc474b2458ec38a8a76ed8f931a592cf29225
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500093"
---
# <a name="how-to-access-the-built-in-fonts-and-color-ccheme"></a>Comment : accéder aux polices intégrées et des couleurs ccheme
L’environnement de développement intégré (IDE) Visual Studio a un jeu de polices et couleurs qui est associé à la fenêtre d’éditeur. Vous pouvez accéder à ce schéma via les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.

 Pour utiliser les polices intégrées et le jeu de couleurs, un VSPackage doit :

-   Définir une catégorie à utiliser avec le service de polices et couleurs par défaut.

-   S’inscrire à la catégorie avec le serveur de polices et couleurs par défaut.

-   Informez l’IDE qu’une fenêtre spécifique utilise les catégories et les éléments d’affichage intégrées à l’aide de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> interfaces.

 L’IDE utilise la catégorie résultant en tant que handle vers la fenêtre. Nom de la catégorie s’affiche dans le **afficher les paramètres de :** zone de liste déroulante dans le **polices et couleurs** page de propriétés.

## <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Pour définir une catégorie à l’aide de couleurs et polices intégrées

1.  Créer un GUID arbitraire.

     Ce GUID est utilisé pour identifier une catégorie. Cette catégorie réutilise la spécification de couleurs et de polices par défaut de l’IDE.

    > [!NOTE]
    >  Lors de la récupération des données de police et de couleur avec la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> ou autres interfaces, les VSPackages utiliser ce GUID pour référencer les informations intégrées.

2.  Nom de la catégorie doit être ajouté à une table de chaînes à l’intérieur les ressources du package Visual Studio (*.rc*) de fichiers, afin qu’elle peut être localisée en fonction des besoins lorsque affichés dans l’IDE.

     Pour plus d’informations, consultez [ajouter ou supprimer une chaîne](/cpp/windows/adding-or-deleting-a-string).

### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Pour inscrire une catégorie à l’aide de couleurs et polices intégrées

1.  Construire un type spécial d’entrée de Registre de catégorie dans l’emplacement suivant :

     *[HKLM\SOFTWARE\Microsoft \Visual Studio\\\<version de Visual Studio > \FontAndColors\\\<catégorie >*]

     *\<Catégorie >* est le nom non localisé de la catégorie.

2.  Remplir le Registre afin d’utiliser le jeu de couleurs et polices du stock avec quatre valeurs :

    |Name|Type|Données|Description|
    |----------|----------|----------|-----------------|
    |Category|REG_SZ|GUID|Un GUID arbitraire qui identifie une catégorie qui contient le schéma de police et couleur stock.|
    |Package|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Ce GUID est utilisé par tous les packages qui utilisent les configurations de couleur et de police par défaut.|
    |NameID|REG_DWORD|Id|L’ID de ressource d’un nom de catégorie localisable dans le VSPackage.|
    |ToolWindowPackage|REG_SZ|GUID|Le GUID de l’implémentation VSPackage le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.|

### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Pour lancer l’utilisation de polices fournis par le système et les couleurs

1.  Créez une instance de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interface dans le cadre de l’implémentation et de l’initialisation de la fenêtre.

2.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> méthode pour obtenir une instance de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> interface correspondant à l’actuel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> instance.

3.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> à deux reprises.

    -   Appeler une seule fois avec `VSEDITPROPID_ViewGeneral_ColorCategory`en tant qu’argument.

    -   Appeler une seule fois avec `VSEDITPROPID_ViewGeneral_FontCategory` en tant qu’argument.

     Cela définit et expose les services de polices et couleurs par défaut en tant que propriété de la fenêtre.

## <a name="example"></a>Exemple
 L’exemple suivant lance l’utilisation intégrées polices et couleurs.

```cpp
CComVariant vt;
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);
if (spPropCatContainer != NULL){
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,
                                                          &spPropContainer))){
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Utiliser des polices et couleurs](../extensibility/using-fonts-and-colors.md)
- [Obtenir des informations de police et de couleur pour la colorisation de texte](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Accès stockés des paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md)
- [Vue d’ensemble de police et de couleur](../extensibility/font-and-color-overview.md)