---
title: Visual C# kod parçacıkları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c06243b4f41919c1c51002f0ed805a3fbd67112
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49297420"
---
# <a name="visual-c-code-snippets"></a>Visual C# Kod Parçacıkları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod parçacıkları, kullanıma hazır, kodunuza hızla ekleyebilirsiniz kod parçacıkları verilmiştir. Örneğin, `for` oluşturur boş bir kod parçacığı `for` döngü. Bazı kod parçacıklarına, kod satırları seçmek etkinleştirmeniz ve sonra seçilen kod satırlarını içeren bir kod parçacığı surround-with kod parçacıkları, verilmiştir. Örneğin, ne zaman isterseniz kod satırlarını seçip ardından etkinleştirmek `for` kod parçacığı, oluşturur bir `for` Bu döngü bloğu içinde kod satırlarını içeren döngü. Kod parçacıkları kod yazma programını daha hızlı, kolay ve daha güvenilir hale getirebilirsiniz.  
  
 İmleç konumuna bir kod parçacığı Ekle ya da şu anda seçili olan kod etrafında surround-with kod parçacığını ekleyin. Kod parçacığı ekleyici aracılığıyla çağrılan **kod parçacığı Ekle** veya **Surround With** komutlarını **IntelliSense** menüsünden veya CTRL + K klavye kısayollarını kullanarak ve ardından X veya CTRL + K ve sonra S sırasıyla.  
  
 Kod parçacığı ekleyici tüm kullanılabilir kod parçacıkları için kod parçacığı adı görüntüler. Kod parçacığı ekleyici kod parçacığı veya bir kod parçacığı adı kısmını adını girebileceğiniz bir giriş iletişim kutusu da içerir. Kod parçacığı ekleyici en yakın eşleşme için kod parçacığı adı vurgulanır. Sekme tuşuna basarak istediğiniz zaman kod parçacığı ekleyici kapatmak ve şu anda seçili kod parçacığını ekleyin. ESC yazarak ya da Kod Düzenleyicisi'nde fareyle tıklamak kod parçacığı ekleyici bir kod parçacığı eklemeden kapatın.  
  
## <a name="default-code-snippets"></a>Varsayılan kod parçacıkları  
 Varsayılan olarak, Visual Studio'da aşağıdaki kod parçacıkları dahil edilir.  
  
|Adı (veya kısayol)|Açıklama|Kod parçacığını eklemek için geçerli konumları|  
|--------------------------|-----------------|---------------------------------------|  
|#if|Oluşturur bir [#if](http://msdn.microsoft.com/library/48cabbff-ca82-491f-a56a-eeccd528c7c2) yönergesi ve [#endif](http://msdn.microsoft.com/library/6a5fca55-5aee-441f-86f6-1c99fbe9ec05) yönergesi.|Herhangi bir yerde.|  
|#region|Oluşturur bir [#region](http://msdn.microsoft.com/library/672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4) yönergesi ve [#endregion](http://msdn.microsoft.com/library/16099660-91b2-49e5-9646-77f9ef069526) yönergesi.|Herhangi bir yerde.|  
|~|Kapsayan sınıfı için yok edici oluşturur.|Bir sınıf içinde.|  
|özniteliği|Türetilen bir sınıf için bir bildirim oluşturur <xref:System.Attribute>.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya yapı içinde.|  
|checked|Oluşturur bir [işaretli](http://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|sınıf|Bir sınıf bildirimi oluşturur.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya yapı içinde.|  
|ctor|Kapsayan sınıfı için bir oluşturucu oluşturur.|Bir sınıf içinde.|  
|cw|Bir çağrı oluşturur <xref:System.Console.WriteLine%2A>.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|do|Oluşturur bir [yapmak](http://msdn.microsoft.com/library/50725f79-9ba6-4898-aa78-6e331568a1bb) `while` döngü.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|else|Oluşturur bir [başka](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|enum|Oluşturur bir [enum](http://msdn.microsoft.com/library/bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c) bildirimi.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya yapı içinde.|  
|eşittir|Geçersiz kılan bir yöntem bildiriminde oluşturur <xref:System.Object.Equals%2A> içinde tanımlanan yöntem <xref:System.Object> sınıfı.|Bir sınıf veya yapı içinde.|  
|özel durum|Bir özel durumdan türetilen bir sınıf için bir bildirim oluşturur (<xref:System.Exception> varsayılan olarak).|Bir ad alanı (genel ad alanı dahil), bir sınıf veya yapı içinde.|  
|for|Oluşturur bir [için](http://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) döngü.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|foreach|Oluşturur bir [foreach](http://msdn.microsoft.com/library/5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec) döngü.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|forr|Oluşturur bir [için](http://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) bu azaltır, her yinelemeden sonra Döngü değişkeninin döngü.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|if|Oluşturur bir [varsa](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|Dizin Oluşturucu|Bir dizin oluşturucu bildirimi oluşturur.|Bir sınıf veya yapı içinde.|  
|arabirim|Oluşturur bir [arabirimi](http://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) bildirimi.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya yapı içinde.|  
|çağırma|Bir olay güvenli bir şekilde çağıran bir blok oluşturur.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|iterator|Bir yineleyici oluşturur.|Bir sınıf veya yapı içinde.|  
|iterindex|İç içe geçmiş bir sınıf kullanarak "adlı" bir yineleyici ve dizin oluşturucu çifti oluşturur.|Bir sınıf veya yapı içinde.|  
|lock|Oluşturur bir [kilit](http://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|mbox|Bir çağrı oluşturur <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. System.Windows.Forms.dll'e bir başvuru eklemeniz gerekebilir.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|ad alanı|Oluşturur bir [ad alanı](http://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) bildirimi.|(Genel ad alanı dahil) bir ad alanı içinde.|  
|prop|Oluşturur bir [otomatik uygulanan özellik](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) bildirimi.|Bir sınıf veya yapı içinde.|  
|propfull|Özellik bildiriminde get ile oluşturur ve erişimcileri ayarlayın.|Bir sınıf veya yapı içinde.|  
|propg|Salt okunur oluşturur [otomatik uygulanan özellik](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) ile özel bir "set" erişimcisi.|Bir sınıf veya yapı içinde.|  
|SIM|Oluşturur bir [statik](http://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[int](http://msdn.microsoft.com/library/212447b4-5d2a-41aa-88ab-84fe710bdb52) ana yöntem bildirimi.|Bir sınıf veya yapı içinde.|  
|struct |Oluşturur bir [yapı](http://msdn.microsoft.com/library/ff3dd9b7-dc93-4720-8855-ef5558f65c7c) bildirimi.|Bir ad alanı (genel ad alanı dahil), bir sınıf veya yapı içinde.|  
|svm|Oluşturur bir [statik](http://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[void](http://msdn.microsoft.com/library/0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4) ana yöntem bildirimi.|Bir sınıf veya yapı içinde.|  
|anahtarı|Oluşturur bir [geçiş](http://msdn.microsoft.com/library/44bae8b8-8841-4d85-826b-8a94277daecb) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|deneyin|Oluşturur bir [try-catch](http://msdn.microsoft.com/library/cb5503c7-bfa1-4610-8fc2-ddcd2e84c438) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|tryf|Oluşturur bir [try-finally](http://msdn.microsoft.com/library/c27623fb-7261-4464-862c-7a369d3c8f0a) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|unchecked|Oluşturur bir [denetlenmeyen](http://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|unsafe|Oluşturur bir [güvenli](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) blok.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
|kullanma|Oluşturur bir [kullanarak](http://msdn.microsoft.com/library/b42b8e61-5e7e-439c-bb71-370094b44ae8) yönergesi.|(Genel ad alanı dahil) bir ad alanı içinde.|  
|while|Oluşturur bir [sırada](http://msdn.microsoft.com/library/72a0765c-6852-4aca-b327-4a11cb7f5c59) döngü.|Bir yöntemi, bir dizin oluşturucu, bir özellik erişimcisi veya bir olay erişimcisi içinde.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod parçacığı işlevleri](../ide/code-snippet-functions.md)   
 [Kod parçacıkları](../ide/code-snippets.md)   
 [Nasıl yapılır: değişiklik ile yeni bir kod parçacığı oluşturma](http://msdn.microsoft.com/en-us/8d56d43c-097a-475b-aa85-cae1554b6338)   
 [Şablon parametreleri](../ide/template-parameters.md)   
 [Nasıl yapılır: Surround-with kod parçacıklarını kullanma](../ide/how-to-use-surround-with-code-snippets.md)   
 [Nasıl Yapılır: C# Yeniden Düzenleme Kod Parçacıklarını Geri Yükleme](../ide/how-to-restore-csharp-refactoring-snippets.md)



