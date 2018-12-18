---
title: Bağlı hizmetler kullanarak mobil hizmet ekleme
description: Visual Studio bağlı Hizmetleri Ekle iletişim kutusunu kullanarak mobil hizmetler ekleyin
documentationcenter: na
author: ghogen
manager: douge
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 5192dcd2a19904db1c97136f41e1e6a1af112a95
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307654"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Visual Studio bağlı Hizmetler'i kullanarak mobil hizmet ekleme
Visual Studio 2015 ile Azure mobil Hizmetleri'ni kullanarak bağlanabilirsiniz **bağlı hizmet Ekle** iletişim. Tüm C# istemci uygulamalarından, tüm JavaScript uygulaması veya platformlar arası Cordova uygulaması bağlanabilirsiniz. Bağlandıktan sonra oluşturma ve verilere erişmek, özel API'ler ve zamanlanan işler oluşturabilir veya anında iletme bildirimleri için destek eklendi.  Bağlı hizmetler işlemi, tüm uygun başvuruları ve bağlantı kodunu ekler. Çeşitli Azure AD gibi popüler kimlik şemaları ile kimlik doğrulaması için yerleşik destek avantajından da sürebilir Facebook, Twitter ve Microsoft Accounts.

## <a name="supported-project-types"></a>Desteklenen proje türleri
> [!NOTE]
> Visual Studio 2015'te, bağlı hizmet Ekle iletişim kutusunu kullanarak bir Windows Evrensel (Windows 10) projeleri için Azure Mobile Services eklenmesi desteklenmiyor. Projeniz için NuGet Paket Yöneticisi'ni kullanarak uygun paketlerini yükleyerek Azure mobil hizmetler ekleyebilirsiniz.
>
>

Aşağıdaki proje türlerini Azure mobil Hizmetler'e bağlanmak için bağlı hizmetler iletişim kutusunu kullanabilirsiniz.

* .NET Windows 8.1 Store, telefon ve evrensel uygulama projeleri
* JavaScript Windows 8.1 Store, telefon ve evrensel uygulama projeleri
* Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan projeler

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Bağlı hizmet Ekle iletişim kutusunu kullanarak Azure mobil Hizmetleri'ne için Bağlan
1. Bir Azure hesabı olduğundan emin olun. Azure hesabınız yoksa, oturum açabileceğiniz bir [ücretsiz deneme sürümü](http://go.microsoft.com/fwlink/?LinkId=518146).
2. Açık **bağlı hizmet Ekle** iletişim kutusu.

   * .NET uygulamaları için projenizi Visual Studio'da açın, bağlam menüsünü **başvuruları** Çözüm Gezgininde düğümünü ve ardından **bağlı hizmet Ekle**

        ![Azure mobil hizmetinize bağlanma](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Apache Cordova uygulaması projeleri için projenizi Visual Studio'da açın, Çözüm Gezgini'nde proje düğümü için bağlam menüsünü açın ve ardından **bağlı hizmet Ekle**.
3. İçinde **bağlı hizmet Ekle** iletişim kutusunda **Azure Mobile Services**ve ardından **yapılandırma** düğmesi. Zaten yapmadıysanız, Azure'a bağlanmanız istenebilir.

    ![Bir Azure mobil hizmet ekleme](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. İçinde **Azure Mobile Services** iletişim kutusunda, varsa var olan bir mobil hizmeti seçin. Yeni bir Azure mobil hizmet oluşturmak ihtiyacınız varsa, bunu yapmak için aşağıdaki yordamı izleyin. Aksi halde, bir sonraki numaralı adıma geçin.

    Yeni bir mobil hizmet hesabı oluşturmak için:

   1. Seçin **hizmet Oluştur** iletişim kutusunun altındaki bağlantıyı.
       ![Yeni mobil bağlı hizmet Ekle](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. Üzerinde **mobil hizmet Oluştur** iletişim kutusu, bir JavaScript arka uç mobil hizmet veya .NET arka uç mobil hizmetinden seçebilirsiniz **çalışma zamanı** aşağı açılan listesi.

       ![Bir mobil hizmet oluşturma](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Basit ve güçlü bir JavaScript arka uç hizmeti. JavaScript arka uç mobil hizmet oluşturma, sunucu tarafı JavaScript kodu bulutta depolanır, ancak Sunucu Gezgini veya Azure Yönetim Portalı'nı kullanarak sunucu komut dosyalarını düzenleyebilirsiniz.

       Bir .NET arka uç mobil hizmetlerini tam gücü ve Entity Framework ile Web API ve esnekliği sunar. Bir .NET arka uç mobil hizmetlerini oluşturursanız, bir projesi için oluşturduğunuz ve çözümünüze eklenir.
   3. Seçin **bölge** Burada, mobil hizmet istediğiniz ve ardından sunucu için bir kullanıcı adı ve parola girin.
   4. Tüm gerekli bilgileri girdikten sonra seçin **Oluştur** mobil hizmet oluşturmak için düğme.
   5. Yeni mobil hizmet üzerinde hizmet listesinde görünmelidir **Azure Mobile Services** iletişim kutusu. Yeni mobil hizmet listeden seçin ve ardından **Ekle** düğmesini hizmet projenize ekleyin.
5. Açılan başlangıç sayfasını inceleyin ve projenizin nasıl değiştirildiğini öğrenin. Bir bağlı hizmet ekleyişinizde tarayıcınızda bir Başlarken sayfası görüntülenir. Önerilen sonraki adımları ve kod örneklerini inceleyebilir veya projenize hangi başvuruların eklendi ve kod ve yapılandırma dosyalarınızın nasıl değiştirilmiş görmek için olanlar sayfasına geçebilirsiniz.
6. Kod örneklerini kılavuz olarak kullanarak, mobil hizmetinize erişmek için kod yazmaya başlayın!

## <a name="how-your-project-is-modified"></a>Projenizi nasıl değiştirilir
Visual Studio'nun projenizi nasıl değiştirdiğini, proje türüne göre değişir. C# için istemci uygulamalar, [ne olduğunu – C# projeleri](http://go.microsoft.com/fwlink/p/?LinkId=513119). JavaScript istemci uygulamalar için [ne olduğunu – JavaScript projeleri](http://go.microsoft.com/fwlink/p/?LinkId=513120). Cordova uygulamaları için bkz: [ne olduğunu – Cordova projeleri](http://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Sonraki adımlar
Soru sorun ve Yardım alın:

* [MSDN forumu: Azure mobil hizmetler](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Azure mobil Hizmetleri Microsoft Azure ekibi blogu](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure.microsoft.com'da Azure mobil hizmetler](https://azure.microsoft.com/services/mobile-services/)
* [Azure.microsoft.com'da Azure mobil hizmetler belgeleri](https://azure.microsoft.com/documentation/services/mobile-services/)
