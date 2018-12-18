---
title: 'Nasıl yapılır: Paket bildirimi oluşturma | Microsoft Docs'
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
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2941000e9fa2c6f1d9fd4835c9fd0b8fa1fd1b4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182435"
---
# <a name="how-to-create-a-package-manifest"></a>Nasıl yapılır: Paket Bildirimi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanız için önkoşul dağıtmak için bir önyükleyici paketi kullanabilirsiniz. Paket bildirimi ancak tek ürün bildirim dosyasını her yerel ayar için bir önyükleyici paketi içerir. Yerelleştirilmiş farklı sürümleri arasında paylaşılan işlevselliği ürün bildirimine gitmeniz gerekir.  
  
 Paket bildirimleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir ürün bildirimi oluşturma](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Paket bildirimi oluşturma  
  
#### <a name="to-create-the-package-manifest"></a>Paket bildirimi oluşturma  
  
1.  Önyükleyici paketi için bir dizin oluşturun. Bu örnek, C:\package kullanır.  
  
2.  İngilizce tr'gibi bir yerel ada sahip bir dizin oluşturun.  
  
3.  Visual Studio'da adlı bir XML dosyası oluşturun `package.xml`ve C:\package\en klasörüne kaydedin.  
  
4.  Önyükleyici paket adı, bu yerelleştirilmiş paket bildirimi ve isteğe bağlı bir lisans sözleşmesi için kültürü listelemek için XML ekleyin. Aşağıdaki XML değişkenleri kullanır `DisplayName` ve `Culture`, bir sonraki öğe tanımlanır.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Yerel ayara özgü dizindeki tüm dosyaları listelemek için XML ekleyin. Aşağıdaki XML için geçerli olan eula.txt adlı bir dosya kullanır **tr** yerel ayar.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Yerelleştirilebilir Dize için önyükleyici paketi tanımlamak için XML ekleyin. Aşağıdaki XML, tr yerel ayar için hata dizesi ekler.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  Visual Studio önyükleyicisi dizine C:\package klasörünü kopyalayın. Visual Studio 2010 için bu \Program SDKs\Windows\v7.0A\Bootstrapper\Packages dizinidir.  
  
## <a name="example"></a>Örnek  
 Paket bildirimi gibi hata iletileri, Yazılım Lisans Koşulları'nı ve dil paketlerinin yerel ayara özgü bilgileri içerir.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ürün ve Paket Şema Başvurusu](../deployment/product-and-package-schema-reference.md)



