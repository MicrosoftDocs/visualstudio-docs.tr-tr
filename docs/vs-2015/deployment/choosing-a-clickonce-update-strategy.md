---
title: ClickOnce güncelleştirme stratejisini seçme | Microsoft Docs
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
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2ed97cecb01a8e42a01a3e358ecc953857ca55b6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191353"
---
# <a name="choosing-a-clickonce-update-strategy"></a>ClickOnce Güncelleştirme Stratejisini Seçme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] otomatik uygulama güncelleştirme imkanı verir. A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması düzenli aralıklarla uygulama güncelleştirmeleri kullanılabilir olup olmadığını görmek için dağıtım bildirimi dosyasını okur. Kullanılabilir olması durumunda uygulamanın yeni sürümü indirilir ve çalıştırılır. Verimlilik için, sadece değişen dosyalar indirilir.  
  
 Tasarlarken bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamanın sahip olduğunuz uygulama denetlemek için kullanacağı uygun güncelleştirmeleri hangi stratejiyi belirlemek. Kullanabileceğiniz üç temel strateji vardır: Uygulama başlangıcında güncelleştirmeleri denetleme, uygulama başlangıcından sonra güncelleştirmeleri denetleme (Arka planda bir iş parçacığı çalıştırılır.) veya güncelleştirmeler için bir kullanıcı arayüzü sağlama.  
  
 Ayrıca, uygulama güncelleştirmelerinin ne sıklıkta denetleneceğini belirleyebilirsiniz ve gerekli güncelleştirmeleri yapabilirsiniz.  
  
> [!NOTE]
>  Uygulama güncelleştirmeleri, ağ bağlantısı gerektirir. Ağ bağlantısı mevcut değilse, uygulama güncelleştirme stratejisi ne olursa olsun güncelleştirmeleri denetlemeden çalışacaktır.  
  
> [!NOTE]
>  .NET Framework 2.0 ve .NET Framework 3.0 herhangi uygulamanız güncelleştirmeler için önce veya sonra başlangıç ya da kullanarak denetlediğinde <xref:System.Deployment.Application> API'leri ayarlamalısınız `deploymentProvider` dağıtım bildirimi içinde. `deploymentProvider` Karşılık gelen öğe için Visual Studio'da **güncelleştirme konumu** alanını **güncelleştirmeleri** iletişim kutusunun **Yayımla** sekmesi. .NET Framework 3.5'te bu kural yumuşatılmıştır. Daha fazla bilgi için [dağıtma ClickOnce uygulamaları test etme ve üretim sunucularına Resigning olmadan](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
## <a name="checking-for-updates-after-application-startup"></a>Uygulama Başlangıcından Sonra Güncelleştirmeleri Denetleme  
 Bu stratejiyi kullanarak, uygulama çalışırken, arka planda dağıtım dosyası bildiriminin yerini belirleyip okumayı deneyecektir. Bir güncelleştirme erişilebilirse, kullanıcının uygulamayı sonraki çalıştırmasında, kullanıcı güncelleştirmeyi indirmek ve kurmak için uyarılacaktır.  
  
 Bu strateji en iyi uzun indirmelere ihtiyaç duyacak büyük uygulamalar için veya düşük bant genişliğine sahip ağ bağlantıları için çalışır.  
  
 Bu güncelleştirme stratejisini etkinleştirmek için tıklayın **uygulama başladıktan sonra** içinde **uygulamanın güncelleştirmeleri denetleyeceği zamanı seçin** bölümünü **uygulama güncelleştirmeleri** iletişim kutusu. Ardından bölümünde bir aralık belirtin **uygulamanın güncelleştirmeleri ne sıklıkla denetleyeceğini belirtin**.  
  
 Bu değiştirme ile aynı olur **güncelleştirme** öğesi dağıtım bildirimi gibi:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## <a name="checking-for-updates-before-application-startup"></a>Uygulama Başlangıcından Önce Güncelleştirmeleri Denetleme  
 Varsayılan strateji, uygulama başlatılmadan önce dağıtım bildirimi dosyasının yerini belirleyip okumayı denemektir. Bu strateji kullanarak, kullanıcı uygulamayı her başlattığında, uygulama dağıtım bildirim dosyasının yerini belirleyip okumaya çalışacaktır. Bir güncelleştirme kullanılabilirse, indirilip başlatılacaktır; aksi durumda uygulamanın var olan sürümü başlatılır.  
  
 Bu strateji en iyi yüksek bant genişliğine sahip ağ bağlantıları için çalışır; uygulama başlatımındaki gecikme düşük bantlı bağlantılar için kabul edilemeyecek kadar uzun olabilir.  
  
 Bu güncelleştirme stratejisini etkinleştirmek için tıklayın **Uygulama başlatılmadan önce** içinde **uygulamanın güncelleştirmeleri denetleyeceği zamanı seçin** bölümünü **uygulama güncelleştirmeleri** iletişim kutusu.  
  
 Bu değiştirme ile aynı olur **güncelleştirme** öğesi dağıtım bildirimi gibi:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## <a name="making-updates-required"></a>Gerekli Güncelleştirmeleri Yapma  
 Kullanıcıların uygulamanızın güncelleştirilmiş bir sürümünü çalıştırmasını istediğiniz durumlar olabilir. Örneğin, çalışan uygulamanızın daha eski bir sürümünün doğru olarak çalışmasını engelleyen bir Web hizmeti gibi harici bir kaynakta değişiklik yapabilirsiniz. Bu durumda, güncelleştirmenizi gerekli olarak işaretlemek ve kullanıcıların daha eski sürümleri çalıştırmasını engellemek isteyeceksinizdir.  
  
> [!NOTE]
>  Bir güncelleştirme stratejileri kullanarak güncelleştirmeleri gerekmesine rağmen denetimi **Uygulama başlatılmadan önce** eski bir sürümün çalışmasını engellemenin tek yoludur. Zorunlu güncelleştirme başlangıçta algılandığında, kullanıcının ya güncelleştirmeyi kabul etmesi ya da uygulamayı kapatması gerekir.  
  
 Güncelleştirme gerekli tıklatın olarak işaretlemek için **bu uygulama için gerekli en düşük sürüm belirtin** içinde **uygulama güncelleştirmeleri** iletişim kutusuna ve ardından yayınlama sürümünü belirtin (**ana**, **Küçük**, **derleme**, **düzeltme**), uygulamanın yüklenebilmesi için en düşük sürüm numarasını belirtir.  
  
 Ayar ile aynıdır **minimumRequiredVersion** özniteliği **dağıtım** öğesi dağıtım bildiriminde; örneğin:  
  
```  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## <a name="specifying-update-intervals"></a>Güncelleştirme Aralıkları Belirtme  
 Uygulamanın güncelleştirmeleri ne sıklıkta denetleyeceğini de belirtebilirsiniz. Bunu yapmak için, bu konuda "Uygulama Başlangıcından Sonra Güncelleştirmeleri Denetleme" bölümünde bahsedildiği gibi uygulamanın güncelleştirmeleri başlangıçtan sonra denetleyeceğini belirtin.  
  
 Güncelleştirme aralığını belirtmek için ayarlayın **uygulamanın güncelleştirmeleri ne sıklıkla denetleyeceğini belirtin** özelliklerinde **uygulama güncelleştirmeleri** iletişim kutusu.  
  
 Bu ayarı ile aynı olur **maximumAge** ve **birim** özniteliklerini **güncelleştirme** dağıtım bildirimi içinde öğesi.  
  
 Örneğin, her zaman uygulama çalıştığında, haftada bir defa veya ayda bir defa denetlemek isteyebilirsiniz. Ağ bağlantısı belirtilen zamanda mevcut değilse, güncelleştirme denetimi uygulamanın sonraki açılışında gerçekleştirilir.  
  
## <a name="providing-a-user-interface-for-updates"></a>Güncelleştirmeler için Bir Kullanıcı Arayüzü Sağlama  
 Bu stratejiyi kullanırken, uygulama geliştiricisi kullanıcıya ne zaman veya ne sıklıkta uygulama güncelleştirmeleri denetlensin seçeneği imkanı veren bir kullanıcı arayüzü sağlar. Örneğin, "Güncelleştirmeleri Şimdi Denetle" komutu veya dört farklı güncelleştirme aralığı içeren bir "Güncelleştirme Ayarları" iletişim kutusu sağlayabilirsiniz. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Dağıtım API'leri kendi güncelleştirme kullanıcı arayüzünüzü programlamanız için bir çerçeve sağlar. Daha fazla bilgi için <xref:System.Deployment.Application> ad alanı.  
  
 Uygulamanız kendi güncelleştirme mantığını denetlemek için dağıtım API'leri kullanıyorsa, aşağıdaki bölümde "Güncelleştirme Denetimini Engelleme"de anlatıldığı gibi güncelleştirme denetimini engellemelisiniz.  
  
 Bu strateji, en iyi farklı kullanıcılar için farklı güncelleştirme stratejileri gerektiğinde çalışır.  
  
## <a name="blocking-update-checking"></a>Güncelleştirme Denetimini Engelleme  
 Uygulamanızın güncelleştirme yapmasını tamamen engellemeniz mümkündür. Örneğin, hiçbir zaman güncelleştirilmeyecek basit bir uygulamanız olabilir, ancak yükleme kolaylığı avantajlarından yararlanmak istediğiniz sağladığı [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım.  
  
 Uygulamanız kendi güncelleştirmelerini gerçekleştirmek için dağıtım API'leri kullanıyorsa da, güncelleştirme denetimini engellemelisiniz; bu konudaki "Güncelleştirmeler için Bir Kullanıcı Arayüzü Sağlama" bölümüne bakın.  
  
 Güncelleştirme denetimini engellemek için Temizle **uygulama güncelleştirmeleri denetlesin** uygulama güncelleştirmeleri iletişim kutusundaki onay kutusu.  
  
 Güncelleştirme denetimini kaldırarak ayrıca engelleyebilirsiniz `<Subscription>` Dağıtım bildiriminden etiketi.  
  
## <a name="permission-elevation-and-updates"></a>İzin Yükseltilmesi ve Güncelleştirmeler  
 Yeni bir sürümü bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama gerektirir, önceki sürümünün çalıştığı güven yüksek seviyede [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ona uygulama bu daha yüksek güven düzeyi verilmesini isteyip istemediğini sorarak kullanıcıyı uyarır. Kullanıcı daha yüksek güven düzeyi vermeyi reddederse, güncelleştirme yüklenmez. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamayı yeniden başlatıldığında, yüklemek için kullanıcıyı uyarır. Bu noktada kullanıcı daha yüksek güven düzeyi verilmesini reddedip güncelleştirme gerekli değil şeklinde işaretlenirse, uygulamanın eski sürümü çalışacaktır. Ancak güncelleştirme gerekli ise, uygulama kullanıcı daha yüksek güven düzeyini kabul edene kadar çalışmaz.  
  
 Güvenilir Uygulama Dağıtımı kullanıyorsanız, güven düzeyleri için hiçbir uyarı ile karşılaşmazsınız. Daha fazla bilgi için [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Deployment.Application>   
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce uygulama güncelleştirmelerini nasıl gerçekleştirir](../deployment/how-clickonce-performs-application-updates.md)   
 [Nasıl yapılır: ClickOnce Uygulaması için Güncelleştirmeleri Yönetme](../deployment/how-to-manage-updates-for-a-clickonce-application.md)



