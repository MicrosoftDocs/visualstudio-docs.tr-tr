---
title: WPF araç kutusu denetimi oluşturma | Microsoft Docs
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
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ad3edfa84ee64425a7a9fbc6b0dfc5098396907
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786034"
---
# <a name="creating-a-wpf-toolbox-control"></a>WPF Araç Kutusu Denetimi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

(Windows Presentation Framework) WPF araç kutusu denetimi şablon otomatik olarak eklenen WPF denetimleri oluşturmanıza olanak tanır. **araç kutusu** uzantısı yüklü olduğunda. Bu konuda şablonu oluşturmak için nasıl kullanılacağını gösterir. bir **araç kutusu** denetimi, diğer kullanıcılara dağıtabilirsiniz.  
  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>WPF Araç Kutusu Denetimi Oluşturma  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>WPF araç kutusu denetimi ile bir uzantı oluşturma  
  
1.  Adlı bir VSIX projesi oluşturun `MyToolboxControl`. VSIX proje şablonunda bulabilirsiniz **yeni proje** iletişim altında **Visual C# / genişletilebilirlik**.  
  
2.  Projeyi açtığında, ekleme bir **WPF araç kutusu denetimi** adlı öğe şablonu `MyToolboxControl`. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. İçinde **Yeni Öğe Ekle** iletişim kutusunda, Git **Visual C# / genişletilebilirlik** seçip **WPF araç kutusu denetimi**. İçinde **adı** alan penceresinin en altında komut dosyası adı için değiştirme `MyToolboxControl.cs`.  
  
     Çözüm, artık bir kullanıcı denetimini içeren bir `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> denetimine ekler **araç kutusu**ve **Microsoft.VisualStudio.ToolboxControl** varlık girişi için VSIX bildirimi  Dağıtım.  
  
#### <a name="to-create-the-control-ui"></a>UI denetimi oluşturmak için  
  
1.  MyToolboxControl.xaml Tasarımcısı'nda açın.  
  
     Tasarımcı gösterir bir <xref:System.Windows.Controls.Grid> içeren denetimi bir <xref:System.Windows.Controls.Button> denetimi.  
  
2.  Kılavuz düzeni düzenleyin. Seçtiğinizde, <xref:System.Windows.Controls.Grid> denetimi üst ve sol kenarlarının kılavuzunun üzerinde mavi denetim çubukları görünür. Çubukları tıklayarak kılavuza satırlar ve sütunlar ekleyebilirsiniz.  
  
3.  Alt denetimler kılavuza ekleyin. Buradan sürükleyerek bir alt denetimin konumlandırabilirsiniz **araç kutusu** kılavuzunun veya ayarlayarak bir bölüme, `Grid.Row` ve `Grid.Column` XAML öznitelikleri. Aşağıdaki örnek iki etiket üst satırdaki kılavuz ve ikinci satırdaki bir düğme ekler.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Denetimi yeniden adlandırma  
 Varsayılan olarak, denetiminizin içinde görünür **araç kutusu** olarak **MyToolboxControl** adlı bir grup içindeki **MyToolboxControl.MyToolboxControl**. MyToolboxControl.xaml.cs dosyasında bu adları değiştirebilirsiniz.  
  
1.  MyToolboxControl.xaml.cs kod Görünümü'nde açın.  
  
2.  MyToolboxControl sınıfı bulun ve TestControl için yeniden adlandırın. (Bunu yapmanın en hızlı yolu, sınıfı yeniden adlandırmak için olan seçip **Yeniden Adlandır** bağlam menüsünden ve adımları tamamlayın. (Hakkında daha fazla bilgi için **Yeniden Adlandır** komutu, bkz: [düzenlemeyi yeniden adlandırma (C#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3.  Git `ProvideToolboxControl` ilk parametre olarak değiştirin ve öznitelik **Test**. Denetimi içeren grubun adıdır **araç kutusu**.  
  
     Sonuçta elde edilen kod gibi görünmelidir:  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>Yapı, test ve dağıtım  
 Projede hata ayıklaması yaparken, yüklü denetim bulmalısınız **araç kutusu** Visual Studio'nun Deneysel örneğinin.  
  
#### <a name="to-build-and-test-the-control"></a>Yapı ve denetim test etmek için  
  
1.  Projeyi yeniden derleyin ve hata ayıklamaya başlayın.  
  
2.  Yeni Visual Studio örneğinde, bir WPF uygulaması projesi oluşturun. XAML Tasarımcısı'nı açık olduğundan emin olun.  
  
3.  Denetiminizi Bul **araç kutusu** ve tasarım yüzeyine sürükleyin.  
  
4.  WPF uygulama hatalarını ayıklamaya başlayın.  
  
5.  Denetiminiz göründüğünü doğrulayın.  
  
#### <a name="to-deploy-the-control"></a>Denetim dağıtmak için  
  
1.  Test edilen projenin derledikten sonra projeyi \bin\debug\ klasöründe .vsix dosyasını bulabilirsiniz.  
  
2.  Bu yerel bir bilgisayarda .vsix dosyasını çift tıklayın ve aşağıdaki yükleme yordamı yükleyebilirsiniz. Denetim kaldırmak için Git **araçları / Uzantılar ve güncelleştirmeler** ve kontrol uzantısı için bakın, sonra da tıklayın **kaldırma**.  
  
3.  .Vsix dosyasını bir ağa veya bir Web sitesine yükleyin.  
  
     Dosyayı karşıya yükleme durumunda [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=123847) Web sitesinin diğer kullanıcıların kullanabileceği **araçları / Uzantılar ve güncelleştirmeler** denetimi çevrimiçi bulmak ve yüklemek için Visual Studio'da.

