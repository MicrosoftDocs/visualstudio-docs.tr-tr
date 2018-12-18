---
title: 'Nasıl yapılır: Windows Forms kullanan bir araç kutusu denetimi oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Toolbox control
- winforms
- toolbox
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
manager: douge
ms.openlocfilehash: 2860f3fca32b3a87967a404fb47626416d9f5dce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263724"
---
# <a name="how-to-create-a-toolbox-control-that-uses-windows-forms"></a>Nasıl yapılır: Windows Forms kullanan bir araç kutusu denetimi oluşturma
Windows Forms araç kutusu denetimi şablonun yer aldığı [!INCLUDE[vssdk_dev11_long](../includes/vssdk-dev11-long-md.md)] otomatik olarak eklenen Windows Forms denetimleri oluşturmanıza olanak tanır **araç kutusu** uzantısı yüklü olduğunda. Bu konuda şablonu oluşturmak için nasıl kullanılacağını gösterir. bir **araç kutusu** diğer kullanıcılara dağıtabilirsiniz denetimi...  
  
> [!NOTE]
>  Visual Studio SDK'nin nasıl öğrenmek için bkz: [Visual Studio genişletilebilirlik Geliştirici Merkezi](http://go.microsoft.com/fwlink/?linkid=121964) MSDN Web sitesinde.  
  
## <a name="creating-a-toolbox-control"></a>Araç kutusu denetimi oluşturma  
 Projeyi oluşturmak için Windows Forms araç kutusu denetim şablonu kullanın ve ardından bir kullanıcı arabirimi (UI) Tasarımcısı'nda oluşturun.  
  
#### <a name="to-create-a-windows-forms-toolbox-control-project"></a>Bir Windows Forms araç kutusu denetimi projesi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde tıklatın **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunun **yüklü şablonlar**, tercih ettiğiniz programlama dilini düğümüne tıklayın ve ardından **genişletilebilirlik**. Proje türleri listesinde seçin **Windows Forms araç kutusu denetimi**.  
  
3.  İçinde **adı** proje için kullanmak istediğiniz adı yazın. **Tamam**'ı tıklatın.  
  
     Visual Studio denetim yerleştirmek için bir öznitelik bir kullanıcı denetimi içeren bir çözüm oluşturur **araç kutusu**, bir VSIX dağıtımı için bildirim.  
  
#### <a name="to-build-the-control-ui"></a>UI denetimi oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, ToolboxControl.cs tasarımcıda açmak için çift tıklayın.  
  
2.  Gelen **araç kutusu**, istediğiniz tüm denetimleri tasarım yüzeyine sürükleyin ve bunları tasarımınıza uygun düzenleyin.  
  
3.  İçinde **özellikleri** penceresinde genel özelliklerini ayarlama kullanıcı denetimi ve alt denetimler.  
  
## <a name="coding-the-control"></a>Denetim kodlama  
 Varsayılan olarak, denetiminizin içinde görünür **araç kutusu** olarak **ToolboxControl1** içinde bir **araç kutusu** çözümünüzü aynı ada sahip öğe grubu. ToolboxControl.cs dosyasında bu adları değiştirebilirsiniz.  
  
#### <a name="to-code-the-control"></a>Code denetimi için  
  
1.  İçinde **Çözüm Gezgini**ToolboxControl.cs sağ tıklayın ve ardından **kodu görüntüle** kod Görünümü'nde dosyayı açmak için.  
  
2.  Denetim uygulayan kısmi bir sınıf tanımı sınıf adına sağ tıklayın, **yeniden düzenleme**ve ardından **Yeniden Adlandır**. Sınıfın adı, görüntülenmesini istediğiniz adla değiştirin **araç kutusu** denetimi yüklü olduğunda.  
  
3.  Hemen üzerinde sınıf tanımının içinde `ProvideToolboxControl` özniteliği bildirimi, ilk parametresinin değeri denetiminde barındıracak öğesi grubunun adını değiştirin **araç kutusu**.  
  
     Aşağıdaki örnekte gösterildiği `ProvideToolboxControl` özniteliği ve adlı bir denetim için ayarlanmış bir sınıf tanımının `Counter` içinde `General` öğesi grubu.  
  
     [!code-csharp[ToolboxControlWinForms#07](../snippets/csharp/VS_Snippets_VSSDK/toolboxcontrolwinforms/cs/toolboxcontrol.cs#07)]  
  
4.  Özellikleri, yöntemleri ve olayları denetimi uygulayın.  
  
## <a name="building-testing-and-deployment"></a>Yapı, test ve dağıtım  
 F5 tuşuna basarak bir .vsix dağıtım dosyası içerir ve denetimin yüklü olan Visual Studio ikinci bir örneğini açar Proje yapıları **araç kutusu**.  
  
#### <a name="to-build-and-test-the-control"></a>Yapı ve denetim test etmek için  
  
1.  F5 tuşuna basın.  
  
2.  Yeni Visual Studio örneğinde, bir Windows Forms uygulaması projesi oluşturun.  
  
3.  Denetiminizi Bul **araç kutusu** ve tasarım yüzeyine sürükleyin.  
  
4.  İçinde **özellikleri** penceresinde özelliklerinizi beklendiği gibi göründüğünü doğrulayın.  
  
5.  Herhangi bir kod veya yöntemleri ve olayları test etmek için gerekli ek denetimler ekleyin.  
  
6.  Windows Forms uygulaması'nı açmak için F5 tuşuna basın.  
  
7.  Özellikleri, yöntemleri ve olayları denetiminizin beklendiği gibi davrandığından emin olun.  
  
#### <a name="to-deploy-the-control"></a>Denetim dağıtmak için  
  
1.  Test edilen projenin derledikten sonra projenin \bin\debug\ klasörü dosya Gezgini'nde açın ve .vsix dosyasını bulun.  
  
2.  .Vsix dosyasını bir ağa veya bir Web sitesine yükleyin.  
  
     Dosyayı karşıya yükleme durumunda [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=123847) Web sitesinin diğer kullanıcıların kullanabileceği **Uzantı Yöneticisi** denetimi bulmak ve yüklemek için Visual Studio'da.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Araç Kutusu Denetimi Oluşturma](../extensibility/creating-a-wpf-toolbox-control.md)