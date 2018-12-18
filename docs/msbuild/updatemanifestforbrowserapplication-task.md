---
title: UpdateManifestForBrowserApplication görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7e86f07d0806f6ce5873cd91b68b4b32d58f4e6
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220703"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication görevi
<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Görevi çalıştırılana eklemek için  **\<HostInBrowser / >** öğe uygulama bildiriminin (*\<projectname >. exe.manifest*) olduğunda bir [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] Proje oluşturulur.  
  
## <a name="task-parameters"></a>Görev parametreleri  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`ApplicationManifest`|Gerekli **Itaskıtem []** parametresi.<br /><br /> Eklemek istediğiniz uygulama bildirim dosyasının adını ve yolunu belirtir `<hostInBrowser />` öğesi.|  
|`HostInBrowser`|Gerekli **Boole** parametresi.<br /><br /> Dahil etmek için uygulama bildirimini değiştirmeniz belirtir  **\<HostInBrowser / >** öğesi. Varsa **true**, yeni bir  **\<HostInBrowser / >** öğe dahil edilir  **\<entryPoint / >** öğesi. Öğe ekleme toplu: varsa bir  **\<HostInBrowser / >** öğe zaten var, kaldırıldı veya üzerine değil. Bunun yerine, ek bir  **\<HostInBrowser / >** öğesi oluşturulur. Varsa **false**, uygulama bildirimini değiştirilmez.|  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] kullanarak çalışan [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] dağıtımı için dağıtım ve uygulama bildirimleri, destekleyici yayımlanmalıdır. [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] kullanan [GenerateApplicationManifest](generateapplicationmanifest-task.md) bir uygulama bildirimi oluşturmak için görev.  
  
 Ardından, uygulamaya bir tarayıcıdan ek barındırılması için yapılandırmak için  **\<HostInBrowser / >** öğesi aşağıdaki örnekte gösterildiği gibi uygulama bildirimine eklenmelidir:  
  
```xml  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Görevi çalıştırılana ne zaman bir [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] projesi eklemek için yapılandırıldığında `<hostInBrowser />` öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek emin olmak nasıl gösterir `<hostInBrowser />` öğesi, bir uygulama bildirimi dosyasında bulunur.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)   
 [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Bir WPF uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [WPF XAML tarayıcı uygulamalarına genel bakış](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)