---
title: 'Nasıl yapılır: denetimleri güvenli denetim olarak işaretle | Microsoft Docs'
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
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 04470034f1fa1531a1677b4acd6b36f0b99c8a62
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120572"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Nasıl yapılır: denetimleri güvenli denetim olarak işaretle
  Güvenlik için komut dosyası ekleme karşı korumalı Web denetimleri ve olmayan Web denetimleri SharePoint ayırır. Denetimleri, korumalı veya *güvenli denetimler*, güvenilir olmayan kullanıcılar tarafından erişilebilir. Denetimleri güvenli denetim girişleri özelliğini, bir SharePoint proje öğesi veya güvenli olarak işaretleyebilirsiniz **paket tasarımcısını** paketi derleme eklediğinizde. Daha fazla bilgi için bkz.  
  
 [Web.config dosyası ayarlarını değiştir](http://go.microsoft.com/fwlink/?LinkId=178965) ve [güvenli bir denetim olarak bir Web Bölümü derlemesi kaydetme](http://go.microsoft.com/fwlink/?LinkId=171013).  
  
> [!IMPORTANT]  
>  Bu yordamlar yalnızca tanım amaçlıdır. İşareti yalnızca güvenli eminseniz güvenli denetler.  
  
## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Güvenli denetimler güvenli denetim girişleri özelliğinde işaretleme  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Denetimleri güvenli veya güvenli denetim girişleri özelliğinde Güvensiz olarak işaretlemek için
  
1.  Bir SharePoint çözüm ile Visual Web Bölümü projesi oluşturun.  
  
2.  Web Bölümü için iki denetimleri ekleme: metin kutusu ve bir düğme. Adları varsayılan değerlerinde, TextBox1 ve Button1, sırasıyla bırakın.  
  
3.  Web bölümünün için iki giriş eklemek **güvenli denetim girişleri** özelliği. Bunu yapmak için üç nokta seçin (![ASP.NET Mobil Tasarımcı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı elips")) düğmesine **güvenli denetim girişleri** özelliği **Özellikler** penceresi.  
  
     **Güvenli denetim girişleri** iletişim kutusu görüntülenir.  
  
4.  İçinde **güvenli denetim girişleri** iletişim kutusunda, seçin **Ekle** iki kez iki güvenli denetim girdisi eklemek için düğmeyi **üyeleri** bölmesi: düğme, diğeri metin kutusu için.  
  
5.  İlk güvenli denetim girdisi seçin ve ardından değerini değiştirmek kendi **güvenli** özelliğine **False**, kendi **türü adı** özelliğine **Button1**ve kendi **karşı güvenli betik** özelliğine **False**.  
  
     Bu adım düğme denetimi güvenli olmayan bir denetimi tanımlar.  
  
6.  İkinci güvenli denetim girdisi listeden seçin. Değerini bırakın, **güvenli** özelliği olarak **True** ve kendi **tür adı** özelliğine **TextBox1** ve kendi **güvenli Komut dosyası karşı** özelliğine **doğru**.  
  
     Metin kutusu denetimi şimdi komut dosyası ekleme karşı güvenli bir denetim olarak işaretlenir.  
  
7.  Seçin **Tamam** düğmesi iletişim kutusunu kapatın.  
  
## <a name="marking-safe-controls-in-the-package-designer"></a>Güvenli denetimler paket Tasarımcısı'nda işaretleme  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Güvenli veya paket Tasarımcısı'nda Güvensiz olarak işaretlemek için denetler
  
1.  Bir SharePoint çözüm ile Visual Web Bölümü projesi oluşturun.  
  
2.  Web Bölümü için iki denetimleri ekleme: metin kutusu ve bir düğme. Adları varsayılan değerlerinde, TextBox1 ve Button1, sırasıyla bırakın.  
  
     Daha sonra kullanıldığından denetimi ad alanı not edin.  
  
3.  Menü çubuğunda seçin **yapı** > **yapı çözümü** Projeyi derlemek için.  
  
4.  Başka bir SharePoint çözüm oluşturun.  
  
5.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın *Package.Package* dosya ve ardından **açmak** açmak için **paket tasarımcısını**.  
  
6.  İçinde **paket tasarımcısını**, seçin **Gelişmiş** sekmesi.  
  
7.  Altında **ek derlemeler**, seçin **Ekle** düğmesine tıklayın ve ardından **varolan derleme Ekle** listeden.  
  
8.  İçinde **varolan derleme Ekle** iletişim kutusunda, üç nokta seçin (![ASP.NET Mobil Tasarımcı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı elips")) düğmesine  **Kaynak yolu**.  
  
9. 1. adımda oluşturduğunuz SharePoint çözümden derleme seçin ve ardından **açık** düğmesi.  
  
10. Bu örnekte, bırakın **dağıtım hedef** seçeneği GlobalAssemblyCache olarak.  
  
     Bu adım sisteme Genel Derleme Önbelleği (GAC) dağıtmak derleme neden olur. Web uygulaması (depo) klasörüne dağıtmak için derleme istiyorsanız, bunun yerine bu seçeneği belirleyin. Daha fazla bilgi için bkz: [Web Bölümleri SharePoint Foundation dağıtma](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. İçinde **güvenli denetimler** kutusunda, seçin **yeni öğe eklemek için burayı tıklatın** düğmesi.  
  
12. Değerleri olan özellikler için aşağıdaki tablodan girin.  
  
    |Özellik adı|Değer|  
    |-------------------|-----------|  
    |Ad Alanı|Denetim için tam ad alanı gibi **BdcModelProject1.VisualWebPart1**.|  
    |Tür adı|Button1|  
    |Derleme adı|Güçlü bir derleme adı, örneğin: Microsoft.Office.SharePoint.ClientExtensions, sürüm 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c =.|  
    |Güvenli|Clear **güvenli** onay kutusu.|  
    |Komut dosyası karşı güvenli|Bırakın **karşı güvenli betik** onay kutusunun işaretini kaldırın.|  
  
    > [!NOTE]  
    >  **Derleme adı** aracılığıyla eklenen derlemeler için değer **Gelişmiş** sekmesinde **paket tasarımcısını** olamaz bir belirteç, onu kesin olarak adlandırılmamış derleme olmalıdır. Daha fazla bilgi için bkz: [bkz](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Seçin **sekmesini** başka bir güvenli denetim girdisi oluşturmak için anahtar.  
  
14. Seçin **yeni öğe eklemek için burayı tıklatın** yeniden düğmesine tıklayın.  
  
15. Değerleri olan özellikler için aşağıdaki tablodan girin.  
  
    |Özellik adı|Değer|  
    |-------------------|-----------|  
    |Ad Alanı|Denetim için tam ad alanı gibi **BdcModelProject1.VisualWebPart1**.|  
    |Tür adı|TextBox1|  
    |Derleme adı|Güçlü bir derleme adı, örneğin: Microsoft.Office.SharePoint.ClientExtensions, sürüm 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c =.|  
    |Güvenli|Seçin **güvenli** onay kutusu.|  
    |Komut dosyası karşı güvenli|Seçin **karşı güvenli betik** onay kutusu.|  
  
16. Seçin **sekmesini** anahtar ve ardından **Tamam** düğmesi iletişim kutusunu kapatın.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Proje öğelerinde paketleme ve dağıtım bilgileri sağlayın](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Paket ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
