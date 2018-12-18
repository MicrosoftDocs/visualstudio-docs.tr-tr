---
title: Projeleri için genellikle kullanılan nesnelerin Catıdlerini | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57af657c888963dc9f33fc729678c0d8c82e0f0a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798514"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>Genişletme Projeleri için Genellikle Kullanılan Nesnelerin CATID’leri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıdaki tabloda genişletmek için kullanılan Catıdlerini `Project` ve `ProjectItem` Otomasyon nesneleri için [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], ve [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projeleri. Bu Catıdlerini VSLangProj.olb içinde tanımlanır.  
  
## <a name="listing-of-catids"></a>Catıdlerini listesi  
  
|Ad|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|  
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|  
  
## <a name="visual-basic-catids"></a>Visual Basic Catıdlerini  
 Aşağıdaki tabloda genişletmek için kullanılan Catıdlerini [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] nesneleri göz atın. Bunlar tüm VSLangProj.olb içinde tanımlanır.  
  
|Ad|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|  
  
## <a name="visual-c-catids"></a>Visual C# Catıdlerini  
 Aşağıdaki Catıdlerini genişletmek için kullanılan [!INCLUDE[csprcs](../../includes/csprcs-md.md)] nesneleri göz atın. Bunlar tüm VSLangProj.olb içinde tanımlanır.  
  
|Ad|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|  
  
## <a name="c-catids"></a>C++ Catıdlerini  
 Aşağıdaki [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] proje sistemi içindeki tür kitaplıklarında Catıdlerini gösterilmez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .NET 2003 ve bu proje nesnelerini genişletmek istediğinizde kodunuzda eklenmesi gerekir. Tür kitaplıkları sonraki sürümlerinde bu Catıdlerini dahil edilecek [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
|Ad|GUID|  
|----------|----------|  
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|  
  
 Aşağıdaki kod örneği, kodunuzda bu Catıdlerini program gösterilmiştir.  
  
```  
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 Aşağıdaki [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] proje sistemi Catıdlerini de gösterilmez tür kitaplıklarında, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .NET 2003 ve bu proje nesnelerini genişletmek istediğinizde kodunuzda eklenmesi gerekir. Yalnızca bu Catıdlerini kullanılabilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .NET 2003 ve sonraki sürümlerinde kullanılabilir olmayacak [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
|Ad|GUID|  
|----------|----------|  
|`CVCAssemblyReferenceNode` **:**|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|  
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|  
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|  
  
 Aşağıdaki kod örneği, kodunuzda bu Catıdlerini programı gösterilmektedir:  
  
```  
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";  
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";  
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 GUID'lerini [!INCLUDE[csprcs](../../includes/csprcs-md.md)] ve [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] proje türleri, aşağıdaki tabloda gösterilmiştir.  
  
|Proje türü|GUID|  
|------------------|----------|  
|[!INCLUDE[csprcs](../../includes/csprcs-md.md)]|{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}|  
|[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]|{F184B08F-C81C-45F6-A57F-5ABD9991F28F}|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Proje ve Öğe Şablonlarını Kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)

