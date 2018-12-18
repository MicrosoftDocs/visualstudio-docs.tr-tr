---
title: VSIX proje şablonu | Microsoft Docs
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
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2b06582e1de7939e34f8fa49aa1cc9435010789
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733856"
---
# <a name="vsix-project-template"></a>VSIX Proje Şablonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir veya daha fazla Visual Studio uzantıları içinde VSIX projesi sarmalamak için VSIX proje şablonu kullanın ve ardından üzerinde paket yayımlama [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=123847) Web sitesi.  
  
 VSPackage'ları, derlemeleri, MEF Bileşenleri, proje şablonları, öğe şablonları, araç kutusu denetimleri ve özel uzantı türleri VSIX dağıtımı destekler.  
  
> [!NOTE]
>  VSIX projeleri kullanmak için Visual Studio SDK'yı yüklemeniz gerekir. Visual Studio SDK'sı hakkında daha fazla bilgi için bkz. [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>VSIX proje şablonunu nerede bulacağını  
 VSIX proje şablonu kullanılabilir **yeni proje** iletişim kutusu. Ya da genişletin **Visual Basic** düğümü veya **Visual C#** düğümünü seçip **genişletilebilirlik**.  
  
> [!TIP]
>  Bu .NET Framework 4.5 emin olmanız gerekir veya en üstündeki açılan yüksek belirtilen **yeni proje** iletişim kutusu.  
  
## <a name="uses-of-the-vsix-project-template"></a>VSIX proje şablonunu kullanır  
 VSIX proje şablonu, iki temel kullanım sahiptir:  
  
- Proje şablonları, öğe şablonları ve VSIX desteği olmayan diğer uzantılar dağıtmak için.  
  
- Birden fazla uzantı çıkışları bir dağıtım paketi sarmalamak için.  
  
  VSPackage veya başka tür bir VSIX desteği olan uzantıları dağıtmak için VSIX proje şablonu kullanmak zorunda değil.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Uzantı boş bir VSIX projesinde paketleme  
 Mevcut bir uzantı veya VSIX desteği, boş bir VSIX projesinde sarmalama tarafından zaten sahip olmayan bir uzantı paketleyebilirsiniz. Sarmalamak için uzantı tarafından desteklenen bir türde olmalıdır [VSIX şema](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Bir VSIX projesi kullanarak uzantı paketlemek için  
  
1.  Uzantınızı yapmak projeleri oluşturun.  
  
2.  Kullanarak bir VSIX projesi oluşturun **VSIX projesi** şablonu.  
  
     Source.extension.vsixmanifest açılır **bildirim Tasarımcısı**.  
  
3.  Üzerinde **varlıklar** sekmesini, **yeni** düğmesi.  
  
     **Yeni varlık Ekle** iletişim kutusu görüntülenir.  
  
4.  İçinde **türü** listesinde, eklemek için uzantı türü seçin.  
  
5.  Geçerli çözümde (örneğin, bir öğe şablonunun veya derlenmiş bir bütünleştirilmiş kod) yer alan bir uzantı veya içerik öğe eklemek için aşağıdaki adımları gerçekleştirin:  
  
    1.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
    2.  İçinde **proje** listesinde, uzantı adını seçin.  
  
    3.  İçinde **bu klasördeki ekleme** kutusuna, varlığı ekleyin ve ardından bir klasör adı girin **Tamam** düğmesi.  
  
6.  Bir uzantı veya geçerli çözümde bulunup bulunmadığına içerik öğesi eklemek için aşağıdaki adımları gerçekleştirin:  
  
    1.  İçinde **kaynak** liste kutusu öğesini **FileSystem'daki**.  
  
    2.  İçinde **yolu** alan, derlenmiş veya sıkıştırılmış uzantısı dosyanın tam yolunu girin veya bunları kullanmanızı **Gözat** dosyasına gözatmak için düğmeyi.  
  
    3.  İçinde **bu klasördeki ekleme** kutusuna, varlığı ekleyin ve ardından bir klasör adı girin **Tamam** düğmesi.  
  
7.  Paketiniz ek uzantıları dahil etmek istiyorsanız, bunları aynı şekilde ekleyin.  
  
8.  Çözümü oluşturun.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSIX bildirim dosyası, [Content_Types] .xml dosyasını ve tüm projeye eklenen uzantı varlıkları içeren bir .vsix dosyası oluşturur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSIX Uzantı Şeması 2.0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Visual Studio Uzantıları’nı bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)

