---
title: Güvenlik Sayfası, Proje Tasarımcısı
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 75877dfd8620af9d3fdfecb5cfcb10761a739515
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949585"
---
# <a name="security-page-project-designer"></a>Güvenlik Sayfası, Proje Tasarımcısı

**Güvenlik** sayfasında **Proje Tasarımcısı** kullanılarak dağıtılan uygulamalar için kod erişimi güvenlik ayarlarını yapılandırmak için kullanılan [!INCLUDE[ndptecclick](../../deployment/includes/ndptecclick_md.md)] dağıtım. Daha fazla bilgi için bkz: [ClickOnce uygulamaları için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).

 Erişim için **güvenlik** sayfasında, bir proje düğümüne tıklayın **Çözüm Gezgini**ve ardından **proje** menüsünde tıklatın **özellikleri**. Zaman **Proje Tasarımcısı** görünen tıklatın **güvenlik** sekmesi.

## <a name="security-settings"></a>Güvenlik ayarları

 **ClickOnce güvenlik ayarlarını etkinleştir**

 Güvenlik ayarları tasarım zamanında etkin olup olmadığını belirler. Ne zaman bu seçeneği işaretli değilse, diğer tüm seçenekleri üzerinde **güvenlik** sayfası kullanılamıyor.

> [!NOTE]
> Kullanarak bir uygulama yayımladığınızda **Yayımla** sihirbazında, bu seçenek otomatik olarak etkinleştirilir.


 Bu seçeneği belirlediğinizde, iki radyo düğmeleri birini seçerek seçeneğiniz vardır: **tam güven uygulamasıdır** veya **kısmi güven uygulamasıdır**.

 Varsayılan olarak, WPF Web tarayıcı uygulaması projeleri için bu seçenek seçilidir.

 Varsayılan olarak, diğer proje türleri için bu seçeneği temizlenir.

 **Bu tam güven bir uygulamadır**

 Bu seçeneği seçerseniz, uygulama yüklendiğinde veya bir istemci bilgisayarda çalışması tam güven izinleri ister. Kaçının uygulamanızı verilecek için tam güven Mümkünse, kullanılarak sınırsız erişimi dosya sistemini ve kayıt defteri gibi kaynaklara.

 Varsayılan olarak, WPF Web tarayıcı uygulaması projeleri için bu seçeneği, kısmi güven için ayarlanır.

 Varsayılan olarak, diğer proje türleri için bu seçeneği, tam güven olarak ayarlanır.

 **Kısmi güven uygulamasıdır**

 Bu seçeneği seçerseniz, uygulama yüklendiğinde veya bir istemci bilgisayarda çalışması kısmi güven izinleri ister. *Kısmi güven* istenen kod erişim güvenliği izinleri altında izin verilen eylemleri anlamına gelir. Güvenlik izinlerini yapılandırma hakkında daha fazla bilgi için bkz: [ClickOnce uygulamaları için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).

 Kısmi güven güvenlik ayarları seçeneklerinde yapılandırarak belirtebilirsiniz **ClickOnce güvenlik izinleri** alanı.

## <a name="clickonce-security-permissions"></a>ClickOnce güvenlik izinleri

 **Bölge, uygulamanızın yüklenir**

 Varsayılan bir kod erişim güvenliği izinleri belirtir. Seçin **Internet** veya **yerel Intranet** kısıtlı izin ayarlamak veya seçin **(özel)** özel bir izni yapılandırmak için ayarlayın. Uygulama bir bölgede verilen daha fazla izin isterse bir ClickOnce güven istemi ek izinleri vermek son kullanıcı için görünür. Güvenlik izinlerini yapılandırma hakkında daha fazla bilgi için bkz: [ClickOnce uygulamaları için kod erişimi güvenliği](../../deployment/code-access-security-for-clickonce-applications.md).

 Varsayılan olarak, WPF Web tarayıcı uygulaması projeleri için bu seçeneği ayarlanmış **Internet**.

 **Permissions XML düzenleme**

 İzinleri yapılandırmak için uygulama bildirim şablonu (app.manifest) için açılır **(özel)** izin kümesi.

 **Gelişmiş**

 Açılır [Gelişmiş Güvenlik Ayarları iletişim kutusu](../../ide/reference/advanced-security-settings-dialog-box.md), kısıtlı izinleri olan uygulamada hata ayıklama için ayarları yapılandırmak için kullanılır. Hata ayıklama sırasında bu ayarları denetlenir ve uygulamanızı bir bölgesi içinde tanımlanan daha fazla izin gerekebilir izni özel durumlarını gösterir.

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [ClickOnce Uygulamaları İçin Kod Erişimi Güvenliği](../../deployment/code-access-security-for-clickonce-applications.md)
- [Nasıl yapılır: ClickOnce Güvenlik Ayarlarını Etkinleştirme](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Nasıl yapılır: ClickOnce Uygulaması için Bir Güvenlik Bölgesi Ayarlama](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Nasıl yapılır: ClickOnce Uygulaması için Özel İzinleri Ayarlama](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Nasıl yapılır: Sınırlı İzinler ile ClickOnce Uygulamasında Hata Ayıklama](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [ClickOnce Güvenliği ve Dağıtımı](../../deployment/clickonce-security-and-deployment.md)
- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Gelişmiş Güvenlik Ayarları İletişim Kutusu](../../ide/reference/advanced-security-settings-dialog-box.md)