---
title: Özel galeriler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e91b3ecec969ab6a717598d8dfb77e674890216a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638589"
---
# <a name="private-galleries"></a>Özel galeriler
Denetimleri, şablonlar ve bunlara yayınlayarak geliştirme araçları paylaşabilirsiniz bir *özel galeri* gösterildiği gibi kuruluşunuz için intranet üzerindeki:  
  
-   Bir Atom (uygun şekilde yapılandırılmış merkezi bir konuma (depo) intranet ağınızdaki RSS akışı) oluşturun. Daha fazla bilgi için [nasıl yapılır: Atom akışı için özel bir galeri oluşturun](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Dağıtma bir *.pkgdef* Özel Galeri tanımlayan dosya. Özel bir galeri aynı anda birçok bilgisayara bağlanmak isteyen yöneticiler için bu yapılandırmayı öneririz.  
  
## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Uzantılar ve güncelleştirmeler Visual Studio'da Özel Galeri ekleme  
 Özel bir galeri kullanılabilir olduğunda, kendisine ekleyebilirsiniz **Uzantılar ve güncelleştirmeler** Visual Studio'da.  
  
 ![Uzantı Yöneticisi ekleme iletişim kutusu](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Uzantılar ve güncelleştirmeler için özel bir galeri ekleme  
  
1.  Menü çubuğunda, **Araçları** > **seçenekleri**.  
  
2.  İçinde **ortam** düğümünü **Uzantılar ve güncelleştirmeler**.  
  
3.  Seçin **Ekle** düğmesi.  
  
4.  İçinde **adı** alanında, özel galeri için bir ad girin, örneğin, `My Gallery`.  
  
5.  İçinde **URL** Atom akışı veya özel galeri barındıran SharePoint sitesinin URL'sini girin.  
  
    1.  Atom akışı ana bilgisayar ise özel Galerisine bağlanır, bu URL'yi benzeyecektir: http://www.mywebsite/mygallery/atom.xml.  Bu URL için bir dosya veya bir ağ yolu başvurabilir.  
  
    2.  Konak, bir SharePoint sitesi ise, URL bu benzeyecektir: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="manage-private-galleries"></a>Özel galeriler yönetme  
 Bir yönetici özel bir galeri kullanılabilir birkaç bilgisayar için aynı zamanda her bilgisayarda Sistem kayıt defterini değiştirerek yapabilirsiniz. Bunu yapmak için oluşturun bir *.pkgdef* yeni kayıt defteri anahtarları ve değerlerini açıklayan dosyası.  Bu dosya biçimi aşağıdaki gibidir.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Daha fazla bilgi için [nasıl yapılır: kayıt defteri ayarlarını kullanarak özel bir galeriyi yönetme](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="install-extensions-from-a-private-gallery"></a>Özel bir Galeriden uzantıları yükleme  
 İçin arama yapın ve Visual Studio uzantıları özel bir galeri yüklersiniz **Uzantılar ve güncelleştirmeler**. Aşağıdaki adımları adlı özel bir galeri kullanın `My Gallery`.  
  
 ![Uzantı Yöneticisi'ni yükleme özel galeri](../extensibility/media/em_.png "EM_")  
  
### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Arama ve özel bir Galeriden uzantıları yüklemek için  
  
1.  Menü çubuğunda, **Araçları** > **Uzantılar ve güncelleştirmeler**.  
  
2.  Sol bölmede seçin **çevrimiçi uzantılara**ve ardından **My galeri**.  
  
3.  Sağ bölmede, bir uzantı seçin ve ardından **indirme** düğmesi.  
  
## <a name="update-extensions-from-a-private-gallery"></a>Özel galerisinden uzantıları  
 Visual Studio Uzantıları'nın yeni sürümlerine özel galeride gönderilen değerler olarak yüklediğiniz uzantıları güncelleştirebilirsiniz. Aşağıdaki adımları adlı özel bir galeri kullanın `My Repository`.  
  
 ![Uzantı Yöneticisi Özel Galeri güncelleştirme](../extensibility/media/em_update.png "EM_Update")  
  
### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Yüklü uzantı özel galerisinden güncelleştirmek için  
  
1.  Menü çubuğunda, **Araçları** > **Uzantılar ve güncelleştirmeler**.  
  
2.  Sol bölmede seçin **güncelleştirmeleri**ve ardından **My depo**.  
  
3.  Sağ bölmede, bir uzantı seçin ve ardından **güncelleştirme** düğmesi.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Bulma ve Visual Studio uzantıları kullanma](../ide/finding-and-using-visual-studio-extensions.md)   
 [Visual Studio uzantıları gönderin](../extensibility/shipping-visual-studio-extensions.md)