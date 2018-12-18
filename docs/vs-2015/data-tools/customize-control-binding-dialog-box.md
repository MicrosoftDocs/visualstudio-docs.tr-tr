---
title: Bağlama iletişim kutusu denetimini özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.datauicustomization
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Customize Control Binding dialog box
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8ca2da23040f3e7a57fe5da2ff8b87cc7fc38099
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889717"
---
# <a name="customize-control-binding-dialog-box"></a>Denetim Bağlamayı Özelleştir İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanım **denetim bağlamayı Özelleştir** iletişim kutusu, hangi denetimlerin öğelerin kullanılabilir olduğunu belirtmek için [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Her öğe **veri kaynakları** pencere öğesine bağlı denetimleri ilişkili bir listesi bulunur. Her öğe için kullanılabilir denetimleri öğe veri türü tarafından belirlenir. Varsayılan Denetim dahil olmak üzere, bu iletişim kutusunda tanımlanan geçerli ilişkili denetimlerin listesini her bir veri türü vardır.  
  
 Veriye bağlı denetim oluşturmak için bir tasarım yüzeyine bir öğe sürüklemeden önce oluşturmak için hangi denetimi seçebilirsiniz. Bir öğeyi sürüklediğinizde **veri kaynakları** bir tasarım yüzeyine bir denetim, varsayılan denetim seçili öğe veri türü tasarım yüzeyine eklenir seçmeden penceresi.  
  
 Denetim öğelerin listesini özelleştirmek için bu iletişim kutusunu kullanma hakkında daha fazla bilgi için **veri kaynakları** penceresinde görmek [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="uielement-list"></a>UIElement Listesi  
 **Veri türü**  
 Dentimleriyle ilişkilendir türlerinin bir listesini görüntüler:  
  
- Tablo, varlıkları ve nesneler olarak gösterilir **[listesi]** türleri.  
  
- Sütun veya varlıkları ve nesneler genel özelliklerini sütunun ya da temel alınan veri deposundaki özelliği gerçek veri türü olarak temsil edilir.  
  
- Kullanıcı tarafından tanımlanmış şekillerle nesneler olarak temsil edilir **[diğer]**. Örneğin, uygulamanızın bir nesnenin birden fazla özellik verileri görüntüleyen özel bir denetim varsa seçin **[diğer]** denetlemek için veri türü.  
  
  **İlişkili denetimler**  
  Belirli veri türü ile ilişkilendirebilirsiniz denetimlerin listesini görüntüler. Seçilen veri türüne sahip bir özel denetime ilişkilendirmek istiyorsanız **veri türü** listesinde, ilgili onay kutusunu seçin. Bir ilişkiyi kaldırmak için bu onay kutusunu temizleyin. Denetimleri görünür kısayol menüsünde tarafından sunulan kullanıma **veri kaynakları** ilişkili veri türünde bir öğe için pencere.  
  
  Çeşitli veri bağlama özniteliklerini birine sahip denetimler ekleyerek denetimleri listesine ekleyebilirsiniz **araç kutusu**. Daha fazla bilgi için [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
  **Varsayılanı Ayarla**  
  Seçili veri türü öğeler için varsayılan olarak seçili denetim türü atar. Varsayılan denetim tarafından sunulan kısayol menüsünü seçimdeki ilk olarak görünür **veri kaynakları** penceresi için bir öğe. Yalnızca bir denetim türü, bir veri türü için varsayılan olarak atanabilir.  
  
  **Varsayılanı Temizle**  
  Bir denetim atamasını seçili veri türü için varsayılan olarak kaldırır. Seçili veri türü için varsayılan yok ise **[Hiçbiri]** tarafından sunulan kısayol menüsünü seçimdeki ilk olarak görünür **veri kaynakları** ilişkili türünde bir öğe için pencere.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)   
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Deneti veri kaynakları penceresinden sürüklendiğinde oluşturulacak şekilde ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)