---
title: 'Nasıl yapılır: Paket bildirimi oluşturma | Microsoft Docs'
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
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 38a0c448bcf629c4e914393cb8eabad93ced574c
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154635"
---
# <a name="how-to-create-a-package-manifest"></a>Nasıl yapılır: Paket bildirimi oluşturma
Uygulamanız için önkoşul dağıtmak için bir önyükleyici paketi kullanabilirsiniz. Paket bildirimi ancak tek ürün bildirim dosyasını her yerel ayar için bir önyükleyici paketi içerir. Yerelleştirilmiş farklı sürümleri arasında paylaşılan işlevselliği ürün bildirimine gitmeniz gerekir.  
  
 Paket bildirimleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: Ürün bildirimi oluşturma](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="create-the-package-manifest"></a>Paket bildirimi oluşturma  
  
#### <a name="to-create-the-package-manifest"></a>Paket bildirimi oluşturma  
  
1.  Önyükleyici paketi için bir dizin oluşturun. Bu örnekte *C:\package*.  
  
2.  Yerel ayar adı ile aşağıdaki gibi bir alt dizin oluşturma *tr* İngilizce.  
  
3.  Visual Studio'da adlı bir XML dosyası oluşturun *package.xml*ve kaydetmesi *C:\package\en* klasör.  
  
4.  Önyükleyici paket adı, bu yerelleştirilmiş paket bildirimi ve isteğe bağlı bir lisans sözleşmesi için kültürü listelemek için XML ekleyin. Aşağıdaki XML değişkenleri kullanır `DisplayName` ve `Culture`, bir sonraki öğe tanımlanır.  
  
    ```xml  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Yerel ayara özgü dizindeki tüm dosyaları listelemek için XML ekleyin. Aşağıdaki XML adında bir dosya kullanır *eula.txt* için geçerli olan **tr** yerel ayar.  
  
    ```xml  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Yerelleştirilebilir Dize için önyükleyici paketi tanımlamak için XML ekleyin. Hata dizeleri için aşağıdaki XML ekler **tr** yerel ayar.  
  
    ```xml  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  Kopyalama *C:\package* Visual Studio önyükleyicisi dizinine klasörü. Visual Studio 2010 için bu, *\Program SDKs\Windows\v7.0A\Bootstrapper\Packages* dizin.  
  
## <a name="example"></a>Örnek  
 Paket bildirimi gibi hata iletileri, Yazılım Lisans Koşulları'nı ve dil paketlerinin yerel ayara özgü bilgileri içerir.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)