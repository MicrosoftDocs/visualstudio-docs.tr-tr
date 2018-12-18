---
title: GenerateBootstrapper görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53ad85f77d014d534d625b8d08e36b7eb8c01f7f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895736"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper görevi
Algılama, indirmek ve bir uygulama ve önkoşulları yüklemek için otomatik bir yol sağlar. Uygulama yaparak tüm bileşenler için ayrı yükleyiciler tümleştiren tek bir yükleyici olarak görev yapar.  
  
## <a name="task-parameters"></a>Görev parametreleri  
 Aşağıdaki parametreleri açıklayan `GenerateBootstrapper` görev.  
  
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
  
  ```xml  
  <BootstrapperItem  
      Include="ProductCode">  
      <ProductName>  
          ProductName  
      </ProductName>  
  </BootstrapperItem>  
  ```  
  
   `Include` Öznitelik yüklenmesi gereken önkoşul adını temsil eder. `ProductName` Öğe meta verileri isteğe bağlıdır ve paket bulunamazsa yapı altyapısı tarafından bir kolay ad kullanılacak. Bu öğeler, gerekli değildir. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] giriş parametreleri, sürece hiçbir `ApplicationFile` belirtilir. Uygulamanız için yüklü olması gereken her bir ön koşul için bir öğe içermelidir.  
  
   Bir yapı hatası kullanılmazsa sonuçlanır `BootstrapperItems` ya da `ApplicationFile` parametre belirtildi.  
  
- `BootstrapperKeyFile`  
  
   İsteğe bağlı `String` çıkış parametresi.  
  
   Yerleşik konumunu belirtir *setup.exe*  
  
- `ComponentsLocation`  
  
   İsteğe bağlı `String` parametresi.  
  
   Yükleme önkoşulları yüklemek aranacak önyükleyici için bir konum belirtir. Bu parametre aşağıdaki değerleri içerebilir:  
  
  - `HomeSite`: Önkoşul bileşeni satıcı tarafından barındırıldığını gösterir.  
  
  - `Relative`: Önkoşul uygulamanın aynı konumda olduğunu gösterir.  
  
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
  
   UI önyükleyici için ve yükleme önkoşulları kültürü belirtir. Belirtilen kültür kullanılamıyorsa, görev değerini kullanır. `FallbackCulture` parametresi.  
  
- `FallbackCulture`  
  
   İsteğe bağlı `String` parametresi.  
  
   UI önyükleyici için ve yükleme önkoşulları ikincil kültürü belirtir.  
  
- `OutputPath`  
  
   İsteğe bağlı `String` parametresi.  
  
   Kopyalanacak konumun belirtir *setup.exe* ve tüm dosyalar paket.  
  
- `Path`  
  
   İsteğe bağlı `String` parametresi.  
  
   Kullanılabilir tüm önkoşul paketleri konumunu belirtir.  
  
- `SupportUrl`  
  
   İsteğe bağlı `String` parametresi.  
  
   Önyükleyici yüklenmesi başarısız olursa sağlamak için URL'yi belirtir.  
  
- `Validate`  
  
   İsteğe bağlı `Boolean` parametresi.  
  
   Varsa `true`, önyükleyici belirtilen giriş önyükleyici öğeleri XSD doğrulaması gerçekleştirir. Bu parametrenin varsayılan değeri `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.TaskExtension> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Bu ek parametrelerin ve Tanımlamaların bir listesi için bkz. [TaskExtension taban sınıfı](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `GenerateBootstrapper` sahip olması gereken bir uygulamayı yüklemek için görev [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] bir önkoşul olarak yüklü.  
  
```xml  
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
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)