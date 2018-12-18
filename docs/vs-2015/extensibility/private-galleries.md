---
title: Özel galeriler | Microsoft Docs
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
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 910764df2f6a6e3069136bce64b77f267e473b9d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749952"
---
# <a name="private-galleries"></a>Özel Galeriler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Denetimleri, şablonlar ve bunlara yayınlayarak geliştirme araçları paylaşabilirsiniz bir *özel galeri* gösterildiği gibi kuruluşunuz için intranet üzerindeki:  
  
-   Bir Atom (uygun şekilde yapılandırılmış merkezi bir konuma (depo) intranet ağınızdaki RSS akışı) oluşturun. Daha fazla bilgi için [nasıl yapılır: özel bir galeri için bir Atom akışı oluşturma](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Özel Galeri açıklayan .pkgdef dosyası dağıtın. Özel bir galeri aynı anda birçok bilgisayara bağlanmak isteyen yöneticiler için bu yapılandırmayı öneririz.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Uzantılar ve güncelleştirmeler Visual Studio'da özel bir galeri ekleme  
 Özel bir galeri kullanılabilir olduğunda, kendisine ekleyebilirsiniz **Uzantılar ve güncelleştirmeler** Visual Studio'da.  
  
 ![Uzantı Yöneticisi ekleme iletişim kutusu](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Uzantılar ve güncelleştirmeler için özel bir galeri ekleme  
  
1.  Menü çubuğunda, **Araçları**, **seçenekleri**.  
  
2.  İçinde **ortam** düğümünü **Uzantılar ve güncelleştirmeler**.  
  
3.  Seçin **Ekle** düğmesi.  
  
4.  İçinde **adı** alanında, özel galeri için bir ad girin, örneğin, `My Gallery`.  
  
5.  İçinde **URL** Atom akışı veya özel galeri barındıran SharePoint sitesinin URL'sini girin.  
  
    1.  Atom akışı ana bilgisayar ise özel Galerisine bağlanır, bu URL'yi benzeyecektir: http://www.mywebsite/mygallery/atom.xml.  Bu URL için bir dosya veya bir ağ yolu başvurabilir.  
  
    2.  Konak, bir SharePoint sitesi ise, URL bu benzeyecektir: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>Özel galeriler yönetme  
 Bir yönetici özel bir galeri kullanılabilir birkaç bilgisayar için aynı zamanda her bilgisayarda Sistem kayıt defterini değiştirerek yapabilirsiniz. Bunu gerçekleştirmek için yeni kayıt defteri anahtarları ve değerlerini açıklayan .pkgdef dosyası oluşturun.  Bu dosya biçimi aşağıdaki gibidir.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Daha fazla bilgi için [nasıl yapılır: bir özel galeri kayıt ayarları kullanılarak yönetme](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Bir özel Galeriden uzantıları yükleme  
 İçin arama yapın ve Visual Studio uzantıları özel bir galeri yüklersiniz **Uzantılar ve güncelleştirmeler**. Aşağıdaki adımları adlı özel bir galeri kullanın `My Gallery`.  
  
 ![Uzantı Yöneticisi'ni yükleme özel galeri](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Arama ve özel bir Galeriden uzantıları yüklemek için  
  
1.  Menü çubuğunda, **Araçları**, **Uzantılar ve güncelleştirmeler**.  
  
2.  Sol bölmede seçin **çevrimiçi uzantılara**ve ardından **My galeri**.  
  
3.  Sağ bölmede, bir uzantı seçin ve ardından **indirme** düğmesi.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Özel bir galeriyi Extensions güncelleştiriliyor  
 Visual Studio Uzantıları'nın yeni sürümlerine özel galeride gönderilen değerler olarak yüklediğiniz uzantıları güncelleştirebilirsiniz. Aşağıdaki adımları adlı özel bir galeri kullanın `My Repository`.  
  
 ![Uzantı Yöneticisi Özel Galeri güncelleştirme](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Yüklü uzantı özel galerisinden güncelleştirmek için  
  
1.  Menü çubuğunda, **Araçları**, **Uzantılar ve güncelleştirmeler**.  
  
2.  Sol bölmede seçin **güncelleştirmeleri**ve ardından **My depo**.  
  
3.  Sağ bölmede, bir uzantı seçin ve ardından **güncelleştirme** düğmesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bulma ve Visual Studio uzantıları kullanma](../ide/finding-and-using-visual-studio-extensions.md)   
 [Visual Studio Uzantıları Gönderme](../extensibility/shipping-visual-studio-extensions.md)

