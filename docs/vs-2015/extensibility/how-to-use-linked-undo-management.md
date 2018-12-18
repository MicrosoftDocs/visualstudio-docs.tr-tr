---
title: 'Nasıl yapılır: bağlantılı geri alma yönetimi | Microsoft Docs'
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
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a5da4b7c25ab97356798fe8c2db184982fc885d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739308"
---
# <a name="how-to-use-linked-undo-management"></a>Nasıl yapılır: bağlantılı geri alma Yönetimi'ni kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bağlantılı geri alma, kullanıcının aynı anda birden fazla dosya aynı düzenlemeleri geri izin verir. Örneğin, bir üstbilgi dosyası ve bir Visual C++ dosya gibi birden fazla program dosyaları arasında eş zamanlı metin değişiklikleri olan bir bağlantılı geri alma işlemi. Bağlantılı geri alma özelliği, geri alma yöneticisi, ortam uygulamasına oluşturulur ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> , bu özelliği ile düzenleme olanak tanır. Bağlantılı geri alma birlikte tek bir geri alma birimi olarak kabul edilmesi için ayrı geri alma yığınlarını bağlayabilirsiniz bir üst geri alma birimi tarafından uygulanır. Kullanarak bağlantılı geri alma yordamı aşağıdaki bölümde ayrıntılı olarak verilmiştir.  
  
### <a name="to-use-linked-undo"></a>Bağlantılı geri alma kullanmak için  
  
1.  Çağrı `QueryService` üzerinde `SVsLinkedUndoManager` işaretçisi almak için `IVsLinkedUndoTransactionManager`.  
  
2.  Çağırarak ilk ana bağlantılı geri alma birimi oluşturma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Bu, bir dizi bağlantılı geri alma yığınlar halinde gruplanması geri alma yığınlarını başlangıç noktasını ayarlar. İçinde `OpenLinkedUndo` yöntemi de gerekecek bağlantılı geri alma katı veya katı olmayan olmasını isteyip istemediğinizi belirtin. Katı olmayan bağlantılı geri alma davranışı ile bağlantılı geri alma eşdüzey belgelerin bazılarına kapatabilirsiniz ve diğer bağlı bırakın geri eşdüzey kendi yığınlarından üzerinde hala anlamına gelir. Katı bağlantılı geri alma davranışını bağlantılı geri alma eşdüzey yığın birlikte ya da hiç geri alınması gerektiğini belirtir. Sonraki bağlantılı geri alma yığınlarını çağırarak ekleme [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) yöntemi.  
  
3.  Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> geri almak için tüm bağlantılı geri alma birimi olarak yedekleyin.  
  
    > [!NOTE]
    >  Bir düzenleyicide bağlantılı geri alma Yönetimi uygulamak için geri alma yönetim ekleyin. Bağlantılı geri alma yönetimini uygulama ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: geri uygulamak Yönetim](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Nasıl Yapılır: Geri Alma Yönetimini Uygulama](../extensibility/how-to-implement-undo-management.md)

