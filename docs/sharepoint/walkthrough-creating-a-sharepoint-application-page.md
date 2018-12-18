---
title: 'İzlenecek yol: SharePoint uygulama sayfası oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 52ff6b3431ac3f87c85eefcf728cfe4c4875f884
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42634793"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>İzlenecek yol: SharePoint uygulama sayfası oluşturma
 
Uygulama sayfası, bir ASP.NET sayfasının özelleştirilmiş bir biçimidir. Uygulama sayfaları, bir SharePoint ana sayfası ile birleştirilmiş içerik bulunuyor. Daha fazla bilgi için [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md).

Bu izlenecek yol, bir uygulama sayfası oluşturmak ve ardından yerel bir SharePoint sitesi kullanarak hata ayıklama işlemini göstermektedir. Bu sayfa, her kullanıcı oluşturduğunuz veya sunucu grubundaki tüm sitelerde değiştirdiğiniz tüm öğeleri gösterir.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- SharePoint projesi oluşturma.
- Bir uygulama sayfasını SharePoint projesine ekleme.
- ASP.NET denetimlerini uygulama sayfasına ekleme.
- ASP.NET denetimlerinin arkasına kod ekleme.
- Uygulama sayfasını test etme.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar

- Windows ve SharePoint sürümleri desteklenir.

## <a name="create-a-sharepoint-project"></a>Bir SharePoint projesi oluşturma

İlk olarak, oluşturun bir **boş SharePoint projesi**. Daha sonra ekleyeceksiniz bir **uygulama sayfası** bu projeye öğe.

1. Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Açık **yeni proje** iletişim kutusunda **Office/SharePoint** kullanın ve ardından istediğiniz dili düğümünde **SharePoint çözümleri** düğümü.

3. İçinde **Visual Studio yüklenmiş şablonlar** bölmesinde seçin **SharePoint 2010 - boş proje** şablonu. Projeyi adlandırın **MySharePointProject**ve ardından **Tamam** düğmesi.

     **SharePoint Özelleştirme Sihirbazı** görünür. Bu sihirbaz, proje ve çözüm güven düzeyini hata ayıklamak için kullanacağınız siteyi seçmenizi sağlar.

4. Seçin **Grup çözümü olarak Dağıt** seçenek düğmesini ve ardından **son** varsayılan yerel SharePoint sitesini kabul etmek için düğmeyi.

## <a name="create-an-application-page"></a>Uygulama sayfası oluşturma

Uygulama sayfası oluşturmak için bir **uygulama sayfası** projeye öğe.

1. İçinde **Çözüm Gezgini**, seçin **MySharePointProject** proje.

2. Menü çubuğunda, **proje** > **Yeni Öğe Ekle**.

3. İçinde **Yeni Öğe Ekle** iletişim kutusunda **uygulama sayfası (yalnızca Grup çözümü** şablonu.

4. Sayfayı adlandırın **Searchıtems**ve ardından **Ekle** düğmesi.

     Visual Web Developer tasarımcısını uygulama sayfasında görüntüler **kaynak** sayfanın HTML öğelerini görebileceğiniz görünümü. Tasarımcı biçimlendirmeyi çeşitli için görüntüler <xref:System.Web.UI.WebControls.Content> kontrol eder. Her denetim eşleyen bir <xref:System.Web.UI.WebControls.ContentPlaceHolder> varsayılan uygulama ana sayfasında tanımlanan denetimi.

## <a name="design-the-layout-of-the-application-page"></a>Uygulama sayfasının düzenini tasarlama

Uygulama sayfası öğesi, uygulama sayfasına ASP.NET denetimleri eklemek için bir tasarımcı kullanmanıza olanak sağlar. Bu tasarımcı, Visual Web Developer ile kullanılanın ' dir. Bir etiket, radyo düğmesi listesi ve tablo ekleme **kaynak** tasarımcısına görüntülemek ve standart bir ASP.NET sayfası tasarlarken yaptığınız gibi özellikleri ayarlayın.

1. Menü çubuğunda, **görünümü** > **araç kutusu**.

2. Standart düğümünde **araç kutusu**, aşağıdaki adımlardan birini gerçekleştirin:

    - Kısayol menüsünü açın **etiket** öğesi öğesini **kopyalama**, altındaki kısayol menüsünü açın **PlaceHolderMain** içerik denetimi Tasarımcısı'nda ve ardından seçin **Yapıştır**.

    - Sürükleme **etiket** öğesini **araç kutusu** gövdesine **PlaceHolderMain** içerik denetimi.

3. Eklemek için önceki adımı yineleyin bir **DropDownList** öğesi ve bir **tablo** öğesinin **PlaceHolderMain** içerik denetimi.

4. Tasarımcıda değiştirin `Text` özniteliği etiket denetiminin **tüm öğeleri göster**.

5. Tasarımcıda değiştirin `<asp:DropDownList>` şu XML ile öğesi.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Sayfadaki denetimlerin olaylarını işlemek

Bir uygulama sayfasındaki denetimleri herhangi bir ASP.NET sayfasında olduğu gibi işleyin. Bu yordamda, işleyecek `SelectedIndexChanged` aşağı açılan listesinin olay.

1. Üzerinde **görünümü** menüsünde seçin **kod**.

     Uygulama sayfası kod dosyası Kod Düzenleyicisi'nde açılır.

2. Aşağıdaki yöntemi ekleyin `SearchItems` sınıfı. Bu kodu işleme <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> olayı <xref:System.Web.UI.WebControls.DropDownList> bu anlatımın ilerleyen kısımlarında oluşturacağınız bir yöntemi çağırarak.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Uygulama sayfası kod dosyasının en üstüne aşağıdaki deyimleri ekleyin.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Aşağıdaki yöntemi ekleyin `SearchItems` sınıfı. Bu yöntem sunucu grubundaki tüm siteler arasında dolaşır ve oluşturulmuş veya geçerli kullanıcı tarafından değiştirilmiş öğeleri arar.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Aşağıdaki yöntemi ekleyin `SearchItems` sınıfı. Bu yöntem, tablodaki geçerli kullanıcı tarafından oluşturulmuş veya değiştirilmiş öğeleri görüntüler.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>Uygulama sayfasını sınama

Projeyi çalıştırdığınızda SharePoint sitesi açılır ve uygulama sayfası görüntülenir.

1. İçinde **Çözüm Gezgini**, uygulama sayfasının kısayol menüsünü açın ve ardından **başlangıç öğesi olarak ayarla**.

2. Seçin **F5** anahtarı.

     SharePoint sitesi açılır.

3. Uygulama sayfasında, **Benim tarafımdan değiştirilen** seçeneği.

     Uygulama sayfası yenilenir ve sunucu grubundaki tüm sitelerde değiştirdiğiniz tüm öğeleri görüntüler.

4. Uygulama sayfasında, **Benim tarafımdan oluşturulan** listesinde.

     Uygulama sayfası yenilenir ve sunucu grubundaki tüm sitelerde oluşturduğunuz tüm öğeleri görüntüler.

## <a name="next-steps"></a>Sonraki adımlar

SharePoint uygulama sayfaları hakkında daha fazla bilgi için bkz: [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md).

Visual Web Designer uygulamasını aşağıdaki konulardan kullanarak SharePoint sayfası içeriği tasarlama hakkında daha fazla bilgi:

- [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Ayrıca bkz.

[Nasıl yapılır: uygulama sayfası oluşturma](../sharepoint/how-to-create-an-application-page.md)  
[Application _layouts sayfa türü](http://go.microsoft.com/fwlink/?LinkID=169274)
