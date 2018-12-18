---
title: Bir yük testi çalışma ayarına bağlam parametreleri ekleme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: cefa93a6f65b4b84b4ece5a4eb428d909dd0596d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53048502"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Nasıl yapılır: yük testi çalışma ayarı için bağlam parametreleri ekleme

Kullanarak yük testi oluşturduktan sonra **Yeni Yük Testi Sihirbazı**, kullanabileceğiniz **Yük Testi Düzenleyicisi** test ihtiyaçlarınızı ve hedeflerinizi karşılayacak şekilde değiştirmek için.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Çalıştırma ayarları özellikleri ve açıklamalarının tam listesi için bkz: [yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).

Çalışma ayarları Yük Testi Düzenleyicisi'ni kullanarak bir yük testinde kullanmak için bağlam parametreleri oluşturabilirsiniz. Bağlam parametreleri bir dizeyi parametre haline getirmek olanak tanır.

Zaten bir bağlam parametresi kullanılarak bir parametreli web sunucusu URL'sini kullanan bir web performans testi, yük testi içerdiğini varsayın. Web performans testinde kullanılan olarak aynı adı değeri kullanan ayarı yük testi için bir bağlam parametresi ekleyebilirsiniz. Yük testi çalıştırdığınızda, bu farklı bir sunucuya web performans testini eşleyecektir. Örneğin, yük testi, URL'deki web sunucusunun adı için websunucusu1 adlı bir bağlam parametresi kullanan bir web performans testi içerir. Yük testi, Yük testiniz çalışma ayarı da WebServer1 adlı bir bağlam parametresi ardından belirtirseniz, yük testi çalışma ayarı atanan bağlam parametresi kullanır. Web performans testi yük testinde yük testinde bağlam parametresi olarak aynı bağlam parametresi adı kullanıyorsa, anlaşılması için yük testinde bağlam parametresi ve web performans testinde kullanılan bağlam parametresi geçersiz kılar.

> [!WARNING]
> Bağlam parametreleri bir çalışma ayarında kullandığınızda yanlışlıkla bir web performans testi bağlam parametresi geçersiz dikkat edin. Bu kasıtlı olarak yapmadığınız sürece aynı bağlam parametre adları kullanmaktan kaçının.

Websunucusu1 bağlam parametresi değeri atamanız durumunda `http://CorporateStagingWebServer`, ardından `WebServer1` yük boyunca, test ve böylece bir kolayca değeri farklı bir web sunucusuna dilediğiniz zaman değiştirin.

Ayrıca, farklı bir yük testi çalışma ayarlarında aynı adı kullanarak bir bağlam parametresi için farklı değerler atama tarafından yük testi farklı ortamları kullanarak çalıştırabilirsiniz:

- Kurumsal hazırlama Web sunucusuna çalışma ayarına: adlı bağlam parametresi `WebServer1=http://CorporateStagingWebServer`

- Kurumsal üretim Web sunucusu çalıştırma ayarı: adlı bağlam parametresi `WebServer1=http://CorporateProductionWebServer`

  **Komut satırından çalıştırma ayarını değiştirme**

  Bağlam parametresi stratejisi yararlanmak için farklı çalıştırma ayarları komut satırından kullanmak istiyorsanız, aşağıdaki komutları kullanın:

  **Test.UseRunSetting= CorporateStagingWebServer ayarlayın**

  - ve -

  **MSTest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Bir çalışma ayarına bağlam parametresi eklemek için

1.  Bir yük testi açın.

2.  Genişletin **çalıştırma ayarları** Yük Testi Düzenleyicisi'nde yük testi ağacında klasör.

3.  Belirli çalıştırma ayarını sağ bağlam parametresi ekleyin ve ardından istediğiniz **bağlam parametresi Ekle**.

     Yeni bir bağlam parametresi eklenir **bağlam parametreleri** klasöründe **çalıştırma ayarları** yük testi ağacında klasör.

     veya

     Çalıştırma ayarı zaten varsa bir **bağlam parametreleri** klasörüne sağ tıklayın ve ardından **bağlam parametresi Ekle**.

4.  İçinde **özellikleri** penceresinde değerini **adı** uygun şekilde (örneğin, WebServer1). İçinde **özellikleri** penceresinde değişiklik **değer** kullanmak istediğiniz parametre (örneğin, `http://CorporateStagingWebServer`).

5.  (İsteğe bağlı) 3 ile 5 arasındaki adımları yineleyin ve kullanmak için farklı bir dize **değer** özelliği (örneğin, `http://CorporateProductionWebServer`).

6.  Hangi çalışma etkin olmasını istediğiniz ayarları seçin. Çalıştırma ayarlarını kısayol menüsünü açın ve seçin **etkin olarak ayarla**.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)