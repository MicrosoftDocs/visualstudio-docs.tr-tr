---
title: 'Nasıl yapılır: Windows için Otomasyon sağlama | Microsoft Docs'
description: Microsoft. VisualStudio. Shell. Interop yöntemlerini kullanarak Visual Studio 'da belge ve araç pencereleri için nasıl Otomasyon sağlayacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 774b32dc1554fb6d6466be7e915fbaeea8185798
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078753"
---
# <a name="how-to-provide-automation-for-windows"></a>Nasıl yapılır: Windows için Otomasyon sağlama

Belge ve araç pencereleri için Otomasyon sağlayabilirsiniz. Otomasyon nesnelerini bir pencerede kullanılabilir hale getirmek istediğinizde otomasyon sağlanması önerilir ve ortam, bir görev listesi ile çalıştığı için önceden hazır bir Otomasyon nesnesi sağlamaz.

## <a name="automation-for-tool-windows"></a>Araç pencereleri için Otomasyon

Ortam, <xref:EnvDTE.Window> Aşağıdaki yordamda açıklandığı gibi standart bir nesne döndürerek bir araç penceresi üzerinde Otomasyon sağlar:

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>Yöntemi __VSFPROPID ile ortam aracılığıyla çağırın [. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) `VSFPROPID` Nesneyi almak için parametre olarak VSFPROPID_ExtWindowObject `Window` .

2. Bir çağıran araç pencerenizin aracılığıyla VSPackage 'a özgü bir Otomasyon nesnesi istediğinde, ortam, <xref:EnvDTE.Window.Object%2A> `QueryInterface` `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> veya `IDispatch` arabirimlerini çağırır. Her ikisi de `IExtensibleObject` `IVsExtensibleObject` bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> yöntemi sağlar.

3. Ortam daha sonra `GetAutomationObject` yöntemi geçirerek `NULL` , VSPackage 'a özgü nesneyi geri geçirerek yanıtlayın.

4. `QueryInterface`Ve için arama `IExtensibleObject` `IVsExtensibleObject` başarısız olursa, ortam öğesine çağrı yapılır `QueryInterface` `IDispatch` .

## <a name="automation-for-document-windows"></a>Belge pencereleri için Otomasyon

Standart bir <xref:EnvDTE.Document> nesne, ortamda da kullanılabilir, ancak bir düzenleyici, <xref:EnvDTE.Document> arabirimini uygulayarak ve yanıt vererek nesnenin kendi uygulamasına sahip olabilir `IExtensibleObject` `GetAutomationObject` .

Ayrıca, bir düzenleyici, <xref:EnvDTE.Document.Object%2A> veya arabirimlerini uygulayarak yöntemi aracılığıyla alınan VSPackage 'a özgü bir Otomasyon nesnesi sağlayabilir `IVsExtensibleObject` `IExtensibleObject` . [VSSDK örnekleri](https://github.com/Microsoft/VSSDK-Extensibility-Samples) , RTF belgesine özgü bir Otomasyon nesnesine katkıda bulunur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
