---
title: Bir yük testi çalışma ayarı için Zamanlama Ayrıntıları Depolama özelliği
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 6c82d0898f53bbe9c02126f7379d2d3a0a96fdbf
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054590"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Nasıl yapılır: yük testi çalışma ayarı için zamanlama ayrıntıları depolama özelliğini belirtme

İle yükleme testinizi oluşturduktan sonra **Yeni Yük Testi Sihirbazı**, kullanabileceğiniz **Yük Testi Düzenleyicisi** test ihtiyaçlarınızı ve hedeflerinizi karşılamak için ayarları değiştirmek için.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bir çalışma ayarının düzenleyebileceğiniz **Zamanlama Ayrıntıları Deposu** özellik değerine **özellikleri** penceresi. **Zamanlama Ayrıntıları Deposu** özelliği aşağıdaki seçeneklerden birine ayarlanabilir:

- **Tüm Bireysel Ayrıntılar:** toplar ve her test, hareket ve test sırasında verilen sayfa için bireysel zamanlama verilerini depolar.

  > [!NOTE]
  > **Tüm Bireysel Ayrıntılar** seçeneği, yük testi sonuçlarınızda Sanal kullanıcı veri bilgisini etkinleştirmek için seçilmelidir. Daha fazla bilgi için [Ayrıntılar görünümünde sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

- **Hiçbiri:** herhangi bir zamanlama ayrıntısı toplamaz. Ancak, ortalama değerler hala kullanılabilirdir.

- **Yalnızca İstatistikler:** bağımsız zamanlama verisini sadece yüzdelik veri depolar. Bu, yer kaynaklarından tasarruf sağlar.

  **Zamanlama Ayrıntıları Depolama özelliğini dikkate alınacak noktalar**

  Varsa **Zamanlama Ayrıntıları Deposu** özelliği etkinse, sonra Yük testi sırasında her bir bireysel test, hareket ve sayfa yürütülme zamanı yükleme testi sonuçları deposunda depolanır. Bu 90'ıncı ve 95 yüzdelik veri gösterilmesini sağlar **Yük Testi Çözümleyicisi** içinde **testleri**, **işlemleri**, ve **sayfaları** tablolar.

  Varsa **Zamanlama Ayrıntıları Deposu** özelliği etkinleştirilmişse, değerini ayarlayarak ya da **StatisticsOnly** veya **AllIndividualDetails**, tüm bireysel testler, sayfalar ve hareketler zamanlanır ve bireysel zamanlama verisinden yüzdelik veri hesaplanır. Fark **StatisticsOnly** seçeneği ile yüzdelik veri hesaplandıktan sonra bireysel zamanlama verileri depodan silinir. Bu zamanlama detayları kullanıldığında deposunda gereken alan miktarını azaltır. Ancak, bu durumda, SQL araçları kullanarak zamanlama ayrıntı verilerini farklı yollarla işlemek isteyebilirsiniz **AllIndividualDetails** seçeneği kullanılmalıdır, böylece zamanlama ayrıntı verileri bu işlem için kullanılabilir. Ayrıca, özelliği ayarlamanız **AllIndividualDetails**, kullanan sanal kullanıcı etkinliğini çözümleyebilirsiniz **sanal kullanıcı aktivite grafiği** içinde **Yük Testi Çözümleyicisi** yük testi çalışmayı tamamladıktan sonra. Daha fazla bilgi için [Ayrıntılar görünümünde sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

  Zamanlama ayarları verisini saklamak için yük testi sonuçları deposunda gereken alan miktarı, özellikle daha uzun yük testleri için çok büyük olabilir. Aynı zamanda verileri depoda depolanan bu veriler yük testi yürütmesini, bitirene kadar yükleme testi aracısında depolanır sonunda, yük testi sonuçları deposu uzun olduğundan yük testi bu verileri depolamak için de süre. **Zamanlama Ayrıntıları Deposu** özelliği varsayılan olarak etkindir. Bu test ortamınızın sorunu ise, ayarlamak isteyebilirsiniz **Zamanlama Ayrıntıları Deposu** için **hiçbiri**.

  Verilerin depolandığı zamanlama ayrıntıları *LoadTestItemResults.dat* dosya çalıştırma sırasında ve yükleme testi tamamlandıktan sonra denetleyiciye geri gönderilir. Uzun süre çalışan bir yük testi için dosya boyutu büyüktür. Aracı makinede yeterli disk alanı yoksa, bu bir sorun olacaktır.

  Bir projeyi Visual Studio Yük testinin önceki bir sürümden yükseltiyorsanız, tam ayrıntılı toplamayı etkinleştirmek için aşağıdaki yordamı kullanın.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Bir yük testi içinde zamanlama ayrıntıları depolama özelliğini yapılandırmak için

1.  Bir yük testi, Yük Testi Düzenleyicisi'nde açın.

2.  Genişletin **çalıştırma ayarları** düğüm yük testinde.

3.  Örneğin, yapılandırmak istediğiniz çalıştırma ayarlarını seçin **çalıştırma Ayarları1 [etkin]**.

4.  Açık **özellikleri** penceresi. Üzerinde **görünümü** menüsünde **Özellikler penceresi**.

5.  Altında **sonuçları** kategorisi seçin **Zamanlama Ayrıntıları Deposu** özelliğini tıklatın ve **Tüm Bireysel Ayrıntılar**.

     Yapılandırmasını tamamladıktan sonra **Tüm Bireysel Ayrıntılar** ayarını **Zamanlama Ayrıntıları Deposu** özelliğini yükleme çalıştırabilirsiniz görüntülemek ve test **sanal kullanıcı aktivite grafiği**. Daha fazla bilgi için [nasıl yapılır: yük testi sırasında sanal kullanıcıların ne yaptıklarını çözümleme](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılar görünümünde sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [İzlenecek yol: sorunları yalıtmak için sanal kullanıcı aktivite Grafiği'ni kullanma](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)