---
title: Birlikte çalışma bütünleştirilmiş kodları kullanarak komut durumunu belirleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9b678e5a7ab87df69ec5f3f41f65a191ecf35911
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822573"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Birlikte çalışma bütünleştirilmiş kodları kullanarak komut durumunu belirleme
VSPackage işleyebileceği komutları durumunu izlemek gerekir. Ortam içinde VSPackage işlenen komut ne zaman etkin veya devre dışı hale belirlenemiyor. Ortam komut durumları hakkında bilgilendirmek için VSPackage sorumluluğu olduğu, örneğin, genel durumu gibi komutlar **Kes**, **kopyalama**, ve **Yapıştır**.  
  
## <a name="status-notification-sources"></a>Durum bildirim kaynakları  
 Ortam VSPackage komutları hakkında bilgi alır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage'nın uygulamanın parçası olan yöntemini, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi. Ortam çağrıları <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> iki koşul altında bir VSPackage yöntemi:  
  
- Bir kullanıcı bir ana menü veya bir bağlam menüsü (sağ tıklayarak) oturum açtığında, ortam yürütür <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> tüm bunların durumunu belirlemek için menü komutlarını yöntemi.  
  
- VSPackage'ı ortamı geçerli kullanıcı arabirimi (UI) güncelleştirme isteğinde bulunduğunda. Bu güncelleştirme gibi kullanıcıya görünen komutlar gerçekleşir **Kes**, **kopyalama**, ve **Yapıştır** standart araç çubuğundaki gruplandırma, hale etkin ve devre dışı bağlam ve kullanıcı eylemlerini yanıt olarak.  
  
  Birden çok VSPackages Kabuk barındıran olduğundan, komut durumunu belirlemek için her VSPackage'ı yoklamak için gerekli kabuğun performansı edilemeyecek kadar düşebilir. Bunun yerine, kullanıcı arabirimini değişiklik zamanında değiştiğinde, VSPackage'ı etkin bir şekilde ortam bildirmesi gerekir. Güncelleştirme bildirimi hakkında daha fazla bilgi için bkz. [kullanıcı arabirimini güncelleştirmek](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Durum bildirim hatası  
 Bir komut durum değişikliği ortamının bildirmek için VSPackage hata UI tutarsız bir durumda yerleştirebilirsiniz. Herhangi bir menü veya bağlam menü komutlarınızı bir araç çubuğu üzerinde kullanıcı tarafından yerleştirilebilir olduğunu unutmayın. Bu nedenle, yalnızca bir menü veya bağlam menüsü açıldığında Başlamayabileceğini bildirir.UI yeterli değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Uygulama](../../extensibility/internals/command-implementation.md)