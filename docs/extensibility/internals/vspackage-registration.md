---
title: VSPackage kaydı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67b80eb48129fb989822e28bcb0ac0e330c426bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828439"
---
# <a name="vspackage-registration"></a>VSPackage Kaydı
VSPackage gerekir öneri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yüklenir ve gereken yüklendi. Bu işlem, kayıt defterine bilgi yazma tarafından gerçekleştirilir. Tipik bir iş yükleyicinin olmasıdır.  
  
> [!NOTE]
>  Bu bir kabul edilen kendi kendine kayıt kullanılacak VSPackage geliştirme sırasında uygulamadır. Ancak, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] iş ortakları, kendi kendine kayıt kurulumunun bir parçası kullanarak ürünlerini gönderilemez.  
  
 Bir Windows Installer paketi kayıt defteri girişleri kayıt defteri tabloda genel olarak yapılır. Bu gibi durumlarda, dosya uzantılarını da kayıt defteri tabloda kaydedebilirsiniz. Ancak, Windows Installer programlı tanımlayıcısı (ProgID), sınıf, uzantı ve fiili tablolar üzerinden yerleşik destek sağlar. Daha fazla bilgi için [veritabanı tabloları](/windows/desktop/Msi/database-tables).  
  
 Kayıt defteri girdileri seçilen yan yana stratejiniz için uygun olan bileşeni ile ilişkilendirildiğinden emin olun. Örneğin, paylaşılan bir dosya için kayıt defteri girdileri dosyanın Windows Installer bileşen ile ilişkili olmalıdır. Benzer şekilde, kayıt defteri girişleri için sürüme özgü dosya o dosyanın bileşen ile ilişkili olmalıdır. Aksi takdirde, yükleme veya bir sürümü için VSPackage kaldırma [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , VSPackage'ı diğer sürümlerinde de uğratabilir. Daha fazla bilgi için [destekleyen birden çok Versions of Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
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
  
- Yükleme, kaldırma, geri yükleme ve kaldırma işlemini geri alma doğru destek RegPkg çağırarak kendi kendini kaydeden her yönetilen VSPackage için dört özel eylem yazmanızı gerektirir.  
  
- Yan yana destek yönelik yaklaşımınızı RegSvr32 veya RegPkg desteklenen her sürümü için çağırma dört özel eylem Yazar gerektirebilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
- Kendi kendine kayıtlı anahtarlar başka bir özellik veya uygulama tarafından kullanılır, söyleyen hiçbir şekilde geri olmadığı için bir yükleme Self kayıtlı modül ile güvenli bir şekilde alınamaz.  
  
- Kendi kendine kayıtlı DLL'leri bazen, mevcut olmayan ya da yanlış sürümü yardımcı DLL'lerine. Buna karşılık, Windows Installer DLL'leri sistemin geçerli durumunu üzerinde hiçbir bağımlılık ile kayıt tabloları kullanarak kaydedebilirsiniz.  
  
- Tür kitaplıkları gibi ağ kaynaklarına erişim bileşeni hem çalışma alanından kaynağı olarak belirtilmişse ve kendi kendini kaydetme tabloda listelenen kendi kayıt kodunu engellenebilir. Bu yükleme bileşen Yönetim yüklemesi sırasında başarısız olmasına neden olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer](/windows/desktop/Msi/windows-installer-portal)   
 [Yönetilen paket kaydı](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)