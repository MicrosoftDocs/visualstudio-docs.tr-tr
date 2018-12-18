---
title: Güvenlik sayfası, Proje Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 967ce9221313c88b10a792f15ffaec80da99de03
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267819"
---
# <a name="security-page-project-designer"></a>Güvenlik Sayfası, Proje Tasarımcısı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**Güvenlik** sayfasının **Proje Tasarımcısı** kullanılarak dağıtılan uygulamalar için kod erişim güvenlik ayarlarını yapılandırmak için kullanılan [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] dağıtım. Daha fazla bilgi için [ClickOnce uygulamaları için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Erişim için **güvenlik** sayfasında, bir proje düğümünde **Çözüm Gezgini**ve ardından **proje** menüsünde tıklayın **özellikleri**. Zaman **Proje Tasarımcısı** görünen tıklayın **güvenlik** sekmesi.  
  
## <a name="security-settings"></a>Güvenlik ayarları  
 **ClickOnce güvenlik ayarlarını etkinleştirme**  
 Güvenlik ayarları tasarım zamanında etkin olup olmadığını belirler. Ne zaman bu seçenek işaretli değilse, diğer tüm seçenekler üzerinde **güvenlik** sayfası kullanılamıyor.  
  
> [!NOTE]
>  Kullanarak bir uygulama yayımladığınızda **Yayımla** sihirbazında, bu seçenek otomatik olarak etkinleştirilir.  
  
 Bu seçeneği belirlediğinizde, iki radyo düğmelerinden birini seçme seçeneğiniz vardır: **tam güven uygulamasıdır** veya **kısmi güven uygulamasıdır**.  
  
 WPF Web tarayıcı uygulaması projeleri için varsayılan olarak bu seçenek seçilidir.  
  
 Varsayılan olarak, diğer proje türleri için bu seçeneği temizlenir.  
  
 **Tam güven uygulamasıdır**  
 Bu seçeneği belirlerseniz, uygulama yüklendiğinde veya bir istemci bilgisayarda çalışması tam güven izinleri ister. Önlemek uygulamanızı verilir çünkü tam güven mümkünse kullanarak sınırsız erişim dosya sistemini ve kayıt defteri gibi kaynaklara bağlayabilirsiniz.  
  
 WPF Web tarayıcı uygulaması projeleri için varsayılan olarak bu seçenek, kısmi güven için ayarlanır.  
  
 Varsayılan olarak, diğer proje türleri için tam güven için bu seçeneği ayarlanır.  
  
 **Kısmi güven uygulamasıdır**  
 Bu seçeneği belirlerseniz, uygulama yüklendiğinde veya bir istemci bilgisayarda çalışması kısmi güven izinleri ister. *Kısmi güven* istenen kod erişimi güvenliği izinleri altında izin verilen eylemleri anlamına gelir. Güvenlik izinlerini yapılandırma hakkında daha fazla bilgi için bkz. [ClickOnce uygulamaları için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Kısmi güven güvenliği ayarları seçenekleri yapılandırarak belirtebilirsiniz **ClickOnce güvenlik izinleri** alan.  
  
## <a name="clickonce-security-permissions"></a>ClickOnce güvenlik izinleri  
 **Bölge, uygulama yüklenir**  
 Kod erişimi güvenliği izinleri varsayılan kümesini belirtir. Seçin **Internet** veya **yerel Intranet** sınırlı bir izin kümesi veya seçin **(özel)** özel izin yapılandırmak için ayarlayın. Uygulama bir bölgede verilen çok daha fazla izne isterse, ek izinler vermek son kullanıcı için bir ClickOnce güven istemi görünür. Güvenlik izinlerini yapılandırma hakkında daha fazla bilgi için bkz. [ClickOnce uygulamaları için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Varsayılan olarak WPF Web tarayıcı uygulaması projeleri için bu seçeneği ayarlanır **Internet**.  
  
 **XML izinleri Düzenle**  
 İzinleri yapılandırmak için uygulama bildirim şablonu (app.manifest) için açılır **(özel)** izin kümesi.  
  
 **Gelişmiş**  
 Açılır [Gelişmiş Güvenlik Ayarları iletişim kutusu](../../ide/reference/advanced-security-settings-dialog-box.md), sınırlı izinler ile uygulamasında hata ayıklama için ayarları yapılandırmak için kullanılır. Bu ayarlar, hata ayıklama sırasında denetlenir ve uygulamanızı bir bölge içinde tanımlanan daha fazla izin gerekebilir izni özel durumları gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Permissions.WebBrowserPermission>   
 <xref:System.Security.Permissions.MediaPermission>   
 [ClickOnce uygulamaları için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md)   
 [Nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştirme](../../deployment/how-to-enable-clickonce-security-settings.md)   
 [Nasıl yapılır: ClickOnce uygulaması için bir güvenlik bölgesi ayarlama](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [ClickOnce güvenliği ve dağıtımı](../../deployment/clickonce-security-and-deployment.md)   
 [Proje Özellikleri başvurusu](../../ide/reference/project-properties-reference.md)   
 [Gelişmiş Güvenlik Ayarları İletişim Kutusu](../../ide/reference/advanced-security-settings-dialog-box.md)



