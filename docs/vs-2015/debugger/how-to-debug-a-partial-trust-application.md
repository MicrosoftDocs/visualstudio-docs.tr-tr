---
title: 'Nasıl yapılır: kısmen güvenilen uygulamada hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76cce8cfcf57f956b5de16b72f7a275e1d629630
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782056"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Nasıl Yapılır: Kısmen Güvenilen Uygulamada Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve konsol uygulamaları için geçerlidir.  
  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md) yararlanan kısmi güven uygulamaları dağıtmayı kolaylaştırır [kod erişim güvenliği](http://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) makine kaynaklarına erişimi sınırlamak için.  
  
 Kısmi güven uygulamasında hata ayıklama olabilir bir challenge, kısmi güven uygulamaları, farklı güvenlik izinlerine sahip (ve bu nedenle farklı davranır çünkü) bağlı olarak burada yüklenirler. Kısmen güvenilen uygulamada, internet'ten yüklü değilse, birkaç izinlerine sahip olur. Yerel intranetten yüklü değilse, daha fazla izne sahip ve yerel bilgisayardan yüklü değilse, tüm izinlere sahip olacaktır. Ayrıca özel bölgeleri, özel izinlere sahip olabilir. Tüm bu koşullar altında kısmen güvenilen uygulamada hata ayıklama gerekebilir. Neyse ki, Visual Studio bu de kolaylaştırır.  
  
 Visual Studio'da hata ayıklama oturumu başlamadan önce bir uygulamanın yüklendiği benzetimini yapmak için istediğiniz bölgeyi seçebilirsiniz. Hata ayıklaması başlattığınızda, uygulama bu bölgeden yüklenmiş bir kısmi güven uygulamanız için uygun izinleri olur. Bu, uygulama davranışını bu bölgeden indirilen bir kullanıcıya görüneceği şekilde görmenize olanak sağlar.  
  
 Uygulama izni yok bir eylem gerçekleştirmeye çalışırsa, bir özel durum oluşur. Bu noktada özel durum Yardımcısı'nı, sorunu önlemek için yeterli izinlere sahip hata ayıklama oturumunu yeniden olanak tanıyan ek bir izni ekleme olanağı sağlar.  
  
 Daha sonra geri dönün ve hata ayıklama sırasında eklenen hangi izinlerin bakın. Hata ayıklama sırasında bir izin eklemek zorunda kalırsa, onu büyük olasılıkla bir kullanıcı onay istemi bu noktada kodunuza ekleyin gerektiğini belirtir.  
  
> [!NOTE]
>  Hata ayıklama görselleştiricileri kısmi güven uygulama tarafından izin verilenden daha yüksek ayrıcalıklar gerektirir. Kısmi güven ile koddaki durdurulduğunda görselleştiriciler yüklemez. Görselleştirici kullanarak hata ayıklama için tam güven ile kodu çalıştırmanız gerekir.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Kısmi güven uygulamanız için bir bölge seçmek için  
  
1.  Gelen **proje** menüsünde seçin _Projectname_**özellikleri**.  
  
2.  İçinde *Projectname* özellik sayfaları, tıklayın **güvenlik** sayfası.  
  
3.  Seçin **ClickOnce güvenlik ayarlarını etkinleştirme**.  
  
4.  Altında **uygulamanızı yükleneceği kaynak bölge**, aşağı açılan liste kutusunda tıklayın ve yüklenen uygulama benzetimini yapmak istediğiniz bölgeyi seçin.  
  
     **Uygulamanın gerektirdiği izinler** kılavuz kullanılabilir tüm izinleri gösterir. Onay işareti, uygulamaya verilen izinleri belirtir.  
  
5.  Seçtiğiniz bölge olduysa **(özel)**, doğru özel ayarları'nda seçin **ayarı** sütununun **izinleri** kılavuz.  
  
6.  Tıklayın **Tamam** özellik sayfalarını kapatmak için.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Bir güvenlik özel durumu oluştuğunda ek bir izin eklemek için  
  
1.  **Özel durum Yardımcısı'nı** iletisiyle iletişim kutusu görüntülenir: **SecurityException işlenmemiş.**  
  
2.  İçinde **özel durum Yardımcısı'nı** iletişim kutusunun **eylemleri**, tıklayın **proje ekleme izni**.  
  
3.  **Yeniden hata ayıklama** iletişim kutusu görüntülenir.  
  
    -   Yeni izni olan hata ayıklama oturumunu yeniden isterseniz **Evet**.  
  
    -   Henüz yeniden istemiyorsanız tıklayın **Hayır**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Hata ayıklama sırasında eklenen ek izinleri görüntülemek için  
  
1.  Gelen **proje** menüsünde seçin _Projectname_**özellikleri**.  
  
2.  İçinde *Projectname* özellik sayfaları, tıklayın **güvenlik** sayfası.  
  
3.  Bakmak **uygulamanın gerektirdiği izinler** kılavuz. Eklediğiniz herhangi bir ek izne sahip iki simgeyi **dahil edilen** sütun: izinleriniz, tüm dahil, normal işaretine ve şuna benzeyen bir balon "i" harfini içeren ek bir simge.  
  
4.  Dikey kaydırma çubuğu tamamını görüntülemek için kullanın **uygulamanın gerektirdiği izinler** kılavuz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)



