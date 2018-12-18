---
title: Kaynak Denetimi Eklentisi uygulamak için en iyi uygulamalar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 16699f520390c0bc4f062f9db82e66a26ef5fd8f
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154215"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Kaynak Denetimi Eklentisi uygulamak için en iyi yöntemler
Aşağıdaki teknik ayrıntıları'nın, güvenilir bir şekilde bir kaynak denetimi eklentisi içinde yardımcı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="memory-management-issues"></a>Bellek yönetimi sorunları  
 Çoğu durumda, çağıranın olan, tümleşik geliştirme ortamı (IDE), serbest bırakır ve bellek ayırır. Kaynak Denetimi Eklentisi, dizeler ve diğer öğeleri arayana ayrılan arabellekler döndürür. Özel durumlar, belirli işlevleri sonuçları ortaya çıktıkları açıklamasında belirtilmiştir.  
  
## <a name="arrays-of-file-names"></a>Dosya adları dizileri  
 Dosyaları bir dizi geçirildiğinde, dosya adları bitişik bir dizi olarak aktarılmaz. Dosya adları için bunu bir işaretçiler dizisi geçirilir. Örneğin, [SccGet](../extensibility/sccget-function.md), dosya adları geçirilir `lpFileNames` parametresi, burada `lpFileNames` gerçekten bir işaretçi bir `char **`. `lpFileNames`[0] ad işaretçisidir `lpFileNames`[1] ikinci adı vb. işaretçisidir.  
  
## <a name="large-model"></a>Büyük model  
 Tüm işaretçiler, 32 bit ve 16-bit işletim sistemlerinde bile ' dir.  
  
## <a name="fully-qualified-paths"></a>Tam olarak nitelenmiş yollar  
 Burada dosya adlarını veya dizinleri bağımsız değişken olarak belirtilirse, tam yol veya UNC yolları, bitiş ters eğik çizgi olmadan olması gerekir. Kaynak Denetimi Eklentisi bu temel alınan kaynak denetim sistemi gereksinimi diğer bir deyişle, göreli yollar çevrilecek sorumluluğundadır.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Kayıtlı DLL için tam nitelenmiş bir yol belirtin  
 IDE DLL'leri göreli yolları artık yükler. (örneğin, *.\NewProvider.dll*). DLL Dosyasının tam yolu belirtilmelidir (örneğin, *C:\Providers\NewProvider.dll*). Bu gereksinim, yetkisiz veya başkasının kimliğine bürünülerek gerçekleştirilen kaynak denetimi DLL'lerin yüklenmesini engelleyerek IDE güvenliğini güçlendirir.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Bir kaynak denetimi eklentiniz yüklediğinizde eklentisi varolan VSSCI denetle  
 Kaynak Denetimi Eklentisi yükleme planları bir kullanıcı zaten yüklü bir var olan kaynak denetimi eklentisi olabilir. Yükleme (Kur) programı eklenti için oluşturduğunuz ilgili kayıt defteri anahtarları için mevcut değerleri olup olmadığını belirlemeniz gerekir. Bu anahtarları zaten ayarlanmışsa, Kurulum programınızı, eklentiyi varsayılan kaynak denetimi eklentisi kaydetmek ve zaten yüklü bir değiştirin kullanıcı istemelisiniz.  
  
## <a name="error-result-codes-and-reporting"></a>Hata sonuç kodlarını ve Raporlama  
 `SCC_OK` Dönüş kodu kaynak denetim işlevi için gösterir işlemi tüm dosyalar için başarılı oldu. İşlem başarısız olursa, karşılaşılan son hata kodu iade beklenir.  
  
 Raporlama için IDE içinde bir hata meydana gelirse, IDE raporlama için sorumlu olduğu kuralıdır. Kaynak denetim sistemi bir hata meydana gelirse, raporlama için kaynak denetimi eklentisi sorumludur. Örneğin, **şu anda seçili dosya** ise IDE bildirilebilecek **bu dosya zaten kullanıma** eklenti tarafından bildirilebilecek.  
  
## <a name="the-context-structure"></a>Bağlam yapısı  
 Çağrı sırasında [Sccınitialize](../extensibility/sccinitialize-function.md), çağıran geçişleri `ppvContext` parametresini bir void başlatılmamış bir işleyicisidir. Kaynak Denetimi Eklentisi Bu parametre yoksayabilirsiniz veya bir yapının herhangi bir türde ayırın ve bir işaretçi bu yapıya geçirilen imleci yerleştirin. IDE bu yapı tanımıyor, ancak her bir çağrı eklentide halinde bu yapıya bir işaretçi geçirir. Bu genel değişkenler kullanmadan işlev çağrıları arasında kalıcı genel durum bilgilerini korumak için kullanabileceğiniz bu eklentiye değerli bağlam önbelleği bilgilerini sağlar. Eklentinin bir çağrı yapıdaki boşaltma için sorumlu olduğu [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Eklenti kümeleri `SCC_CAP_REENTRANT` içindeki bit [Sccınitialize](../extensibility/sccinitialize-function.md) (özellikle de `lpSccCaps` parametresi), birden çok içerik yapıları açık olan tüm projeleri izlemek için kullanılır.  
  
## <a name="bitflags-and-other-command-options"></a>Bit bayrakları ve diğer komut seçenekleri  
 Her komut için gibi [SccGet](../extensibility/sccget-function.md), IDE komut davranışını değiştirmek pek çok seçenek belirtebilirsiniz.  
  
 API, belirli seçenekleri aracılığıyla IDE ile ayarını destekler `fOptions` parametresi. Bu seçeneği, şurada açıklanan [özel komutlar tarafından kullanılan bit bayrakları](../extensibility/bitflags-used-by-specific-commands.md) etkiledikleri komutları birlikte. Genel olarak, bunlar için kullanıcı olmayan girmeniz istenirdi seçeneklerdir.  
  
 Yaygın olarak kaynak denetimi eklentileri arasında değiştiğinden en kullanıcı tarafından yapılandırılabilir seçenekleri bu şekilde, tanımlı değil. Bu nedenle, önerilen mekanizmadır bir **Gelişmiş** düğmesi. Örneğin, **alma** iletişim kutusu, IDE'yi anlar, ancak aynı zamanda görüntüler bilgi görüntüler bir **Gelişmiş** düğmesi eklentisi bu komutu için seçenek vardır. Kullanıcı tıkladığında **Gelişmiş** button, IDE çağrıları [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) bit bayrakları ya da bir tarih/saat gibi bilgileri kullanıcıdan eklenti kaynak denetimi etkinleştirmek için. Geri sırasında geçirilen bir yapı bu bilgileri eklenti döndürür `SccGet` komutu.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [Kaynak Denetimi Eklentisi oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md)