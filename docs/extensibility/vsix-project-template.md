---
title: VSIX proje şablonu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f897c2ae11e9b9677557684ca4755d0df66ddbdd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864796"
---
# <a name="vsix-project-template"></a>VSIX proje şablonu
Bir veya daha fazla Visual Studio uzantıları içinde VSIX projesi sarmalamak için VSIX proje şablonu kullanın ve ardından üzerinde paket yayımlama [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=123847) Web sitesi.  
  
 VSPackage'ları, derlemeleri, MEF Bileşenleri, proje şablonları, öğe şablonları, araç kutusu denetimleri ve özel uzantı türleri VSIX dağıtımı destekler.  
  
> [!NOTE]
>  VSIX projeleri kullanmak için Visual Studio SDK'yı yüklemeniz gerekir. Visual Studio SDK'sı hakkında daha fazla bilgi için bkz. [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>VSIX proje şablonunu nerede bulacağını  
 VSIX proje şablonu kullanılabilir **yeni proje** iletişim kutusu. Ya da genişletin **Visual Basic** düğümü veya **Visual C#** düğümünü seçip **genişletilebilirlik**.  
  
> [!TIP]
>  Bu .NET Framework 4.5 emin olmanız gerekir veya en üstündeki açılan liste kutusunda yüksek belirtilen **yeni proje** iletişim kutusu.  
  
## <a name="uses-of-the-vsix-project-template"></a>VSIX proje şablonunu kullanır  
 VSIX proje şablonu, iki temel kullanım sahiptir:  
  
- Proje şablonları, öğe şablonları ve VSIX desteği olmayan diğer uzantılar dağıtmak için.  
  
- Birden fazla uzantı çıkışları bir dağıtım paketi sarmalamak için.  
  
  VSPackage veya başka tür bir VSIX desteği olan uzantıları dağıtmak için VSIX proje şablonu kullanmak zorunda değil.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Uzantı boş bir VSIX projesinde paketleme  
 Mevcut bir uzantı veya VSIX desteği, boş bir VSIX projesinde sarmalama tarafından zaten sahip olmayan bir uzantı paketleyebilirsiniz. Sarmalamak için uzantı tarafından desteklenen bir türde olmalıdır [VSIX şema](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Bir VSIX projesi kullanarak uzantı paketlemek için  
  
1. Uzantınızı yapmak projeleri oluşturun.  
  
2. Kullanarak bir VSIX projesi oluşturun **VSIX projesi** şablonu.  
  
    *Source.extension.vsixmanifest* açılır **bildirim Tasarımcısı**.  
  
3. Üzerinde **varlıklar** sekmesini, **yeni** düğmesi.  
  
    **Yeni varlık Ekle** iletişim kutusu görüntülenir.  
  
4. İçinde **türü** listesinde, eklemek için uzantı türü seçin.  
  
5. Geçerli çözümde (örneğin, bir öğe şablonunun veya derlenmiş bir bütünleştirilmiş kod) yer alan bir uzantı veya içerik öğe eklemek için aşağıdaki adımları gerçekleştirin:  
  
   1.  İçinde **kaynak** listesinde **mevcut çözümde bir proje**.  
  
   2.  İçinde **proje** listesinde, uzantı adını seçin.  
  
   3.  İçinde **bu klasördeki ekleme** kutusuna, varlığı ekleyin ve ardından bir klasör adı girin **Tamam** düğmesi.  
  
6. Bir uzantı veya geçerli çözümde bulunup bulunmadığına içerik öğesi eklemek için aşağıdaki adımları gerçekleştirin:  
  
   1.  İçinde **kaynak** liste kutusu öğesini **FileSystem'daki**.  
  
   2.  İçinde **yolu** alan, derlenmiş veya sıkıştırılmış uzantısı dosyanın tam yolunu girin veya bunları kullanmanızı **Gözat** dosyasına gözatmak için düğmeyi.  
  
   3.  İçinde **bu klasördeki ekleme** kutusuna, varlığı ekleyin ve ardından bir klasör adı girin **Tamam** düğmesi.  
  
7. Paketiniz ek uzantıları dahil etmek istiyorsanız, bunları aynı şekilde ekleyin.  
  
8. Çözümü oluşturun.  
  
    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturur bir *.vsix* [Content_Types] bir VSIX bildirim dosyasını içeren dosya *.xml* dosyasını ve tüm projeye eklenen uzantı varlıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSIX Uzantı Şeması 2.0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Visual Studio uzantıları bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)