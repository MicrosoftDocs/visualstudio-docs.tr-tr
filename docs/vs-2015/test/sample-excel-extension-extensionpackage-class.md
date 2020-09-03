---
title: 'Örnek Excel uzantısı: ExtensionPackage Sınıfı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1c1f4c746fa505b50bab9caa7a516a2abc77f69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672204"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Örnek Excel Uzantısı: ExtensionPackage Sınıfı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu sınıf, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> sınıfını genişletir ve bir çalışma sayfasını test eden KODLANMıŞ UI testi için giriş noktası sağlar [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .

## <a name="assembly-attribute"></a>Derleme özniteliği
 Dosya, derlemeyi bir UI test uzantısı olarak tanımlayan bir derleme özniteliğiyle başlar.

```
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
    "ExcelExtensionPackage",
    typeof(
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]
```

 Bu öznitelik, taban sınıf adını, paket sınıfının adını ve özel uzantı paketi sınıfı için tam sınıf adını bildirir.

## <a name="simple-properties"></a>Basit özellikler
 Bu sınıfta, uzantısı ve derlemeyi tanımlamak ve tanımlamak için kodlanmış UI test çerçevesi tarafından kullanılan değerler sağlayan özellikler vardır. Daha fazla bilgi için bkz. kod açıklamaları.

## <a name="getservice-method"></a>GetService yöntemi
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A>Yöntemi, KODLANMıŞ UI test çerçevesi tarafından, her nesne için temel sınıf tarafından tanımlanan şekilde teknoloji yöneticisine, özellik sağlayıcısına ve eylem filtresine erişim kazanmak için kullanılan tek giriş noktasıdır.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
