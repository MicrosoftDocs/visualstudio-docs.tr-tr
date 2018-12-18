---
title: 'Nasıl yapılır: bir etki alanına özgü dili yeni sürüme geçirme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 52d8cb794b205631e7cc455241f48bcc78b879b9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844477"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Nasıl yapılır: Etki Alanına Özgü Dili Yeni Sürüme Geçirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tanımlamak ve etki alanına özgü dil kullanan projeler geçirebileceğiniz [!INCLUDE[vs2010](../includes/vs2010-md.md)] sürümünden [!INCLUDE[dsl](../includes/dsl-md.md)] , ile dağıtılan [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].  
  
 Geçiş Aracı bir parçası olarak sağlanan [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)]. Aracı dönüştürür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projeler ve çözümler kullanın veya DSL araçları tanımlayın.  
  
 Geçiş Aracı açıkça çalıştırmanız gerekir: bir çözümde açtığınızda otomatik olarak başlatılmaz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ayrıntılı yönergeler belge ve araç bu yolda bulunabilir:  
  
 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>DSL projelerinizin geçiş önce  
 Geçiş Aracı değiştirir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje dosyaları (**.csproj**) ve çözüm dosyaları (**.sln**).  
  
#### <a name="to-prepare-projects-for-migration"></a>Projeleri geçişe hazırlamak için.  
  
-   Emin **.csproj** ve **.sln** dosyaları yazılabilir. Kaynak denetimi altında olmaları durumunda, bunlar kullanıma emin emin olun.  
  
-   Geçirmek istediğiniz klasörleri bir kopyasını oluşturun.  
  
## <a name="migrating-a-collection-of-projects"></a>Proje koleksiyonu geçirme  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>DSL projeler ve çözümler, Visual Studio 2010'a geçirmeye  
  
1. DSL geçiş aracını başlatın.  
  
   -   Windows Explorer (veya dosya Gezgini) araca çift tıklayın veya bir komut istemi'nden aracını başlatın. Bu konumda aracıdır:  
  
        **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2. Dönüştürmek istediğiniz projeler ve çözümler içeren bir klasör seçin.  
  
   - Üst kısmındaki araç kutusunda yolunu girin veya **Gözat**.  
  
     Geçiş Aracı tanımlayın veya DSL kullanan projeler ağacını görüntüler. Ağaç kullanan her bir proje içerir **Microsoft.VisualStudio.Modeling.Sdk** veya **TextTemplating** derlemeler.  
  
3. Proje ağacını gözden geçirin ve projeleri dönüştürmek istiyor musunuz işaretini kaldırın.  
  
   -   Bir proje veya çözüm, araç haline getiren değişikliklerin bir listesini görmek için seçin.  
  
       > [!NOTE]
       >  Klasör adları yanında görünen onay kutularını hiçbir etkisi yoktur. Projeler ve çözümler incelemek için klasörleri genişletmeniz gerekir.  
  
4. Projeleri dönüştürün.  
  
   1.  Tıklayın **Dönüştür**.  
  
        Her proje dosyası dönüştürülür önce bir kopyasını _proje_**.csproj** olarak kaydedilen _proje_**. vs2008.csproj**  
  
        Her bir kopyasını _çözüm_**.sln** olarak kaydedilen _çözüm_**. vs2008.sln**  
  
   2.  Bildirilen herhangi bir başarısız dönüştürmeler araştırın.  
  
        Metin penceresindeki hataları raporlanır. Ayrıca, ağaç görünümünde kırmızı bayrak dönüştürmek için başarısız olan her düğümde gösterir. Bu hata hakkında daha fazla bilgi almak için düğüme tıklayabilirsiniz.  
  
5. **Tüm Şablonları dönüştürme** çözümlerinde başarıyla içeren projeleri dönüştürülür.  
  
   1.  Çözümü açın.  
  
   2.  Tıklayın **tüm Şablonları Dönüştür** Çözüm Gezgini başlığını düğmesi.  
  
       > [!NOTE]
       >  Bu adım, gereksiz yapabilirsiniz. Daha fazla bilgi için [otomatikleştirmek tüm Şablonları Dönüştür nasıl](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
6. Özel kodunuz dönüştürülmüş projelerinde güncelleştirin.  
  
   -   Projeleri derlemek ve tüm hataları araştırmak çalışır.  
  
   -   Tasarımcınıza test edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görselleştirme ve SDK Modellemedeki yenilikler](../misc/what-s-new-in-visualization-and-modeling-sdk.md)



