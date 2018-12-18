---
title: Office çözümleri geliştirmesine genel bakış (VSTO)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3586d6bc141992d7d8fe4629e7f56d04e4e247aa
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672632"
---
# <a name="office-solutions-development-overview-vsto"></a>Office çözümleri geliştirmesine genel bakış (VSTO)
  Çözümleri Microsoft Office'in ön ucu olarak kullanarak, tanıdık Microsoft Office kullanıcı arabirimleri ve sözcük işlem özellikleri Word, Excel verilerini analiz özelliklerini ve Outlook e-posta yönetimi özelliklerini gibi araçları yararlanabilir . Office uygulamalarını özelleştirin ve iş süreçleriniz için gereken belirli özellikleri eklemek için Visual Studio çözümleri geliştirebilirsiniz. Örneğin, Word'ün kullanıma sözleşmeleri düzenlenebilir veya düzenlenemez yapılabilmesi için önceden varolan parçaların çeviren bir sözleşme oluşturucuyu kapatabilirsiniz. Excel ile farklı projeler için özelleştirilmiş bir otomatik bütçe çalışma sayfası oluşturabilirsiniz. Kullanıcılarınızın, karmaşık çözümleri web tabanlı bir mimari kullanırsanız, duruma göre daha pratik hale getiren office çözümlerini çevrimdışı da yararlanabilirsiniz.  
  
 Bu konu başlığı altında bulunan Visual Studio Office geliştirici araçları (VSTO) Office Şablonları için Visual Studio araçları kullanarak oluşturabileceğiniz Office çözümlerinin türlerine genel bakış sağlar. Office ile geliştirme hakkında genel bilgi için bkz. [Office Geliştirici Merkezi](https://dev.office.com/).  
  
## <a name="choose-an-office-project-type"></a>Bir Office proje türünü seçin  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] VSTO tabanlı Office geliştirme için proje şablonları aşağıdaki türlerini sağlar:  
  
- **Belge düzeyi özelleştirmeleri** belirli bir belgeyle ilişkilidir.  
  
- **VSTO eklentileri** uygulamayla ilişkilendirilir.  
  
  Bu proje türleri, çözümünüz için en iyi olduğuna karar vermek için kodunuzu çalıştırmak için istediğinizi düşünün yalnızca belirli bir belge açık olduğundan veya uygulama kodunun kullanılabilir olmasını isteyip istemediğinizi her çalıştığı. Proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).  
  
  Oluşturabileceğiniz proje türleri, hangi Office uygulamalarını geliştirme bilgisayarına yüklediğiniz bağlıdır. Daha fazla bilgi için [Office uygulaması ve proje türüne göre kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).  
  
### <a name="document-level-customizations"></a>Belge düzeyinde özelleştirmeler  
 Belge düzeyi özelleştirmelerini tek bir belge, çalışma kitabı veya Microsoft Office Word veya Microsoft Office Excel şablonu ile ilişkili olan derleme oluşur. İlişkili belge açıldığında derleme yüklenir. Oluşturma, özelleştirme özellikleri, ilişkili belge açık olduğunda kullanılabilir. Özelleştirmeleri, herhangi bir belge açık olduğunda, yeni bir menü öğesi veya Şerit sekmesi görüntüleme gibi birçok farklı uygulama değişiklikleri yapamazsınız.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Belge düzeyi özelleştirmeleri oluşturmanıza yardımcı olacak araçlar içerir. Bir tasarım yüzeyini olarak özelleştirdiğiniz belge barındırılan [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], denetimler üzerine sürükleyip bırakarak belge tasarım sağlar. Diğer birçok [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] özellikleri, belge düzeyinde projelerde, Windows Forms denetimleri, sürükle ve bırak veri bağlama ve tümleşik bir hata ayıklayıcı gibi kullanılabilir.  
  
 Özelleştirmeler hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Excel için belge düzeyi özelleştirmelerini programlama kullanmaya başlayın](../vsto/getting-started-programming-document-level-customizations-for-excel.md)  
  
-   [Word için belge düzeyi özelleştirmelerini programlama kullanmaya başlayın](../vsto/getting-started-programming-document-level-customizations-for-word.md)  
  
-   [Belge düzeyi özelleştirmeler mimarisi](../vsto/architecture-of-document-level-customizations.md)  
  
### <a name="vsto-add-ins"></a>VSTO eklentileri  
 VSTO eklentileri, Microsoft Office uygulaması ile ilişkili olan derleme oluşur. İlişkili uygulama başlatıldığında uygulama çalışmaya başladıktan sonra kullanıcılar ayrıca VSTO eklentileri yükleyebilir, ancak genellikle, VSTO eklentisi çalışır. Oluşturduğunuz VSTO Add-Ins özellikleri uygulamanın kendisinin belgeler açık olduğu bağımsız olarak kullanılabilir.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] VSTO eklentileri oluşturmanıza yardımcı olacak araçlar içerir. Eklenti projeleri için VSTO eklentisi temsil eden bir otomatik olarak oluşturulan sınıf içerir. Bu sınıf, özellikler ve konak uygulamanın nesne modeline erişme ve VSTO eklentisi yüklendi ve kapandığında kodu çalıştırmak için kullanabileceğiniz olaylar sağlar. Diğer birçok [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] VSTO eklentisi projelerinde, Windows Forms ve tümleşik bir hata ayıklayıcı gibi özellikleri kullanılabilir.  
  
 VSTO eklentileri hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [VSTO eklentileri programlama kullanmaya başlayın](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)  
  
## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Birincil birlikte çalışma derlemelerini kullanarak Office uygulamalarını otomatikleştirme  
 Uygulamanın nesne modeli erişen kod yazarak çözümünüze bir Office uygulamasının özelliklerini program aracılığıyla ekleyebilirsiniz. Nesne, çeşitli özellikler ve yöntemler aracılığıyla işlevselliği kullanıma sunan sınıflarının düzenleme modelleridir. Her bir Office uygulaması için nesne modeli farklıdır.  
  
 Office geliştirme araçları kullanılarak oluşturulmuş bir çözümü bir Office uygulamasından nesne modelini kullanmak için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], uygulama için birincil birlikte çalışma derlemesi (PIA) kullanmanız gerekir. PIA, yönetilen kodun çözümünüzdeki Office uygulamasının COM tabanlı nesne modeliyle etkileşimini sağlar.  
  
 Office yüklü ve uygulamanızı geliştirme bilgisayarınızın genel derleme önbelleğinde kayıtlı çoğu geliştirme görevlerinin gerçekleştirilebilmek için PIA'ların olması gerekir. Daha fazla bilgi için [Office çözümleri geliştirmek için bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md). VSTO Office çözümlerinin çalışması için son kullanıcı bilgisayarlarında Office PIA'ların gerekmez. Daha fazla bilgi için [tasarım ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md).  
  
 VSTO Office çözümlerinde PIA'ların kullanma hakkında daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)  
  
-   [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)  
  
## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Son kullanıcı bilgisayarlarında Microsoft VSTO Office çözümleri çalıştırın  
 Bir VSTO Office çözüm oluşturduğunuzda, dağıtım gereksinimleri geliştirme seçimlerinizi nasıl etkileyeceğini göz önünde bulundurun.  
  
### <a name="deployment-options"></a>Dağıtım seçenekleri  
 Office geliştirme araçları kullanarak oluşturduğunuz çözümleri dağıtmak için ClickOnce veya Windows Installer'ı kullanın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. ClickOnce dağıtımı, yüklü ve minimum kullanıcı müdahalesiyle çalıştırma kendi kendini güncelleştirme çözümleri oluşturmanıza olanak sağlar. Windows Installer (*.msi*) dosyaları kolayca son kullanıcı bilgisayarlara dağıtılan veya Systems Management Server (SMS) kullanılarak dağıtılmış. VSTO Office çözümlerini dağıtma hakkında daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).  
  
### <a name="install-prerequisites"></a>Ön koşulları yükle  
 Son kullanıcıların bir çözümü çalıştırabilmeniz için önce Office geliştirme araçları kullanarak oluşturduğunuz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], bilgisayarlarını bazı Önkoşullar yüklü olması gerekir. ClickOnce kullanarak veya bir Windows Installer dosyası oluşturma çözümünüzün dağıtırsanız, bu önkoşulları çözümünüzle birlikte yüklenebilir. Daha fazla bilgi için [Office çözüm dağıtım önkoşullarını](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e) ve [nasıl yapılır: son kullanıcı bilgisayarlarında Office çözümlerinin çalışması için Önkoşulları Yükleme](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
### <a name="security"></a>Güvenlik  
 Güvenlik VSTO Office çözümleri zorlanır için bir dizi tarafından denetim [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çözüm yüklendiğinde yapar. Dağıtım bildiriminin konumunu güveniliyor ya da dağıtım bildirimi imzalamak için kullanılan sertifikanın güvenilir olup olmadığını doğrulamayı bu denetimleri içerir. Daha fazla bilgi için [güvenli Office çözümleri](../vsto/securing-office-solutions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Başlama &#40;Visual Studio'da Office geliştirme&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Belge düzeyi özelleştirmeler mimarisi](../vsto/architecture-of-document-level-customizations.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [Excel için belge düzeyi özelleştirmelerini programlama kullanmaya başlayın](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Word için belge düzeyi özelleştirmelerini programlama kullanmaya başlayın](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [VSTO eklentileri programlama kullanmaya başlayın](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  