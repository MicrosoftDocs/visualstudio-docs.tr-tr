---
title: Yan yana dosya ilişkilendirmelerini yönetme | Microsoft Docs
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
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 171342bf920c2cf1e56da78f5cc7a4bb6d87ea0c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764780"
---
# <a name="managing-side-by-side-file-associations"></a>Yan Yana Dosya İlişkilendirmelerini Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dosya ilişkilendirmeleri, VSPackage sağlıyorsa, yan yana yüklemeleri, işlemeye nasıl karar vermeniz gerekir belirli bir sürümü [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir dosyayı açmak için çağrılmalıdır. Uyumsuz dosya biçimlerine sorunu bileşik.  
  
 Kullanıcılar, veri kaybı olmadan yeni bir sürümde var olan dosyaları yüklenebilir, böylece önceki sürümleriyle uyumlu olacak şekilde bir ürünün yeni bir sürümü bekler. İdeal olarak, VSPackage hem yükleyin ve önceki sürümleri dosya biçimlerinin kaydedin. Bu doğru değilse, dosya biçimi, VSPackage'ı yeni sürüme yükseltmek sunmalıdır. Bu yaklaşımın bir dezavantajı, yükseltilen dosyayı önceki sürümde açılamaz ' dir.  
  
 Bu sorunu önlemek için uzantıları dosya biçimleri uyumsuz olduğunda değiştirebilirsiniz. Örneğin, 1. sürümünü, VSPackage uzantısı, .mypkg10 ve sürüm 2 uzantısı kullanın kullanabilirsiniz .mypkg20. Bu fark, belirli bir dosya açılır VSPackage'ı tanımlar. Eski uzantısıyla ilişkili olan programların listesi için daha yeni VSPackages eklerseniz, kullanıcıların dosyaya sağ tıklayın ve daha yeni bir VSPackage içinde açmak seçin. Bu noktada, dosyanın yeni biçime yükseltmek veya dosyayı açıp VSPackage'nın önceki sürümleriyle uyumluluğu korumak, VSPackage sunabilir.  
  
> [!NOTE]
>  Bu yaklaşımları birleştirebilirsiniz. Örneğin, daha eski bir dosya yükleyerek geriye dönük uyumluluk sağlar ve kullanıcının kaydettiğinde dosya biçimi yükseltme olanağı sunar.  
  
## <a name="facing-the-problem"></a>Sorun karşılıklı  
 Birden çok yan yana VSPackages aynı uzantı kullanmak istiyorsanız, sürümü seçmelisiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısıyla ilişkili. İki seçenekleri şunlardır:  
  
- Dosyanın en son sürümünde açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir kullanıcının bilgisayarında yüklü.  
  
   Bu yaklaşımda, yükleyici en son sürümünü belirlemek için sorumlu olduğu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , dosya ilişkilendirme için yazılmış kayıt defteri girişi dahil. Bir Windows yükleyici paketinde, en son sürümünü belirten bir özelliği ayarlamak için özel eylemler dahil edebileceğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
  > [!NOTE]
  >  Bu bağlamda "desteklenen son sürümü." "son" anlamına gelir Bu yükleyici girişleri sonraki bir sürümünü otomatik olarak algılamaz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Girdiler [sistem gereksinimlerini algılama](../extensibility/internals/detecting-system-requirements.md) ve [komutları, gerekir olması çalıştırma sonra yükleme](../extensibility/internals/commands-that-must-be-run-after-installation.md) burada belirtilen ayarlara benzerdir ve diğer sürümleri desteklemek için gerekli olan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
   Özel tablosundaki aşağıdaki satırları DEVENV_EXE_LATEST özelliği bir özellik tarafından AppSearch kümesi olacak şekilde ayarlayın ve RegLocator tabloları ele alınan [komutları, gerekir olması çalıştırma sonra yükleme](../extensibility/internals/commands-that-must-be-run-after-installation.md). Özel eylemleri yürütme sırası erken InstallExecuteSequence tablosundaki satırları zamanlayın. Koşul sütunu yap mantıksal iş değerleri:  
  
  - Yalnızca mevcut sürüm ise, visual Studio .NET 2002 en son sürümüdür.  
  
  - Visual Studio .NET 2003 varsa, yalnızca en son sürümü olan ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mevcut değil.  
  
  - [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Yalnızca mevcut sürümüyse, en son sürümüdür.  
  
    Sonucunda DEVENV_EXE_LATEST devenv.exe en son sürümünü yolunu içermesidir.  
  
  ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Visual Studio'nun en son sürümü belirlemek özel tablo satırları  
  
  |Eylem|Tür|Kaynak|Hedef|  
  |------------|----------|------------|------------|  
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|  
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|  
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|  
  
  ### <a name="installexecutesequence-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Visual Studio'nun en son sürümü belirlemek InstallExecuteSequence tablo satırları  
  
  |Eylem|Koşul|Dizisi|  
  |------------|---------------|--------------|  
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 DEĞİL (DEVENV_EXE_2003 VEYA DEVENV_EXE_2005)|410|  
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 VE DEVENV_EXE_2005 DEĞİL|420|  
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|  
  
   HKEY_CLASSES_ROOT yazmak için Windows Installer paketi kayıt defteri tabloda DEVENV_EXE_LATEST özelliği kullanabilirsiniz*ProgID*ShellOpenCommand anahtarının varsayılan değeri, [DEVENV_EXE_LATEST] "%1"  
  
- Kullanılabilir VSPackage sürümleri en iyi seçim yapabileceğiniz bir paylaşılan Başlatıcısı programını çalıştırın.  
  
   Geliştiriciler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birçok sürümlerinden neden projeler ve çözümler, birden çok biçimde karmaşık gereksinimleri işlemek için bu yaklaşım seçilmiştir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bu yaklaşımda, bir Başlatıcısı program uzantı işleyici olarak kaydedin. Başlatıcı dosyayı inceler ve hangi sürümünün karar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve bu dosyada, VSPackage işleyebilir. Bir kullanıcı, VSPackage'ı belirli bir sürümü tarafından son kaydedildiği bir dosyasını açarsa, örneğin, başlatıcı bu VSPackage'nın eşleşen sürümünün başlayabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ayrıca, bir kullanıcı her zaman en son sürümünü başlatmak için Başlatıcı yapılandırabilirsiniz. Bir başlatıcı ayrıca dosyasının biçimi yükseltme açmasına isteyebilir. Dosya biçimi sürüm numarası içeriyorsa, bir veya daha fazla yüklenmiş VSPackages sonraki bir sürümün dosya biçiminin olup olmadığını başlatıcısı bir kullanıcıyı bilgilendirmeniz.  
  
   Başlatıcısı, VSPackage'ı tüm sürümleri ile paylaşılan bir Windows Installer bileşeni olması gerekir. Bu işlem, en son sürümü her zaman yüklenir ve tüm sürümlerini, VSPackage kaldırılana kadar kaldırılmaz emin olur. VSPackage'ı bir sürümü kaldırılır olsa bile bu şekilde, dosya ilişkilendirmeleri ve diğer kayıt defteri girdilerini Başlatıcısı bileşenin korunur.  
  
## <a name="uninstall-and-file-associations"></a>Kaldırın ve dosya ilişkilendirmeleri  
 Dosya ilişkilendirmeleri için kayıt defteri girdileri yazan VSPackage kaldırma dosya ilişkilendirmeleri kaldırılır. Bu nedenle, ilişkili bir program yok uzantılıdır. Windows Installer "Vspackage'i yüklediğinizde, eklenen kayıt defteri girdilerini kurtarılmıyor". Bir kullanıcının dosya ilişkilendirmeleri düzeltmek için bazı yollar şunlardır:  
  
-   Daha önce açıklandığı gibi bir paylaşılan Başlatıcısı bileşeni'ni kullanın.  
  
-   Kullanıcının dosya ilişkilendirmesi kendi istediği VSPackage'ı sürümünün bir onarım gerçekleştirin kullanıcıya bildirin.  
  
-   Uygun kayıt defteri girdileri yeniden yazar ayrı bir yürütülebilir program belirtin.  
  
-   Kullanıcıların dosya ilişkilendirmeleri seçin ve kayıp ilişkilendirmeleri geri kazan olanak tanıyan bir yapılandırma seçenekleri sayfası veya iletişim kutusu sağlar. Kullanıcıların kaldırılmasından sonra çalıştırmasına izin vermelerini isteyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yan yana dağıtımlar için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Dosya Adı Uzantıları için Fiil Kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md)

