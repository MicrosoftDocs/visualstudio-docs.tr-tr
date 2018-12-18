---
title: 'Nasıl yapılır: kümesi hata ayıklama ve yayın yapılandırmaları | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba827fda69b1dc455df4efe9c9f6eb83687780f3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758492"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Nasıl Yapılır: Hata Ayıklama ve Dağıtım Yapılandırmalarını Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio projeleri ayrı sürümü ve hata ayıklama yapılandırması, programınız için. Adların da ifade ettiği şekilde, hata ayıklama sürümünün hata ayıklama ve yayın sürümünü son sürüm dağıtımı oluşturun.  
  
 Programınızın hata ayıklama yapılandırması tam sembolik hata ayıklama bilgileri ve en iyileştirme olmadan derlenir. Kaynak kodu ve oluşturulan yönergeler arasındaki ilişki daha karmaşık olacağından en iyileştirme hata ayıklama, karmaşık hale getirir.  
  
 Programınızın sürüm yapılandırması hiçbir sembolik hata ayıklama bilgisi içermez ve tamamen en iyileştirilmiştir. Hata ayıklama bilgileri oluşturulabilir PDB dosyalarında kullanılan derleyici seçeneklerine bağlı olarak. PDB dosyaları oluşturmak, daha sonra yayım sürümünüzde hata ayıklama gerekirse çok kullanışlı olabilir.  
  
 Derleme yapılandırmaları hakkında daha fazla bilgi için bkz. [derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md).  
  
 Derleme yapılandırmasını değiştirebilirsiniz **derleme** menüsünde, araç çubuğundan veya projenin özellik sayfalarındaki. Dile özgü proje özellik sayfaları. Aşağıdaki yordam, menü ve araç, yapı yapılandırmasını değiştirme işlemi gösterilmektedir. Farklı dillerde projelerde derleme yapılandırmasını değiştirme hakkında daha fazla bilgi için İlgili Konular'a bölümüne bakın.  
  
### <a name="to-change-the-build-configuration"></a>Yapı yapılandırmasını değiştirmek için  
  
1.  Yapı menüsünde: tıklayın **derleme / Configuration Manager**, ardından **hata ayıklama** veya **yayın**.  
  
2.  Ya da araç çubuğunda **hata ayıklama** veya **yayın** gelen **çözüm yapılandırmaları** liste kutusu.  
  
     ![araç derleme Yapılandırması](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Bu araç, Express sürümlerinde kullanılamaz. Kullanabileceğiniz **Çözümü Derle F6** ve **hata ayıklamayı Başlat F5** menü öğelerinin yapılandırmayı seçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Hata ayıklama yapılandırması proje ayarları C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Hata ayıklama yapılandırması proje ayarları bir Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)   
 [Hata ayıklama ve yayın proje yapılandırmaları](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)



