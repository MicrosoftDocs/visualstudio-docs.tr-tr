---
title: Projeler ve düzenleyiciler için ek kaynak denetimi yönergeleri | Microsoft Docs
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
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c52244aa91217ae57d4265ce37a530b2e48d0e93
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770697"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Projeler ve Düzenleyiciler için Ek Kaynak Denetimi Yönergeleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projeler ve düzenleyiciler için kaynak denetimi desteklemek için uyması kuralları vardır.  
  
## <a name="guidelines"></a>Kuralları  
 Proje veya Düzenleyicisi de kaynak denetimi desteklemek için aşağıdakileri yapmalıdır:  
  
|Alan|Proje|Düzenleyici|Ayrıntılar|  
|----------|-------------|------------|-------------|  
|Özel dosyaların kopyalarını|X||Ortam, özel dosyaların kopyalarını destekler. Diğer bir deyişle, projede kayıtlı her kişi projedeki dosyaları onun kendi özel kopyasına sahip olur.|  
|ANSI/Unicode kalıcılığı|X|X|Kalıcılık kod yazma, çoğu kaynak denetimi program Unicode şu anda desteklemediğinden dosyaları ANSI biçiminde kalıcı hale getirin.|  
|Dosyaları numaralandırma|X||Project kullanarak dosyaları listesini numaralandırır kaldırılmasının belirli içerdiği tüm dosyaların listesini içermelidir ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Proje öğesi adları ile aynı zamanda açığa kendi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> (özel dosyaları dahil) uygulama ve Destek ad araması aracılığıyla kendi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> uygulaması.|  
|Metin biçimi|X|X|Mümkün olduğunda, dosyaları birleştirme farklı sürümlerini desteklemek üzere metin biçiminde olmalıdır. Metin biçiminde olmayan dosyalar daha sonra dosyayı diğer sürümleri ile birleştirilemez. Tercih edilen metin XML biçimindedir.|  
|Tabanlı başvurusu|X||Başvuru tabanlı projeler kaynak denetimine kolayca desteklenir. Ancak, projeyi olup bu dosyalar disk üzerinde mevcut bağımsız olarak, isteğe bağlı olarak, dosyaların listesini oluşturabilir sürece dizin tabanlı projeler kaynak denetimi tarafından da desteklenir. Kaynak denetiminden bir proje açıldığında, proje dosyasının ilk önce dosyalarından birini aşağı getirilir.|  
|Nesnelerle ve özelliklerle öngörülebilir sırayla Sürdür|X|X|Birleştirme kolaylaştırmak için alfabetik sırayla gibi tahmin edilebilir bir sırada dosyalarınızı kalıcı hale getirin.|  
|Yeniden yükle|X|X|Bir dosya değiştirildiğinde diskte düzenleyiciniz yeniden mümkün olması gerekir. Kaynak denetiminde katıldığınızda, ortam verileri sizin için çağırarak yeniden yükleyecektir, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> uygulaması. Kullanıma alma IVsQueryEditQuerySave çağrıldığında gerçekleşir en zor yeniden durumdur::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ve bilgileri işleniyor. Ancak yeniden kodunuzu bu durumda çalıştırılabilmesi gerekir.<br /><br /> Ortam, proje dosyaları otomatik olarak yeniden yükler. Ancak, bir proje uygulamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> iç içe toplamalar, hiyerarşiler yeniden yüklemeyi desteklemek için proje dosyaları iç içe geçmiş.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)

