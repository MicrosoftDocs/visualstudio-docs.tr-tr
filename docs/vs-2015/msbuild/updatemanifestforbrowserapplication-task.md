---
title: UpdateManifestForBrowserApplication görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d1549616dcaa2ec998e242c5d39821baabfa39b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220003"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Görevi çalıştırılana eklemek için  **\<HostInBrowser / >** öğe uygulama bildiriminin (*projectname*. exe.manifest) olduğunda bir [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] Proje oluşturulur.  
  
## <a name="task-parameters"></a>Görev parametreleri  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`ApplicationManifest`|Gerekli **Itaskıtem []** parametresi.<br /><br /> Eklemek istediğiniz uygulama bildirim dosyasının adını ve yolunu belirtir `<hostInBrowser />` öğesi.|  
|`HostInBrowser`|Gerekli **Boole** parametresi.<br /><br /> Dahil etmek için uygulama bildirimini değiştirmeniz belirtir  **\<HostInBrowser / >** öğesi. Varsa **true**, yeni bir `<` **HostInBrowser / >** öğe dahil edilir  **\<entryPoint / >** öğesi. Bu öğe unutmayın toplu ekleme: varsa bir  **\<HostInBrowser / >** öğe zaten var, bunu üzerine veya kaldırıldığında değil. Bunun yerine, ek bir  **\<HostInBrowser / >** öğesi oluşturulur. Varsa **false**, uygulama bildirimini değiştirilmez.|  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[TLA2#tla_xbap#plural](../includes/tla2sharptla-xbapsharpplural-md.md)] kullanarak çalışan [!INCLUDE[TLA#tla_clickonce](../includes/tlasharptla-clickonce-md.md)] dağıtım ve bu nedenle, gereken tarafından yayımlanan dağıtım ve uygulama bildirimleri destekleme ile. [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] kullanan [GenerateApplicationManifest](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) bir uygulama bildirimi oluşturmak için görev.  
  
 Ardından, uygulamaya bir tarayıcıdan, ek bir öğe barındırılması için yapılandırmak için  **\<HostInBrowser / >** uygulama bildirimine, aşağıdaki örnekte Göster olarak eklenmesi gerekir:  
  
```  
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
  
 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Görevi çalıştırılana ne zaman bir [!INCLUDE[TLA2#tla_xbap](../includes/tla2sharptla-xbap-md.md)] projesi eklemek için yapılandırıldığında `<hostInBrowser />` öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek emin olmak nasıl gösterir `<hostInBrowser />` öğesi, bir uygulama bildirimi dosyasında bulunur.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)   
 [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [WPF uygulaması (WPF) oluşturma](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [WPF XAML Tarayıcı Uygulamalarına Genel Bakış](http://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)



