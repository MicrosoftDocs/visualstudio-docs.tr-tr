---
title: 'İzlenecek yol: Visual Studio uzantısı yayımlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae0b9d48e2a2292229b40e3aaf2a1c755e4c844e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815747"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>İzlenecek yol: Visual Studio uzantısı yayımlama

Bu izlenecek yol, Visual Studio Market'te Visual Studio uzantısı yayımlama gösterilmektedir. Market'te uzantınızı eklediğinizde, geliştiriciler kullanabilir **Uzantılar ve güncelleştirmeler** için yeni ve güncelleştirilmiş uzantıları gidin.

## <a name="prerequisites"></a>Önkoşullar

 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Visual Studio uzantısı oluşturun

Bu makalede bir varsayılan VSPackage uzantısı kullanır, ancak adımları her uzantı türü için geçerlidir.

1. C# ' adlı bir VSPackage'ı oluşturma `TestPublish` olan bir menü komutu. Daha fazla bilgi için [ilk uzantınızı oluşturun: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Uzantınızı paketi

1. Uzantıyı Güncelleştir *.vsixmanifest* ürün adı, yazar ve sürüm hakkında doğru bilgileri.

   ![Uzantı vsixmanifest güncelleştir](media/update-extension-vsixmanifest.png)

2. Uzantınızı yapı içinde **yayın** modu. Artık uzantınızı bir VSIX \bin\Release klasör olarak paketlenir.

3. Yüklemeyi doğrulamak için VSIX dosyasına çift tıklayabilirsiniz.

## <a name="test-the-extension"></a>Uzantıyı test etmek

 Uzantı dağıtmadan önce yapı ve Visual Studio'nun deneysel örneğinde doğru şekilde yüklendiğinden emin olmak için test edin.

1. Visual Studio'da açın, Visual Studio'nun deneysel örneği için hata ayıklamayı başlatın.

2. Deneysel örneğinde Git **Araçları** menüsüne ve ardından **Uzantılar ve güncelleştirmeler**. TestPublish uzantısı, Orta bölmede görünür olmalıdır ve etkinleştirilmesi.

3. Üzerinde **Araçları** menüsünde, test komut gördüğünüzden emin olun.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Uzantı Visual Studio Market'te yayımlama

1. Uzantınızı sürümü oluşturulan ve güncel olduğundan emin olun.

2. Bir web tarayıcısında açın [Visual Studio Market](https://marketplace.visualstudio.com/vs) Web sitesi.

3. Sağ üst köşede **oturum**.

4. Oturum açmak için Microsoft hesabınızı kullanın. Bir Microsoft hesabınız yoksa bir bu noktada oluşturabilirsiniz.

5. Tıklayın **uzantıları Yayımla**.  Bu seçenek, tüm uzantıları Yönet sayfasına götürür. Bir yayımcı hesabı yoksa, şu anda oluşturmanız istenir.

   ![Market'te karşıya yükleme](media/upload-to-marketplace.png)

6. Uzantınızı karşıya yüklemek için kullanmak istediğiniz publisher'ı seçin. Yayımcılar, sol tarafta listelenen yayımcı adlarını tıklatarak değiştirebilirsiniz. Tıklayarak **yeni uzantı** seçip **Visual Studio**.

7. İçinde **1: karşıya uzantı**, doğrudan Visual Studio Market VSIX dosyasını karşıya yükleyin veya sadece kendi Web sitesine bir bağlantı eklemek seçebilirsiniz. Bu örnekte, uzantı *TestPublish.vsix* yüklenir. Sürükleyip bırakın uzantınızı veya kullanın **tıklayın** dosyasına gözatmak için bağlantı. Uzantınızı projenin \bin\Release klasöründe bulun.  
              **Devam**'a tıklayın.

8. İçinde **2: uzantı ayrıntılarını sağlayın**, otomatik olarak doldurulan gelen bazı alanlar *source.extension.vsixmanifest* uzantınızı dosyasından. Her hakkında daha fazla ayrıntı bulabilirsiniz:

    * **İç ad** uzantı ayrıntı sayfasında URL'de kullanılır. Örneğin, "myname" Yayımcı adı altında bir uzantısı yayımlama ve iç adı "uzantım" olacak şekilde belirterek bir URL'de sonuçları "marketplace.visualstudio\.com/items?itemName=myname.myextension", uzantının ayrıntılı bilgi için Sayfa.
    
    * **Görünen ad** uzantınızın. Bu ad alanından otomatik olarak doldurulmuş *source.extension.vsixmanifest* dosya.
   
    * **Sürüm** karşıya yüklediğiniz uzantı sayısı. Bu sürümü otomatik olarak doldurulan gelen *source.extension.vsixmanifest* dosya.
    
    * **VSIX kimliği** Uzantınız için Visual Studio kullanan benzersiz tanımlayıcı. Bu tanımlayıcı, otomatik olarak yükseltilerek uzantınızı olmasını istiyorsanız gereklidir. Bu tanımlayıcı gelen otomatik olarak doldurulmuş *source.extension.vsixmanifest* dosya.
    
   * **Logo** Uzantınız için kullanılır. Bu logo gelen otomatik olarak doldurulmuş *source.extension.vsixmanifest* sağlanırsa, dosya.
    
     * **Kısa açıklama** uzantınızın ne yaptığını. Bu açıklama, gelen otomatik olarak doldurulmuş *source.extension.vsixmanifest* dosya.
    
     * **Genel Bakış** ekran görüntüleri ve uzantınızın ne yaptığını hakkında ayrıntılı bilgi dahil etmek için iyi bir yerdir.
    
     * **Desteklenen Visual Studio sürümleri** seçtiğiniz uzantınızı çalışır, Visual Studio'nun hangi sürümlerinin sağlar. Uzantınızı yalnızca sürümler yüklenir.
    
     * ** Desteklenen Visual Studio sürümü uzantınızı üzerinde çalışacağı Visual Studio'nun hangi sürümlerinin seçmenize olanak sağlar. Uzantınızı yalnızca bu sürümü için yüklenir.
    
     * **Tür**. En yaygın türü uzantıları **Araçları**.
    
     * **Kategorileri**. En çok üç Uzantınız için bir en uygun olan seçin.
    
     * **Etiketleri** uzantınızı olduğunu kullanıcıları Yardım anahtar sözcükleri. Etiketler, uzantılarınızı Market'te, aramanın ilgi düzeyini artırmaya yardımcı olabilir.
    
     * **Fiyatlandırma kategorisi** uzantınızı maliyetidir.
    
     * **Kaynak kodu deposu** toplulukla bağlantı kaynak kodunuzu paylaşmanıza olanak tanır.
    
     * **Uzantınız için soru- cevap izin** uzantısı giriş sayfanızda sorular bırakın olanak sağlar.

9. Tıklayın **Kaydet ve karşıya yükle**. Sayfa yayımcınıza için yedekleme bu seçeneği alır yönetin. Uzantınızı henüz yayımlanmamış. Uzantınızı yayımlamak için uzantı sağ tıklatın ve **genel yap**. Nasıl uzantınızı Market'te seçerek görüneceğini görüntüleyebileceğiniz **uzantıyı görüntüle**. Alım sayıları için tıklayarak **raporları**. Uzantınız için değişiklik yapmak için tıklatın **Düzenle**.

   ![Uzantı girişi menüsü](media/extension-entry-menu.png)

10. ' I tıklattıktan sonra **genel yap**, uzantınızın genel sunulmuştur. Uzantınız için Visual Studio Market'te arayın.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Yayımcı hesabınızı yönetmek için ek kullanıcı ekleme

Market erişmek ve bir yayımcı hesabı yönetmek için ek kullanıcılara izin verme destekler.

1. Ek kullanıcılar için eklemek istediğiniz yayımcı hesabı gidin.

2. Seçin **üyeleri** tıklayın **Ekle**.

   ![Ek kullanıcı ekleme](media/add-users.png)

3. Ardından, eklemek ve doğru altında erişim düzeyini vermek istediğiniz kullanıcının e-posta adresi belirtebilirsiniz **bir rol seçin**.  Aşağıdaki seçeneklerden birini seçebilirsiniz:

   * **Oluşturucu**: Kullanıcı Uzantıları yayımlayabilir ancak olamaz görüntüleyebilir veya diğer kullanıcıların yayımladığı uzantıları yönetebilirsiniz.
  
   * **Okuyucu**: kullanıcı görüntüleyebilir uzantıları, ancak olamaz yayımlama veya uzantıları yönetin.
  
   * **Katkıda bulunan**: kullanıcı yayımlama ve uzantıları yönetebilen ancak Yayımcı ayarlarını düzenleyebilir ya da erişimi yönetme.
  
   * **Sahibi**: kullanıcı yayımlamak ve uzantıları yönetin, yayımcı ayarlarını düzenleyebilir ve erişimi yönetin.
  
## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Market'ten uzantı yükleme

Uzantı yayımlandıktan sonra Visual Studio'da yükleyin ve test etmek.

1. Visual Studio'da üzerinde **Araçları** menüsünü tıklatın **Uzantılar ve güncelleştirmeler**.

2. Tıklayın **çevrimiçi** bulun **TestPublish**.

3. **İndir**'e tıklayın. Uzantıyı daha sonra yüklenmek üzere zamanlandı.

4. Yüklemeyi tamamlamak için Visual Studio'nun tüm örneklerini kapatın.

## <a name="remove-the-extension"></a>Uzantıyı kaldırın

Uzantı, Visual Studio Market'ten ve bilgisayarınızdan kaldırabilirsiniz.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Market'ten uzantıyı kaldırmak için

1. Açık [Visual Studio Market](https://marketplace.visualstudio.com/vs) Web sitesi.

2. Sağ üst köşede tıklayın **Yayımla** uzantıları. Yayımlamak için kullanılan yayımcı çekme **TestPublish**. Listesi **TestPublish** görünür.

3. Uzantı girdiye sağ tıklatıp **Kaldır**. Uzantıyı kaldırmak isteyip istemediğinizi onaylamanız istenir. **Tamam**'ı tıklatın.

### <a name="to-remove-the-extension-from-your-computer"></a>Uzantıyı bilgisayarınızdan kaldırmak için

1. Visual Studio'da üzerinde **Araçları** menüsünü tıklatın **uzantı ve güncelleştirmeler**.

2. Seçin **TestPublish** ve ardından **kaldırma**. Uzantı ardından kaldırılmak üzere zamanlandı.

3. Kaldırma işlemini tamamlamak için Visual Studio'nun tüm örneklerini kapatın.
