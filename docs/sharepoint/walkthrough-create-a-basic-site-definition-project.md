---
title: 'İzlenecek yol: temel bir Site tanımı projesi oluşturma | Microsoft Docs'
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8a9a879db7c1d24dbfd8312dbc75d9b0bbaa8803
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844427"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>İzlenecek yol: temel bir site tanımı projesi oluşturma
  Bu izlenecek yol, üzerinde bazı denetimler içeren bir görsel Web bölümü içeren bir temel site tanımını nasıl oluşturulacağını gösterir. Açıklık için oluşturduğunuz görsel Web Bölümü, yalnızca birkaç denetimlerine sahiptir. Ancak, daha fazla işlevsellik içeren daha karmaşık SharePoint site tanımları oluşturabilirsiniz.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Kullanarak bir site tanımı oluşturma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proje şablonu.  
  
- SharePoint'te bir site tanımı kullanarak bir SharePoint sitesi oluşturuluyor.  
  
- Bir görsel Web Bölümü çözüme ekleniyor.  
  
- Yeni görsel Web bölümü ekleyerek sitenin default.aspx sayfasında özelleştirme.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Microsoft Windows ve SharePoint sürümleri desteklenir. SharePoint çözümleri geliştirmek için gereksinimler daha fazla bilgi için bkz.  
  
-   Visual Studio.  
  
## <a name="create-a-site-definition-solution"></a>Site tanımı çözümü oluşturma
 İlk olarak, bir site tanımı projesi oluşturma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-site-definition-project"></a>Bir site tanımı projesi oluşturmak için  
  
1. Menü çubuğunda, **dosya** > **yeni** > **proje**. IDE'nizi menü çubuğundaki Visual Basic geliştirme ayarlarını kullanmaya ayarlanmışsa seçin **dosya** > **yeni proje**.  
  
    **Yeni proje** iletişim kutusu görüntülenir.  
  
2. Genişletin **Visual C#**  düğümü veya **Visual Basic** düğümünü genişletin **SharePoint** düğümünü seçip **2010** düğümü.  
  
3. İçinde **şablonları** listesinde **SharePoint 2010 projesi** şablonu.  
  
4. İçinde **adı** kutusuna **TestSiteDef**ve ardından **Tamam** düğmesi.  
  
    **SharePoint Özelleştirme Sihirbazı** görünür.  
  
5. Üzerinde **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, site tanımı hata ayıklamak istediğiniz SharePoint sitesinin URL'sini girin veya varsayılan konumu kullanın (http://<em>sistem adı</em>/).  
  
6. İçinde **bu SharePoint çözümünün güven düzeyi nedir?** bölümünde, seçin **Grup çözümü olarak Dağıt** seçenek düğmesini.  
  
    Tüm site tanımı projeleri Grup çözümlerini dağıtılması gerekir. Grup çözümlerini karşı korumalı çözümler hakkında daha fazla bilgi için bkz. [korumalı çözümle ilgili konular](../sharepoint/sandboxed-solution-considerations.md).  
  
7. Seçin **son** düğmesi.  
  
    Proje görünür **Çözüm Gezgini**.  
  
8. İçinde **Çözüm Gezgini**, proje düğümünü seçin ve ardından, menü çubuğunda, **proje** > **Yeni Öğe Ekle**.  
  
9. Ya da altında **Visual C#** veya **Visual Basic**, genişletme **SharePoint** düğümünü seçip **2010** düğümü.  
  
10. İçinde **şablonları** bölmesinde seçin **Site tanımı** şablon bırakın **adı** olarak **SiteDefinition1**, seçin **Ekleme** düğmesi.  
  
## <a name="create-a-visual-web-part"></a>Visual web bölümü oluşturma
 Ardından, site tanımının ana sayfasında görünecek bir görsel Web bölümü oluşturun.  
  
#### <a name="to-create-a-visual-web-part"></a>Bir görsel web bölümü oluşturmak için
  
1.  İçinde **Çözüm Gezgini**, seçin **tüm dosyaları göster** düğmesi.  
  
2.  Seçin **SiteDefinition1** proje düğümünü ve ardından, menü çubuğunda, **proje** > **Yeni Öğe Ekle**.  
  
     **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
3.  Genişletin **Visual C#**  düğümü veya **Visual Basic** düğümünü genişletin **SharePoint** düğümünü seçip **2010** düğümü.  
  
4.  Şablonlar listesinde seçin **görsel Web Bölümü** şablon, varsayılan VisualWebPart1 adlandırın ve ardından canlı **Ekle** düğmesi.  
  
     *VisualWebPart1.ascx* dosyasını açar.  
  
5.  Sayfanın alt kısmında *VisualWebPart1.ascx*, üç denetim forma eklemek için aşağıdaki işaretlemeyi ekleyin: bir metin kutusu, bir düğme ve bir etiketi:  
  
    ```aspx-csharp  
    <table>  
      <tr>  
        <td>  
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>  
        </td>  
        <td>  
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>  
        </td>  
        <td>  
          <asp:Label runat="server" ID="lblName"></asp:Label>  
        </td>  
      </tr>  
    </table>  
    ```  
  
6.  Altında *VisualWebPart1.ascx*açın *VisualWebPart1.ascx.cs* dosyası (için [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) veya *VisualWebPart1.ascx.vb* (için [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) ve ardından ekleyin Aşağıdaki kodu:  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     Bu kod web bölümünün düğmesi tıklamasından için işlevsellik ekler.  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Varsayılan ASPX sayfasına visual web bölümü ekleme
 Ardından, site tanımının varsayılan ASPX sayfasına visual Web bölümü ekleyin.  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Varsayılan ASPX sayfasına bir görsel web bölümü eklemek için
  
1.  Default.aspx sayfasını açın ve ardından altındaki şu satırı ekleyin `WebPartPages` etiketi:  
  
    ```aspx-csharp  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Bu satırı adı MyWebPartControls Web Bölümü ve kodu ile ilişkilendirir. *Namespace* parametre olarak kullanılan ad alanı eşleşiyor *VisualWebPart1.ascx* kod dosyası.  
  
2.  Sonra `</asp:Content>` öğesi tamamını değiştirin `ContentPlaceHolderId="PlaceHolderMain"` bölümü ve içeriğini aşağıdaki kodla:  
  
    ```aspx-csharp  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Bu kod, daha önce oluşturduğunuz bir görsel Web Bölümü bir başvuru oluşturur.  
  
3.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın **SiteDefinition1** düğümünü seçip **başlangıç öğesi olarak ayarla**.  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>Dağıtma ve site tanım çözümü çalıştırma
 Ardından, projeyi SharePoint için dağıtın ve ardından projeyi çalıştırın.  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>Site tanımını dağıtmak ve çalıştırmak için  
  
-   Menü çubuğunda, **derleme** > **dağıtma TestSiteDef**.  
  
-   Seçin **F5** anahtarı.  
  
     Visual Studio kodu derler özelliklerini ekler, tüm dosyaları bir SharePoint çözüm (WSP) dosyası paketler ve WSP dosyasını SharePoint sunucusuna dağıtır. SharePoint ardından dosyalarını yükler ve ardından özellikleri etkinleştirir.  
  
## <a name="create-a-site-based-on-the-site-definition"></a>Site tanımını temel alan bir site oluşturma
 Ardından, yeni site tanımını kullanarak bir site oluşturun.  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>Site tanımını kullanarak bir site oluşturmak için  
  
1.  SharePoint sitesinde yeni SharePoint sitesi sayfası görüntülenir.  
  
2.  İçinde **başlık ve açıklama** bölümünde, girin **Yeni Sitem** başlığı ve bir sitenin açıklaması.  
  
3.  İçinde **Web sitesi adresi** bölümünde, girin **YeniSitem** içinde **URL adı** kutusu.  
  
4.  İçinde **şablon** bölümünde, seçin **SharePoint özelleştirmeleri** sekmesi.  
  
5.  İçinde **bir şablon seçin** listesinde **SiteDefinition1**.  
  
6.  Diğer ayarları varsayılan değerlerinde bırakın ve ardından **Oluştur** düğmesi.  
  
     Yeni site görünür.  
  
## <a name="test-the-new-site"></a>Yeni siteyi Sına
 Ardından, yeni sitenin doğru şekilde çalışıp çalışmadığını doğrulamak için test edin.  
  
#### <a name="to-test-the-new-site"></a>Yeni siteyi sınamak için  
  
-   Varsayılan ASPX sayfasına üzerinde bazı metinler girin ve ardından **değişiklik etiket metni** metin kutusunun yanındaki düğmeyi.  
  
     İşlecin sağ tarafındaki düğmenin etiket metni görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: olay alıcısı oluşturma](../sharepoint/how-to-create-an-event-receiver.md)   
 [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)  
  
