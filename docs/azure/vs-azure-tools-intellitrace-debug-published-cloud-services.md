---
title: Bir Azure bulut hizmeti IntelliTrace ile hata ayıklama yayımlama
description: Bir bulut hizmetinde Visual Studio ve IntelliTrace ile hata ayıklama hakkında bilgi edinin
author: mikejo5000
manager: douge
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: seodec18
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.openlocfilehash: 20c8ac64707c6305b8677c8567855bb7c7e37491
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061665"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Visual Studio ve IntelliTrace ile yayımlanan bir Azure bulut hizmetinin hatalarını ayıklama
IntelliTrace ile Azure içinde çalıştığında bir rol örneği için kapsamlı hata ayıklama bilgileri günlüğe kaydedebilirsiniz. Bir sorunun nedenini bulmak gerekiyorsa, IntelliTrace günlüklerini, Visual Studio'dan, Azure'da çalışıyormuş gibi kodunuzda adım adım ilerleyin için de kullanabilirsiniz. Aslında Azure uygulamanızın Azure'daki bir bulut hizmeti olarak çalışan ve Visual Studio'dan kaydedilen verileri yeniden yürütme olanak tanır, Intellitrace'in kaydettiği kod yürütme ve ortam verilerini anahtarı. 

Visual Studio Enterprise yüklüyse IntelliTrace ve Azure uygulama hedeflerinizi .NET Framework 4 veya sonraki bir sürümünü kullanabilirsiniz. IntelliTrace rollerinizi Azure için bilgi toplar. Bu roller için sanal makinelerin her zaman 64-bit işletim sistemlerinde çalışır.

Alternatif olarak, kullandığınız [uzaktan hata ayıklama](http://go.microsoft.com/fwlink/p/?LinkId=623041) doğrudan Azure'da çalışan bir bulut hizmetine eklemek için.

> [!IMPORTANT]
> IntelliTrace yalnızca hata ayıklama senaryoları içindir ve Üretim dağıtımı için kullanılmamalıdır.
> 

## <a name="configure-an-azure-application-for-intellitrace"></a>Azure uygulaması için IntelliTrace'i yapılandırın
Azure uygulaması için IntelliTrace etkinleştirmek için oluşturma ve bir Visual Studio Azure project uygulamayı yayımlayın. Azure'da yayımlamadan önce Azure uygulamanız için IntelliTrace yapılandırmanız gerekir. IntelliTrace yapılandırmadan uygulamanızı yayımlayın, projeyi yeniden yayımlamanız gerekir. Daha fazla bilgi için [yayımlama bir Azure bulut hizmeti projeleri Visual Studio kullanarak](http://go.microsoft.com/fwlink/p/?LinkId=623012).

1. Azure uygulamanızı dağıtmaya hazır olduğunuzda, Proje yapı hedefleri ayarlandığından doğrulayın **hata ayıklama**.

1. İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve bağlam menüsünden seçin **Yayımla**.
   
1. İçinde **Azure uygulamasını Yayımla** iletişim, Azure aboneliği seçin ve Seç **sonraki**.

1. İçinde **ayarları** sayfasında **Gelişmiş ayarlar** sekmesi.

1. Açma **IntelliTrace'i etkinleştirin** bulutta yayımlandığında uygulamanız için IntelliTrace günlükleri toplamak için seçeneği.
   
1. Temel IntelliTrace yapılandırma özelleştirmek için işaretleyin **ayarları** yanındaki **IntelliTrace'i etkinleştirin**.

    ![IntelliTrace ayarları bağlantısı](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)
   
1. İçinde **IntelliTrace ayarları** iletişim kutusunda, hangi olayların günlük, çağrı bilgilerini toplamak etkinleştirilip etkinleştirilmeyeceğini, hangi modüllerin ve toplamak için işlemleri günlüğe kaydeder ve kayıt için ayırmak üzere ne kadar alan belirtebilirsiniz. IntelliTrace hakkında daha fazla bilgi için bkz: [IntelliTrace ile hata ayıklama](http://go.microsoft.com/fwlink/?LinkId=214468).
   
    ![IntelliTrace ayarları](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

IntelliTrace günlük (varsayılan boyutu 250 MB'tır) IntelliTrace ayarlarında belirtilen disk boyutu, döngüsel günlük dosyasıdır. Sanal makine dosya sistemindeki bir dosyaya IntelliTrace günlükleri toplanır. Günlükleri istediğinizde, bir anlık görüntü o noktasında alınan ve yerel bilgisayarınıza indirilir.

Azure bulut hizmeti, Azure'a yayımlandıktan sonra IntelliTrace Azure düğümünden etkinleştirilmiş olup olmadığını belirleyebilirsiniz **Sunucu Gezgini**, aşağıdaki görüntüde gösterildiği gibi:

![Sunucu Gezgini - etkin IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Bir rol örneği için IntelliTrace günlüklerini indir
Visual Studio kullanarak, aşağıdaki adımları izleyerek bir rol örneği için IntelliTrace günlüklerini indirebilirsiniz:

1. İçinde **Sunucu Gezgini**, genişletme **Cloud Services** düğümünü ve günlükleri indirmek istediğiniz rol örneği bulun. 

1. Rol örneği sağ tıklayın ve s bağlam menüsünden seçin **IntelliTrace günlüklerini görüntüle**. 

    ![IntelliTrace günlüklerini menü seçeneği görüntüleyin](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. IntelliTrace günlüklerinin yerel bilgisayarınızda bir dizindeki bir dosya indirilir. IntelliTrace istek her zaman günlükleri, yeni bir anlık görüntü oluşturulur. Günlükleri indirilirken, Visual Studio işlemin ilerlemesini görüntüler **Azure etkinlik günlüğü** penceresi. Aşağıdaki resimde gösterildiği gibi işlemin daha fazla ayrıntı görmek için satır öğesi genişletebilirsiniz.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

IntelliTrace günlüklerini indirerek Visual Studio'da çalışmaya devam edebilirsiniz. Günlük indirmeyi bitirdiğinde, Visual Studio'da açılır.

> [!NOTE]
> IntelliTrace günlüklerini framework oluşturur ve ardından işleyen özel durumları içerebilir. Bu özel durumlar için bunları güvenle yoksayabilirsiniz bir rolü, başlatma, normal bir parçası olarak iç framework kod oluşturur.
> 
> 

## <a name="next-steps"></a>Sonraki adımlar
- [Azure bulut hizmetlerinde hata ayıklama seçenekleri](vs-azure-tools-debugging-cloud-services-overview.md)
- [Visual Studio kullanarak bir Azure bulut hizmeti yayımlama](vs-azure-tools-publishing-a-cloud-service.md)