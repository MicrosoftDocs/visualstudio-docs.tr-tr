---
title: 'Nasıl yapılır: yerelleştirilmiş önyükleyici paketi oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1083633410c42c63f8c3e9a2ff341a2278f0b63a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153221"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Nasıl yapılır: yerelleştirilmiş önyükleyici paketi oluşturma
Bir önyükleyici paketi oluşturduktan sonra her yerel ayar için iki daha fazla dosya oluşturarak yerelleştirilmiş önyükleyici paketi sürümlerini oluşturabilirsiniz: dosya bir yazılım lisans koşulları (gibi bir *eula.rtf*) ve bir paket bildirimi (*package.xml*).  
  
 Varsayılan olarak, yalnızca .NET Framework 4, .NET Framework 4 istemci profili, F # çalışma zamanı 2.0 ve F # çalışma zamanı 4.0 için Visual Studio 2010 yerelleştirilmiş önyükleyici paketleri içerir. Yerelleştirilmiş paketler, diğer önyükleyiciler için üç adımları izleyerek oluşturabilirsiniz.  
  
1.  Yerel ayar adı sonra adlı bir klasör oluşturun *\Program SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >*.  
  
2.  Önyükleyici paketini Yazılım Lisans Koşulları'nı içeren bir dosya oluşturun ve yeni klasöre yerleştirin.  
  
3.  Adlı bir paket bildirimi oluşturma *package.xml*, kültür ve dizeleri güncelleştirmek ve dosyanın yeni klasöre yerleştirin. Visual Studio'nun bir önyükleyici hedef dilde zaten oluşturduysanız, Visual Studio kopyalayabilirsiniz *package.xml* dosya ve bu adımda değiştirin.  
  
> [!NOTE]
>  Uygulamaları dağıtmak için bir kurulum projesi kullanıyorsanız değiştirerek, uygulamanızın yerelleştirebilirsiniz **yerelleştirme** özelliği.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>Yerelleştirilmiş önyükleyici paketi oluşturmak için  
  
1.  Yerel ayar adından sonra adlı bir klasör oluşturun.  
  
     32-bit bilgisayarlarda, klasörde oluşturmak *\Program SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >\\*  klasör.  
  
     64-bit bilgisayarlarda, klasörde oluşturmak *\Program dosyaları (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >\\*  klasör.  
  
     Aşağıdaki tabloda, bir yerel ayar eşleştirmek için kullanabileceğiniz klasör adlarını gösterir.  
  
    |Yerel Ayar|Klasör adı|  
    |------------|-----------------|  
    |ve|zh-Hans|  
    |seçenekleri yerine|zh-Hant|  
    |Çekçe|cs|  
    |Almanca|de|  
    |İngilizce|tr|  
    |İspanyolca|ES|  
    |Fransızca|FR|  
    |İtalyanca|Bunu|  
    |Kore Dili|Ko|  
    |Japonca|ja|  
    |Lehçe|PL|  
    |Portekizce (Brezilya)|pt-BR|  
    |Rusça|RU|  
    |Türkçe|tr|  
  
2.  Önyükleyici paketini Yazılım Lisans Koşulları'nı içeren bir dosya oluşturun ve yeni klasöre yerleştirin.  
  
3.  Adlı bir paket bildirimi oluşturma *package.xml* ve yeni klasöre yerleştirin. Daha fazla bilgi için [nasıl yapılır: Paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md).  
  
4.  Güncelleştirme `<Strings>` paketin bölümünü bildirim yerel ayarı için doğru dilde dizelerdir.  
  
5.  Değişiklik `<String Name="Culture">` klasör adı eşleşecek değer.  
  
6.  Kaydet *package.xml* dosya.  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>.NET Framework 3.5 Service Pack 1'de Fransızca yerelleştirilmiş önyükleyici paketi oluşturmak için  
  
1.  Adlı bir klasör oluşturma *fr*. Klasör adı, yerel ayar adı eşleşmelidir.  
  
     32-bit bilgisayarlarda, klasörde oluşturmak *\Program SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*  klasör.  
  
     64-bit bilgisayarlarda, klasörde oluşturmak *\Program dosyaları (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*  klasör.  
  
2.  İçinde yazılım lisans koşulları yerelleştirilmiş bir sürümünü *fr* klasör.  
  
3.  Kopyalama *\Program dosyaları (x86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* dosyasını *fr* klasörü ve dosyayı XML Tasarımcısı'nda açın.  
  
4.  Güncelleştirme `<Strings>` paketin bölümünü bildiriminin Fransızca hata dizelerdir.  
  
5.  Değişiklik `<String Name="Culture">` değerini *fr*.  
  
6.  Kaydet *package.xml* dosya.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md)   
 [Uygulama dağıtımının önkoşulları](../deployment/application-deployment-prerequisites.md)   
 [Nasıl yapılır: Paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md)