---
title: 'Nasıl yapılır: şablonlarda sorun giderme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a68097745de1f1d94e5c09963a474a0095588fba
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296432"
---
# <a name="how-to-troubleshoot-templates"></a>Nasıl Yapılır: Şablonlarda Sorun Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geliştirme ortamında yüklemek bir şablon başarısız olursa, sorunu bulmak için birkaç yolu vardır.  
  
## <a name="validating-the-vstemplate-file"></a>.Vstemplate dosyası doğrulanıyor  
 Bir şablonun .vstemplate dosyasında kalmıyor, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] şablon şeması şablon görüntülenmeyebilir **yeni proje** iletişim kutusu.  
  
#### <a name="to-validate-the-vstemplate-file"></a>.Vstemplate dosyasını doğrulamak için  
  
1.  Şablonu içeren .zip dosyasını bulun.  
  
2.  .Zip dosyasını çıkartın.  
  
3.  Üzerinde **dosya** menüde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], tıklayın **açık**ve ardından **dosya**.  
  
4.  Şablonu için .vstemplate dosyasını seçin ve tıklayın **açık**.  
  
5.  .Vstemplate dosyasının XML için uyar doğrulayın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] şablon şeması. .Vstemplate şeması hakkında daha fazla bilgi için bkz. [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md).  
  
    > [!NOTE]
    >  .Vstemplate dosyası geliştirme sırasında IntelliSense desteği almak için ekleyin bir `xmlns` özniteliğini `VSTemplate` öğe değerini atayın http://schemas.microsoft.com/developer/vstemplate/2005.  
  
6.  .vstemplate dosyasını kaydedip kapatın.  
  
7.  Şablonunuzda, içerdiği dosyaları seçin sağ tıklayın, **göndermek için**, tıklatıp **sıkıştırılmış (daraltılmış) klasör**. Seçtiğiniz dosyaların bir .zip dosyasına sıkıştırılır.  
  
8.  Eski bir .zip dosyası olarak aynı dizinde yeni bir .zip dosyası yerleştirin.  
  
9. Ayıklanan şablon dosyalarını ve eski şablonu .zip dosyasını silin.  
  
## <a name="monitoring-the-event-log"></a>Olay günlüğünü izleme  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Şablon .zip dosyalarını işleme sırasında karşılaşılan hataları günlüğe kaydeder. Bir şablon olarak görünmez, **yeni proje** iletişim kutusu olarak beklendiği gibi kullanabileceğiniz **Olay Görüntüleyicisi'ni** sorunu gidermek için.  
  
#### <a name="to-locate-template-errors-in-event-viewer"></a>Olay Görüntüleyicisi'nde şablon hataları bulmak için  
  
1.  Windows içinde tıklayın **Başlat**, tıklayın **Denetim Masası**, çift tıklatın **Yönetimsel Araçlar**ve çift tıklatarak **Olay Görüntüleyicisi'ni**.  
  
2.  Sol bölmede **uygulama**.  
  
3.  Olayları arayın bir **kaynak** değerini `Visual Studio - VsTemplate`.  
  
4.  Hata görüntülemek için bir şablon olayı çift tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)   
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)



