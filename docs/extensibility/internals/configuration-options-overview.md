---
title: Yapılandırma seçenekleri, genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fde39c346313dc66d5d94a5beb0e9e3b256ea436
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920228"
---
# <a name="configuration-options-overview"></a>Yapılandırma seçeneklerine genel bakış
Projelerinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oluşturulabilir, hatası ayıklanmış, çalıştırma ve/veya dağıtılan birden fazla yapılandırmaları destekler. Açıklanan özellikler, genellikle derleyici anahtarları ve dosya konumlarını adlandırılmış kümesi ile bir yapı türünü bir yapılandırmadır. Varsayılan olarak, yeni çözümleri iki yapılandırması içeren *hata ayıklama* ve *yayın*. Bu yapılandırmalar, kendi varsayılan ayarları kullanarak veya değiştirilmiş çözüm veya proje belirli gereksinimlerinizi karşılamak için uygulanabilir. Bazı paketler iki şekilde oluşturulabilir: yerinde bileşeni olarak veya bir ActiveX Düzenleyici. Projeleri birden çok yapılandırmada ancak destek gerekmez. Kullanılabilir tek yapılandırması varsa, bu yapılandırma tüm çözüm yapılandırmaları eşlenir.  
  
 Yapılandırmaları, genellikle iki bölümden oluşur: yapılandırma adı (gibi *hata ayıklama* veya *yayın*) platform ayarları. Bir yapılandırmasının platform adı gibi bir API configuration hedefleri ayarlanan ortam veya işletim sistemi platformunu tanımlar. Kullanıcıları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir platform; oluşturulamıyor seçimlerden VSPackage sağlayan bir proje seçmelisiniz. Bir kullanıcı yüklemelerini bir VSPackage'ı paket geliştirme sırasında oluşturulan teslim platformu istenen herhangi bir platform adı ne zaman ortaya çıkabilir paket Oluşturucu tarafından ayarlanmış herhangi ölçütlere göre. Kullanıcı, ardından özellik sayfaları örnek oluşturulduğunda VSPackage'ı kullanılabilir platformlar listesinden seçebilirsiniz.  
  
 Platform adlarını isteğe bağlı olduğundan tüm projeleri platformları kavramını destekler. Ne zaman bir yapılandırma eksik dize bir platform adı **yok** kullanıcı Arabiriminde görüntülenir.  
  
 Her çözüm yapılandırmaları yalnızca biri aynı anda etkin olabilir, kendi kümesine sahiptir. Bir çözüm yapılandırması, her proje birden fazla yapılandırmasından kümesidir. Bir çözüm yapılandırmasından bir proje dışlamak için seçeneği "en fazla" artını kaynaklanır. Kullanıcılar, kendi özel çözüm yapılandırmaları oluşturabilir.  
  
 Aşağıdaki tabloda, bir proje için yapılandırmalardan Kurulum gösterilmektedir. Satırları yapılandırma adları ve platform adlarını sütunları ile etiketlenir.  
  
|Yapılandırma adı|Platform: Win32|Platform: Win64|  
|------------------------|----------------------|----------------------|  
|*Hata ayıklama*|\<Hata ayıklama Win32 Ayarları >|\<Hata ayıklama Win64 Ayarları >|  
|*Sürüm*|\<Yayın Win32 Ayarları >|\<Yayın Win64 Ayarları >|  
|*MyConfig*|Yok|\<MyConfig Win64 Ayarları >|  
  
> [!NOTE]
>  Oluşturamazsınız bir *MyConfig* Win32 platformu hedeflediğiniz proje sürece bırakan çözüm yapılandırma Win32 desteklemez.  
  
 Etkin bir çözüm yapılandırmasını değiştirme bu çözümde oluşturulan, çalıştırma, hata ayıklama dağıtılan veya proje yapılandırmaları kümesini seçer. Örneğin, etkin çözüm yapılandırmasını değiştirirseniz *yayın* için *hata ayıklama*, tüm projeler, çözüm içinde belirtilen proje yapılandırması ile otomatik olarak oluşturulur çözümün hata ayıklama yapılandırması. Ayrıca proje yapılandırmaları adlı *hata ayıklama* sürece kullanıcı ortamının Yapılandırma Yöneticisi'nde el ile değişiklikler yaptı.  
  
 Her proje için depolanan çözüm yapılandırma özellikleri, proje adı, proje yapılandırması adı, alınıp alınmayacağını oluşturmak veya dağıtmak için belirtmek için bayrakları ve platform adı içerir. Daha fazla bilgi için [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md).  
  
 Kullanıcı görüntüleyebilir ve hiyerarşi içinde (Çözüm Gezgini) çözümü seçme ve özellik sayfaları açarak çözümü yapılandırma parametrelerini ayarlayın. Benzer şekilde, görüntüleyebilir ve Çözüm Gezgini'nde bir proje seçerek ve proje özellik sayfalarını açma proje yapılandırma parametrelerini ayarlayın.  
  
 Kullanıcı ayrıca sürüm yapılandırma ayarlarını ve diğer hata ayıklama yapılandırma ayarlarıyla gerekirse kullanarak bir proje oluşturabilirsiniz. Daha fazla bilgi için [derleme için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md).  
  
 Aşağıdaki diyagramda, çözüm ve proje yapılandırmaları destekler arabirimleri nasıl uygulandığı gösterilmiştir:  
  
 ![Yapılandırma arabirimleri grafiği](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Yapılandırma arabirimleri  
  
 Önceki diyagramda ilgili birkaç Not:  
  
- `IDispatch` İsteğe bağlı yapılandırma nesnesi olarak işaretlenir. Özellikle, göz atma nesne üzerinde yapılandırma arabirime sahip isteğe bağlıdır.  
  
- `IVsDebuggableProjectCfg` Yapılandırma nesnesi isteğe bağlı olarak işaretlenmiş, ancak hata ayıklama desteği için gereklidir.  
  
- `IVsProjectCfg2` Yapılandırma nesnesi isteğe bağlı olarak işaretlenmiş, ancak çıkış destek gruplandırma için gereklidir.  
  
- Yapılandırma sağlayıcısı nesne isteğe bağlı bir nesne olarak işaretlenmiş ancak seçeneğini uygulamak yerdir. Proje nesne veya ayrı bir nesne üzerinde nesne uygulayabilir.  
  
- `IVsCfgProvider2` platform desteği ve yapılandırmasını düzenleme için gereklidir. `IVsCfgProvider` Bu işlevselliği uygulamak, yeterli olur.  
  
- Aşağıdaki diyagramda ayrı nesneler aynı sınıfına pratik olduğunda birleştirilebilir olarak gösterilen bu nesnelerin bazıları belirli tasarım gereksinimlerinize göre. Bu bölümdeki diğer konulara göz ancak nesneleri ve bu nesnelerle ilişkili arabirimi Diyagramda gösterilen senaryoya göre açıklanmıştır.  
  
- Belirli nesneleri ayrı ayrı uygulanır. Örneğin, ayrı iş parçacığı ve nesne derleme olduğu yapı yapılandırmasını tanımlayan nesne ayrı olarak yönetmek için proje ve çözüm oluşturma oluşur.  
  
  Önceki diyagramda yapılandırma sağlayıcısı nesnesi arabirimleri ve yapılandırma nesnesi arabirimleri hakkında daha fazla bilgi için bkz. [proje yapılandırması nesnesi](../../extensibility/internals/project-configuration-object.md). Ayrıca, [derleme için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md) nesnesi arabirimleri yapılandırma oluşturucusu ve yapı bağımlılığını daha fazla bilgi sağlar ve [dağıtımını yönetmek için proje yapılandırması](../../extensibility/internals/project-configuration-for-managing-deployment.md) Daha fazla yapılandırma dağıtıcı ve dağıtım bağımlılık nesneleri bağlı arabirimler açıklanmaktadır. Son olarak, [çıkış için proje yapılandırması](../../extensibility/internals/project-configuration-for-output.md) görüntülemek ve yapılandırmaya bağlı özellikleri ayarlamak için çıkış grubu ve çıkış nesnesi arabirimleri ve özellik sayfaları kullanımını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Derleme için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md)   
 [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)