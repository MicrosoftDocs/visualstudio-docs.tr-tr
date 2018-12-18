---
title: Yapılandırma seçenekleri, genel bakış | Microsoft Docs
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
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44c5f424ec36d3c04403f62547920f59622208a9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747987"
---
# <a name="configuration-options-overview"></a>Yapılandırma Seçeneklerine Genel Bakış
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projelerinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] oluşturulabilir, hatası ayıklanmış, çalıştırma ve/veya dağıtılan birden fazla yapılandırmaları destekler. Açıklanan özellikler, genellikle derleyici anahtarları ve dosya konumlarını adlandırılmış kümesi ile bir yapı türünü bir yapılandırmadır. Varsayılan olarak, yeni çözümleri iki yapılandırma, hata ayıklama ve yayın içerir. Bu yapılandırmalar, kendi varsayılan ayarları kullanarak veya değiştirilmiş çözüm veya proje belirli gereksinimlerinizi karşılamak için uygulanabilir. Bazı paketler iki şekilde oluşturulabilir: yerinde bileşeni olarak veya bir ActiveX Düzenleyici. Projeleri birden çok yapılandırmada ancak destek gerekmez. Kullanılabilir tek yapılandırması varsa, bu yapılandırma tüm çözüm yapılandırmaları eşlenir.  
  
 Yapılandırmaları, genellikle iki bölümden oluşur: platform ayarları ve yapılandırma adı (gibi hata ayıklama veya sürüm). Bir yapılandırmasının platform adı gibi bir API configuration hedefleri ayarlanan ortam veya işletim sistemi platformunu tanımlar. Kullanıcıları [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bir platform; oluşturulamıyor seçimlerden VSPackage sağlayan bir proje seçmelisiniz. Bir kullanıcı yüklemelerini bir VSPackage'ı paket geliştirme sırasında oluşturulan teslim platformu istenen herhangi bir platform adı ne zaman ortaya çıkabilir paket Oluşturucu tarafından ayarlanmış herhangi ölçütlere göre. Kullanıcı, ardından özellik sayfaları örnek oluşturulduğunda VSPackage'ı kullanılabilir platformlar listesinden seçebilirsiniz.  
  
 Platform adlarını isteğe bağlı olduğundan tüm projeleri platformları kavramını destekler. Bir yapılandırma bir platform adı yoksa kullanıcı Arabiriminde "Yok" dizesi görüntülenir.  
  
 Her çözüm yapılandırmaları yalnızca biri aynı anda etkin olabilir, kendi kümesine sahiptir. Bir çözüm yapılandırması, her proje birden fazla yapılandırmasından kümesidir. Bir çözüm yapılandırmasından bir proje dışlamak için seçeneği "en fazla" artını kaynaklanır. Kullanıcılar, kendi özel çözüm yapılandırmaları oluşturabilir.  
  
 Aşağıdaki tabloda, bir proje için yapılandırmalardan Kurulum gösterilmektedir. Satırları yapılandırma adları ve platform adlarını sütunları ile etiketlenir.  
  
|Yapılandırma adı|Platform — Win32|Platform — Win64|  
|------------------------|----------------------|----------------------|  
|Hata ayıklama|\<Hata ayıklama Win32 Ayarları >|\<Hata ayıklama Win64 Ayarları >|  
|Sürüm|\<Yayın Win32 Ayarları >|\<Yayın Win64 Ayarları >|  
|MyConfig|Yok|\<MyConfig Win64 Ayarları >|  
  
> [!NOTE]
>  "Win32" platformu hedeflediğiniz proje Win32 desteklemiyor sürece bırakan bir "MyConfig" çözüm yapılandırması oluşturulamıyor.  
  
 Etkin bir çözüm yapılandırmasını değiştirme bu çözümde oluşturulan, çalıştırma, hata ayıklama veya dağıtıldığı proje yapılandırmaları kümesini seçer. Örneğin, hata ayıklama sürümü etkin çözüm yapılandırmasını değiştirirseniz, bu çözüm içindeki tüm projeleri otomatik olarak çözümün hata ayıklama yapılandırmasında belirtilen proje yapılandırması oluşturulur. Kullanıcı el ile yapılan değişiklikler ortam Yapılandırma Yöneticisi'nde yapmamışsa projelerin genellikle ayrıca adlı hata ayıklama yapılandırmalardır.  
  
 Her proje için depolanan çözüm yapılandırma özellikleri, proje adı, proje yapılandırması adı, alınıp alınmayacağını oluşturmak veya dağıtmak için belirtmek için bayrakları ve platform adı içerir. Daha fazla bilgi için [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md).  
  
 Kullanıcı görüntüleyebilir ve hiyerarşi içinde (Çözüm Gezgini) çözümü seçme ve özellik sayfaları açarak çözümü yapılandırma parametrelerini ayarlayın. Benzer şekilde, görüntüleyebilir ve Çözüm Gezgini'nde bir proje seçerek ve proje özellik sayfalarını açma proje yapılandırma parametrelerini ayarlayın.  
  
 Kullanıcı ayrıca sürüm yapılandırma ayarlarını ve tüm rest gerekirse ile hata ayıklama yapılandırma ayarlarını kullanarak bir proje oluşturabilirsiniz. Daha fazla bilgi için [derleme için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md).  
  
 Aşağıdaki diyagramda, çözüm ve proje yapılandırmaları destekler arabirimleri nasıl uygulandığı gösterilmiştir:  
  
 ![Yapılandırma arabirimleri grafiği](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Yapılandırma arabirimleri  
  
 Önceki diyagramda ilgili birkaç Not:  
  
- `IDispatch` Yapılandırma nesnesi isteğe bağlı olarak işaretlenir. Özellikle, göz atma nesne üzerinde yapılandırma arabirime sahip isteğe bağlıdır.  
  
- `IVsDebuggableProjectCfg` Yapılandırma nesnesi isteğe bağlı olarak işaretlenmiş, ancak hata ayıklama desteği için gereklidir.  
  
- `IVsProjectCfg2` Yapılandırma nesnesi isteğe bağlı olarak işaretlenmiş, ancak çıkış destek gruplandırma için gereklidir.  
  
- `Config Provider` Nesne, isteğe bağlı bir nesne olarak işaretlenmiş, ancak seçeneğini uygulamak yerdir. Proje nesne veya ayrı bir nesne üzerinde nesne uygulayabilir.  
  
- `IVsCfgProvider2` platform desteği ve yapılandırmasını düzenleme için gereklidir. `IVsCfgProvider` Bu işlevselliği uygulamak, yeterli olur.  
  
- Aşağıdaki diyagramda ayrı nesneler aynı sınıfına pratik olduğunda birleştirilebilir olarak gösterilen bu nesnelerin bazıları belirli tasarım gereksinimlerinize göre. Bu bölümdeki diğer konulara göz ancak nesneleri ve bu nesnelerle ilişkili arabirimi Diyagramda gösterilen senaryoya göre açıklanmıştır.  
  
- Belirli nesneleri ayrı ayrı uygulanır. Örneğin, ayrı iş parçacığı ve nesne derleme olduğu yapı yapılandırmasını tanımlayan nesne ayrı olarak yönetmek için proje ve çözüm oluşturma oluşur.  
  
  Yapılandırma nesnesi arabirimleri ve önceki diyagramdaki yapılandırma sağlayıcısı nesnesi arabirimleri hakkında daha fazla bilgi için bkz: [proje yapılandırması nesnesi](../../extensibility/internals/project-configuration-object.md). Ayrıca, [derleme için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md) yapılandırma oluşturucusu ve derleme bağımlılık nesnesi arabirimleri üzerinde daha fazla bilgi sağlar ve [dağıtımı yönetmek için proje yapılandırması](../../extensibility/internals/project-configuration-for-managing-deployment.md) Daha fazla yapılandırma dağıtıcı ve dağıtım bağımlılık nesneleri bağlı arabirimler açıklanmaktadır. Son olarak, [çıkış için proje yapılandırması](../../extensibility/internals/project-configuration-for-output.md) çıkış grubu ve çıkış nesnesi arabirimleri ve özellik sayfaları görüntülemek ve yapılandırmaya bağlı özellikleri ayarlamak için kullanımını açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Derleme için proje yapılandırması](../../extensibility/internals/project-configuration-for-building.md)   
 [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)

