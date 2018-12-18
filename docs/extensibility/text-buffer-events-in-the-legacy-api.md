---
title: Metin arabelleği olayları eski API | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f147171d8af075029a4a763a84fd48c5209f8fe1
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080614"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Metin arabelleği olayları eski API
Metin arabelleği nesne farklı durumlar için yanıt olanak tanıyan birkaç farklı olaylar gönderir.  
  
 Eski API'si kullanılırken, metin arabelleğini değişiklikleri bildirim almak için aşağıdaki arabirimlerinden uygulamalıdır. Metin arabelleği kullanılarak arabirimleri kullanıma `IConnectionPointContainer` satır bildirim almak için metin arabelleği arabirimde arabellekteki değiştirir. Daha fazla bilgi için [nasıl yapılır: metin arabelleği olayları eski API'si ile kaydolma](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). Durumunda, `IVsTextStreamEvents` veya `IVsTextLinesEvents` arabirimleri, değişiklikleri geri gönderilir ya da bir veya two dimensional koordinatlarında, sırasıyla.  
  
## <a name="text-buffer-interfaces"></a>Metin arabelleği arabirimleri  
 Metin arabelleği nesne tarafından uygulanan arabirimler aşağıda verilmiştir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Bileşik eylemleri (diğer bir deyişle, bir tek geri al/Yinele biriminde gruplandırılır eylemleri) oluşturulmasını sağlar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Metin arabelleği tarafından yönetilen belge veri kalıcılığını etkinleştirir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Temel hizmetleri sağlar. birden çok istemci tarafından kullanılır.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Sağlar okuma ve yazma iki boyutlu koordinatlarını kullanarak özellikleri. Devralınan `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Hızlı, arabellekteki metni akışa dayalı olarak sıralı erişim sağlar.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Sağlar okuma ve yazma özellikleri kullanarak tek boyutlu koordinatları. Devralınan `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Genel Özellikler koleksiyonu erişim sağlar. En önemli özellik adını veya bilinen ad, arabellek olur. Bir GUID oluşturma ve bir anahtar olarak kullanarak rastgele verilerinizi bu arabirimle arabellek depolayabilirsiniz.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Bağlantı noktaları için olayları destekler.|  
  
## <a name="text-buffer-event-interfaces"></a>Metin arabelleği olay arabirimleri  
 Metin arabelleği olay bildirimi için arabirimleri aşağıda verilmiştir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Yeni bir dil hizmeti bir metin arabelleği ile ilişkili olduğunda istemciler bildirir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|İstemciler, bir metin arabelleği başlatıldığında ve metin arabelleğini verilerde değişiklik yapıldığında size bildirir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Tek boyutlu koordinatlarını temel alınan metin arabellekteki değişiklikler istemcileri bildirir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|İstemcileri iki boyutlu koordinatlarını temel alınan metin arabellekteki değişiklikler bildirir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Kullanıcı verilerini değişiklikleri istemcileri bildirir.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Son Yürütme hareket olayı tetiklemek için istemcileri size bildirir ve metin değiştirildi yelpazesi sunar. `IVsPreliminaryTextChangeCommitEvents` Arabirimi değil geri alınacak veya yinelenecek komutları yanıt olarak harekete geçirilir. Olayları yalnızca bir geri alma yöneticisi olan arabelleklerini kov. `IVsPreliminaryTextChangeCommitEvents` düzgün listeleme gibi diğer olayları önce değişiklikleri uygulanmadan önce diğer olaylarla metni değiştirmeyin emin olmak için tetiklenir. VSPackage'ı ya da izlemelidir `IVsPreliminaryTextChangeCommitEvents` arabirimi veya `IVsFinalTextChangeCommitEvents` arabirimi, ancak ikisine birden değil.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Son Yürütme hareket olayı tetiklemek için istemcileri size bildirir ve metin değiştirildi yelpazesi sunar. `IVsFinalTextChangeCommitEvents` Arabirimi değil geri alınacak veya yinelenecek komutları yanıt olarak harekete geçirilir. Olayları yalnızca bir geri alma yöneticisi olan arabelleklerini kov. `IVsFinalTextChangeCommitEvents` Yalnızca dil Hizmetleri ya da düzenleme üzerinde tam denetime sahip diğer nesneler tarafından kullanıma yöneliktir. VSPackage'ı ya da izlemelidir `IVsPreliminaryTextChangeCommitEvents` arabirimi veya `IVsFinalTextChangeCommitEvents` arabirimi, ancak ikisine birden değil.|  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Eski API'yi kullanarak metin arabelleğini erişim](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) [nasıl yapılır: metin arabelleği olayları eski API'si ile kaydolma](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)