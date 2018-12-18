---
title: 'Örnek Excel uzantısı: ExtensionPackage sınıfı | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: 64e6d838172325bb00cdd8a28ef6adb6d1a345b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286019"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Örnek Excel Uzantısı: ExtensionPackage Sınıfı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu sınıf genişletir <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> sınayan bir kodlanmış UI testi için giriş noktası sağlar ve sınıfı bir [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] çalışma.  
  
## <a name="assembly-attribute"></a>Bütünleştirilmiş kod özniteliği  
 Dosyanın derleme bir UI testi uzantısı olarak tanımlayan bir bütünleştirilmiş kod özniteliği ile başlar.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Bu öznitelik, temel sınıf adı, paket sınıfı adı ve özel uzantı paketi sınıf için tam nitelikli sınıf adınız bildirir.  
  
## <a name="simple-properties"></a>Basit Özellikler  
 Bu sınıf, kodlanmış UI test çerçevesi tarafından belirlemek ve uzantı ve derlemeyi tanımlamak için kullanılan değerleri sağlayan özelliklere sahiptir. Daha fazla bilgi için açıklamalarına bakın.  
  
## <a name="getservice-method"></a>GetService yöntemi  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> Her nesne için temel sınıfı tarafından tanımlandığı gibi teknoloji Yöneticisi, özellik sağlayıcısı ve eylem filtresi erişim kazanmak için kodlanmış UI test çerçevesi tarafından kullanılan tek giriş noktası bir yöntemdir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



