---
title: Ampullerle hızlı eylemler gerçekleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 990ee487-cf9a-4b89-9784-e7b47c220e8c
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3eff05df37dd1d15774fb059396f3f94b0fff2a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883464"
---
# <a name="perform-quick-actions-with-light-bulbs"></a>Ampullerle hızlı eylemler gerçekleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ampuller, Visual Studio 2015'te yeni bir üretkenlik özelliğidir. Visual Studio Düzenleyicisi'nde görüntülenen ve yeniden düzenleme hataların giderilmesi de dahil olmak üzere hızlı eylemler gerçekleştirmek üzere tıklayabileceği simgeleri değildirler. Ampuller, hatanın düzeltilmesi getirin ve tek bir odak noktasına Yardım yeniden düzenleme genellikle burada yazdığınız satırına sağ.  
  
 ![Küçük ampul](../ide/media/vs2015-lightbulbsmall.png "VS2015_LightBulbSmall")  
  
 C# ve Visual Basic'te, sorunun nasıl çözüleceğini önereceğin bir kırmızı dalgalı ve Visual Studio varsa ampul sahip görürsünüz. Örneğin bir kırmızı dalgalı tarafından belirtilen bir hata varsa, bu hata düzeltmeleri kullanılabilir olduğunda bir ampul görünür. C++'da yeni bir işlev bir üstbilgi dosyasına eklediğinizde, bu işlev bir saplama uygulaması oluşturmak için sunan bir ampul görürsünüz. Herhangi bir dilde üçüncü taraflara özel tanılama ve öneriler, örneğin bir SDK'ın bir parçası olarak sağlayabilir ve Visual Studio ampuller bu kurallara göre görüntülenir.  
  
## <a name="to-see-a-light-bulb"></a>Bir ampul görmek için  
  
1. Çoğu durumda, giriş işaretini bir hata var. bir satır taşıdığınız zaman noktasında bir hata veya düzenleyicinin sol kenar boşluğunda fare geldiğinizde ampuller kendiliğinden görünür. Kırmızı dalgalı gördüğünüzde, ampul görüntülemek için onu gelebilirsiniz. Ayrıca, herhangi bir satırda sorunun nerede oluştuğunu gitmek için klavye ve fare kullandığınızda görüntülemek bir ampul de neden olabilir.  
  
2. Tuşuna **Ctrl +.** Ampul çağırmak ve doğrudan olası listesine gitmek için bir satırda herhangi bir yere düzeltir.  
  
   ![Ampul fare vurgulama ile](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")  
  
## <a name="to-see-potential-fixes"></a>Olası düzeltmeleri görmek için  
 Bulunan aşağı oka tıklayın ya da ampul için izleyebileceğiniz hızlı eylemlerin bir listesini görüntülemek için bağlantıyı Show olası düzeltmeleri.  
  
 ![Genişletilmiş ampul](../ide/media/vs2015-lightbulb-hover-expanded.png "VS2015_LightBulb_hover_expanded")  
  
## <a name="to-do-a-refactoring"></a>Bir yeniden düzenleme yapmak için  
 Bağlam menüsünü açmak için sağ tıklayarak yeniden düzenlemeler yine de gerçekleştirebilirsiniz ancak Ctrl tuşuna da basabilirsiniz +. yeniden düzenleme seçeneklerini görüntülemek için. Aşağıdaki çizimde, ayıklama yöntemi yeniden düzenleme Ctrl tuşuna bastıktan sonra sunulan +. herhangi bir yerde içeren satırda `Math.Abs` çağırın:  
  
 ![Yeniden düzenleme seçeneklerini gösteren bir ampul](../ide/media/vs2015-lightbulbs-refactor.png "VS2015_LightBulbs_refactor")



