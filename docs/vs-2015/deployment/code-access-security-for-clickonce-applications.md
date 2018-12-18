---
title: ClickOnce uygulamaları için kod erişimi güvenliği | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.XBAPProjectPropertiesSecurity.HowTo
- vb.XBAProjectPropertiesSecurity.HowTo
- vb.ProjectPropertiesSecurity.HowTo
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], security
- ClickOnce applications, caspol
- security [ClickOnce], WPF browser-hosted applications
- security [ClickOnce], ClickOnce applications
- ClickOnce applications, code access security policies
- security, ClickOnce
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ea1f91a50180dce6edec17afead5649ecd3e1f50
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816072"
---
# <a name="code-access-security-for-clickonce-applications"></a>ClickOnce Uygulamaları İçin Kod Erişimi Güvenliği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce uygulamaları, .NET Framework tabanlı ve kod erişim güvenliği sınırlamalarına tabi olan. Bu nedenle, uygulamaları kod erişim güvenliği ve ClickOnce uygulamalarınızı buna göre yazma anlamak önemlidir.  
  
 Kod erişimi güvenliği, kod korumalı kaynaklara ve işlemlere sahip olan erişimini sınırlamaya yardımcı olan .NET Framework için kullanılan bir mekanizmadır. Uygulama yükleyici konumu için uygun bölgeyi kullanmak, ClickOnce uygulaması için kod erişimi güvenliği izinleri yapılandırmanız gerekir. Çoğu durumda, seçtiğiniz **Internet** sınırlı bir izin kümesi bölgenin veya **yerel Intranet** bölge için büyük bir izin kümesi.  
  
## <a name="default-clickonce-code-access-security"></a>Varsayılan ClickOnce kod erişimi güvenliği  
 Yüklendiğinde veya bir istemci bilgisayarda varsayılan olarak, ClickOnce uygulaması tam güven izinleri alır.  
  
- Tam güven izinleri olan bir uygulama, dosya sistemini ve kayıt defteri gibi kaynaklara erişim varmazlar. Bu büyük olasılıkla uygulamanızı (ve son kullanıcının sistem) kötü amaçlı kod tarafından kullanılmasına izin verir.  
  
- Bir uygulama tam güven izinleri gerektirdiğinde, son kullanıcının uygulama izinlerini vermek için istenebilir. Bu uygulamayı gerçek anlamda bir ClickOnce deneyimi sağlamaz ve istemi potansiyel olarak daha az deneyimli kullanıcılar için kafa karıştırıcı olabilir anlamına gelir.  
  
  > [!NOTE]
  >  Bir uygulamayı bir CD-ROM gibi çıkarılabilir medyadan yüklemek, kullanıcıya sorulmaz. Ayrıca, böylece kullanıcılar uygulamanın güvenilir bir kaynaktan yüklediklerinde istenmez bir ağ yöneticisi ağ ilkesi yapılandırabilirsiniz. Daha fazla bilgi için [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
  ClickOnce uygulaması için izinleri kısıtlamak için uygulamanızın gerektirdiği izinler için en uygun bölgeyi istemek için uygulamanıza kod erişim güvenlik izinlerini değiştirebilirsiniz. Çoğu durumda, uygulamanın dağıtıldığı bölge seçebilirsiniz. Örneğin, uygulamanız bir kuruluş uygulaması ise, kullanabileceğiniz **yerel Intranet** bölge. Uygulamanız bir Internet uygulaması ise, kullanabileceğiniz **Internet** bölge.  
  
## <a name="configuring-security-permissions"></a>Güvenlik izinlerini yapılandırma  
 Her zaman, kod erişimi güvenliği izinleri sınırlamak için uygun bölgeyi istemek için ClickOnce uygulamanızı yapılandırmanız gerekir. Güvenlik izinlerini yapılandırabilirsiniz **güvenlik** sayfasının **Proje Tasarımcısı**.  
  
 **Güvenlik** sayfasını **Proje Tasarımcısı** içeren bir **ClickOnce güvenlik ayarlarını etkinleştirme** onay kutusu. Bu onay kutusu seçildiğinde, güvenlik izin isteklerini uygulamanız için dağıtım bildirimi eklenir. Yükleme sırasında istenen izinlere uygulamanın dağıtıldığı bölge için varsayılan izinler aşarsa izinleri vermek için kullanıcı istenir. Daha fazla bilgi için [nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md).  
  
 Farklı konumlardan dağıtılan uygulamaları sormadan farklı düzeylerde izinler verilir. Örneğin, Internet'ten uygulama dağıtıldığında, son derece kısıtlayıcı bir izin kümesini alır. Yerel Intranet üzerinden yüklendiğinde, daha fazla izin alır ve bir CD-ROM'dan yüklendiğinde tam güven izinleri alır.  
  
 Bir güvenlik bölgesi'nden seçebileceğiniz izinlerini yapılandırmak için başlangıç noktası olarak **bölge** listesini **güvenlik** sayfası. Uygulamanızı potansiyel olarak birden fazla bölgeden dağıtılacaksa, en az izinlere sahip bir bölge seçin. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).  
  
 İzin kümesi tarafından ayarlanabilir özellikleri değişir; tüm izin kümeleri yapılandırılabilir özelliklere sahiptir. Uygulamanızın isteyebileceği izinleri tam listesi hakkında daha fazla bilgi için bkz. <xref:System.Security.Permissions>. Özel bir bölge için izinlerin nasıl ayarlanacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
## <a name="debugging-an-application-that-has-restricted-permissions"></a>Sınırlı izinlere sahip bir uygulamada hata ayıklama  
 Bir geliştirici olarak, büyük olasılıkla tam güven izinleri olan geliştirme bilgisayarınıza çalıştırın. Bu nedenle, kısıtlanmış izinler ile çalıştırdıklarında kullanıcıların görebileceği uygulama hata ayıklaması yaparken aynı güvenlik özel durumları görmez.  
  
 Bu özel durumları yakalamak için uygulama son kullanıcı olarak aynı izinlere sahip olması. Sınırlı izinler ile hata ayıklama etkinleştirilebilir **güvenlik** sayfasının **Proje Tasarımcısı**.  
  
 Kısıtlı izinleri olan bir uygulamada hata ayıklaması yaparken, özel durumlar için üzerinde etkinleştirilmemiş herhangi bir kod güvenlik talebi ortaya çıkacaktır **güvenlik** sayfası. Özel durum önlemek için kodunuzu değiştirmek konusunda öneriler sağlayan bir özel durum Yardımcısı görüntülenir.  
  
 Ayrıca, kod yazdığınızda, IntelliSense özelliği Kod Düzenleyicisi'nde, yapılandırmış olduğunuz güvenlik izinlerini bulunmayan herhangi bir üye devre dışı bırakır.  
  
 Daha fazla bilgi için [nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
## <a name="security-permissions-for-browser-hosted-applications"></a>Tarayıcıda tutulan uygulamalar için güvenlik izinleri  
 Visual Studio, Windows Presentation Foundation (WPF) uygulamaları için aşağıdaki proje türlerini sağlar:  
  
- WPF Windows uygulaması  
  
- WPF Web tarayıcı uygulaması  
  
- WPF Özel Denetim Kitaplığı  
  
- WPF Hizmet Kitaplığı  
  
  Bu proje türleri yalnızca WPF Web tarayıcı uygulamaları bir Web tarayıcısında barındırılan ve bu nedenle özel dağıtımı ve güvenlik ayarları gerektirir. Bu uygulamalar için varsayılan güvenlik ayarlarını aşağıdaki gibidir:  
  
- **ClickOnce güvenlik ayarlarını etkinleştirme**  
  
- **Kısmi güven uygulamasıdır**  
  
- **Internet bölgesi** (WPF Web tarayıcı seçili uygulamalar için varsayılan izin ile)  
  
  İçinde **Gelişmiş güvenlik ayarları** iletişim kutusu, **bu uygulama için seçili izin kümesi ile hata ayıklama** onay kutusu işaretli ve devre dışı. Bölge içinde hata ayıklama için tarayıcıda tutulan uygulamalar devre dışı bırakılamaz. olmasıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [Nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Nasıl yapılır: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Güvenilir Uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)   
 [Güvenlik Sayfası, Proje Tasarımcısı](../ide/reference/security-page-project-designer.md)



