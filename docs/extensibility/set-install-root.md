---
title: VSIX v3 uzantıları klasörüyle dışında yükleme | Microsoft Docs
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8476b300974d66efc60f647c897ec6892191e7fa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136789"
---
# <a name="installing-outside-the-extensions-folder"></a>Uzantıları klasörünün dışında yükleme

Visual Studio 2017 ve VSIX v3 ile başlayan (uzantısı varlıklar uzantıları klasörünü dışında yüklemek için şimdi destek sürüm 3). Şu anda, (burada [INSTALLDİR] Visual Studio örneğinin yükleme dizin ile eşlenen) geçerli yükleme konumları olarak aşağıdaki konumlarda etkin:

* [INSTALLDİR] \MSBuild
* [INSTALLDİR] \Xml\Schemas
* [INSTALLDİR] \Common7\IDE\PublicAssemblies
* [INSTALLDİR] \Licenses
* [INSTALLDİR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDİR] \Common7\IDE\RemoteDebugger
* [INSTALLDİR] \Common7\IDE\VC\VCTargets

>**Not:** VSIX biçimi dışında VS yükleme klasör yapısı yüklemeye izin vermez.

Bu dizinleri yüklemeyi desteklemek için VSIX "makine başına örnek başına" yüklenmelidir. Bu extension.vsixmanifest Tasarımcısı'nda "tüm kullanıcılar" onay kutusunu işaretleyerek etkin hale getirilebilir:

![tüm kullanıcılar denetleyin](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Yüklemekökü ayarlama

Yükleme dizinleri ayarlamak için kullanabileceğiniz **özellikleri** Visual Studio'daki. Örneğin, ayarlayabileceğiniz `InstallRoot` yukarıdaki konumlardan birine proje başvurusu özelliği:

![kök özellikleri yükleyin](media/install-root-properties.png)

Bu ilgili bazı meta veri ekler `ProjectReference` özelliği VSIX proje .csproj dosya içinde:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Not:** tercih ederseniz, doğrudan .csproj dosyasını düzenleyin.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Bir alt yolu yüklemekökü altında ayarlama

Bir alt yolu yüklemek isteyip istemediğinizi `InstallRoot`, ayarlayarak yapabilirsiniz `VsixSubPath` özelliği olduğu gibi `InstallRoot` özelliği. Örneğin, yüklemek için bizim proje referansının çıktısı istiyoruz söyleyin ' [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'. Kolayca özelliği Tasarımcısı ile bunu yapabilirsiniz:

![set alt yolu](media/set-subpath.png)

Karşılık gelen .csproj değişiklikleri şuna benzeyecektir:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Ek bilgi

Özellik Tasarımcı değişiklikleri daha fazlasını proje başvuruları için geçerlidir; ayarlayabileceğiniz `InstallRoot` projenizi de içinde öğeleri için meta veriler (yukarıda açıklanan aynı yöntemleri kullanarak).
