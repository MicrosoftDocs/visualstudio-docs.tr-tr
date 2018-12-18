---
title: 'Nasıl yapılır: XML kod parçacıklarını kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 774a0f5639057ea5b1dc190ce475278477a7f373
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219620"
---
# <a name="how-to-use-xml-snippets"></a>Nasıl yapılır: XML kod parçacıklarını kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML Düzenleyicisi kısayol menüsünde aşağıdaki iki komutu kullanarak XML kod parçacıklarını çağırabilirsiniz. **Parçacık Ekle** komut İmleç konumuna XML kod parçacığı ekler. **Surround With** komut XML kod parçacığı seçili metin etrafına sarmalar. Her XML kod parçacığı, kod parçacığı türleri atadığı. Kod parçacığı türleri, kod parçacığı ile kullanılabilir olup olmadığını belirlemek **parçacık Ekle** komutu **Surround With** komut veya her ikisi de.  
  
 Düzenleyici için XML kod parçacığı eklendikten sonra kod parçacığında düzenlenebilir tüm alanlar sarı renkle vurgulanır ve imleç ilk düzenlenebilir bir alanı üzerinde konumlandırıldı.  
  
## <a name="insert-snippet"></a>Kod parçacığı Ekle  
 Aşağıdaki yordamlar nasıl erişileceğini açıklar **parçacık Ekle** komutu.  
  
> [!NOTE]
>  **Parçacık Ekle** komuttur ayrıca klavye kısayolunu (CTRL + K, ardından CTRL + X) kullanılabilir.  
  
#### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Kısayol menüsünden kod parçacığı eklemek için  
  
1.  XML kod parçacığı eklemek istediğiniz imleci getirin.  
  
2.  Sağ tıklayıp **parçacık Ekle**.  
  
     Kullanılabilir XML kod parçacıklarını listesi görüntülenir.  
  
3.  Fareyi kullanarak listeden veya kod parçacığı adını yazarak ve sekme veya ENTER tuşuna basarak bir kod parçacığı seçin.  
  
#### <a name="to-insert-snippets-using-the-intellisense-menu"></a>IntelliSense menüsünü kullanarak kod parçacığı eklemek için  
  
1.  XML kod parçacığı eklemek istediğiniz imleci getirin.  
  
2.  Gelen **Düzenle** menüsünde **IntelliSense**ve ardından **parçacık Ekle**.  
  
     Kullanılabilir XML kod parçacıklarını listesi görüntülenir.  
  
3.  Fareyi kullanarak liste veya kod parçacığı adını yazarak ve sekme veya ENTER tuşuna basarak bir kod parçacığı seçin.  
  
#### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Tam sözcük IntelliSense listesinde kod parçacığı eklemek için  
  
1.  XML kod parçacığı eklemek istediğiniz imleci getirin.  
  
2.  Dosyanıza eklemek istediğiniz XML kod parçacığı yazmaya başlayın. Otomatik tamamlama açıksa, IntelliSense tam sözcük listesi görüntülenir. Etkinleştirmek için CTRL + Ara çubuğu görünmüyorsa, basın.  
  
3.  XML kod parçacığı tam sözcük listeden seçin.  
  
4.  Sekme tuşuna basın, XML kod parçacığı çağırmak için SEKMESİNDE.  
  
> [!NOTE]
>  XML kod parçacığı çağrılmayacağı durumlar olabilir. Örneğin, eklemeye çalışırsanız bir `xs:complexType` öğesi içinde bir `xs:element` düğüm, düzenleyici XML kod parçacığı oluşturmaz. Olduğunda bir `xs:complexType` öğesi içinde kullanılan bir `xs:element` düğüm, düzenleyici eklemek için herhangi bir veri içermez gerekli öznitelikleri veya alt öğeleri, yoktur.  
  
#### <a name="to-insert-snippets-using-the-shortcut-name"></a>Kısayol adı kullanarak kod parçacığı eklemek için  
  
1.  XML kod parçacığı eklemek istediğiniz imleci getirin.  
  
2.  Tür `<` Düzenleyicisi bölmesinde.  
  
3.  Tam sözcük IntelliSense listesini kapatmak için ESC tuşuna basın.  
  
4.  Kod parçacığı kısayol adını yazın ve XML kod parçacığı çağırmak için SEKME tuşuna basın.  
  
## <a name="surround-with"></a>Şununla Çevrele  
 Aşağıdaki yordamlar nasıl erişileceğini açıklar **Surround With** komutu.  
  
> [!NOTE]
>  **Surround With** komuttur ayrıca klavye kısayolunu (CTRL + K, ardından CTRL + S) kullanılabilir.  
  
#### <a name="to-use-surround-with-from-the-context-menu"></a>Bağlam menüsünden çevrelemeyi kullanmak için  
  
1.  XML Düzenleyicisi'nde kapsamak için metni seçin.  
  
2.  Sağ tıklayıp **Surround With**.  
  
     XML kod parçacıklarını kullanılabilir çevreleyen listesi görüntülenir.  
  
3.  Fareyi kullanarak listeden veya kod parçacığı adını yazarak ve sekme veya ENTER tuşuna basarak bir kod parçacığı seçin.  
  
#### <a name="to-use-surround-with-from-the-intellisense-menu"></a>IntelliSense menüsünden çevrelemeyi kullanmak için  
  
1.  XML Düzenleyicisi'nde kapsamak için metni seçin.  
  
2.  Gelen **Düzenle** menüsünde **IntelliSense**ve ardından **Surround With**.  
  
     XML kod parçacıklarını kullanılabilir çevreleyen listesi görüntülenir.  
  
3.  Fareyi kullanarak listeden veya kod parçacığı adını yazarak ve sekme veya ENTER tuşuna basarak bir kod parçacığı seçin.  
  
## <a name="using-xml-snippets"></a>XML kod parçacıklarını kullanma  
 XML kod parçacığı seçtikten sonra metin kod parçacığının İmleç konumuna otomatik olarak eklenir. Kod parçacığı düzenlenebilir tüm alanlarda vurgulanır ve ilk düzenlenebilir bir alanı otomatik olarak seçilir. Şu anda seçili alanı Kutulu olmasıdır.  
  
 Bir alan seçildiğinde, alan için yeni bir değer yazabilirsiniz. Sekme döngüleri parçacığının düzenlenebilir alanlarından basarak; SHIFT + SEKME döngüleri bunları ters sırada tuşuna basın. Bir alana tıklayarak alana imleci koyar ve seçen bir alana çift tıklayın. Bir alan vurgulandığında, alanın açıklaması sunan bir araç ipucu görüntülenebilir.  
  
 Yalnızca ilk örneği, belirli bir alanın düzenlenebilir. Bu alan de vurgulandığında, bu alana diğer örneklerini özetlenmiştir. Düzenlenebilir bir alanın değerini değiştirdiğinizde, bu alan kod parçacığında kullanılan her yerde değiştirilir.  
  
 ENTER veya ESC tuşuna basarak alan düzenleme iptal eder ve düzenleyici normale döner.  
  
 Düzenlenebilir bir kod parçacığı alanlar için varsayılan renkleri, kod parçacığı alanı ayarı değiştirerek değiştirilebilir **yazı tipleri ve renkler** bölmesinde **seçenekleri** iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: değişiklik yazı tipleri ve renkler Düzenleyicisi'nde](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML kod parçacıkları](../xml-tools/xml-snippets.md)   
 [Nasıl yapılır: XML şemasından XML kod parçacığı oluşturma](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)   
 [Nasıl Yapılır: XML Kod Parçacıkları Oluşturma](../xml-tools/how-to-create-xml-snippets.md)



