---
title: 'Nasıl yapılır: Ürün bildirimi oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69ecc5e6547d84531579169ac7dcf7fcc31bc8f7
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153117"
---
# <a name="how-to-create-a-product-manifest"></a>Nasıl yapılır: Ürün bildirimi oluşturma
Uygulamanız için önkoşul dağıtmak için bir önyükleyici paketi oluşturabilirsiniz. Paket bildirimi ancak tek ürün bildirim dosyasını her yerel ayar için bir önyükleyici paketi içerir. Paket bildirimi paketinin yerelleştirme özgü özelliklerini içerir. Bu dizeler, son kullanıcı lisans sözleşmelerini ve dil paketlerini içerir.  
  
 Ürün bildirimleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: Paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="create-the-product-manifest"></a>Ürün bildirimi oluşturma  
  
#### <a name="to-create-the-product-manifest"></a>Ürün bildirimi oluşturma  
  
1.  Önyükleyici paketi için bir dizin oluşturun. Bu örnek, C:\package kullanır.  
  
2.  Adlı yeni bir XML dosyasını Visual Studio'da oluşturma *product.xml*ve kaydetmesi *C:\package* klasör.  
  
3.  XML ad alanı ve ürün kodu için paket açıklamak için aşağıdaki XML'i ekleyin. Ürün kodu, paket için benzersiz bir tanımlayıcıyla değiştirin.  
  
    ```xml  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Paket bağımlılığı olduğunu belirtmek için XML ekleyin. Bu örnek, bir bağımlılık üzerinde Microsoft Windows Installer 3.1 kullanır.  
  
    ```xml  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Önyükleyici paketteki tüm dosyaların listesi için XML ekleyin. Bu örnekte paket dosyası adı *CorePackage.msi*.  
  
    ```xml  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Kopyalamak veya taşımak *CorePackage.msi* dosyasını *C:\package* klasör.  
  
7.  Önyükleyici komutları kullanarak paketini yüklemek için XML ekleyin. Önyükleyici otomatik olarak ekler **/qn** bayrak *.msi* dosyasını sessizce yükler. Eğer dosya bir *.exe*, önyükleyici çalıştıran *.exe* kabuğunu kullanarak dosya. Aşağıdaki XML bağımsız değişken olmadan gösterir *CorePackage.msi*, ancak komut satırı bağımsız değişkeni içine koyabilirsiniz `Arguments` özniteliği.  
  
    ```xml  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Bu önyükleyici paketi yüklü olup olmadığını denetlemek için aşağıdaki XML'i ekleyin. Yeniden dağıtılabilir bileşen için GUID ürün kodu değiştirin.  
  
    ```xml  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Önyükleyici bileşeninin zaten yüklü değilse bağlı olarak önyükleyici davranışını değiştirmek için XML ekleyin. Bileşeni yüklü değilse, önyükleyici paketi çalıştırmaz. Aşağıdaki XML, çünkü bu bileşen yönetici ayrıcalıkları geçerli kullanıcının yönetici olup olmadığını denetler.  
  
    ```xml  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Yükleme başarılı olursa ve yeniden başlatma gerekli değilse çıkış kodları ayarlamak için XML ekleyin. Aşağıdaki XML, hata ve FailReboot çıkış, önyükleyici paketleri yüklemeye devam edeceğini belirtir kodlarını gösterir.  
  
    ```xml  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Önyükleyici komutlar bölümünü sonuna aşağıdaki XML'i ekleyin.  
  
    ```xml  
        </Command>  
    </Commands>  
    ```  
  
12. Taşıma *C:\package* Visual Studio önyükleyicisi dizinine klasörü. Visual Studio 2010 için bu, *\Program SDKs\Windows\v7.0A\Bootstrapper\Packages* dizin.  
  
## <a name="example"></a>Örnek  
 Ürün bildirimi özel Önkoşullar için yükleme yönergeleri içerir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)