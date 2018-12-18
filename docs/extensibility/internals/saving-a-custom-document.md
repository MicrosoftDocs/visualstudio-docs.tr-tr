---
title: Özel belge kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5425a1c35816fd85847915029e3b6f2da1ed75a6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132554"
---
# <a name="saving-a-custom-document"></a>Özel belge kaydetme
Ortam tanıtıcıları **kaydetmek**, **Kaydet**, ve **Tümünü Kaydet** komutları. Bir kullanıcı tıkladığında **kaydetmek**, **Kaydet**, **veya Tümünü Kaydet** üzerinde **dosya** menüsü veya bir Tümünü Kaydet içinde aşağıdaki kaynaklanan çözüm kapatır işlem gerçekleşir.  
  
 ![Müşteri Düzenleyicisini Kaydetme](../../extensibility/internals/media/private.gif "özel")  
Kaydet Kaydet ve Tümünü Kaydet komut için özel bir düzenleyici işleme  
  
 Bu işlem aşağıdaki adımlarda ayrıntılı olarak açıklanmıştır:  
  
1.  İçin **kaydetmek** ve **Kaydet** komutları ortamı kullanır <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> etkin belge penceresini belirlemek için hizmet ve böylece hangi öğeler kaydedilmelidir. Etkin belge penceresini bilinen sonra ortamı öğe tanımlayıcısı (ItemId) ve hiyerarşi işaretçi çalışan belge tablosu belgede bulur. Daha fazla bilgi için bkz: [çalıştıran Belge tablosu](../../extensibility/internals/running-document-table.md).  
  
     Tümünü Kaydet komut için ortam kaydetmek için tüm öğeleri listesi derlemek için çalışan belge tablosunda bilgileri kullanır.  
  
2.  Çözümü zaman alan bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> çağrısı, seçilen öğeleri kümesi içinde tekrarlanan (tarafından sunulan başka bir deyişle, birden çok seçimin <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> hizmet).  
  
3.  Seçilen her bir öğede çözüm çağırmak için hiyerarşi işaretçisi kullanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> Kaydet menü komutu etkin olup olmadığını belirlemek için yöntem. Bir veya daha fazla öğe kirli, Kaydet komutunu etkindir. Hiyerarşi Standart Düzenleyici kullanıyorsa, ardından sorgulanırken hiyerarşi temsilciler Düzenleyicisi durumuna çağırarak kirli <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> yöntemi.  
  
4.  Kirli her seçili öğeye bağlı, çözüm çağırmak için hiyerarşi işaretçisi kullanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> uygun hiyerarşileri yöntemi.  
  
     Özel bir düzenleyici söz konusu olduğunda, belge veri nesnesi ve proje arasındaki iletişimi özeldir. Bu nedenle, bu iki nesne tüm özel Kalıcılık sorunları ele alınır.  
  
    > [!NOTE]
    >  Kendi Kalıcılık uygularsanız, çağırdığınızdan emin olun <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> zamandan tasarruf yöntemi. Dosyayı kaydetmek güvenli olduğundan emin olmak için bu yöntem denetler (örneğin, dosya salt okunur değil).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)