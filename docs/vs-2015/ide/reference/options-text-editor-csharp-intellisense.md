---
title: Seçenekler, metin düzenleyici, C#, IntelliSense | Microsoft Docs
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
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31c9909e5ea9364e806fdd2d7a39903bf1468abb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262177"
---
# <a name="options-text-editor-c-intellisense"></a>Seçenekler, Metin Düzenleyici, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Kullanım **IntelliSense** Visual C# için IntelliSense'in davranışını etkileyen ayarları değiştirmek için özellik sayfası. Erişebildiğiniz **IntelliSense** tıklayarak özellik sayfasını **seçenekleri** üzerinde **Araçları** menüsü, ardından **C#** içinde**Metin düzenleyici** klasörünü ve ardından **IntelliSense.**  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **IntelliSense** özellik sayfası, aşağıdaki özellikleri içerir:  
  
## <a name="completion-lists"></a>Tamamlanma listeleri  
 **Bir karakter girildikten sonra Tamamlama listesini göster**  
 Bu seçenek belirlendiğinde, yazmaya başladığınızda IntelliSense tamamlanma listesi otomatik olarak görüntüler. Bu seçenek seçilmezse, IntelliSense tamamlama hala kullanılabilir **IntelliSense** menüsünü veya CTRL + boşluk tuşlarına basarak.  
  
 **Anahtar sözcükleri tamamlama listelerine Yerleştir**  
 Bu seçenek belirlendiğinde, IntelliSense C# anahtar sözcükleri, örneğin, ekler [sınıfı](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), tamamlanma listesi.  
  
 **Kod parçacıklarını tamamlama listelerine Yerleştir**  
 Bu seçenek belirlendiğinde, IntelliSense, C# kod parçacıkları için diğer adlar tamamlanma listesine ekler. Kod parçacığı diğer ad olduğu bir anahtar sözcüğü ile aynı örneğin, durumda [sınıfı](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), anahtar sözcüğü kısayol tarafından değiştirilir. Daha fazla bilgi için [Visual C# kod parçacıkları](../../ide/visual-csharp-code-snippets.md).  
  
## <a name="selection-in-completion-lists"></a>Tamamlanma listeleri seçimi  
 **Aşağıdaki karakterleri yazarak işleyen:**  
 Bunlar yazılan sonra tamamlama listesinde seçilen öğe için IntelliSense otomatik tamamlama yürütülen tüm karakterleri belirtir.  
  
 **Boşluk çubuğuna basarak işlendi**  
 Seçili öğe için IntelliSense otomatik tamamlama tamamlanma listesine dâhil yürütmek için Ara çubuğuna basarak eylemi içermesini belirtir.  
  
 **Yeni bir satır eklemek, tam yazılmış kelimenin sonuna enter**  
 Tamamlama listesinde bir girişi tüm karakterleri yazdıktan sonra ENTER tuşuna basın, yeni bir satır otomatik olarak oluşturulur ve imleç yeni satıra taşır belirtir.  
  
 Örneğin, `else` ve ardından aşağıdaki Düzenleyicisi'nde belirir ENTER tuşuna basın:  
  
 `else`  
  
 `|` (imleç konumu)  
  
 Ancak, yalnızca yazarsanız `el` ve ardından aşağıdaki Düzenleyicisi'nde belirir ENTER tuşuna basın:  
  
 `else|` (imleç konumu)  
  
## <a name="intellisense-member-selection"></a>IntelliSense üye seçimi  
 **Öncesi seçer üye en son kullanılan**  
 Bu seçenek belirlendiğinde, IntelliSense, kısa süre önce geçerli oturumunuzu tümleşik geliştirme ortamında (IDE) sırasında otomatik nesne adı tamamlama açılır liste üyelerini kutusunda seçtiğiniz üyeleri önceden seçer. En son kullanılan üyeler geçmişi, her oturum IDE içindeki arasında temizlenir. Daha fazla bilgi için [son kullanılan üyeler için IntelliSense](../../misc/intellisense-for-most-recently-used-members.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel, ortam, Seçenekler iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md)   
 [XML belge açıklamaları](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [IntelliSense Kullanma](../../ide/using-intellisense.md)



