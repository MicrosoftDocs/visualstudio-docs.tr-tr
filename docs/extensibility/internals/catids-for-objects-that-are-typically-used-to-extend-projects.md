---
title: Projeleri genişletmek için genellikle kullanılan nesneler için CATIDs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf67b12288408feebebff2c33f525713416d4990
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742839"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>Projeleri genişletmek için genellikle kullanılan nesneler için CATIDs
Aşağıdaki tabloda `Project` `ProjectItem` [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] , ve projeleri için nesneleri genişletmek ve otomasyon Için kullanılan catids listelenmiştir [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] . Bu CATIDs, *VSLangProj. olb*içinde tanımlanmıştır.

## <a name="listing-of-catids"></a>CATIDs listesi

|Name|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|

## <a name="visual-basic-catids"></a>Visual Basic CATIDs
 Aşağıdaki tabloda, tarama nesnelerini genişletmek için kullanılan CATIDs listelenmiştir [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . Hepsi *VSLangProj. olb*içinde tanımlanmıştır.

|Name|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|

## <a name="visual-c-catids"></a>Visual C# CATIDs
 Aşağıdaki CATIDs 'Ler, gezinme nesnelerini genişletmek için kullanılabilir [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . Hepsi *VSLangProj. olb*içinde tanımlanmıştır.

|Name|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|

## <a name="c-catids"></a>C++ CATIDs
 Aşağıdaki [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Proje sistemi CATIDs, .net 2003 ' deki tür kitaplıklarında gösterilmez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve bu proje nesnelerini genişletmek istediğiniz her seferinde kodunuza dahil edilmemelidir. Bu CATIDs, daha sonraki sürümlerindeki tür kitaplıklarına dahil edilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

|Name|GUID|
|----------|----------|
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|

 Aşağıdaki kod örneği, kodunuzda bu CATIDs 'nin nasıl çalıştığını gösterir.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Aşağıdaki [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Proje sistemi kasaları ayrıca .net 2003 ' deki tür kitaplıklarında gösterilmez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve bu proje nesnelerini genişletmek istediğiniz her seferinde kodunuza dahil edilmemelidir. Bu CATIDs yalnızca .NET 2003 ' de kullanılabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve sonraki sürümlerinde kullanılamaz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

|Name|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|

 Aşağıdaki kod örneği, kodunuzda bu CATIDs 'nin nasıl programlanacağını göstermektedir:

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]Ve proje türleri Için GUID 'ler [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Aşağıdaki tabloda gösterilmiştir.

| Proje türü | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>Ayrıca bkz.
- [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Proje ve öğe şablonlarını Kaydet](../../extensibility/internals/registering-project-and-item-templates.md)
