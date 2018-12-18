---
title: Uzantıları Windows Installer dağıtımı için hazırlama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cc742fecbbe03ff3d3aa0fb3f8d61a9c5f09254b
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495277"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Uzantıları Windows Installer dağıtımı için hazırlama
Bir Windows Installer paketi (MSI), bir VSIX paketi dağıtmak için kullanamazsınız. Ancak, bir VSIX paketi MSI dağıtım içeriğini ayıklayabilirsiniz. Bu belge, bir kurulum projesi eklenmek üzere bir VSIX paketi varsayılan çıktısı bir projesini Hazırlama işlemi gösterilmektedir.  
  
## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Uzantı projesini Windows Installer dağıtımı için hazırlama  
 Bu adımları bir kurulum projesi için eklemeden önce yeni uzantı projelerde gerçekleştirin.  
  
### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Uzantı projesini Windows Installer dağıtımı için hazırlama  
  
1.  VSPackage, MEF Bileşeni, düzenleyici kenarlığı veya bir VSIX bildirimi içeren başka bir genişletilebilirlik projesi türü oluşturun.  
  
2.  VSIX bildirimi Kod Düzenleyicisi'nde açın.  
  
3.  Ayarlama `InstalledByMsi` öğesi için VSIX bildiriminin `true`. VSIX bildirimi hakkında daha fazla bilgi için bkz: [VSIX Uzantı Şeması 2.0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Bu VSIX yükleyicisi bileşeni yüklemek üzere çalışmadan engeller.  
  
4.  Projeye sağ **Çözüm Gezgini** tıklatıp **özellikleri**.  
  
5.  Seçin **VSIX** sekmesi.  
  
6.  Başlıklı kutuyu işaretleyin **kopyalama VSIX içeriğini aşağıdaki konuma** ve Kurulum projesi dosyaları burada çeker yolunu yazın.  
  
## <a name="extract-files-from-an-existing-vsix-package"></a>Var olan bir VSIX paketinden dosyaları ayıklayın  
 Kaynak dosyalar olmadığında bir kurulum projesi için mevcut bir VSIX paketinin içeriği eklemek için aşağıdaki adımları gerçekleştirin.  
  
### <a name="to-extract-files-from-an-existing-vsix-package"></a>Varolan bir VSIX paketi dosyalarını ayıklamak için  
  
1.  Yeniden adlandırma *. VSIX* dosya uzantısını içeren *filename.vsix* için *filename.zip*.  
  
2.  İçeriğini kopyalayın *.zip* bir dizine dosya.  
  
3.  Silme *[Content_types] .xml* dosyası.  
  
4.  VSIX bildirimi, önceki yordamda gösterildiği gibi düzenleyin.  
  
5.  Kalan dosyaları kurulum projenize ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio Installer dağıtımı](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [İzlenecek yol: özel bir eylem oluşturur.](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))