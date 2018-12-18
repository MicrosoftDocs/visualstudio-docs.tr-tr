---
title: Kaynak denetimi tasarım kararları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a0932d0029ee924d900dead6b80c3ad2d7e555a0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726074"
---
# <a name="source-control-design-decisions"></a>Kaynak Denetimi Tasarım Kararları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıdaki tasarım kararlarını projeler için kaynak denetimi uygularken dikkate alınmalıdır.  
  
## <a name="will-information-be-shared-or-private"></a>Bilgi, paylaşılan veya özel olacak mı?  
 Yapabileceğiniz en önemli tasarım özel nedir ve hangi bilgilerin paylaşılabilir kararıdır. Örneğin, proje için dosyaların listesini paylaşılan, ancak bu dosyaları listesi içinde bazı kullanıcılar özel dosyaları sahip olmak isteyebilirsiniz. Derleyici ayarları paylaşılır, ancak başlangıç projesi genellikle özeldir. Yalnızca paylaşılan, paylaşılan bir geçersiz kılma ile veya tamamen özel ayarlarıdır. Çözüm kullanıcı seçenekleri (. suo) dosyaları gibi tasarım gereği, özel öğeler halinde denetlenmez [!INCLUDE[vsvss](../../includes/vsvss-md.md)]. Herhangi bir özel bilgi .suo dosya ya da oluşturduğunuz, örneğin, belirli bir özel dosya gibi özel dosyaları depolamak mutlaka bir. csproj.user dosya Visual C# veya. vbproj.user dosya Visual Basic için.  
  
 Bu karar, her şeyi içeren değil ve bir öğe tarafından temelinde yapılamaz.  
  
## <a name="will-the-project-include-special-files"></a>Projeye özel dosyaları içerecek?  
 Başka bir önemli tasarım proje özel dosyaları kullanıp kullanmadığını kararıdır. Çözüm Gezgini'nde ve iade görünür ve kullanıma iletişim kutuları dosyaları temelini oluşturan gizli dosyalar özel dosyalarıdır. Özel dosyaları kullanıyorsanız, aşağıdaki yönergeleri izleyin:  
  
1.  Özel dosyalar proje kök düğümü ile ilişkilendirilmemiş — diğer bir deyişle, kendi proje ile dosya. Proje dosyanız, tek bir dosya olmalıdır.  
  
2.  Ne zaman özel dosya eklendiğinde, kaldırılır veya bir proje, uygun olarak yeniden adlandırıldı <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> dosyalarıdır özel dosyaları gösteren bayrak kümesi ile olayları tetiklendi. Bu olaylar uygun çağırma projeye yanıt ortama göre adlandırılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> yöntemleri.  
  
3.  Proje veya Düzenleyicisi çağırdığında <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> bir dosya için özel bu dosyayla ilişkili dosyaları otomatik olarak kullanıma alınmamış. Özel dosyaların yanı sıra üst dosya geçirin. Ortam içinde geçirilen tüm dosyaları arasındaki ilişki algılar ve uygun şekilde kullanıma kullanıcı arabiriminde özel dosyaları gizle.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)

