---
title: Ayarları kategorisi oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66667b97ef10d6b07bef3e8c1c3b19842a07482e
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388675"
---
# <a name="create-a-settings-category"></a>Ayarları kategorisi oluşturma

Bu kılavuzda Visual Studio ayarları kategorisi oluşturma ve değerleri kaydedin ve değerleri ayarları dosyasından geri yüklemek için kullanın. Ayarları kategorisi olan bir grup görünür bir "özel ayarları noktası olarak"; ilgili özellikleri diğer bir deyişle, bir onay kutusuna olarak **içeri ve dışarı aktarma ayarları** Sihirbazı. (Üzerinde bulabilirsiniz **Araçları** menü.) Ayarlar kaydedildi veya kategori olarak geri ve ayarlardan sihirbazında görüntülenmez. Daha fazla bilgi için [ortam ayarları](../ide/environment-settings.md).

Ondan türetilen ayarları kategorisi oluşturma <xref:Microsoft.VisualStudio.Shell.DialogPage> sınıfı.

Bu izlenecek yolda başlatmak için önce ilk bölümünü tamamlamalısınız [bir seçenekler sayfası oluşturma](../extensibility/creating-an-options-page.md). Sonuç Seçenekleri Özellik Kılavuzu inceleyin ve kategorideki özelliklerini değiştirmek olanak sağlar. Özellik kategorisi ayarları dosyasında kaydettikten sonra özellik değerlerinin nasıl depolandığını görmek için dosyaya inceleyin.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Ayarları kategorisi oluşturma
 Bu bölümde, kaydetme ve geri yükleme ayarları kategorisi değerleri için özel ayarlar noktası kullanın.

### <a name="to-create-a-settings-category"></a>Ayarları kategorisi oluşturma

1.  Tamamlamak [bir seçenekler sayfası oluşturma](../extensibility/creating-an-options-page.md).

2.  Açık *VSPackage.resx* dosya ve bu üç dize kaynakları ekleyin:

    |Ad|Değer|
    |----------|-----------|
    |106|My kategorisi|
    |107|Ayarlarım|
    |108|OptionInteger ve OptionFloat|

     Adı "My Category" kategorisi, nesne "ayarlarım" ve "OptionInteger ve OptionFloat" Kategori açıklaması bu kaynakları oluşturur.

    > [!NOTE]
    >  Bu üç, yalnızca kategori adı görünmez **içeri ve dışarı aktarma ayarları** Sihirbazı.

3.  İçinde *MyToolsOptionsPackage.cs*, ekleme bir `float` adlı özellik `OptionFloat` için `OptionPageGrid` , aşağıdaki örnekte gösterildiği gibi sınıf.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    >  `OptionPageGrid` Artık "My Category" adlı kategoriden oluşuyorsa iki özelliklerini `OptionInteger` ve `OptionFloat`.

4.  Ekleme bir <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> için `MyToolsOptionsPackage` sınıfı ve "My Category" CategoryName adı verin, "My ayarları" ObjectName verin ve isToolsOptionPage true olarak ayarlayın. CategoryResourceID objectNameResourceID ve DescriptionResourceID kimlikleri daha önce oluşturduğunuz karşılık gelen dize kaynağını ayarlayın.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5.  Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneğinde, görmelisiniz **kılavuz sayfam** artık hem tamsayı ve kayan nokta değerlerine sahip.

## <a name="examine-the-settings-file"></a>Ayarlar dosyasını inceleyin.
 Bu bölümde, özellik kategorisi değerlerini bir ayarları dosyasına aktarın. Dosyasını inceleyin ve sonra özellik kategorisine değerleri alın.

1.  Basarak projenin hata ayıklama modunda başlatın **F5**. Bu deneysel örneği başlatır.

2.  Açık **Araçları** > **seçenekleri** iletişim.

3.  Sol bölmede ağaç görünümünde genişletin **My kategori** ve ardından **kılavuz sayfam**.

4.  Değiştirin **OptionFloat** 3.1416 için ve **OptionInteger** 12. **Tamam**'ı tıklatın.

5.  Üzerinde **Araçları** menüsünde tıklatın **içeri ve dışarı aktarma ayarları**.

     **İçeri ve dışarı aktarma ayarları** Sihirbazı görünür.

6.  Emin **seçili ortam ayarlarını dışarı aktar** seçilir ve ardından **sonraki**.

     **Dışarı aktarma ayarlarını seçin** sayfası görüntülenir.

7.  Tıklayın **ayarlarımı**.

     **Açıklama** değişikliklerini **OptionInteger ve OptionFloat**.

8.  Emin olun **ayarlarım** seçilir ve ardından yalnızca kategori **sonraki**.

     **Ayarları dosyanızın adını** sayfası görüntülenir.

9. Yeni ayarlar dosyanıza ad *MySettings.vssettings* ve uygun bir dizinde kaydedin. **Son**'a tıklayın.

     **Verme tamamlandı** Raporları Sayfası ayarlarınız başarıyla dışarı aktarıldı.

10. Üzerinde **dosya** menüsünde **açık**ve ardından **dosya**. Bulun *MySettings.vssettings* ve açın.

     (, GUID'leri farklılık gösterir) dosyasının aşağıdaki bölümünde dışarı aktardığınız özellik kategorisine bulabilirsiniz.

    ```
    <Category name="My Category_My Settings"
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"
          RegisteredName="My Category_My Settings">
          PackageName="MyToolsOptionsPackage">
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>
       <PropertyValue name="OptionInteger">12</PropertyValue>
    </Category>
    ```

     Tam bir kategori adı alt çizgi ve nesne adından kategori adı için ek olarak biçimlendirilmiş dikkat edin. Dışarı aktarılan değerlerine birlikte kategorisinde OptionFloat ve OptionInteger görünür.

11. Ayarlar dosyası, değişiklik yapmadan kapatın.

12. Üzerinde **Araçları** menüsünde tıklayın **seçenekleri**, genişletin **My kategori**, tıklayın **kılavuz sayfam** ve ardından değiştirin  **OptionFloat** 1.0 için ve **OptionInteger** 1. **Tamam**'ı tıklatın.

13. Üzerinde **Araçları** menüsünde tıklatın **içeri ve dışarı aktarma ayarları**seçin **seçili ortam ayarlarını içeri aktarma**ve ardından **sonraki**.

     **Geçerli ayarları Kaydet** sayfası görüntülenir.

14. Seçin **Hayır, sadece yeni ayarları almak** ve ardından **sonraki**.

     **, Koleksiyonu ayarları içeri aktarmak için** sayfası görüntülenir.

15. Seçin *MySettings.vssettings* dosyası **ayarlarım** ağaç görünümünün düğümü. Ağaç görünümünde dosya görünmüyorsa, tıklayın **Gözat** ve bulmak. **İleri**'ye tıklayın.

     **İçeri aktarma ayarlarını seçin** iletişim kutusu görüntülenir.

16. Emin olun **ayarlarım** seçilir ve ardından **son**. Zaman **içeri aktarma tamamlandı** sayfası görüntülendikten sonra **Kapat**.

17. Üzerinde **Araçları** menüsünde tıklatın **seçenekleri**, genişletin **My kategori**, tıklayın **kılavuz sayfam** ve özellik kategorisi değerlerine sahip olduğunuzu doğrulayın geri.