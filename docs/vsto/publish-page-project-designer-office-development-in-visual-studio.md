---
title: Yayımlama Sayfası, Proje Tasarımcısı (Visual Studio'da Office Geliştirme)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e4d315a00f527953500b47095ee4080b4eafd4cc
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672723"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Yayımlama Sayfası, Proje Tasarımcısı (Visual Studio'da Office Geliştirme)
  **Yayımla** sayfasının **Proje Tasarımcısı** dağıtım özelliklerini yapılandırmak için kullanılır.  
  
 Bu sayfaya erişmek için projeyi seçin **Çözüm Gezgini**ve ardından **proje** menüsünde seçin *Projectname* **özellikleri** . Varsa **Yayımla** sayfası görüntülenmez öğesini **Yayımla** sekmesi.  
  
> [!NOTE]  
>  De Yayınlama konumu ayarlayabilirsiniz **Yayımlama Sihirbazı**. Daha fazla bilgi için [nasıl yapılır: ClickOnce kullanarak Office çözümü yayımlama](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).  
  
## <a name="uielement-list"></a>UIElement listesi  
 **Yayımlama klasörü konumu (web sitesi, ftp sunucusu veya dosya yolu)**  
 Gerekli.  
  
 Yayımlama klasörü konumu için ve Visual Studio çözüm dosyalarını bildirimleri, derlemeleri ve diğer dosyalar gibi yapı kopyaladığı dizin olan. Bu dizine yazma erişimi olmalıdır.  
  
 Seçenekler, yerel bilgisayar, bir UNC dosyası paylaşımı veya bir HTTP/HTTPS web sitesi içerir. Yol yerel olabilir (*c:\foldername\publishfolder*), göreli (*yayımlama\\*), veya tam bir konum (*\\\servername\foldername* veya http://<em>servername/foldername</em>).  
  
 Varsayılan olarak, yayımlama konumdur *http://localhost/projectname/* , IIS yüklü değilse veya *yayımlama\\*  IIS yüklü değilse dizin.  
  
 **Yükleme klasörü URL'si**  
 İsteğe bağlı.  
  
 Yükleme klasörü URL'si, son kullanıcının özelleştirme yükleyecek dizindir. Ayrıca çözüm güncelleştirmeleri denetlemek için kullanacağı yoludur. Yayımlama klasörü konumu ile aynı yol olabilir, ancak bu zorunlu değildir.  
  
 Seçenekler, yerel bilgisayar, bir UNC dosyası paylaşımı veya bir HTTP/HTTPS web sitesi içerir. Yol yerel olabilir (*c:\foldername\publishfolder*), göreli (*yayımlama\\*), veya tam bir konum (*\\\servername\foldername* veya http://<em>servername/foldername</em>). Tüm HTTP/HTTPS konumlar US-ASCII karakter ile oluşturulması gerekir. Unicode karakterler desteklenmez.  
  
 Yükleme yolu olarak ayarlanırsa özelleştirme dosyaları kullanıcıların özelleştirme yükleyebilmesi o konumda olmalıdır. Yalnızca son dağıtım konumunu biliyorsanız konumu olarak ayarlanmalıdır.  
  
 Yükleme dosyaları belge veya Kurulum programı ilişkili bir konuma gibi CD seçeneğiyle kullanılıyorsa bu kutuyu boş bırakın.  
  
 Bu değer daha sonra yönetici tarafından atanabilir. Daha fazla bilgi için [nasıl yapılır: bir Office çözümünü yükleme yolunu değiştirmek](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 **Önkoşullar**  
 Önkoşullar Kurulum programına dahil veya yükleme sırasında isteğe bağlı olarak indirilir.  
  
- **Bileşen satıcısının web sitesinden önkoşulları**: Microsoft'tan bu önkoşulları indirmek için bu seçeneği kullanın.  
  
- **Uygulamamla aynı konumdan önkoşulları karşıdan yükleyin**: yükleyicinizi önkoşullarda paketlemek için bu seçeneği kullanın. Kurulum programı önkoşul dosyalarıyla dahil olmak üzere çözüm boyutu artar.  
  
- **Aşağıdaki konumdan önkoşulları karşıdan yükleyin**: Önkoşullar son kullanıcılar için ayrı bir web sayfası veya ağ paylaşımında başka bir Kurulum programı olarak kullanılabilmesi için bu seçeneği kullanın.  
  
  **Güncelleştirmeler**  
  Güncelleştirme aralığı çözüm güncelleştirmeleri ne sıklıkla denetleyeceğini belirler. Her yedi günde denetlemek için varsayılandır.  
  
  Belge düzeyinde özelleştirme veya VSTO eklentisi her yüklenişinde güncelleştirmeleri denetleme güncel tutmanın, ancak başlangıç performansı etkiler.  
  
  Bir CD veya çıkarılabilir sürücü kullanarak dağıtıyorsanız, bu ayar **asla güncelleştirmeleri denetleme**.  
  
  **Seçenekler (Açıklama)**  
  Yayımlama seçenekleri aşağıdaki özellikler için ayarlanabilir:  
  
- Yayımlama dili: Office çözümünün yerel ayar.  
  
- Yayımcı adı: şirketiniz veya Geliştirici adıyla görünür **Program Ekle/Kaldır** veya **programlar ve Özellikler**.  
  
- Ürün adı: olarak Office çözümünün adı görünür **Program Ekle/Kaldır** veya **programlar ve Özellikler**.  
  
- Destek URL'si: konumun son kullanıcıların bir Office çözümü için teknik destek birimine başvurun.  
  
  **Seçenekler (Office ayarları)**  
  Yayımlama seçenekleri aşağıdaki özellikler için ayarlanabilir:  
  
- Çözüm adı: olarak Office çözümünün adı Office uygulamasında görünür.  
  
- Açıklama: Office uygulamasında Office çözümünün haliyle açıklaması görünür.  
  
- VSTO eklenti yükleme davranışı.  
  
  -   Başlangıçta yüklenen: Office uygulaması başlatıldığında VSTO eklentisi yükleneceğini belirtir.  
  
  -   İsteğe bağlı yükleme: uygulama, bir kullanıcı VSTO eklenti işlevini kullanan bir kullanıcı Arabirimi öğesi tıkladığında gibi gerektirdiğinde, VSTO eklentisi yükleneceğini belirtir.  
  
  **Yayımlama dili** bu seçenek, Microsoft Yazılımı Lisans koşulları dili ayarlar ve önkoşullar listesinde dil paketlerini içerir. Dil özelleştirme etkilemez. Dil Kurulum programı, Visual Studio'nun yüklü dilleri tarafından belirlenir.  
  
  Değiştirme hakkında daha fazla bilgi için **yayımlama dilini**, bkz: [nasıl yapılır: ClickOnce uygulaması için yayımlama dilini değiştirme](/visualstudio/deployment/how-to-change-the-publish-language-for-a-clickonce-application).  
  
  **Yayım sürümü**  
  Özelleştirme için sürüm numarasını ayarlar. Sürüm numarası değiştirildiğinde, uygulama bir güncelleştirme olarak yayımlanır. Yeni bir klasör, önceden yayımlanmış sürümünün üzerine yazmasını engellemek için derleme işlemi sırasında her sürüm için oluşturulur. Yayınlama sürümünü her parçası (**ana**, **küçük**, **derleme**, **düzeltme**) en fazla beş rakam içerebilir.  
  
  **Her yayında düzeltmeyi otomatik artış**  
  İsteğe bağlı. (Varsayılan) seçildiğinde **düzeltme** parçası sürüm numarası artırılır bir özelleştirme her yayımlandığında. Bu, bir güncelleştirme olarak yayımlanacak özelleştirme neden olur.  
  
  **Şimdi Yayımla**  
  Geçerli ayarları kullanarak uygulamanın yayınlar. Eşdeğer **son** düğmesine **Yayımlama Sihirbazı**.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Office çözüm dağıtım önkoşulları](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e)  
  
  