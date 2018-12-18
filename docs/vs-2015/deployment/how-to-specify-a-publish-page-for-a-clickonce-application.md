---
title: 'Nasıl yapılır: ClickOnce uygulaması için bir yayımlama sayfası belirtme | Microsoft Docs'
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
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c10033f7e3f3a4336177c8c66721bd6b79ba4c71
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196696"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce Uygulaması için bir Yayımlama Sayfası Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yayımlama sırasında bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] varsayılan bir Web sayfası (publish.htm) oluşturulur ve uygulama ile birlikte yayımlanan uygulama. Bu sayfaya uygulaması, uygulama ve/veya tüm önkoşulları yüklemek için bir bağlantı ve açıklayan bir Yardım konusu için bir bağlantı adını içeren [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. **Yayımla Sayfası** projeniz için özellik, Web sayfası için bir ad belirtmenize olanak sağlar, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama.  
  
 Sonraki yayımladığınızda, yayımlama sayfasında belirtilen sonra yayımlama konumuna kopyalanır; yeniden yayımlarsanız yazılmaz. Sayfa görünümünü özelleştirmek istiyorsanız, değişikliklerinizi kaybetmek hakkında endişelenmeden bunu yapabilirsiniz. Daha fazla bilgi için [nasıl yapılır: ClickOnce Varsayılan Web sayfasını özelleştirme](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 **Yayımla Sayfası** özellik ayarlanabilir **yayımlama seçeneği** iletişim kutusu, erişilebilir **Yayımla** bölmesinde **Proje Tasarımcısı**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>ClickOnce uygulaması için özel bir Web sayfasını belirtmek için  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünü tıklatın **özellikleri**.  
  
2.  Seçin **Yayımla** bölmesi.  
  
3.  Tıklayın **seçenekleri** açmak için düğmeyi **yayımlama seçeneği** iletişim kutusu.  
  
4.  Tıklayın **dağıtım**.  
  
5.  İçinde **yayımlama seçeneği** iletişim kutusunda, emin olun **sonra açık dağıtım web sayfasını yayımlama** onay kutusu seçildiğinde (varsayılan olarak seçili).  
  
6.  İçinde **dağıtım web sayfasını:** kutusuna Web sayfası için bir ad girin ve ardından **Tamam**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Yayımlama sayfasında her yayımlama işleminde başlamasını engellemek için  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünü tıklatın **özellikleri**.  
  
2.  Seçin **Yayımla** bölmesi.  
  
3.  Tıklayın **seçenekleri** açmak için düğmeyi **yayımlama seçeneği** iletişim kutusu.  
  
4.  Tıklayın **dağıtım**.  
  
5.  İçinde **yayımlama seçeneği** iletişim kutusu, NET **sonra açık dağıtım web sayfasını yayımlama** onay kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Nasıl yapılır: ClickOnce Varsayılan Web Sayfasını Özelleştirme](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)



