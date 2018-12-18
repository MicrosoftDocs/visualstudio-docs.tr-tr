---
title: Belge düzeyi çözümlerde belge koruması
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 22c8f135770fbd427d361b9c9b113da3b20e609a
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447875"
---
# <a name="document-protection-in-document-level-solutions"></a>Belge düzeyi çözümlerde belge koruması
  Microsoft Office Word ve Microsoft Office Excel koruma özelliklerini belge düzeyi projelerine kullanabilirsiniz. Bu özellikler, korumalı bir belge bölümlerine değişiklik yapmasını yetkisiz kullanıcıların engelleyin.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Çalışma kitabı tasarımcıda açıkken Excel kullanarak, koruma açıp kapatabilirsiniz. Word kullanarak, koruma yalnızca tasarımcının dışında açabilirsiniz. Çalışma zamanında etkinleştirmek ya da program aracılığıyla Word ve Excel için korumayı devre dışı bırakın.  
  
 Tasarımcıda açık olan bir belgenin belge koruması etkinleştirildiğinde, tüm denetimler çıkarılır **araç** veya kullanılamıyorsa yapılan herhangi bir şeyin sürükleyin olamaz **veri kaynakları** belge penceresine.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument ve korumalı belgeler  
 Bir belge korunuyorsa, veri önbelleği gelen belgenin dışında erişilemez. Kullanamazsınız <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> almak veya Korumalı belgede önbelleğe alınmış verileri işlemek için sınıf ya da diğer yöntemlerini <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> sınıfı.  
  
## <a name="word-document-protection-in-the-designer"></a>Word Tasarımcısı'nda belge koruması  
 Visual Studio'da açıkken koruma Word belgesine veya şablon sayfasına eklerseniz, Tasarımcısı'nda korumayı zorlamayı başlatılamıyor. Visual Studio'da açın ve korumayı zorlamayı başlamadan önce çalışma modunda gerekir, belge tasarım modunda değil.  
  
 Ancak, koruması etkin olan mevcut bir Word belgesini kullanan bir proje oluşturduğunuzda, belge Tasarımcısı'nda açıkken korunur. Belgenin korumalı bölümlerini düzenleyemezsiniz, ancak belgeyi otomatikleştirmek için Kod Düzenleyicisi'nde hala kod yazabilirsiniz. Belge Visual Studio'da açıkken koruma etkinse, projeyi de yapılandıramazsınız.  
  
 Böylece belgeyi düzenlemek ve projeyi derlemek belge tasarımcıda açıkken korumayı kapatabilirsiniz. Hata ayıklarken tasarımcıda kopya için korumayı devre dışı bırakamazsınız; hata ayıklama sırasında açan Tasarımcısı'nda açık olandan ayrı bir kopyasını belgedir (çıktı kopya depolanır *\bin* Visual Basic için dizin ve *\bin\debug* için C# dizin).  
  
 Visual Studio Proje kapatma, proje dizinindeki belgenin kopyasını açarak ve korumayı etkinleştirme Tasarımcısı'nda açılır belgenin kopyasında korumayı etkinleştirebilirsiniz.  
  
## <a name="enforce-word-document-protection-on-build"></a>Yapı Word Belge Korumasını zorla  
 Koruma etkin hata ayıklama için bir belge açıldığında, böylece visual Studio derleme işlemi sırasında koruma Word belgelerini ve şablonları için zorlamayı başlatır. Belgenin boş bir parolayla korunuyor.  
  
 Koruma belgede kodu ise derleme sırasında etkindir <xref:Microsoft.Office.Tools.Word.Document.Startup> durumlara veya uygulamanın davranışını değiştirme olayı, bu kod hata ayıklaması yapılması doğru. Belge açıldıktan sonra koruma devre dışı bırakırsanız, başlatma kod hata ayıklaması veya test.  
  
## <a name="setting-the-password"></a>Parolayı ayarlama  
 Visual Studio otomatik olarak koruma sağlar, ancak varsayılan olarak hiçbir parola sağlar. Bir parola sağlamak için belge koruması istiyorsanız, çözümünüzü dağıtmadan önce onu eklemeniz gerekir. Parola eklemek, belgeden korumayı kaldırma yetkili kullanıcıların olanak sağlar; bir parola olmadan koruma kolayca kaldırılamaz. Bir parola ayarlama hakkında ayrıntılı bilgi için belirli Office uygulamasında yardımına bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: program aracılığıyla belgeleri ve belge parçalarını koruma](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)   
 [Bilgi Hakları Yönetimine ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Office belgelerinde parola koruması](../vsto/password-protection-on-office-documents.md)   
 [Nasıl yapılır: kodun kısıtlı izinle belgelerin arkasında çalışmasına izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Tasarlama ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md)  
  
  