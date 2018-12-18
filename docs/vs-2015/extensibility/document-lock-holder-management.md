---
title: Belge kilit tutucusu Yönetimi | Microsoft Docs
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
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8eaeb8529f570db112bf43813fe20339f3bca7c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786307"
---
# <a name="document-lock-holder-management"></a>Belge Kilit Tutucusu Yönetimi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çalıştırılan Belge tablosu (RDT) açık belgeler veya sahip oldukları herhangi bir düzenleme kilitleri sayısını tutar. Bu program aracılığıyla arka planda bir belge penceresi açık bir belgede görmeye kullanıcı olmadan düzenlendiğinde RDT belgede bir düzenleme kilidi yerleştirebilirsiniz. Bu işlev, genellikle grafik kullanıcı arabirimi aracılığıyla birden çok dosyayı değiştiren tasarımcılar tarafından kullanılır.  
  
## <a name="document-lock-holder-scenarios"></a>Belge kilit tutucusu senaryoları  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Dosya "a" olan bir bağımlılığa dosya "b"  
 Dosya türü için bir standart Düzenleyici "A", uygulamadan burada bir durum düşünün "a" ve her dosya türü "a" bir başvuru (veya bağımlılığa) sahip bir dosya türü "b". Bir standart Düzenleyici "B", "b" türündeki dosyalar için bulunmaktadır. Düzenleyici "A" dosya açıldığında, "a" BT "b" karşılık gelen dosyaya başvuru alır. Dosya "b" görüntülenmez ancak "A" Düzenleyicisi değiştirebilirsiniz. Düzenleyicisi "A" alır bir başvuru dosyasının belge verileri "b" öğesinden <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> yöntemi ve ayrıca, "b" dosya çubuğunda bir düzenleme kilidi tutar. Düzenleyici "A" yapıldıktan sonra "dosya b azaltma düzenleme kilidi" değiştirme sayısı "b" dosya çağırarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> yöntemi. Adlı değilse bu adımı atlayabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> yöntemi parametresi ile `dwRDTLockType` kümesine <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Dosya "b", farklı bir düzenleyici tarafından açılmış  
 Düzenleyici "A", açmaya çalıştığında "b" dosya "B" Düzenleyicisi tarafından zaten açıldığında, olay, işlemek için iki ayrı senaryo vardır:  
  
-   Dosya "b" uyumlu bir düzenleyicide açık olduğunda, "dosya"b"kullanarak bir belge düzenleme kilidi kaydetme Düzenleyicisi A" olmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> yöntemi. "A" düzenleyiciniz değiştirme dosya "b" yapıldıktan sonra kaydını belge düzenleme kilidi kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> yöntemi.  
  
-   Dosya "b" uyumsuz bir şekilde açık değilse, başarısız "A" veya "A" kısmen açın ve uygun bir hata iletisi görüntüler düzenleyici ile ilişkili görünüm verebilirsiniz Düzenleyicisi tarafından ya da dosya "b" denenen açılmasına izin verebilirsiniz. Hata iletisi kullanıcının dosya "b" uyumsuz bir düzenleyicide kapatın ve ardından "a" kullanarak dosyayı yeniden açın istemeniz gerekir Düzenleyicisi "A". Ayrıca uygulayabilirsiniz [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> uyumlu bir düzenleyicide açık olan dosya "b" kapatmak için kullanıcıdan istemek için. Kullanıcı dosya "b", dosyanın açılmasını kapanıyorsa içinde "a" Düzenleyicisi "A" normal şekilde devam eder.  
  
## <a name="additional-document-edit-lock-considerations"></a>Ek belge düzenleme kilidi konuları  
 Düzenleyicisi "A", "b" dosya çubuğunda kilit sahip bir belge Düzenleyicisi "B" bir belge tutuyorsa yaptığınız çok "b" dosyasının kilidi Düzenle yalnızca Düzenleyicisi'ni düzenlemek, varsa, farklı bir davranış alırsınız. İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **Sınıf Tasarımcısı** düzenleme kilidi ilişkili kod dosyasına bulundurmayan bir görsel tasarımcı örneğidir. Diğer bir deyişle, ilişkili kod dosyasına kullanıcının sahip olduğu bir sınıf diyagramı Tasarım Görünümü'nde açın ve aynı anda açarsanız ve kullanıcı kod dosyası değiştirir ancak değişiklikleri kaydedemez değişiklikler de için sınıf diyagramı (.cd) dosyası kaybolur. Varsa **Sınıf Tasarımcısı** sahip yalnızca belge kilit kod dosyası Düzenle, kullanıcı kod dosyası kapatılırken değişiklikleri kaydetmek için istenmez. IDE yalnızca kullanıcı kapatıldıktan sonra değişiklikleri kaydetmek için kullanıcıdan **Sınıf Tasarımcısı**. Her iki dosyada kaydedilen değişiklikler yansıtılır. Her iki **Sınıf Tasarımcısı** ve kullanıcı kod dosyası ya da formun kapatırken kaydedilecek istenir dosyası Kod Düzenleyicisi'ni kod dosya belge düzenleme kilitleri tutulur. Bu noktada kaydedilen değişiklikleri hem formun ve kod dosyasında yansıtılır. Sınıf diyagramları hakkında daha fazla bilgi için bkz. [(Sınıf Tasarımcısı) Sınıf diyagramları ile çalışma](../ide/working-with-class-diagrams-class-designer.md).  
  
 Bir belge Düzenleyicisi olmayan bir düzenleme kilit yerleştirmek gerekiyorsa, uygulamanız gereken Not <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> arabirimi.  
  
 Kod dosyaları programlı olarak değiştirir, birden çok kez bir kullanıcı Arabirimi Tasarımcısı için birden fazla dosya değişiklikleri yapar. Böyle durumlarda <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> yöntemi yoluyla bir veya daha fazla belge kaydetme işler **aşağıdaki öğelerdeki değişiklikleri kaydetmek istiyor musunuz?** iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalıştırılan Belge tablosu](../extensibility/internals/running-document-table.md)   
 [Kalıcılık ve Çalıştırılan Belge Tablosu](../extensibility/internals/persistence-and-the-running-document-table.md)

