---
title: Birden çok işlemciye duyarlı Günlükçüler yazılıyor | Microsoft Docs
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
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b05c0f1782382f437a5e1d90bf19c724a05ca6a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826396"
---
# <a name="writing-multi-processor-aware-loggers"></a>Birden Çok İşlemciye Duyarlı Günlükçüler Yazılıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Yeteneğini [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] birden çok işlemci yararlanmak için süre oluşturmanın proje azaltabilir, ancak ayrıca olay günlüğü oluşturmak için karmaşıklık ekler. Bir tek işlemcili ortamda olaylar, iletiler, uyarıları ve hataları sırasında Günlükçü sıralı tahmin edilebilir bir şekilde ulaşır. Ancak, bir çok işlemcili ortamda farklı kaynaklardan gelen olaylar aynı anda veya sıra dışı ulaşır. Bunun için sağlamak [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] birden çok işlemciye duyarlı bir Günlükçü ve yeni bir günlük modeli sağlar ve özel "iletme günlükçüleri." oluşturmanıza olanak sağlar  
  
## <a name="multi-processor-logging-challenges"></a>Çok işlemcili günlük kaydetme sorunları  
 Birden çok işlemcili veya çok çekirdekli bir sistemde bir veya daha fazla proje oluşturduğunuzda [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] tüm projeleri aynı anda oluşturulan olaylar derleme. Bir olay iletileri avalanche Günlükçü aynı anda veya sıra dışı gelebilir. Çünkü bir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0 Günlükçü bu durumu yönetmek için tasarlanmamıştır, bu Günlükçü sık zora ve artan derleme zamanlarını, yanlış Günlükçü çıkış veya bozuk bir yapının neden. Bu adres sorunlarını için Günlükçü (başlatmadaki [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5) sıra dışı olayları işleyebilir ve olaylar ve kaynakları ilişkilendirin.  
  
 Bir özel iletme Günlükçü oluşturarak daha fazla günlük verimliliği artırabilir. Bir özel iletme Günlükçü vererek bir filtre işlevi görür seçin, derlemeden önce izlemek istediğiniz olayları. Bir özel iletme Günlükçü kullandığınızda, istenmeyen olayları, Günlükçü sık zora, günlüklerinizi dağıtmayı veya yavaş kez derleme olamaz.  
  
## <a name="multi-processor-logging-models"></a>Çok işlemcili günlük kaydetme modelleri  
 Derleme çok-işlemciye ilgili sorunlarda, sağlamak [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , merkezi ve dağıtılmış iki günlük kaydı modelleri destekler.  
  
### <a name="central-logging-model"></a>Merkezi günlük kaydı modeli  
 Merkezi günlük kaydı modelinde, MSBuild.exe tek bir örneğini "merkezi düğümü" olarak görev yapar ve alt örneklerini merkezi düğümü ("ikincil düğüm"), derleme görevleri gerçekleştirmenize yardımcı olmak için merkezi düğümü ekleyin.  
  
 ![Merkezi Günlükçü modeli](../msbuild/media/centralnode.png "CentralNode")  
  
 Günlükçüleri merkezi düğümüne ekleme çeşitli türlerde "merkezi günlükçüler." denir. Her bir Günlükçü türü yalnızca bir örneği aynı anda merkezi düğüme eklenebilir.  
  
 Bir derleme gerçekleştiğinde, ikincil bir düğümü merkezi düğüme kendi derleme olaylarını yönlendirme. Merkezi düğümü, bir veya daha fazla ekli merkezi günlükçüler için tüm olayları ve ayrıca bu ikincil bir düğümü yönlendirir. Günlükçüler ardından gelen verileri temel alan bir günlük dosyalarını oluşturun.  
  
 Yalnızca <xref:Microsoft.Build.Framework.ILogger> olduğu merkezi Günlükçü tarafından uygulanması gereken, ayrıca uygulama öneririz <xref:Microsoft.Build.Framework.INodeLogger> böylece yapı katılan düğüm sayısı ile merkezi Günlükçü başlatır. Aşağıdaki aşırı yükleme <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> Günlükçü altyapısı başlattığında yöntemini çağırır.  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
 Tüm önceden varolan <xref:Microsoft.Build.Framework.ILogger>-tabanlı günlükçüleri merkezi günlükçüleri görev yapabilir ve yapıya ekleyebilirsiniz. Ancak birden çok işlemcili günlük kaydı senaryoları ve sıra dışı olayları açık desteği olmadan yazılan merkezi günlükçüleri bir yapı sonu veya anlamsız çıktı üretir.  
  
### <a name="distributed-logging-model"></a>Dağıtılmış model günlük  
 Aynı anda çok sayıda proje oluşturma sırasında Merkezi günlük kaydı modelinde çok fazla gelen ileti trafiği merkezi düğümü, örneğin, sık zora sokar. Bu, sistem kaynakları stres ve derleme performansı düşürür. Bu sorunu kolaylaştırmak için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] dağıtılmış günlük modelini destekler.  
  
 ![Dağıtılmış günlüğü modeli](../msbuild/media/distnode.png "DistNode")  
  
 Dağıtılmış günlüğü modeli, bir iletme Günlükçü oluşturmanıza izin vererek Merkezi günlük kaydı modelini genişletir.  
  
#### <a name="forwarding-loggers"></a>İletme Günlükçüleri  
 Bir iletme Günlükçü ikincil düğüme ekler ve bu düğümden gelen derleme olayları alan bir olay filtresi olan ikincil ve basit bir Günlükçü ' dir. Bu, gelen olayları filtreler ve merkezi düğümü için belirttiğiniz ayarlara iletir. Bu merkezi düğüme gönderilir ve genel derleme performansı artıran ileti trafiğini azaltır.  
  
 Dağıtılmış, aşağıdaki gibi oturum kullanmanın iki yolu vardır:  
  
- Adlı önceden oluşturulmuş iletme Günlükçü özelleştirme <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>.  
  
- Kendi özel iletme Günlükçü yazın.  
  
  ConfigurableForwardingLogger gereksinimlerinize uyacak şekilde değiştirebilirsiniz. Bunu yapmak için Günlükçü komut satırında MSBuild.exe kullanarak çağırın ve Günlükçü merkezi düğüme iletmek istediğiniz derleme olayları listeler.  
  
  Alternatif olarak, bir özel iletme Günlükçü oluşturabilirsiniz. Bir özel iletme Günlükçü oluşturarak Günlükçü davranışını hassas ayarlamalar yapabilirsiniz. Ancak, bir özel iletme Günlükçü oluşturuluyor yalnızca ConfigurableForwardingLogger özelleştirme daha çok daha karmaşıktır. Daha fazla bilgi için [iletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md).  
  
## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Günlüğe kaydetme için basit ConfigurableForwardingLogger kullanarak dağıtılmış  
 Bir ConfigurableForwardingLogger ya da bir özel iletme Günlükçü eklemek için kullanın `/distributedlogger` geçiş (`/dl` kısaca) MSBuild.exe komut satırı derleme. Günlükçü türlerin ve sınıfların adlarını belirtmek için aynı biçimdir `/logger` geçiş dışında dağıtılmış bir Günlükçü her zaman bir, iletme Günlükçü ve merkezi Günlükçü yerine iki günlük kaydı sınıfları içerir. XMLForwardingLogger adlı bir özel iletme Günlükçü ekleme konusunda bir örnek verilmiştir.  
  
```  
msbuild.exe myproj.proj/distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral  
```  
  
> [!NOTE]
>  Bir yıldız işareti (*) iki Günlükçü adlarında ayırmalısınız `/dl` geçin.  
  
 ConfigurableForwardingLogger kullanmaktır başka bir Günlükçü kullanma gibi (açıklandığı şekilde [derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md)) tipik yerine ConfigurableForwardingLogger Günlükçü ekleme dışında [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Günlükçü ve Merkezi düğüme geçmesine ConfigurableForwardingLogger istediğiniz olayları parametre olarak belirtin.  
  
 Örneğin, bir derleme başladığında ve sona erer ve bir hata oluştuğunda size bildirilmesini istiyorsanız, geçip geçmeyeceğini `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT`, ve `ERROREVENT` parametre olarak. Noktalı virgülle ayrılarak birden çok parametre geçirilebilir. Yalnızca iletmek için ConfigurableForwardingLogger kullanmaya ilişkin bir örnek verilmiştir `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT`, ve `ERROREVENT` olayları.  
  
```  
msbuild.exe myproj.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT  
```  
  
 Kullanılabilir ConfigurableForwardingLogger parametrelerin bir listesi verilmiştir.  
  
|ConfigurableForwardingLogger parametreleri|  
|---------------------------------------------|  
|BUILDSTARTEDEVENT|  
|BUILDFINISHEDEVENT|  
|PROJECTSTARTEDEVENT|  
|PROJECTFINISHEDEVENT|  
|TARGETSTARTEDEVENT|  
|TARGETFINISHEDEVENT|  
|TASKSTARTEDEVENT|  
|TASKFINISHEDEVENT|  
|ERROREVENT|  
|WARNINGEVENT|  
|HIGHMESSAGEEVENT|  
|NORMALMESSAGEEVENT|  
|LOWMESSAGEEVENT|  
|CUSTOMEVENT|  
|KOMUT SATIRI|  
|PERFORMANCESUMMARY|  
|NOSUMMARY|  
|SHOWCOMMANDLINE|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İletme Günlükçüleri Oluşturma](../msbuild/creating-forwarding-loggers.md)



