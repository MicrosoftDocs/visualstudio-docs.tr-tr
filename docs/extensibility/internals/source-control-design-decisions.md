---
title: Kaynak denetimi tasarım kararları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0385d5feb7baf7fe60e253616c8db0f326932e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131320"
---
# <a name="source-control-design-decisions"></a>Kaynak denetimi tasarım kararları
Aşağıdaki tasarım kararlarını projeleri için kaynak denetimi uygularken dikkate alınmalıdır.  
  
## <a name="will-information-be-shared-or-private"></a>Bilgiler, paylaşılan veya özel olacak?  
 Yapabileceğiniz en önemli tasarım kararı hangi bilgilerin paylaşılabilir ve özel nedir ' dir. Örneğin, proje için dosya listesini paylaşılan, ancak bu dosyaları listede bazı kullanıcılar özel dosyaları sahip olmak isteyebilirsiniz. Derleyici ayarları paylaşılan ancak başlangıç projesi genellikle özeldir. Tamamen paylaşılan, paylaşılan bir geçersiz kılma ile veya yalnızca özel ayarlar. (.Suo) dosyaları, çözümü kullanıcı seçenekleri gibi tasarım gereği, özel öğeleri içine denetlenmez [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Özel bir bilgi .suo dosya ya da oluşturduğunuz, örneğin, belirli bir özel dosya gibi özel dosyaları depolamak mutlaka bir. csproj.user dosya Visual C# için veya bir. vbproj.user dosya Visual Basic.  
  
 Bu kararı her şeyi içeren değil ve bir öğe tarafından olarak yapılır.  
  
## <a name="will-the-project-include-special-files"></a>Proje özel dosyaları içerir?  
 Başka bir önemli tasarım proje yapınızı özel dosyaları kullanıp kullanmadığını bir karardır. Çözüm Gezgini'nde ve iade görünür ve teslim alma iletişim kutuları dosyaları temelini oluşturan gizli dosyaları özel dosyalarıdır. Özel dosyaları kullanırsanız, aşağıdaki yönergeleri izleyin:  
  
1.  Özel dosyaları proje kök düğüm ilişkilendirmeyin — diğer bir deyişle, proje ile kendini dosya. Proje dosyası tek bir dosya olmalıdır.  
  
2.  Ne zaman özel dosyaları eklenen, kaldırıldı veya yeniden adlandırılmış bir projede uygun <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> dosyalarıdır özel dosyaları belirten bayrak kümesi ile olay tetiklenir. Bu olaylar uygun çağırma proje yanıta ortamında tarafından denir <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> yöntemleri.  
  
3.  Proje veya Düzenleyicisi çağırdığında <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> bir dosya için bu dosyayla ilişkili özel dosyalar otomatik olarak kullanıma değil. Özel dosyalarında birlikte üst dosya geçirin. Ortam olarak geçirilen tüm dosyaları arasındaki ilişkiyi algılar ve uygun şekilde kullanıma UI özel dosyaları gizle.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)