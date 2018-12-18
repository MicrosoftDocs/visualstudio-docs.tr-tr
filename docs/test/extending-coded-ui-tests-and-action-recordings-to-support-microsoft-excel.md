---
title: Kodlanmış UI testlerini ve Eylem kayıtlarını genişletme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: cbf4d89fc0a32501a2ea275c5168969dd2a0fd19
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894124"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Kodlanmış UI testleri ve eylem kayıtları genişletin

Kodlanmış UI testleri ve eylem kayıtları için test çerçevesi, her olası kullanıcı arabirimi desteklemiyor. Test etmek istediğiniz belirli bir kullanıcı Arabirimi desteklemiyor olabilir. Örneğin, hemen bir kodlanmış UI testi ya da eylem için bir Microsoft Excel hesap çizelgesi kaydı oluşturulamıyor. Ancak, kodlanmış UI testi framework'ün genişletilebilirlik avantajlarından yararlanarak belirli kullanıcı Arabirimi destekler kodlanmış UI test Framework kendi uzantınızı oluşturabilirsiniz.

![UI Test mimarisi](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Microsoft Excel test etmek için örnek uzantısı

Bu [blog gönderisi](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/3-introducing-sample-excel-extension/) bir bağlantısını içeren bir [örnek uzantısı](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) kodlanmış UI testi çerçevesi için. Ayrıca tüm görüntüleyebilirsiniz [blog gönderisi serisi için kodlanmış UI test genişletilebilirlik](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/series-on-coded-ui-test-extensibility/).

> [!NOTE]
> Örnek Microsoft Excel 2010 ile kullanıma yöneliktir. Excel diğer sürümleri ile çalışmıyor veya olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri için en iyi uygulamalar](../test/best-practices-for-coded-ui-tests.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)