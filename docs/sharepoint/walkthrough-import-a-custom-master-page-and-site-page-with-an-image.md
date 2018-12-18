---
title: 'İzlenecek yol: özel bir ana sayfa ve Site içeri aktarma bir görüntüyle | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 45f1ded9cf6eca3715c5050f93aa24630a1bc4e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890999"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>İzlenecek yol: özel ana sayfasını ve görüntü ile site sayfasını içeri aktarma
  Bu izlenecek yol, bir SharePoint özel ana sayfasını ve görüntüye sahip bir site sayfasını içeri aktarma gösterir bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint Proje.  

 Bu izlenecek yol aşağıdaki görevlerin nasıl gerçekleştirileceğini gösterir:  

- Özel bir ana sayfa ve site sayfasını SharePoint Tasarımcısı'nda bir görüntü kullanarak oluşturun.  

- Özel ana sayfasını, resmi ve site sayfası için bir SharePoint çözümünü dışarı aktar (*.wsp*) dosyası.  

- İçeri aktarın ve dağıtın *.wsp* dosyasını bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanarak SharePoint çözüm paketini İçeri Aktar projenin SharePoint Proje.  

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  

## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere sahip olmanız gerekir:  

-   Desteklenen sürümleri [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] ve SharePoint.  

-   Visual Studio.  

-   SharePoint Designer 2010'u.  

## <a name="create-items-in-sharepoint-designer"></a>SharePoint Tasarımcısı'nda öğeleri oluşturma
 Bu örnekte, üç öğeye dışarı aktarma için SharePoint Tasarımcısı'nda oluşturma işlemi gösterilmektedir: özel bir ana sayfa, özel ana sayfa ve site sayfasında görünecek bir resim dosyası başvuran bir site sayfası. Görüntü, SharePoint /images/ klasörüne eklenir.  

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>SharePoint Tasarımcısı'nda özel bir ana sayfa oluşturma

1.  SharePoint Tasarımcı'da gezinti bölmesinde seçin **ana sayfalar** site nesnesi.  

2.  Üzerinde **ana sayfalar** şeridinden **boş ana sayfa**.  

3.  Yeni ana sayfa seçin ve ardından **ana sayfalar** şeridinden **dosya Düzenle**.  

4.  SharePoint Designer'ın alt kısmında seçin **kod** sekmesi.  

5.  Mevcut biçimlendirme, aşağıdaki biçimlendirme ile değiştirin.  

    ```aspx-csharp  
    <%@ Master Language="C#" %>  
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <html dir="ltr">  
    <head runat="server">  
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">  
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>  
    <title>Web Page</title>  
    </head>  
    <body>  
    <form id="form1" runat="server">  
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"   
            runat="server">  
          </asp:ContentPlaceHolder>  
    </form>  
    </body>  
    </html>  
    ```  

6.  Sayfayı kaydedin öğesini **ana sayfalar** sekmesini ve ana sayfa olarak yeniden adlandır **mybasic1.master**.  

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>SharePoint designer'daki içerik veritabanına resim ekleme
 Artık site sayfasında gösterilmek üzere görüntü ekleyebilirsiniz. Görüntü SharePoint içerik veritabanını dağıtılır.  

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>SharePoint designer'daki içerik veritabanını bir görüntü eklemek için

1.  Gezinti bölmesinde **tüm dosyaları** site nesnesi ve ardından, ağaç görünümünde **görüntüleri** klasör.  

2.  Üzerinde **tüm dosyaları** şeridinden **dosyalarını içeri aktarın**, seçtiğiniz bir dosya seçin ve ardından **Tamam** düğmesi. Bu örnekte, dosyanın nasıl adlandırıldığı **myimg1.png**.  

     İsteğe bağlı olarak, görüntüleri düzenlenmesine yardımcı olmak için bir alt klasör oluşturabilirsiniz.  

3.  Kapat **alma** iletişim kutusu.  

## <a name="create-a-site-page"></a>Bir site sayfası oluşturma
 Bu temel site sayfası özel ana sayfasını kullanır ve önceki adımda eklediğiniz görüntüyü görüntüler.  

#### <a name="to-create-a-site-page"></a>Bir site sayfası oluşturmak için  

1.  Gezinti bölmesinde **Site sayfaları** nesne.  

2.  Üzerinde **sayfaları** şeridinden **sayfa** düğmesini öğesini **ASPX** sayfa türü ve yeni dosya adı **mycontentpage1.aspx**.  

     İsteğe bağlı olarak, site sayfaları düzenlenmesine yardımcı olmak için bir alt klasör oluşturabilirsiniz.  

3.  Site sayfaları listesinde **MyContentPage1.aspx** , Özellikler sayfasını açın ve ardından sayfanın alt kısmında **dosya Düzenle** bağlantı.  

     Bir ileti görüntülenir ve bu sayfa güvenli modda düzenlenebilir bir bölge içermediğini bildiren ve Gelişmiş kipte, bu sayfayı açın, isteyip istemediğinizi soran **Evet** düğmesi.  

4.  Sayfanın en altında seçin **kod** düğmesi.  

5.  Mevcut biçimlendirme, aşağıdaki biçimlendirme ile değiştirin.  

    ```aspx-csharp  
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>  
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>  
    <%@ Import Namespace="Microsoft.SharePoint" %>  
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>  

    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">  
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />  
    </asp:Content>  
    ```  

6.  Güncelleştirilmiş site sayfası kaydedin.  

## <a name="export-the-items-from-sharepoint"></a>SharePoint'ten öğeleri dışarı aktarma
 Öğeler için bir SharePoint çözümünü SharePoint'ten dışarı aktar (*.wsp*) dosyası.  

#### <a name="to-export-items-from-sharepoint-designer"></a>SharePoint Designer'daki öğeleri dışarı aktarmak için

1.  SharePoint Tasarımcı'da gezinti bölmesinde seçin **ekip sitesi** nesnesi ve ardından **Site** şeridinden **şablon olarak Kaydet**.  

2.  İçinde **şablon olarak Kaydet** iletişim kutusunda, bir dosya adı ve select şablon adı girin **dahil içerik** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  

     Bu sitede içeriğini kaydeder *.wsp* dosya.  

3.  Çözümü dışarı aktarır sonra seçin **çözüm Galerisi** kullanılabilir çözüm dosyaları listesini görüntülemek için bağlantı.  

4.  Yeni kısayol menüsünü açın *.wsp* dosya ve ardından **Hedefi Farklı Kaydet** sistemine kaydetmek için.  

## <a name="import-the-items-into-visual-studio"></a>Öğeleri Visual Studio'ya içeri aktarma
 İçeri aktarma *.wsp* doyasını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. İçerik alındıktan sonra özelleştirebilir, daha fazla öğe ekleyin ve dağıttıktan sonra.  

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Öğeleri Visual Studio'ya .wsp dosyasından içeri aktarmak için  

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], oluşturun bir **SharePoint 2010 çözüm paketini içeri aktar** proje.  

2. Üzerinde **içeri aktarılacak öğeleri seçin** sayfasındaki **Modülü** içinde **türü** sütun, aşağıdaki tabloda içeri aktarma için yalnızca dosyalar için onay kutularını seçin.  


   | Dosya Adı | Açıklama |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | Özel ana sayfa. |
   | images_ | SharePoint dosya sisteminde resim dosyası. |
   | SitePages_ | Site sayfası. |


3. Seçin **son** seçilen öğeleri içe aktarmak için düğme.  

4. İçinde **Çözüm Gezgini**, seçin \_catalogsmasterpage\_ düğümünü ve değerini kendi **dağıtım çakışması çözümü** özelliğini **otomatik** .  

    Bu dağıtım çakışmaları otomatik olarak çözümlendiğinden emin olun yardımcı olur.  

5. Yeni ana sayfanıza var olan bir sayfa ile aynı ada sahipse, var olan sayfanın varsayılan bir ana sayfa veya SharePoint designer'daki özel ana sayfa olarak işaretlenmemiş emin olun.  

    Mevcut bir ana sayfa varsayılan ana sayfa veya özel bir ana sayfa olarak işaretlenmişse, ana sayfa silinemiyor belirten bir dağıtım hata alırsınız. Bu sorunu önlemek için şunu yapın:  

   -   Geçici olarak mevcut ana sayfaya varsayılan ana sayfa ayarlanırsa, başka bir ana sayfa varsayılan ana sayfa ayarlayın. SharePoint için dosyaları dağıttıktan sonra yeni ana sayfanıza varsayılan ana sayfa ayarlayın.  

   -   Geçici olarak mevcut ana sayfaya özel bir ana sayfa olarak ayarlanırsa, başka bir ana sayfa özel bir ana sayfa olarak ayarlayın. SharePoint için dosyaları dağıttıktan sonra yeni ana sayfanıza özel bir ana sayfa olarak ayarlayın.  

6. Menü çubuğunda, **derleme** > **çözüm dağıtma**.  

7. Dağıtılan öğeleri görüntülemek için SharePoint sitesini açın.  

   Dosyaların içeri aktarmak için alternatif bir yolu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve bu bilgisayarlara dağıtın SharePoint olan modüllere dosyaları eklemek için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Nasıl yapılır: bir ana sayfa veya temayı içeri aktarma](../sharepoint/how-to-import-a-master-page-or-theme.md) ve [çözüme dosyaları dahil etmek için modül kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md).  

## <a name="see-also"></a>Ayrıca bkz.
 [Mevcut bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)   
 [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturma](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  

