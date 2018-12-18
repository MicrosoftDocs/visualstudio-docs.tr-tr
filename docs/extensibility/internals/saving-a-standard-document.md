---
title: Standart belge kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 251a9a7632a9d9615302cd3c5c1bf2a406529caf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875612"
---
# <a name="saving-a-standard-document"></a>Standart Belge Kaydetme
Ortam, kaydetme, Farklı Kaydet ve Tümünü Kaydet komutları işler. Bir kullanıcı seçtiğinde **Kaydet**, **Kaydet**, veya **Tümünü Kaydet** gelen **dosya** menüsü ya da sonuçta çözümü kapatır bir  **Tümünü Kaydet**, aşağıdaki süreç gerçekleşir.  
  
 ![Standart Düzenleyici](../../extensibility/internals/media/public.gif "genel")  
Kaydet ve işleme için standart bir düzenleyici Tümünü Kaydet komut Kaydet  
  
 Bu işlem aşağıdaki adımları ayrıntılı olarak verilmiştir:  
  
1. Zaman **Kaydet** ve **Kaydet** ortamı kullanır, komutları seçili <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> etkin belge penceresini belirlemek için hizmet ve böylece hangi öğeler kaydedilmelidir. Etkin belge penceresini tanındıktan sonra ortam öğe tanımlayıcısı (öğe kimliği) ve hiyerarşi işaretçi çalıştırılan Belge tablosu belgede bulur. Daha fazla bilgi için [çalıştırılan Belge tablosu](../../extensibility/internals/running-document-table.md).  
  
    Zaman **Tümünü Kaydet** komutu seçilene, ortam bilgileri kaydetmek için tüm öğelerin listesini derlemek için çalışan belge tablosunda kullanır.  
  
2. Çözüm aldığında bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> çağrı, seçilen öğeleri dizi aracılığıyla yinelenir (diğer bir deyişle, tarafından kullanıma sunulan birden çok seçimin <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> hizmeti).  
  
3. Seçimdeki her bir öğede çözüm çağırmak için hiyerarşi işaretçi kullanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> belirlemek için yöntemi olup olmadığını **Kaydet** menü komutu etkinleştirilmelidir. Kirli, bir veya daha fazla öğe varsa sonra **Kaydet** komut etkin. Hiyerarşi Standart Düzenleyici kullanıyorsa, ardından sorgulama hiyerarşi temsilcileri Düzenleyicisi durumuna çağırarak kirli <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> yöntemi.  
  
4. Kirli her seçili öğe üzerinde çözüm çağırmak için hiyerarşi işaretçi kullanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> uygun hiyerarşilerindeki yöntemi.  
  
    Belgeyi düzenlemek için standart bir düzenleyici kullanmak hiyerarşi için yaygın bir durumdur. Bu düzenleyici desteklemesi için bu durumda, belge verileri nesne <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> arabirimi. Alma bağlı <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> yöntemi çağrısı, proje bildirin belge çağırarak kaydediliyor Düzenleyicisi <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> belge veri nesnesi üzerinde yöntemi. Düzenleyici işlemek için ortamı izin verebilirsiniz **Kaydet** çağırarak iletişim kutusu, `Query Service` için <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> arabirimi. Bu bir işaretçi döndürür <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> arabirimi. Düzenleyici ardından çağırmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> yöntemi, bir işaretçi düzenleyicinin geçirme <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> uygulama yoluyla `pPersistFile` parametresi. Ortamı daha sonra kaydetme işlemi gerçekleştirir ve sağlar **Kaydet** iletişim kutusu Düzenleyicisi için. Ortamı daha sonra geri Düzenleyicisi ile çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5. Kullanıcı adsız bir belge (diğer bir deyişle, daha önce kaydedilmemiş bir belge) kaydetmeye çalışıyor, gerçekten Farklı Kaydet komutu gerçekleştirilir.  
  
6. Farklı Kaydet komutu için kullanıcıdan bir dosya adı için Farklı Kaydet iletişim kutusunda, ortam görüntüler.  
  
    Dosya adı değişmişse sonra bilgileri çağırarak önbelleğe belge çerçeve güncelleştirmek için hiyerarşi sorumludur <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).  
  
   Varsa **Kaydet** komut belgesinin konumunu taşır ve hiyerarşi için belge konumunu duyarlıdır ve hiyerarşideki başka bir hiyerarşide açık belge penceresi sahipliğini teslim etme için sorumludur. Proje dosyası proje ile ilgili bir iç veya dış dosya (çeşitli dosya) olup olmadığını izler, örneğin, bu oluşur. Çeşitli dosyalar projeye bir dosya sahipliğini değiştirmek için aşağıdaki yordamı kullanın.  
  
## <a name="changing-file-ownership"></a>Dosya sahipliğini değiştirme  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Çeşitli dosyalar projeleri için dosya sahipliğini değiştirmek için  
  
1.  Hizmet için sorgu <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> arabirimi.  
  
     Bir işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> döndürülür.  
  
2.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) yeni hiyerarşiye belge aktarmak için yöntemi. Farklı Kaydet komutu yürüttükten hiyerarşi bu yöntemi çağırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)