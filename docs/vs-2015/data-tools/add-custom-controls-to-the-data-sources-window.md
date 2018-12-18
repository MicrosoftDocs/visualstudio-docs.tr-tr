---
title: Veri kaynakları penceresine özel denetimler ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e84224d4ebd066891d4fdf90b4ad488a79cc0b1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183644"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Veri kaynakları penceresine özel denetimler ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bir öğeyi sürüklediğinizde **veri kaynakları** penceresinde bir veriye bağlı denetim oluşturmak için bir tasarım yüzeyine, oluşturduğunuz denetim türünü seçebilirsiniz. Penceresinde her öğenin, aralarından seçim yapabileceğiniz denetimleri görüntüleyen bir açılır liste vardır. Her bir öğeyle ilişkili denetimler kümesini öğesinin veri türüne göre belirlenir. Oluşturmak istediğiniz Denetim listede görünmüyorsa, denetim listesine eklemek için bu konudaki yönergeleri takip edebilirsiniz.  
  
 Öğeleri oluşturmak için verilere bağlı denetimler seçme hakkında daha fazla bilgi için **veri kaynakları** penceresinde görmek [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
> [!NOTE]
>  İletişim kutuları ve menü komutları gördüğünüz açıklanana Yardım'da, etkin ayarlarınıza ve sürüm bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için **Araçları** menüsünde **içeri ve dışarı aktarma ayarları**. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="customizinglist"></a> Bir veri türü için bağlanabilir denetim listesini özelleştirme  
 Ekleme veya öğe mevcut denetimlerin listesinin denetimleri kaldırma için **veri kaynakları** aşağıdaki adımları uygulayın, bir özel veri türüne sahip bir pencere.  
  
#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Bir veri türü için listelenen denetimleri seçin  
  
1.  WPF Tasarımcısı ya da Windows Form Tasarımcısı açık olduğundan emin olun.  
  
2.  İçinde **veri kaynakları** penceresinde, pencereye eklenen bir veri kaynağının bir parçası olan bir öğeye tıklayın ve açılan menü öğesi için'a tıklayın.  
  
3.  Aşağı açılan menüden **Özelleştir**. Aşağıdaki iletişim kutularından birini açar:  
  
    -   Windows Forms Tasarımcısı açıksa **veri UI özelleştirmesi** sayfasının **seçenekleri** iletişim kutusu açılır.  
  
    -   WPF Tasarımcısı açıksa **denetim bağlamayı Özelleştir** iletişim kutusu açılır.  
  
4.  İletişim kutusunda veri türünden **veri türü** aşağı açılan listesi.  
  
    -   Bir tablo veya nesne için denetim listesini özelleştirmek için işaretleyin **[listesi]**.  
  
    -   Bir tablo sütunu ya da bir nesnenin bir özellik için denetim listesini özelleştirmek için temel alınan veri deposunda sütun veya özelliğin veri türünü seçin.  
  
    -   Kullanıcı tanımlı şekillere sahip veri nesneleri görüntülemek için denetimler listesini özelleştirmek için işaretleyin **[diğer]**. Örneğin, **[diğer]** uygulamanızın belirli bir nesnenin birden fazla özellik verileri görüntüleyen özel bir denetim varsa.  
  
5.  İçinde **ilişkili denetimler** kutusuna, seçilen veri türü için kullanılabilir olmasını istediğiniz her bir denetim seçin veya listeden kaldırmak istediğiniz herhangi bir denetim seçimini temizleyin.  
  
    > [!NOTE]
    >  Olarak seçmek istediğiniz denetim belirmiyorsa **ilişkili denetimler** kutusunda denetim listesine eklemeniz gerekir. Daha fazla bilgi için [listesini, ilişkili denetimler veri türü için ekleme denetimlerini](#addingcontrols).  
  
6.  **Tamam**'ı tıklatın.  
  
7.  İçinde **veri kaynakları** penceresinde, bir veri öğesi yalnızca bir veya daha fazla denetim ilişkili yazın ve açılan menü öğesi için'a tıklayın.  
  
     Denetimler, seçtiğiniz **ilişkili denetimler** kutusu öğenin açılan menüde artık görünür.  
  
##  <a name="addingcontrols"></a> Veri ilişkili denetimler listesine Addcontrols yazın  
 Denetim bir veri türü ile ilişkilendirmek istediğiniz, ancak denetimin görünmez **ilişkili denetimler** kutusunda denetim listesine eklemeniz gerekir. Denetim geçerli çözümde veya başvurulan bir derlemede yer almalıdır. Bu da kullanılabilir olmalıdır **araç kutusu**, ve denetimin veri bağlamanın davranışını belirten bir özniteliği vardır.  
  
#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>İlişkili denetimler listesine denetimler ekleme  
  
1.  Eklemek istediğiniz denetime **araç kutusu** sağ tıklanarak **araç kutusu** seçerek **öğelerini Seç**.  
  
     Denetimi aşağıdaki öznitelikleri birine sahip olmalıdır.  
  
    |Öznitelik|Açıklama|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Gibi bir tek sütun (veya özellik) verileri görüntüleyen basit denetimler Bu öznitelikte uygulayan bir <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Bu özniteliği veri listeleri (veya tablo) görüntüleyen denetimler gibi uygulama bir <xref:System.Windows.Forms.DataGridView>.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Bu özniteliği veri ancak tek bir sütun veya özelliği sunmak için ihtiyaç listeleri (veya tablo) görüntüleyen denetimler gibi uygulama bir <xref:System.Windows.Forms.ComboBox>.|  
  
2.  Windows Forms üzerindeki **seçenekleri** açık iletişim kutusunu **veri UI özelleştirmesi** sayfası. Ya da WPF için açık **denetim bağlamayı Özelleştir** iletişim kutusu. Daha fazla bilgi için [bir veri türü için liste, bağlanabilir denetimleri özelleştirme](#customizinglist).  
  
3.  İçinde **ilişkili denetimler** kutusunda, az önce eklediğiniz denetimin **araç kutusu** artık görünmelidir.  
  
    > [!NOTE]
    >  Geçerli çözüm içindeki ya da başvurulan bir derlemede bulunan denetimler yalnızca ilişkili denetimler listesine eklenebilir. (Denetimler de veri bağlama özniteliklerinden biri önceki tabloda uygulamanız gerekir.) Veri bulunmayan özel bir denetim bağlamak için **veri kaynakları** penceresinde denetimi **araç kutusu** tasarım yüzeyi ve gelen bağlamak için öğeyi sürükleyin **veri Kaynakları** içerisindeyse denetimdeki penceresi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)

