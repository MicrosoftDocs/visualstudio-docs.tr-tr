---
title: 'Nasıl yapılır: Ürün bildirimi oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: fc5662763e7932cc024169969801c9c321343e32
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270094"
---
# <a name="how-to-create-a-product-manifest"></a>Nasıl yapılır: Ürün Bildirimi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanız için önkoşul dağıtmak için bir önyükleyici paketi oluşturabilirsiniz. Paket bildirimi ancak tek ürün bildirim dosyasını her yerel ayar için bir önyükleyici paketi içerir. Paket bildirimi paketinin yerelleştirme özgü özelliklerini içerir. Bu dizeler, son kullanıcı lisans sözleşmelerini ve dil paketlerini içerir.  
  
 Ürün bildirimleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Ürün bildirimi oluşturma  
  
#### <a name="to-create-the-product-manifest"></a>Ürün bildirimi oluşturma  
  
1.  Önyükleyici paketi için bir dizin oluşturun. Bu örnek, C:\package kullanır.  
  
2.  Adlı yeni bir XML dosyasını Visual Studio'da oluşturma `product.xml`ve C:\package klasörüne kaydedin.  
  
3.  XML ad alanı ve ürün kodu için paket açıklamak için aşağıdaki XML'i ekleyin. Ürün kodu, paket için benzersiz bir tanımlayıcıyla değiştirin.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Paket bağımlılığı olduğunu belirtmek için XML ekleyin. Bu örnek, bir bağımlılık üzerinde Microsoft Windows Installer 3.1 kullanır.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Önyükleyici paketteki tüm dosyaların listesi için XML ekleyin. Bu örnekte, paket dosyası adı CorePackage.msi kullanır.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Kopyalayın veya CorePackage.msi dosyasını C:\package klasörüne taşıyın.  
  
7.  Önyükleyici komutları kullanarak paketini yüklemek için XML ekleyin. Önyükleyici otomatik olarak ekler **/qn** sessiz yükleme .msi dosyasını bayrak. Bir .exe dosyası ise önyükleyici Kabuğu'nu kullanarak .exe dosyasını çalıştırır. Aşağıdaki XML CorePackage.msi için bağımsız değişken olmadan gösterir, ancak komut satırı bağımsız değişkeni bağımsız değişkenler özniteliği koyabilirsiniz.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Bu önyükleyici paketi yüklü olup olmadığını denetlemek için aşağıdaki XML'i ekleyin. Yeniden dağıtılabilir bileşen için GUID ürün kodu değiştirin.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Önyükleyici bileşeninin zaten yüklü değilse bağlı olarak önyükleyici davranışını değiştirmek için XML ekleyin. Bileşeni yüklü değilse, önyükleyici paketi çalıştırmaz. Aşağıdaki XML, çünkü bu bileşen yönetici ayrıcalıkları geçerli kullanıcının yönetici olup olmadığını denetler.  
  
    ```  
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
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Önyükleyici komutlar bölümünü sonuna aşağıdaki XML'i ekleyin.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Visual Studio önyükleyicisi dizine C:\package klasöre taşıyın. Visual Studio 2010 için bu \Program SDKs\Windows\v7.0A\Bootstrapper\Packages dizinidir.  
  
## <a name="example"></a>Örnek  
 Ürün bildirimi özel Önkoşullar için yükleme yönergeleri içerir.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ürün ve Paket Şema Başvurusu](../deployment/product-and-package-schema-reference.md)



