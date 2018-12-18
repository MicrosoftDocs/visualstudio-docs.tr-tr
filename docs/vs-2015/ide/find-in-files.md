---
title: Dosyalarda Bul | Microsoft Docs
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
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4529b44014b209bdef1fc919ac413b61d77407c1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902145"
---
# <a name="find-in-files"></a>Dosyalarda Bul
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Find dosyalar ** belirtilen bir dosya kümesi aramanıza olanak sağlar. Eşleşme bulundu ve gerçekleştirilen eylemler listelenen **sonuçları Bul** seçili penceresi **neden seçenekleri**.  
  
 Görüntülemek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz **dosyalarda Bul** içinde **Bul ve Değiştir** penceresi.  
  
### <a name="to-display-find-in-files"></a>Dosyalarda Bul görüntülemek için  
  
1. Menü çubuğunda, **Düzenle**, **Bul ve Değiştir**.  
  
2. Seçin **dosyalarda Bul**.  
  
   Bulma işlemi iptal etmek için CTRL + BREAK tuşlarına basın.  
  
> [!NOTE]
>  Bul ve Değiştir araç dizinlerle aramaz `Hidden` veya `System` öznitelik kümesi.  
  
## <a name="find-what"></a>Sonrakini Bul  
 Yeni metin dizesi veya ifadesi için arama yapmak için kutuya belirtin. Herhangi biri için en son Aranan 20 dizeleri aramak için listeyi açın ve arama yapmak istediğiniz dizesi seçin. Bitişik seçin **ifade oluşturucu** bir veya daha fazla normal ifadeler, arama dizesinde kullanmak istiyorsanız düğmesi. Daha fazla bilgi için [Visual Studio'da normal ifadeler kullanarak](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="look-in"></a>İçine bak  
 Seçilen seçeneği **konum** açılır listede belirler olmadığını **dosyalarda Bul** aramaları yalnızca şu anda etkin dosyalar veya belirli klasörlerde depolanan tüm dosyalar. Listeden bir arama kapsamı seçin veya **Gözat (...)**  görüntülemek için düğmeyi **arama klasörlerini Seç** iletişim kutusu ve kendi dizinlerinin girin. Doğrudan bir yolu da yazabilirsiniz **konum** kutusu.  
  
> [!WARNING]
>  İle **çözümün tamamında** veya **geçerli proje** seçenekleri, proje ve çözüm dosyaları değil aranır. Proje dosyalarında aramak istiyorsanız, bir arama klasörü seçin.  
  
> [!NOTE]
>  Varsa **konum** seçeneğe kullanıma kaynak kod denetiminden yalnızca yerel makinenize indirilen dosyanın sürüm aranır dosya arama neden olur.  
  
## <a name="include-subfolders"></a>Alt klasörleri dahil et  
 Belirtir, alt **konum** klasörü aranır.  
  
## <a name="find-options"></a>Bulma seçenekleri  
 Genişlet veya daralt **bulma seçeneklerini** bölümü. Aşağıdaki seçenekler seçilen veya temizlenen:  
  
 Büyük küçük harf duyarlı  
 Seçili olduğunda, bir **sonuçları Bul** arama büyük/küçük harfe olacaktır  
  
 Bütün kelimeyi eşleştir  
 Bu onay kutusu seçildiğinde, **sonuçları Bul** windows yalnızca tam sözcük eşleşmeleri döndürür.  
  
 Normal ifadeleri kullanma  
 Bu onay kutusunu seçtiyseniz, özel gösterimler ile eşleşen metnin desenleri tanımlamak için kullanabilirsiniz **Aranan** veya **değiştirin** metin kutuları. Bu gösterimler listesi için bkz. [Visual Studio'da normal ifadeler kullanarak](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Bu dosya türlerini Ara  
 Bu liste içinde arama yapmak dosya türlerini gösterir **konum** dizinleri. Bu alanı ise boş, tüm dosyaların **konum** dizinler aranır.  
  
 Listede bu belirli türlerin dosyaları bulursunuz bir önceden yapılandırılmış bir arama dizesi girin herhangi bir öğeyi seçin.  
  
## <a name="result-options"></a>Sonuç seçenekleri  
 Genişlet veya daralt **neden seçenekleri** bölümü. Aşağıdaki seçenekler seçilen veya temizlenen:  
  
 1 sonuçları Bul penceresi  
 Bu onay kutusu seçildiğinde, geçerli arama sonuçları içeriğini değiştirin **Bul sonuçları 1** penceresi. Bu pencere, arama sonuçlarını görüntülemek için otomatik olarak açılır. El ile bu pencereyi açmak için seçmeniz **diğer Windows** gelen **görünümü** menü ve **Bul sonuçları 1**.  
  
 2 sonuçları Bul penceresi  
 Bu onay kutusu seçildiğinde, geçerli arama sonuçları içeriğini değiştirin **Bul sonuçları 2** penceresi. Bu pencere, arama sonuçlarını görüntülemek için otomatik olarak açılır. El ile bu pencereyi açmak için seçmeniz **diğer Windows** gelen **görünümü** menü ve **Bul sonuçları 2**.  
  
 Sadece dosya adlarını görüntüler  
 Arama görüntüleme kendilerini eşleşen yerine arama içeren dosyaların bir listesini görüntüler eşleşir.  
  
 Sonuçları sona Ekle  
 Arama sonuçları önceki arama sonuçlarına ekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)   
 [Dosyalarda Değiştir](../ide/replace-in-files.md)   
 [Visual Studio Komutları](../ide/reference/visual-studio-commands.md)



