---
title: Özel düzenleyiciler ve tasarımcılar oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 05eeae4901af8780927e0ce0577b385ee9ffa371
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950909"
---
# <a name="create-custom-editors-and-designers"></a>Özel düzenleyiciler ve tasarımcılar oluşturma
Visual Studio tümleşik geliştirme ortamı (IDE), farklı türde bir düzenleyici barındırabilirsiniz:  
  
- Visual Studio çekirdek Düzenleyicisi  
  
- Özel düzenleyiciler  
  
- Dış düzenleyiciler  
  
- Tasarımcılar  
  
  Aşağıdaki bilgileri Düzenleyicisi ihtiyacınız türünü seçmenize yardımcı olur.  
  
## <a name="types-of-editor"></a>Düzenleyici türleri  
 Visual Studio çekirdek Düzenleyicisi hakkında daha fazla bilgi için bkz. [düzenleyici ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md).  
  
### <a name="custom-editors"></a>Özel düzenleyiciler  
 Özel bir düzenleyici, özel durumlarda çalışmak üzere tasarlanmış bir uygulamadır. Örneğin, okumak ve Microsoft Exchange server gibi belirli bir depoya veri yazmak için işlev, bir düzenleyici oluşturabilirsiniz. Yalnızca, proje türü ile birlikte çalışan bir düzenleyici istediğiniz ya da bir düzenleyici istiyorsanız, yalnızca birkaç belirli komutları olan özel bir düzenleyici seçin. Ancak, kullanıcıların standart düzenlemek için özel bir düzenleyici kullanmanız mümkün olmayacaktır unutmayın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeleri.  
  
 Özel bir düzenleyici bir düzenleyici fabrikası kullanabilir ve kayıt defterine Düzenleyicisi hakkında bilgi ekleyin. Ancak, özel düzenleyici ile ilişkili proje türü herhangi bir şekilde özel düzenleyici örneği oluşturabilir.  
  
 Özel bir düzenleyici, yerinde etkinleştirme veya Basitleştirilmiş ekleme, bir görünüm uygulamak için kullanabilirsiniz.  
  
### <a name="external-editors"></a>Dış düzenleyiciler  
 Dış düzenleyicileri Microsoft Word, Not Defteri veya Microsoft FrontPage gibi Visual Studio'yla tümleşik olmayan Düzenleyicileri ' dir. Örneğin, metin için, VSPackage geçiriyorsanız, bu tür bir düzenleyici çağırabilirsiniz. Dış düzenleyici kendilerini ve Visual Studio dışında kullanılabilir. Ardından bir dış düzenleyici çağırmak ve bir ana penceresinde eklenebilir, IDE bir pencerede görüntülenir. Aksi durumda, sonra IDE ayrı bir pencerede için oluşturur.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Yöntemi kullanarak belge önceliği ayarlar <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> sabit listesi. Varsa `DP_External` değeri belirtilirse, dosyanın bir dış düzenleyici tarafından açılabilir.  
  
## <a name="editor-design-decisions"></a>Düzenleyicisi tasarım kararları  
 Aşağıdaki tasarım soruları uygulamanıza uygun en iyi Düzenleyicisi türünü seçmenize yardımcı olur:  
  
- Uygulamanız kendi veri dosyalarında veya tasarruf edeceksiniz? Dosya verilerini kaydeder, özel veya standart bir biçimde olacak mı?  
  
   Standart bir dosya biçimi kullanıyorsanız, projenize yanı sıra diğer proje türleri açabilir ve okuma/veri kendisine Yazma olacaktır. Ancak, bir özel dosya biçimi kullanırsanız, yalnızca proje türünüzü açabilir ve okuma/veri kendisine Yazma devam edecektir.  
  
   Proje dosyaları kullanıyorsa, standart Düzenleyici özelleştirmeniz gerekir. Projenizi dosyalarını kullanmaz, ancak bunun yerine bir veritabanı veya başka bir depodan öğelerinde kullanır, özel bir düzenleyici oluşturmanız gerekir.  
  
- Düzenleyici ActiveX denetimlerini barındırma gerekiyor mu?  
  
   Düzenleyici ActiveX denetimlerini barındırıyorsa, bir yerinde etkinleştirme Düzenleyici açıklandığı gibi uygulamak [yerinde etkinleştirme](../extensibility/in-place-activation.md). ActiveX denetimleri barındırmıyorsa, ardından basitleştirilmiş bir gömme düzenleyicisi kullanın veya özelleştirme [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] varsayılan düzenleyici.  
  
- Düzenleyici, birden çok görünüm desteklenecek? Görünümleri düzenleyiciniz aynı zamanda varsayılan düzenleyici görünür olmasını istiyorsanız, birden çok görünüm desteklemesi gerekir.  
  
   Düzenleyici birden çok görünüm desteklemesi gerekiyorsa, belge Düzenleyicisi için Görünüm nesneleri ve belge verilerini ayrı nesnelerin olması gerekir. Daha fazla bilgi için [birden çok belge görünümünü desteklemek](../extensibility/supporting-multiple-document-views.md).  
  
   Birden çok görünüm düzenleyiciniz destekliyorsa, kullanmayı planlıyor musunuz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] düzenleyicinin metin arabelleği uygulaması çekirdek (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> nesne) belge veri nesneniz için? Diğer bir deyişle, düzenleyici görünümü yan yana ile destek istiyorsunuz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çekirdek Düzenleyicisi? Bunu yapmak için özelliği Form Tasarımcısı'nın temelini...  
  
- İçinde bir dış düzenleyici barındırmak gereksinim duyarsanız, düzenleyici eklenebilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
   Gömülü olması, bir ana penceresi için dış düzenleyici oluşturma ve sonra çağrı gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> yöntemi ve kümesi <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> numaralandırma değerini `DP_External`. Düzenleyici eklenemiyor, IDE otomatik olarak için ayrı bir pencere oluşturur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İzlenecek yol: özel düzenleyici oluşturma](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Bir özel düzenleyici oluşturma açıklanır.  
  
 [İzlenecek yol: özel bir düzenleyici özellikleri ekleyin](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Özellikler için özel bir düzenleyici ekleme işlemi açıklanmaktadır.  
  
 [Tasarımcı başlatma ve meta verileri yapılandırma](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Bir designer başlatılmaya açıklanmaktadır.  
  
 [Tedarik tasarımcılara geri alma desteği](../extensibility/supplying-undo-support-to-designers.md)  
 Tasarımcılar için geri alma desteği açıklanmaktadır.  
  
 [Özel düzenleyicilerde söz dizimi renklendirmesi](../extensibility/syntax-coloring-in-custom-editors.md)  
 Sözdizimi çekirdek Düzenleyicisi'nde ve özel düzenleyicilerde renklendirme arasındaki farkı açıklar.  
  
 [Belge verileri ve özel düzenleyicilerde belge görünümü](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Özel düzenleyicilerde belge verileri ve belge görünümleri uygulamak açıklanmaktadır.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Eski arabirimleri Düzenleyicisi](../extensibility/legacy-interfaces-in-the-editor.md)  
 Çekirdek Düzenleyici yoluyla eski api'de açıklanmaktadır.  
  
 [Eski dil hizmeti geliştirme](../extensibility/internals/developing-a-legacy-language-service.md)  
 Dil hizmeti ekleme açıklanmaktadır.  
  
 [Visual Studio'nun diğer bölümlerini genişletme](../extensibility/extending-other-parts-of-visual-studio.md)  
 Kalan eşleşen kullanıcı Arabirimi öğeleri oluşturma açıklanır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>