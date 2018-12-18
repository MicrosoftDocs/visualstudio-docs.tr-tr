---
title: GenerateBootstrapper görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c5c96c91a48e854c1619aa112bae5e1d84737765
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811914"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Algılama, indirmek ve bir uygulama ve önkoşulları yüklemek için otomatik bir yol sağlar. Uygulama yaparak tüm bileşenler için ayrı yükleyiciler tümleştiren tek bir yükleyici olarak görev yapar.  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Parametreleri aşağıdaki tabloda açıklanmıştır `GenerateBootstrapper` görev.  
  
- `ApplicationFile`  
  
   İsteğe bağlı `String` parametresi.  
  
   Önyükleyici tüm önkoşulları yüklendikten sonra uygulamanın yükleme işlemini başlatmak için kullanacağı dosyasını belirtir. Bir yapı hatası kullanılmazsa sonuçlanır `BootstrapperItems` ya da `ApplicationFile` parametre belirtildi.  
  
- `ApplicationName`  
  
   İsteğe bağlı `String` parametresi.  
  
   Önyükleyici yükleyecek uygulamanın adını belirtir. Bu ad, yükleme sırasında önyükleyici kullanır kullanıcı arabiriminde görüntülenir.  
  
- `ApplicationRequiresElevation`  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, hedef bilgisayarda yüklü olduğunda bileşeni yükseltilmiş izinlerle çalıştırır.  
  
- `ApplicationUrl`  
  
   İsteğe bağlı `String` parametresi.  
  
   Uygulamanın yükleyici barındırma Web konumu belirtir.  
  
- `BootstrapperComponentFiles`  
  
   İsteğe bağlı `String[]` çıkış parametresi.  
  
   Yerleşik önyükleyici paketi dosyalarının konumunu belirtir.  
  
- `BootstrapperItems`  
  
   İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.  
  
   Önyükleyici derleme ürünlerin belirtir. Bu parametreye geçirilen öğe, aşağıdaki söz dizimini sahip olmanız gerekir:  
  
  ```  
  <BootstrapperItem  
      Include="ProductCode">  
      <ProductName>  
          ProductName  
      </ProductName>  
  </BootstrapperItem>  
  ```  
  
   `Include` Özniteliği yüklü olması bir önkoşul adını göstermek için kullanılır. `ProductName` Öğe meta verileri isteğe bağlıdır ve derleme altyapısı tarafından bir kolay ad kullanılacak durumda paketi bulunamıyor. Bu öğeler, gerekli değildir. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] giriş parametreleri sürece hiçbir `ApplicationFile` belirtilir. Uygulamanız için yüklenmesi gereken her bir ön koşul için bir öğe içermelidir.  
  
   Bir yapı hatası kullanılmazsa sonuçlanır `BootstrapperItems` ya da `ApplicationFile` parametre belirtildi.  
  
- `BootstrapperKeyFile`  
  
   İsteğe bağlı `String` çıkış parametresi.  
  
   Setup.exe yerleşik konumunu belirtir  
  
- `ComponentsLocation`  
  
   İsteğe bağlı `String` parametresi.  
  
   Yükleme önkoşulları yüklemek aranacak önyükleyici için bir konum belirtir. Bu parametre aşağıdaki değerleri içerebilir:  
  
  - `HomeSite`: Önkoşul bileşeni satıcı tarafından barındırıldığını gösterir.  
  
  - `Relative`: Preqrequisite uygulamanın aynı konumda olduğunu gösterir.  
  
  - `Absolute`: Tüm bileşenleri merkezi bir URL'de bulunabilir olduğunu gösterir. Bu değer ile birlikte kullanılması gereken `ComponentsUrl` giriş parametresi.  
  
    Varsa `ComponentsLocation` belirtilmezse, `HomeSite` varsayılan olarak kullanılır.  
  
- `ComponentsUrl`  
  
   İsteğe bağlı `String` parametresi.  
  
   Yükleme önkoşulları içeren URL'yi belirtir.  
  
- `CopyComponents`  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, tüm çıktı dosyaları önyükleyici belirtilen yola kopyalar `OutputPath` parametresi. Değerlerini `BootstrapperComponentFiles` parametresi tüm tabanlı bu yolda. Varsa `false`, dosyalar kopyalanır değil ve `BootstrapperComponentFiles` değerleri değerini temel alarak `Path` parametresi.  Bu parametrenin varsayılan değeri `true`.  
  
- `Culture`  
  
   İsteğe bağlı `String` parametresi.  
  
   UI önyükleyici için ve yükleme önkoşulları kültürü belirtir. Belirtilen kültür kullanılamıyor, görev değerini kullanır. `FallbackCulture` parametresi.  
  
- `FallbackCulture`  
  
   İsteğe bağlı `String` parametresi.  
  
   UI bootstraper için ve yükleme önkoşulları ikincil kültürü belirtir.  
  
- `OutputPath`  
  
   İsteğe bağlı `String` parametresi.  
  
   Kopyalama setup.exe ve tüm paket dosyaları konumu belirtir.  
  
- `Path`  
  
   İsteğe bağlı `String` parametresi.  
  
   Kullanılabilir tüm önkoşul paketleri konumunu belirtir.  
  
- `SupportUrl`  
  
   İsteğe bağlı `String` parametresi.  
  
   Önyükleyici yüklemenin başarısız olması sağlamak için URL'yi belirtir  
  
- `Validate`  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, önyükleyici belirtilen giriş önyükleyici öğeleri XSD doğrulaması gerçekleştirir. Bu parametrenin varsayılan değeri `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `GenerateBootstrapper` sahip olması gereken bir uygulamayı yüklemek için görev [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] bir önkoşul olarak yüklü.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">  
            <ProductName>Microsoft .NET Framework 2.0</ProductName>  
        </BootstrapperFile>  
    </ItemGroup>  
  
    <Target Name="BuildBootstrapper">  
        <GenerateBootstrapper  
            ApplicationFile="WindowsApplication1.application"  
            ApplicationName="WindowsApplication1"  
            ApplicationUrl="http://mycomputer"  
            BootstrapperItems="@(BootstrapperFile)"  
            OutputPath="C:\output" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)



