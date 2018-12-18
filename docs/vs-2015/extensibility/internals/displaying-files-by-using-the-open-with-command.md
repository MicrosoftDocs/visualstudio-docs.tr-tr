---
title: Komutu ile Aç'ı kullanarak dosyaları görüntüleme | Microsoft Docs
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
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 716e9f1551681b9e194bd300522f55ab5e927dab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816466"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Birlikte Aç Komutunu Kullanarak Dosyaları Görüntüleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir proje görüntülemek için IDE sorabilir **birlikte Aç** iletişim kutusu. Bu istek standart düzenleyicileri seçimi sahip bir dosyayı açmak için kullanıcıya sorar. Aşağıdaki adımlar, bu işlemi açıklanmaktadır.  
  
1.  Proje çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, için OSE_UseOpenWithDialog değerini belirterek `OSEOpenDocEditor` parametresi.  
  
2.  Belgenin dosya adı uzantısına bağlı olarak, IDE kayıt defteri can listelenen hangi düzenleyicileri belirtilen belgeyi açmayı belirler ve bu bilgiyi görüntüler **birlikte Aç** iletişim kutusu.  
  
    > [!NOTE]
    >  İçinde içermesi gereken bir iç Düzenleyicisi olan projelerin **birlikte Aç** iletişim kutusu için böyle bir düzenleyici her bir düzenleyici fabrikası kaydetmeniz gerekir. İç düzenleyiciler yalnızca işlev uygulamasında zorlanan proje, belirli bir türü ile birlikte <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemi. IDE, temel metin düzenleyicisi ve ikili düzenleyicide yerleşik Düzenleyici fabrikası sahiptir. IDE da bir düzenleyici fabrikası adına her kayıtlı Windows dosya ilişkilendirmesi örneği oluşturur. Microsoft Word gibi bir dosya örneğidir.  
  
3.  Kullanıcının seçtiği bir öğeden hemen sonra **birlikte Aç** çağırarak belge açılır iletişim kutusu, IDE'yi ardından <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> yöntemi. Daha fazla bilgi için [nasıl yapılır: açık standart düzenleyicileri](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Açma ve proje öğelerini kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Dosya Aç komutunu kullanarak dosyaları görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)

