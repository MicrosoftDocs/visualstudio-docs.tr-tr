---
title: SharePoint çözüm paketleri oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 87b80d7c607cf4de686e601263bcb67dcc2f92ae
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326858"
---
# <a name="create-sharepoint-solution-packages"></a>SharePoint çözüm paketleri oluşturma
  Paket Tasarımcısını kullanarak oluşturabilir ve dağıtım paketleri özelleştirebilirsiniz. Örneğin, SharePoint Proje öğeleri ve özellikler, IIS sunucusu sıfırlandığında, özelliğini etkinleştirme kapsamlarını ayarlayın ve özellik bağımlılıkları tanımlamak ekleyebilirsiniz. Tasarımcı de bildirim, her paket tanımlayan bir XML dosyası oluşturur.  
  
## <a name="packaging-tools"></a>Paketleme araçları
 Kullanabileceğiniz **paket tasarımcısını** paket özelleştirmek ve bildirim oluşturmak için. SharePoint Proje öğeleri içerir, Web sunucusu sıfırlamak ve dağıtım sunucusu türü ayarlamak olup olmadığını yapılandırın. Daha fazla bilgi için bkz: [nasıl yapılır: ekleyip özellikler ve öğeler bir paket için paket Tasarımcısını kullanarak](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 Alternatif olarak, kullanabileceğiniz **paketleme Gezgini'ni** özellikleri ve paket dosyası öğeleri değiştirmek için (*.wsp*). Daha fazla bilgi için bkz: [nasıl yapılır: ekleyip özellikler ve öğeler bir pakete paketleme Gezgini'ni kullanarak](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 Paketi oluşturmak için Visual Studio ve MSBuild kullanabilirsiniz (*.wsp*) dosyaları, SharePoint çözüm dağıtma. Bu işlem SharePoint dağıtım için gerekli bildirim dosyası oluşturur. Daha fazla bilgi için bkz: [nasıl yapılır: MSBuild görevlerini kullanarak bir SharePoint çözüm paketi oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Paket Tasarımcı seçenekleri
 Aşağıdaki tabloda, SharePoint paketlerde özelleştirebilirsiniz özellikleri gösterir **paket tasarımcısını**.  
  
|Paket tasarlayıcı özelliği|Varsayılan ayar açıklaması|  
|-------------------------------|------------------------------------|  
|Ad|Gerekli. Paketin varsayılan adını ayarlamak *ProjectName*.|  
|Web sunucusu Sıfırla|İsteğe bağlı. Web sunucusu sonra yeniden başlatmak istiyorsanız seçin *.wsp* dosyasını SharePoint sunucusuna yüklenir.|  
|Dağıtım sunucusu türü|Gerekli. Varsayılan olarak, kapsam ApplicationServer için ayarlanır.<br /><br /> ApplicationServer: hizmetlerini barındıran bir sunucu açıklar.<br /><br /> WebFrontEnd: Web sitelerini barındıran bir sunucu açıklar.|  
|Çözüm öğeleri|Tüm SharePoint Proje öğeleri ve pakete eklenen özellikler.|  
|Paket öğeleri|İsteğe bağlı. Tüm SharePoint öğeleri ve paketinizdeki dağıtmak istediğiniz özellikleri.|  
  
## <a name="configure-the-packaging-process"></a>Paketleme işlemi yapılandırmak
 Visual Studio'da SharePoint çözümleri geliştirmek sonra projeleri nasıl paketlenir özelleştirebilirsiniz.  
  
 Aşağıdaki tabloda özelleştirmek için kullanabileceğiniz iki MSBuild hedefleri gösterilmektedir nasıl *.wsp* dosyası oluşturulur.  
  
|Hedef|Açıklama|  
|------------|-----------------|  
|BeforeLayout|Dosyaları bir ara dizinine hemen kopyalanmadan önce görevleri gerçekleştiren hedefi. Bir paket dosyası oluşturmadan önce dosyaları değiştirebilirsiniz (*.wsp*).|  
|AfterLayout|Dosyalar bir ara dizinine hemen kopyalandıktan sonra görevleri gerçekleştiren hedefi.|  
  
 Daha fazla bilgi için [nasıl yapılır: MSBuild hedeflerini kullanarak SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Paketleme mimarisi
 Bir SharePoint paketi oluşturduğunuzda, aşağıdaki adımlar gerçekleşir (*.wsp*) Visual Studio.  
  
1.  Paketler ve özellikler, paket fiziksel ve anlam yapısını doğru olduğundan emin olmak için doğrulanır.  
  
2.  Özellikler, proje öğeleri ve paket dosyaları paketindeki numaralandırılır. Paketler ve özellikler için bildirim dosyası, dağıtım ve etkinleştirme için gerekli tüm bilgileri içerecek şekilde dönüştürülür. Belirteçleri tam değeriyle değiştirilir.  
  
3.  Özelleştirilebilir BeforeLayout MSBuild hedef gerçekleştirilir. Paketten önce tüm özel değişiklikler yapmak için bu adımı oluşturabilirsiniz *.wsp* dosyası oluşturulur.  
  
4.  Numaralandırılmış dosyalar bir ara dizinine kopyalanır.  
  
5.  Özelleştirilebilir AfterLayout MSBuild hedef gerçekleştirilir. Paketten önce tüm özel değişiklikler yapmak için bu adımı oluşturabilirsiniz *.wsp* dosyası oluşturulur.  
  
6.  Ara dizindeki dosyaların eklenir *.wsp* dosya.  
  
## <a name="package-folder-structure"></a>Paket klasör yapısı
 SharePoint projenizi paketini oluşturduğunuzda bir *.wsp* dosyası oluşturuldu uygulamasında *SolutionFolder\bin\\\<BuildConfiguration >* klasör. Örneğin, çözümünüz içinde ise *C:\Visual Studio 2013\Projects\ListDefinition1* ve derleme yapılandırması yayın olarak ayarlanmış *.wsp* dosyasının bulunduğu *C:\Visual Studio 2013\ Projects\ListDefinition1\bin\Release*.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Nasıl yapılır: ekleme ve özellikler ve öğeler bir paket için paket Tasarımcısını kullanarak kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Nasıl yapılır: MSBuild görevlerini kullanarak bir SharePoint çözüm paketi oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Nasıl yapılır: MSBuild görevlerini kullanarak bir SharePoint çözüm paketi oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Nasıl yapılır: MSBuild hedeflerini kullanarak SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
 
