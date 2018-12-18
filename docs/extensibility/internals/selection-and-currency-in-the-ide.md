---
title: Seçim ve para birimi IDE'de | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f71a176d469a5cd71aa377c800516e743eb1cc15
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840577"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE’de Seçim ve Para Birimi
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı (IDE) tutar kullanıcıların hakkında bilgi seçili nesnelerin seçimini kullanarak *bağlam*. Seçim bağlamı ile VSPackage iki yolla izleme para biriminde yer alabilir:  
  
-   IDE VSPackages para birimi bilgilerine göre yayılıyor.  
  
-   Şu anda etkin kullanıcıların seçimlerine IDE içinden izleyerek.  
  
## <a name="selection-context"></a>Seçim bağlamı  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE genel olarak izler, kendi genel seçimi bağlam nesnesi IDE para birimi. Aşağıdaki tablo, seçim bağlamı öğeleri gösterir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Geçerli hiyerarşi|Geçerli proje genellikle; bir NULL geçerli hiyerarşi bir bütün olarak çözüm geçerli olduğunu gösterir.|  
|Geçerli öğe kimliği|Seçili öğeyi geçerli hiyerarşi içinde; Proje bir pencerede birden çok seçimin olduğunda, birden çok geçerli öğe olabilir.|  
|Geçerli `SelectionContainer`|Özellikler penceresi özelliklerini görüntülemek için bir veya daha fazla nesneler içerir.|  
  
 Ayrıca, ortamın iki genel listeleri tutar:  
  
-   Etkin kullanıcı Arabirimi komut tanımlayıcıları listesi  
  
-   Şu anda etkin öğe türlerinin listesi.  
  
### <a name="window-types-and-selection"></a>Pencere türleri ve seçim  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE windows iki genel tür olarak düzenler:  
  
- Hiyerarşi türü windows  
  
- Araç ve belge pencereleri gibi çerçeve pencereleri  
  
  Para birimi, IDE Bu pencere türlerinin her biri için farklı bir şekilde izler.  
  
  En yaygın proje türü IDE denetimleri Çözüm Gezgini'nde bir penceredir. Bir proje türü penceresi ItemId genel seçimi bağlam ve genel hiyerarşi izler ve pencerenin geçerli hiyerarşi belirlemek için kullanıcının seçimine göre kullanır. Proje türü windows için küresel hizmet ortamı sağlayan <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>temellidir hangi VSPackages açık öğeler için geçerli değerler izleyebilirsiniz. Ortamda gözatma özelliği, bu genel hizmet tarafından yönetilir.  
  
  Çerçeve pencereleri çerçeve penceresi içinde DocObject SelectionContext değeri (hiyerarşi/öğe kimliği/SelectionContainer sorularının cevabını) göndermek için diğer taraftan, kullanın. biçimindeki telefon numarasıdır. Çerçeve pencerelerini kullanma hizmet <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> bu amaç için. DocObject hiyerarşi yerel değerlerini bırakarak yalnızca seçim kapsayıcısı için değerler gönderebilir ve MDI alt belgeler için tipik olan öğe kimliği değiştirilmemiş.  
  
### <a name="events-and-currency"></a>Olayları ve para birimi  
 İki tür olay ortamın para birimi kavramı etkileyen oluşabilir:  
  
-   Pencere çerçevesi seçim bağlamı için genel düzeyde yayılır ve olaylar. Bu tür bir olay örnekleri açıldı, açılan bir genel araç penceresi ya da açılan bir proje türü araç penceresi bir MDI alt penceresi içerir.  
  
-   Pencere çerçevesi seçim bağlamı içinde izlenen öğelerini değiştirme olayları. DocObject içinde seçimini değiştirmeden veya bir proje türü penceresinde seçimi değiştirme örneklerindendir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md)   
 [Kullanıcıya Geri Bildirim](../../extensibility/internals/feedback-to-the-user.md)