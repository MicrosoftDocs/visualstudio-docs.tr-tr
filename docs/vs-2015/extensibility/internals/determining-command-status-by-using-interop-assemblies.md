---
title: Birlikte çalışma bütünleştirilmiş kodları kullanarak komut durumunu belirleme | Microsoft Docs
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
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1983f66158c00e5812823bbbf36eeea3aa139ea8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789310"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Birlikte Çalışma Bütünleştirilmiş Kodları Kullanarak Komut Durumunu Belirleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage işleyebileceği komutları durumunu izlemek gerekir. Ortam içinde VSPackage işlenen komut ne zaman etkin veya devre dışı hale belirlenemiyor. Ortam komut durumları hakkında bilgilendirmek için VSPackage sorumluluğu olduğu, örneğin, genel durumu gibi komutlar **Kes**, **kopyalama**, ve **Yapıştır**.  
  
## <a name="status-notification-sources"></a>Durum bildirim kaynakları  
 Ortam VSPackage komutları hakkında bilgi alır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage'nın uygulamanın parçası olan yöntemini, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi. Ortam çağrıları <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> iki koşul altında bir VSPackage yöntemi:  
  
- Bir kullanıcı bir ana menü veya bir bağlam menüsü (sağ tıklayarak) oturum açtığında, ortam yürütür <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> tüm bunların durumunu belirlemek için menü komutlarını yöntemi.  
  
- VSPackage'ı ortamı geçerli kullanıcı arabirimi (UI) güncelleştirme isteğinde bulunduğunda. Bu gibi kullanıcıya görünen komutlar meydana **Kes**, **kopyalama**, ve **Yapıştır** standart araç çubuğundaki gruplandırma, hale etkin ve devre dışı yanıt içeriği ve kullanıcı eylemleri için.  
  
  Birden çok VSPackages Kabuk barındıran olduğundan, komut durumunu belirlemek için her VSPackage'ı yoklamak için gerekli kabuğun performansı edilemeyecek kadar düşebilir. Bunun yerine, kullanıcı arabirimini değişiklik zamanında değiştiğinde, VSPackage'ı etkin bir şekilde ortam bildirmesi gerekir. Güncelleştirme bildirimi hakkında daha fazla bilgi için bkz. [kullanıcı arabirimini güncelleştirme](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Durum bildirim hatası  
 Bir komut durum değişikliği ortamının bildirmek için VSPackage hata UI tutarsız bir durumda yerleştirebilirsiniz. Herhangi bir menü veya bağlam menü komutlarınızı bir araç çubuğu üzerinde kullanıcı tarafından yerleştirilebilir olduğunu unutmayın. Bu nedenle, yalnızca bir menü veya bağlam menüsü açıldığında Başlamayabileceğini bildirir.UI yeterli değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Uygulama](../../extensibility/internals/command-implementation.md)

