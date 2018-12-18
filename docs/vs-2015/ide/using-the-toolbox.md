---
title: Araç kutusunu kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.chooseitems
- vs.toolboxpages.activexcontrols
- VS.CHOOSEITEMS.windowsuixamlcomponents
- VS.chooseitems.silverlightcomponents
- VC.EDITORS.RIBBON
- vs.customizetoolbox
- VS.chooseitems.System.Workflow_Components
- vs.chooseitems.frameworkcomponents
- VS.ToolboxPages..NET_Framework_Components
- VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage
- vs.chooseitems.comcomponents
- vs.toolboxpages.NGWS_components
helpviewer_keywords:
- toolbox, adding items
- Visual Studio, toolbox
- toolbox, tabs
- toolbox
ms.assetid: 82e7cb43-4d0b-4e17-b7b0-43f96c22c3c2
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 28f142a011f86afe70bfe83fd2cec274548c7b50
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173153"
---
# <a name="using-the-toolbox"></a>Araç Kutusunu Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Araç kutusu denetimleri ve diğer öğeleri projenize eklemek için kullanabilirsiniz. Kullanmakta olduğunuz ve yeniden boyutlandırma ve yerleştirmenize Tasarımcı yüzeyine başka denetimler sürükleyip bırakabilirsiniz.  
  
 Araç, Tasarımcı görünümü bir XAML dosyasının gibi tasarımcı görünümleri ile birlikte görüntülenir. Araç, kullanılabilir denetimleri geçerli tasarımcıda görüntüler.  
  
 Projenizi denetimleri araç kutusunda görünür kümesini de etkiler hedefleyen .NET Framework sürümü. Varsayılan olarak, [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] projeleri .NET Framework 4.5.1'i hedefleyen. Projenizi'nde proje düğümüne seçerek farklı bir .NET Framework sürümünü hedefleyecek şekilde ayarlayabileceğiniz **Çözüm Gezgini**, öğesine göz atarak **özellikleri/uygulama/hedef Framework'ü**.  
  
## <a name="managing-the-toolbox-and-its-controls"></a>Araç ve denetimlerini yönetme  
 Varsayılan olarak araç Visual Studio IDE'nin sol tarafında daraltılmış ve imleci üzerine taşındığında görünür. Araç kutusu sabitleyebilirsiniz (tıklayarak **PIN** araç çubuğunda simge) açık kalması taşıdığınızda imleç. Ayrıca, araç penceresi çıkar ve ekran üzerinde herhangi bir yere sürükleyin. Yerleştirme, çıkar ve araç sağ tıklayarak ve seçeneklerden birini seçerek araç gizle.  
  
 Araç kutusu sekmeyi öğeleri yeniden düzenlemek veya bağlam menüsünde aşağıdaki komutları kullanarak özel sekme ve öğeleri ekleyin:  
  
-   **Öğeyi yeniden adlandır** -seçili öğeyi yeniden adlandırır.  
  
-   **Tümünü Göster** -tüm olası denetimleri (geçerli Tasarımcı için geçerli olanları değil) gösterir.  
  
-   **Liste görünümü** -denetimleri dikey listesini gösterir. Denetimleri yatay olarak işaretlenmemişse, görünür.  
  
-   **Seç öğeleri** -açılır **araç kutusu öğelerini Seç** iletişim kutusunda görünen öğeler belirtebilirsiniz böylece **araç kutusu**. Göstermek veya seçerek ya da onay kutusunu temizleyerek bir öğeyi gizler.  
  
-   **Öğeleri alfabetik olarak Sırala** -öğeleri ada göre sıralar.  
  
-   **Araç çubuğunu sıfırlama** - varsayılan araç kutusunu ayarlarını geri yükler ve öğeleri.  
  
-   **Sekme Ekle** -yeni bir araç kutusu sekmesi ekler.  
  
-   **Yukarı Taşı** -seçili öğeyi yukarı taşır.  
  
-   **Aşağı Taşı** -seçili öğeyi aşağı taşır.  
  
## <a name="creating-and-distributing-custom-toolbox-controls"></a>Oluşturma ve özel araç kutusu denetimleri dağıtma  
 Visual Basic veya Visual C# içinde bir özel araç kutusu denetimi oluşturun ve temel alan bir proje şablonu ile başlayabilirsiniz [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) veya [Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md). Denetiminiz için kodunuza dağıtmak veya kullanarak Web'de Yayımlama [araç kutusu denetimleri yükleyici](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).



