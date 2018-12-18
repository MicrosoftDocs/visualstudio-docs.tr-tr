---
title: Araç kutusu öğelerini, WPF bileşenlerini seçme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3c04a5f4be811c7cb1cae525ef0a16b437dd88b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887143"
---
# <a name="choose-toolbox-items-wpf-components"></a>Araç Kutusu Öğelerini, WPF Bileşenlerini Seçme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Bu sekme, **araç kutusu öğelerini Seç** iletişim kutusu, yerel bilgisayarınızda Windows Presentation Foundation (WPF) kullanılabilir denetimleri bir listesini görüntüler. Bu listeyi görüntülemek için seçin **araç kutusu öğelerini Seç** gelen **Araçları** görüntülenecek menü **araç kutusu öğelerini Seç** iletişim kutusunu ve ardından kendi **WPF Bileşenleri** sekmesi. Listelenen bileşenleri sıralamak için herhangi bir sütun başlığını seçin.  
  
- Bir bileşen yanındaki onay kutusunu seçtiğinizde, söz konusu bileşen için bir simge görüntülenir **araç kutusu**.  
  
  > [!TIP]
  >  Örneği WPF denetiminin proje belge düzenlenmesi için açıldı eklemek için sürükleyin, **araç kutusu** Tasarım görünümü yüzeyine simgesi. Varsayılan işaretleme ve kod bileşeni için projenize değiştirmek hazır eklenir. Daha fazla bilgi için [nasıl yapılır: araç kutusu penceresini yönetme](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2) ve [nasıl yapılır: araç kutusu sekmeleri işlemek](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
- Bir bileşen yanındaki onay kutusunu temizlendiğinde, karşılık gelen simgeyi kaldırılacak **araç kutusu.**  
  
  > [!NOTE]
  >  Bunlar için simgeler görüntülenir olup olmadığını bilgisayarınızda yüklü .NET Framework bileşenlerini sunulmaya **araç kutusu**.  
  
  Sütunlarda **WPF bileşenleri** sekmesine aşağıdaki bilgileri içerir:  
  
  Ad  
  WPF denetimleri, girdileri bilgisayarınızın kayıt defterinde mevcut adlarını listeler.  
  
  Ad Alanı  
  Hiyerarşisini görüntüler [NIB: .NET Framework sınıf kitaplığı](http://msdn.microsoft.com/en-us/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) bileşeni yapısını tanımlayan ad. Bilgisayarınızda yüklü her .NET Framework ad alanı içinde kullanılabilir bileşenleri listelemek için bu sütun sıralama.  
  
  Derleme adı  
  Her bileşen için ad alanı içeren bir .NET Framework derlemesinin adını görüntüler. Bilgisayarınızda yüklü her .NET Framework derlemesi içindeki ad alanlarını listelemek için bu sütun sıralama.  
  
  Dizin  
  .NET Framework derlemesinin konumunu görüntüler. Genel Derleme Önbelleği tüm derlemeler için varsayılan konumdur. Genel Derleme Önbelleği hakkında daha fazla bilgi için bkz: [derlemeler ve genel derleme önbelleği ile çalışma](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).  
  
## <a name="uielement-list"></a>UIElement Listesi  
 **Filtre**  
 Metin kutusunda sağladığınız dizenin göre WPF denetim listesini filtreler. Tüm eşleşmeleri herhangi birinden dört sütun gösterilmektedir.  
  
 **Temizle**  
 Filtre dizesi temizler.  
  
 **Göz atma**  
 Açılır **açık** iletişim kutusunda, WPF denetimleri içeren derlemeler gezinmenize olanak tanır. Hangi genel derleme önbelleğinde bulunmayan derlemeler yüklemek için bunu kullanın.  
  
 **Dil**  
 Seçili WPF denetimi içeren bütünleştirilmiş kodun yerelleştirilmiş dilini gösterir.  
  
## <a name="limitations"></a>Sınırlamalar  
 Özel denetim ekleme veya <xref:System.Windows.Controls.UserControl> araç kutusuna aşağıdaki sınırlamalara sahiptir.  
  
- Yalnızca güncel proje dışında tanımlanmış özel denetimler için çalışır.  
  
- Doğru sürüm için hata ayıklama veya sürüm hata ayıklama çözüm yapılandırması değiştirdiğinizde güncelleştirmez. Başvuru yapılan proje başvurusunun değildir, ancak bunun yerine derleme diskte içindir olmasıdır. Denetim, hata ayıklama'dan sürümüne değiştirdiğinizde geçerli çözümün bir parçası ise, projenizin hata ayıklama sürümü denetimi başvurmak devam eder.  
  
  Ayrıca, tasarım zamanı meta verileri özel denetim ve bu meta veriler için uygulanırsa belirtir <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> ayarlanır `false`, denetimin araç kutusunda görünmüyor.  
  
  Ad alanını ve derlemeyi denetiminizin eşleyerek denetimlerinizi XAML görünümünde doğrudan başvurabilirsiniz. Daha fazla bilgi için [nasıl yapılır: bir Namespace XAML alma](http://msdn.microsoft.com/en-us/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araç kutusu öğelerini Seç iletişim kutusu (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [Araç kutusu](../../ide/reference/toolbox.md)   
 [Nasıl yapılır: üçüncü taraf WPF denetim bir WPF uygulamasında kullanma](http://msdn.microsoft.com/en-us/f4c0b601-3818-4f9f-85e5-77905f3b427f)   
 [WPF Tasarımcısı](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)



