---
title: Kaynak denetimi yapılandırma ayrıntıları | Microsoft Docs
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
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55e2364ca096b5329369e51ccdadf07f191720e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753706"
---
# <a name="source-control-configuration-details"></a>Kaynak Denetimi Yapılandırma Ayrıntıları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak denetimi uygulamak için proje sistemi ya da aşağıdakileri yapmak için düzenleyici düzgün şekilde yapılandırmak gerekir:  
  
-   Geçiş için durum değiştirme izni iste  
  
-   Bir dosyayı kaydetmeye izin iste  
  
-   Ekleme, kaldırma veya projedeki dosyaları yeniden adlandırmak için izin istemesi  
  
## <a name="request-permission-to-transition-to-changed-state"></a>Geçiş için durum değiştirme izni iste  
 Bir proje ya da Düzenleyicisi geçiş (değişiklik içeriyor) durum değiştirme izni çağırarak istemelisiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Uygulayan her Düzenleyicisi <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> çağırmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ve belge ortamdan döndürmeden önce değiştirmek için onay alma `True` için `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`. Bir proje, aslında bir proje dosyası için bir düzenleyici ve sonuç olarak, bir metin düzenleyicisi için dosyaları gibi proje dosyasının durumu değişti izleme uygulama için aynı sorumluluğuna sahip. Ortam değiştirilen çözüm durumunu işler, ancak çözüm başvuruyor, ancak, bir proje dosyası veya öğelerinden gibi depolamaz herhangi bir nesnenin durum değiştirme işlemesi gerekir. Proje veya düzenleyen bir öğe için Kalıcılık yönetmekten sorumlu ise, genel olarak, ardından bu durumu değişti izleme uygulamak için sorumludur.  
  
 Yanıt olarak `IVsQueryEditQuerySave2::QueryEditFiles` çağrısı, ortam aşağıdakileri yapabilirsiniz:  
  
- Düzenleyici ya da proje çalışması değişmeden (temiz) durumda kalması gereken değiştirmek için çağrı reddeder.  
  
- Belge verilerini yüklenmesi belirtir. Bir proje için proje verileri ortamı yeniden yükler. Bir düzenleyici üzerinden disk verileri yeniden yüklemeniz gerekir, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> uygulaması. Verileri yeniden yüklendiğinde, her iki durumda da proje veya düzenleyici bağlam değiştirebilirsiniz.  
  
  Uygun yükseltmek için karmaşık ve zor bir görev olduğundan `IVsQueryEditQuerySave2::QueryEditFiles` varolan bir kod tabanına üzerine çağırır. Sonuç olarak, bu çağrılar Düzenleyicisi ve proje oluşturma sırasında tümleştirilmesi gerekir.  
  
## <a name="request-permission-to-save-a-file"></a>Bir dosyayı kaydetmeye izin iste  
 Bir proje veya düzenleyen bir dosyayı kaydetmeden önce çağırmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Proje dosyaları için bu çağrılar zaman bir proje dosyasını kaydetmeyi bilir çözümü tarafından otomatik olarak doldurulur. Düzenleyiciler sürece bu çağrıları yapmaktan sorumlu Düzenleyicisi uygulamasını `IVsPersistDocData2` yardımcı işlevini kullanan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Düzenleyici uyguluyorsa `IVsPersistDocData2` bu şekilde, ardından çağrısı içinde `IVsQueryEditQuerySave2::QuerySaveFile` veya `IVsQueryEditQuerySave2::QuerySaveFiles` sizin yerinize yapılır.  
  
> [!NOTE]
>  Bu çağrılar sıd'lerde yaptığınız her zaman — diğer bir deyişle, birer birer düzenleyicinizi olduğunda iptal alabilirsiniz.  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Ekleme, kaldırma veya projedeki dosyaları yeniden adlandırmak için izin istemesi  
 Bir proje eklemek, yeniden adlandırmak veya bir dosya veya dizin kaldırmadan önce uygun çağırmalıdır `IVsTrackProjectDocuments2::OnQuery*` ortamından izin istemek yöntemi. İzni verildi sonra proje işlemi tamamlayın ve ardından uygun çağrı `IVsTrackProjectDocuments2::OnAfter*` ortamı işleminin tamamlandığını bildirmek için yöntemi. Proje yöntemlerini çağırmanız gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> tüm dosyalar (örneğin, özel dosyaları) ve yalnızca üst dosyaları için arabirim. Dosya aramaları zorunludur, ancak dizin çağrıları isteğe bağlıdır. Dizin bilgileri projenizi sahip sonra uygun çağırmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> yöntemleri, ancak bu bilgiler yok sonra ortamı dizin bilgileri çıkarımlar.  
  
 Proje yöntemlerini çağırmalıdır değil `IVsTrackProjectDocuments2` proje açın veya kapatın. Bu bilgileri başlangıçta istediğiniz dinleyicileri için tamamlanmasını bekleyebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> olay ve gereksinim duyduğu bilgileri bulmak için çözüm tekrarlayabilirsiniz. Kapanma durumunda bu bilgiler gerekli değildir. `IVsTrackProjectDocuments2` tablodan sağlanan <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.  
  
 Her ekleme, yeniden adlandırma ve kaldırma eylemi için bir `OnQuery*` yöntemi ve bir `OnAfter*` yöntemi. Çağrı `OnQuery*` eklemek, izin istemek için yöntemi yeniden adlandırın veya dosya veya dizin kaldırın. Çağrı `OnAfter*` yöntemi sonra dosya veya dizin eklendi, kaldırıldı veya yeniden adlandırılıp ve yeni durum proje durumu yansıtır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)

