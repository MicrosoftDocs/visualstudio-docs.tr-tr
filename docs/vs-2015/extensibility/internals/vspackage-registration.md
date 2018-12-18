---
title: VSPackage kaydı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30da9208df8c5b9b7c3368ef10fc85e55a994baa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782030"
---
# <a name="vspackage-registration"></a>VSPackage Kaydı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage gerekir öneri [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yüklenir ve gereken yüklendi. Bu işlem, kayıt defterine bilgi yazma tarafından gerçekleştirilir. Tipik bir iş yükleyicinin olmasıdır.  
  
> [!NOTE]
>  Bu bir kabul edilen kendi kendine kayıt kullanılacak VSPackage geliştirme sırasında uygulamadır. Ancak, [!INCLUDE[vsipprvsip](../../includes/vsipprvsip-md.md)] iş ortakları, kendi kendine kayıt kurulumunun bir parçası kullanarak ürünlerini gönderilemez.  
  
 Bir Windows Installer paketi kayıt defteri girişleri kayıt defteri tabloda genel olarak yapılır. Bu gibi durumlarda, dosya uzantılarını da kayıt defteri tabloda kaydedebilirsiniz. Ancak, Windows Installer programlı tanımlayıcısı (ProgID), sınıf, uzantı ve fiili tablolar üzerinden yerleşik destek sağlar. Daha fazla bilgi için [veritabanı tabloları](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Kayıt defteri girdileri seçilen yan yana stratejiniz için uygun olan bileşeni ile ilişkilendirildiğinden emin olun. Örneğin, paylaşılan bir dosya için kayıt defteri girdileri dosyanın Windows Installer bileşen ile ilişkili olmalıdır. Benzer şekilde, kayıt defteri girişleri için sürüme özgü dosya o dosyanın bileşen ile ilişkili olmalıdır. Aksi takdirde, yükleme veya bir sürümü için VSPackage kaldırma [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , VSPackage'ı diğer sürümlerinde de uğratabilir. Daha fazla bilgi için [destekleyen birden çok Versions of Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Kayıt yönetmek için en kolay yolu aynı verileri aynı dosyaların Geliştirici kayıt ve yükleme zamanı kayıt için kullanmaktır. Örneğin, bazı yükleyici geliştirme araçları, oluşturma zamanında biçimde .reg dosyası kullanabilir. Geliştiriciler kendi günlük geliştirme için .reg dosyaları korumak ve hata ayıklama, aynı dosyaları Yükleyicisi'nde otomatik olarak dahil edilebilir değilse. Kayıt verileri otomatik olarak paylaşım yapamazsınız, kayıt verilerin kopyasını Yükleyicisi'nin güncel olduğundan emin olmanız gerekir.  
  
## <a name="registering-unmanaged-vspackages"></a>Yönetilmeyen VSPackage'ları kaydetme  
 Yönetilmeyen VSPackage'ları (Visual Studio Paket şablon tarafından oluşturulan dahil), kayıt bilgileri depolamak için ATL stil .rgs dosyaları kullanın. .Rgs dosya biçimi için ATL özel ve genel olarak kullanılamaz-yazma aracı bir yükleme tarafından. VSPackage yükleyici için kayıt bilgileri ayrı olarak korunmalıdır. Örneğin, geliştiriciler dosya .reg biçiminde .rgs ile eşitlenmiş dosya değişiklikleri tutabilirsiniz. .Reg dosyalarını geliştirme çalışması için RegEdit ile birleştirilmiş veya bir yükleyici tarafından tüketilen.  
  
## <a name="registering-managed-vspackages"></a>Yönetilen VSPackage'ları kaydetme  
 RegPkg aracı yönetilen VSPackage kaydı öznitelikleri okur ve doğrudan bir yükleyici tarafından tüketilebilecek yazma .reg biçimli dosya ve kayıt defteri için bilgileri yazabilirsiniz.  
  
> [!NOTE]
>  RegPkg Aracı'nı yeniden dağıtılabilir değil ve bir kullanıcının sisteminde bir VSPackage'ı kaydetmek için kullanılamaz.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Neden VSPackage yükleme zamanında Self kaydetmemelidir  
 VSPackage yükleyiciler, kendi kendine kayıt üzerinde güvenmemelisiniz. İlk bakışta, yalnızca VSPackage kendisine VSPackage'nın kayıt defteri değerlerini tutma gibi iyi bir fikir gibi görünüyor. Verilen geliştiricilerin rutin işlerini için kayıt defteri değerlerini gerekir ve test etme, yükleyici kayıt defteri verileri ayrı bir kopyasını koruyarak önlemek için mantıklıdır. Yükleyici, kayıt defteri değerlerini yazmak için VSPackage üzerinde kendisini güvenebilirsiniz.  
  
 Teorik olarak daha fazla iyi, kendi kendine kayıt VSPackage yükleme için uygun hale getiren birden çok fabrikadan sahiptir:  
  
-   Yükleme, kaldırma, geri yükleme ve kaldırma işlemini geri alma doğru destek RegPkg çağırarak kendi kendini kaydeden her yönetilen VSPackage için dört özel eylem yazmanızı gerektirir.  
  
-   Yan yana destek yönelik yaklaşımınızı RegSvr32 veya RegPkg desteklenen her sürümü için çağırma dört özel eylem Yazar gerektirebilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
-   Kendi kendine kayıtlı anahtarlar başka bir özellik veya uygulama tarafından kullanılır, söyleyen hiçbir şekilde geri olmadığı için bir yükleme Self kayıtlı modül ile güvenli bir şekilde alınamaz.  
  
-   Kendi kendine kayıtlı DLL'leri bazen, mevcut olmayan ya da yanlış sürümü yardımcı DLL'lerine. Buna karşılık, Windows Installer DLL'leri sistemin geçerli durumunu üzerinde hiçbir bağımlılık ile kayıt tabloları kullanarak kaydedebilirsiniz.  
  
-   Tür kitaplıkları gibi ağ kaynaklarına erişim bileşeni hem çalışma alanından kaynağı olarak belirtilmişse ve kendi kendini kaydetme tabloda listelenen kendi kayıt kodunu engellenebilir. Bu yükleme bileşen Yönetim yüklemesi sırasında başarısız olmasına neden olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Yönetilen paket kaydı](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)

