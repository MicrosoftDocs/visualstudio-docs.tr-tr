---
title: Birden çok işlemcili ortamda oturum açma | Microsoft Docs
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
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc2a75c5aab920d6b2ab93ce53bc7f65263e8657
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249671"
---
# <a name="logging-in-a-multi-processor-environment"></a>Birden Çok İşlemcili Ortamda Oturum Açma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Birden çok işlemci kullanma yeteneğini MSBuild proje süre oluşturmanın önemli ölçüde azaltabilir, ancak ayrıca günlüğe kaydetme için karmaşıklık ekler. Bir tek işlemcili ortamda Günlükçü gelen olayları, iletileri, uyarılar ve hatalar sıralı tahmin edilebilir bir şekilde işleyebilir. Ancak, birden çok işlemcili ortamda, çeşitli kaynaklardan gelen olaylar aynı anda veya sıra dışı gelmesi. MSBuild özel "iletme günlükçüleri." oluşturmayı etkinleştirir ve birden çok işlemciye duyarlı olan yeni bir Günlükçü sağlar  
  
## <a name="logging-multiple-processor-builds"></a>Birden çok işlemcili günlük oluşturur  
 Birden çok işlemcili veya çok çekirdekli bir sistemde bir veya daha fazla proje oluşturduğunuzda, MSBuild derleme olaylarını tüm projeleri aynı anda oluşturulur. Olay verilerinin bir avalanche Günlükçü aynı anda veya sıra dışı gelebilir. Günlükçü sık zora ve artan derleme zamanlarını, yanlış Günlükçü çıkış veya bozuk bir yapının neden olabilir. Bu sorunları ele almak için MSBuild Günlükçü sıra dışı olayları işleyebilir ve olaylar ve kaynakları ilişkilendirin.  
  
 Bir özel iletme Günlükçü oluşturarak daha fazla günlük verimliliği artırabilir. Bir özel iletme Günlükçü vererek bir filtre işlevi görür seçin, derlemeden önce izlemek istediğiniz olayları. Bir özel iletme Günlükçü kullandığınızda, istenmeyen olayları değil Günlükçü sık zora, günlüklerinizi dağıtmayı veya yavaş zamanları oluşturun.  
  
### <a name="central-logging-model"></a>Merkezi günlük kaydı modeli  
 Birden çok işlemcili derlemeler için MSBuild "Merkezi günlük kaydı modeli." kullanır. Merkezi günlük kaydı modelinde, MSBuild.exe örneği, birincil yapı işlemi ya da "merkezi düğümü." çalışır. İkincil örneğini MSBuild.exe veya "ikincil düğüm," merkezi düğümüne eklenir. Merkezi düğüme bağlı herhangi bir ILogger tabanlı günlükçüleri "merkezi günlükçüleri" olarak adlandırılır ve ikincil düğümlerine ekli günlükçüleri "ikincil günlükçüler." olarak bilinir  
  
 Bir derleme gerçekleştiğinde, ikincil günlükçüler olay trafiklerini merkezi günlükçüler için yönlendirme. İkincil düğümlerde olayları kaynaklı olduğundan, veri merkezi bir düğümde aynı anda ulaşan ancak aralıklı. Olay proje ve olay hedef başvurularını çözümlemek için olay bağımsız değişkenleri ek yapı olay bağlam bilgilerini içerir.  
  
 Yalnızca <xref:Microsoft.Build.Framework.ILogger> olduğu merkezi bir Günlükçü tarafından uygulanması gereken, ayrıca uygulama öneririz <xref:Microsoft.Build.Framework.INodeLogger> merkezi Günlükçü yapı katılan düğüm sayısı ile başlatmak istiyorsanız. Aşağıdaki aşırı yükleme <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> Günlükçü altyapısı başlattığında yöntemi çağrılır:  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### <a name="distributed-logging-model"></a>Dağıtılmış model günlük  
 Merkezi günlük kaydı modelinde, ne zaman tek seferde çok sayıda proje yapı gibi çok fazla gelen ileti trafiği, sistem stresses ve derleme performansı düşürür merkezi düğümü sık zora sokar.  
  
 Bu sorunu azaltmak için MSBuild "iletme günlükçüleri oluşturma vererek Merkezi günlük kaydı modelini genişletir bir dağıtılmış günlük modeli" de sağlar. Bir iletme Günlükçü, ikincil bir düğüme bağlı olduğundan ve bu düğümden gelen derleme olayları alır. İletme Günlükçü olayları filtre uygulayabilir ve ardından merkezi düğümü yalnızca istenen ayarlara iletin dışında yalnızca normal bir Günlükçü gibi aynıdır. Bu işlem merkezi düğümü, ileti trafiğini azaltır ve bu nedenle daha iyi performans sağlar.  
  
 Bir iletme Günlükçü uygulayarak oluşturabilirsiniz <xref:Microsoft.Build.Framework.IForwardingLogger> türetilen arabirimi <xref:Microsoft.Build.Framework.ILogger>. Arabirim olarak tanımlanır:  
  
```  
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 Bir iletme Günlükçü olayları iletmek için çağrı <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> yöntemi <xref:Microsoft.Build.Framework.IEventRedirector> arabirimi. Uygun geçirmek <xref:Microsoft.Build.Framework.BuildEventArgs>, ya da parametre olarak bir türev.  
  
 Daha fazla bilgi için [iletme Günlükçüleri oluşturma](../msbuild/creating-forwarding-loggers.md).  
  
### <a name="attaching-a-distributed-logger"></a>Dağıtılmış bir Günlükçü ekleme  
 Bir komut satırı derleme üzerinde dağıtılmış bir Günlükçü eklemek için kullanın `/distributedlogger` (veya `/dl` kısaca) geçin. Günlükçü türlerin ve sınıfların adlarını belirtmek için biçim aynıdır olanlar için `/logger` geçiş dışında dağıtılmış bir Günlükçü iki günlük kaydı sınıfları oluşur: bir iletme Günlükçü ve merkezi bir Günlükçü. Dağıtılmış bir Günlükçü ekleme bir örneği verilmiştir:  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 İki Günlükçü adlarında bir yıldız işareti (*) ayıran `/dl` geçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Günlükçüleri derleme](../msbuild/build-loggers.md)   
 [İletme Günlükçüleri Oluşturma](../msbuild/creating-forwarding-loggers.md)





