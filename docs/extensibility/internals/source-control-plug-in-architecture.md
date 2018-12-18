---
title: Kaynak denetimi eklenti mimarisi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 498f3aeb87855a0dac5afacc1baa7e2e816375f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132397"
---
# <a name="source-control-plug-in-architecture"></a>Kaynak Denetim eklenti mimarisi
Kaynak denetimi desteği ekleyebilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uygulama ve kaynak denetimi eklenti ekleme tümleşik geliştirme ortamı (IDE). IDE iyi tanımlanmış kaynak denetim eklentisi API üzerinden eklenti kaynak denetimi bağlanır. IDE araç çubukları ve menü komutlarını oluşan bir kullanıcı arabirimi (UI) sağlayarak kaynak denetim sistemi sürüm denetim özelliklerini gösterir. Kaynak Denetim Eklentisi Kaynak denetimi işlevlerinin uygular.  
  
## <a name="source-control-plug-in-resources"></a>Kaynak denetimi eklentisi kaynakları  
 Kaynak Denetim eklentisi oluşturabilir ve sürüm oluşturma bağlamak yardımcı olacak kaynaklar sunulmaktadır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Kaynak Denetim Eklentisi Kaynak denetimi eklenti tarafından uygulanan gerekir ve böylece içine tümleştirilebilir API belirtimi içeriyor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Ayrıca, bir iskelet kaynak denetimi eklenti gösteren uyarlamasını temel işlevleri kaynak denetim eklentisi API'si ile uyumlu uygulayan kod örneği (C++ ile yazılmış) içerir.  
  
 Kaynak Denetim eklentisi API belirtimine uygun olarak kaynak denetimi eklentisi API uygulanan işlevler gerekli kümesini içeren bir kaynak denetimi DLL oluşturursanız, tüm kaynak denetim sistemi tercih ettiğiniz yararlanan olanak sağlar.  
  
## <a name="components"></a>Bileşenler  
 Kaynak denetimi bağdaştırıcı paketi diyagramdaki bir kaynak denetimi işlemi kaynak denetimi eklentisi tarafından desteklenen bir işlev çağrısı için kullanıcının isteği çevirir IDE bileşenidir. Bunun yapılması, IDE ve eklenti kaynak denetimi bilgileri ve geriye IDE ve eklenti arasında geçirir etkili bir iletişim kutusu olmalıdır. Bu iletişim gerçekleşmesi, her ikisi de aynı dili konuşan gerekir. Kaynak Denetim eklentisi bu belgede özetlenen bu değişim için ortak sözlük API'dir.  
  
 ![Kaynak kodu denetimi mimarisi diyagramı](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch")  
VS ve kaynak denetimi arasındaki etkileşim eklenti gösteren mimarisi diyagramı  
  
 Mimari diyagramda gösterildiği gibi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VS Kabuğu'nda, diyagram olarak etiketlenmiş Kabuk barındıran kullanıcının çalışma projeleri ve düzenleyicileri ve Çözüm Gezgini gibi ilişkili bileşenleri. Kaynak denetimi bağdaştırıcı paketi IDE ve eklenti kaynak denetimi arasındaki etkileşimi işler. Kaynak denetimi bağdaştırıcı paketi kendi kaynak denetimi kullanıcı Arabirimi sağlar. Bu kullanıcı başlatmak ve kaynak denetimi işlemi kapsamını tanımlamak için etkileşimde en üst düzey UI olur.  
  
 Kaynak Denetim eklentisi şekilde gösterildiği gibi iki bölümden oluşur, kendi kullanıcı Arabirimi olabilir. Kutunun "Satıcı UI" etiketli sağladığınız kaynak denetimi eklenti oluşturucusu, özel kullanıcı arabirimi öğelerini temsil eder. Kullanıcı bir Gelişmiş kaynak denetim işlemi çalıştırdığında bu doğrudan kaynak denetimi eklentisi tarafından görüntülenir. "Yardımcısı UI" etiketli kutuyu IDE dolaylı olarak çağrılan kaynak denetimi eklenti kullanıcı Arabirimi özellikleri kümesidir. Kaynak Denetim eklentisi UI ilgili iletileri IDE IDE tarafından sağlanan özel geri arama işlevleri üzerinden geçirir. IDE ile daha sorunsuz bir tümleştirme UI Yardımcısı kolaylaştıran (genellikle kullanım yoluyla bir **Gelişmiş** düğmesi) ve bu nedenle daha birleşik bir son kullanıcı deneyimi sağlar.  
  
 Kaynak Denetim eklentisi değişiklikler yapamazsınız [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kabuk ve sonuç olarak, kaynak denetim bağdaştırıcı paketi veya kaynak için IDE tarafından sağlanan kullanıcı Arabirimi denetim. Son kullanıcı için tümleşik bir deneyim katkıda çeşitli kaynak denetim eklentisi API işlevleri uyarlamasını aracılığıyla sunulan esneklik maksimum kullanım yapmanız gerekir. Kaynak Denetim eklentisi API belgelerine başvuru bölümü, bazı gelişmiş kaynak denetim eklentisi özellikleri için bilgileri içerir. Bu özelliklerden yararlanmak için kaynak denetim eklentisi başlatma sırasında gelişmiş özelliklerini IDE'ye bildirmeniz gerekir ve her yetenek için belirli gelişmiş işlevler uygulamalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetim Eklentileri](../../extensibility/source-control-plug-ins.md)   
 [Sözlük](../../extensibility/source-control-plug-in-glossary.md)   
 [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)