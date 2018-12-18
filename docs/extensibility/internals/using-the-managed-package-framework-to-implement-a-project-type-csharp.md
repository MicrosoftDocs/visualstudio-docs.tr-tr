---
title: Yönetilen paket çerçevesini kullanarak proje türü için (C#) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1317fd507d1efaeb40fac0220c94d6ddf51b2c5
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902702"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Yönetilen Paket Çerçevesini Kullanarak Proje Türü Uygulama (C#)
Yönetilen paket Framework (MPF) kullanabilir veya kendi proje türleri uygulamak için devralınan C# sınıfları sağlar. MPF Visual Studio sağlamak için bir proje türü bekliyor arabirimlerin çoğu proje türünüz Bununla uygulamaya odaklanmasına olanak boş bırakarak uygular.  
  
## <a name="using-the-mpf-project-source-code"></a>MPF proje kaynak kodunu kullanarak  
 Projeleri (MPFProj) için yönetilen paket çerçevesini oluşturmak ve yeni proje sistemi yönetmek için yardımcı sınıflar sağlar. MPF diğer sınıflardan farklı olarak, proje sınıfları Visual Studio ile birlikte gelen derlemeleri dahil değildir. Bunun yerine, kaynak kodu olarak proje sınıfları sağlanan [projeleri 2013'ün MPF](https://github.com/tunnelvisionlabs/MPFProj10).  
  
 Bu proje VSPackage çözümünüze eklemek için aşağıdakileri yapın:  
  
1.  MPFProj indirmek *MPFProjectDir*.  
  
2.  İçinde *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, aşağıdaki bloğu değiştirin:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  VSPackage projesi oluşturun.  
  
2.  VSPackage projeyi.  
  
3.  Diğer önce aşağıdaki blok ekleyerek VSPackage .csproj dosyasını düzenlemek `<Import>` blokları:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  Projeyi kaydedin.  
  
2.  VSPackage çözümü kapatıp yeniden açın.  
  
3.  VSPackage projeyi yeniden açın. ProjectBase adlı yeni bir dizin görmeniz gerekir.  
  
4.  VSPackage projesi şu başvuruyu ekleyin:  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Projeyi oluşturun.  
  
## <a name="hierarchy-classes"></a>Hiyerarşi sınıfları  
 Proje hiyerarşi desteği MPFProj sınıflarda aşağıdaki tabloda özetlenmiştir. Daha fazla bilgi için [hiyerarşiler ve seçim](../../extensibility/internals/hierarchies-and-selection.md).  
  
|Sınıf adı|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>Belge işleme sınıfları  
 Belge işleme desteği MPF sınıflarda aşağıdaki tabloda listelenmektedir. Daha fazla bilgi için [açma ve kaydetme proje öğeleri](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Sınıf adı|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Yapılandırma ve çıktı sınıfları  
 Proje türleri hata ayıklama ve yayın proje çıkışı koleksiyonları gibi birden çok yapılandırmada desteği sağlayan MPF sınıfları aşağıdaki tabloda listelenmektedir. Daha fazla bilgi için [yapılandırma seçeneklerini yönetme](../../extensibility/internals/managing-configuration-options.md).  
  
|Sınıf adı|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Otomasyon desteği sınıfları  
 Otomasyon destekler ve böylece kullanıcılar proje türünüz eklentileri yazabilirsiniz MPF sınıflarda aşağıdaki tabloda listelenmektedir.  
  
|Sınıf adı|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Özellikler sınıfları  
 Aşağıdaki tabloda, proje türleri izin MPF sınıflarda kullanıcılar göz atın ve bir özellik tarayıcısında değiştirmek özellikleri ekleyin.  
  
|Sınıf adı|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|