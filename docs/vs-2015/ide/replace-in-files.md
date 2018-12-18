---
title: Dosyalarda Değiştir | Microsoft Docs
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
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 92029377d5e7d4faf4c6b7f38deda1eecdeaa395
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228832"
---
# <a name="replace-in-files"></a>Dosyalarda Değiştir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dosyaları ** Değiştir, belirtilen kümenin dize veya ifade için dosyaları, kod arama ve bazılarını veya tümünü eşleştirmeler değiştirmek sağlar. Eşleşme bulundu ve gerçekleştirilen eylemler listelenen **sonuçları Bul** seçili penceresi **neden seçenekleri**.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden içeri ve dışarı aktarma ayarları seçin. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Görüntülemek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz **dosyalarda Değiştir** içinde **Bul ve Değiştir** penceresi.  
  
### <a name="to-display-replace-in-files"></a>Dosyalarda Değiştir görüntülemek için  
  
1.  Üzerinde **Düzenle** menüsünü genişletin **Bul ve Değiştir**.  
  
2.  Seçin **dosyalarda Değiştir**.  
  
     — veya —  
  
     Varsa **Bul ve Değiştir** penceresinde zaten açıkken, araç çubuğunda, seçin **dosyalarda Değiştir**.  
  
## <a name="find-what"></a>Sonrakini Bul  
 Yeni metin dizesi veya ifadesi için arama yapmak için kutuya belirtin. Herhangi biri için en son Aranan 20 dizeleri aramak için listeyi açın ve arama yapmak istediğiniz dizesi seçin. Bitişik seçin **ifade oluşturucu** bir veya daha fazla normal ifadeler, arama dizesinde kullanmak istiyorsanız düğmesi. Daha fazla bilgi için [Visual Studio'da normal ifadeler kullanarak](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="replace-with"></a>Değiştirin  
 Dizede örneklerini değiştirmek için **Aranan** kutusuna başka bir dizeyle, değiştirme dizesinde girin **konan** kutusu. Dizede örneklerini silmek için **Aranan** kutusunda, bu alanı boş bırakın. Kendisi için en son Aranan 20 dizelerini listeyi açın. Bitişik seçin **ifade oluşturucu** bir veya daha fazla normal ifadeler, değiştirme dizesinde kullanmak istiyorsanız düğmesi. Daha fazla bilgi için [Visual Studio'da normal ifadeler kullanarak](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="look-in"></a>İçine bak  
 Seçilen seçeneği **konum** açılır listede belirler olmadığını **dosyalarda Değiştir** arar yalnızca şu anda etkin dosyalarda veya belirli klasörlerde depolanan tüm dosyaları arar. Listeden bir arama kapsamı seçin, bir klasör yolunu yazın veya tıklayın **Gözat (...)**  görüntülemek için düğmeyi **arama klasörlerini Seç** iletişim kutusu ve aranacak klasörler kümesi seçin. Doğrudan bir yolu da yazabilirsiniz **konum** kutusu.  
  
> [!NOTE]
>  Varsa **konum** seçeneğe kullanıma kaynak kod denetiminden yalnızca yerel makinenize indirilen dosyanın sürüm aranır dosya arama neden olur.  
  
## <a name="find-options"></a>Bulma seçenekleri  
 Genişlet veya daralt **bulma seçeneklerini** bölümü. Aşağıdaki seçenekler seçilen veya temizlenen:  
  
 Büyük küçük harf duyarlı  
 Bu onay kutusu seçildiğinde, **sonuçları Bul** windows örneklerini görüntüler yalnızca **Aranan** hem içeriği hem çalışması eşleşen bir dize. Örneğin, "MyObject" ile arama **eşleşen servis talebi** seçili olacak "MyObject" ancak "myobject" veya "MYOBJECT." döndürür  
  
 Bütün kelimeyi eşleştir  
 Bu onay kutusu seçildiğinde, **sonuçları Bul** windows örneklerini görüntüler yalnızca **Aranan** tam sözcükleri eşleşen bir dize. Örneğin, "MyObject" Ara "MyObject" ancak "CMyObject" veya "MyObjectC." döndürür  
  
 Normal ifadeleri kullanma  
 Bu onay kutusu işaretli olduğunda özel gösterimler metin desenleri tanımlamak için kullanabileceğiniz **Aranan** veya **değiştirin** metin kutuları. Bu gösterimler listesi için bkz. [Visual Studio'da normal ifadeler kullanarak](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Bu dosya türlerini Ara  
 Bu liste içinde arama yapmak dosya türlerini gösterir **konum** dizinleri. Bu alan bırakılırsa blank, tüm dosyaların **konum** dizinler aranır.  
  
 Listede bu belirli türlerin dosyaları bulursunuz bir önceden yapılandırılmış bir arama dizesi girin herhangi bir öğeyi seçin.  
  
## <a name="result-options"></a>Sonuç seçenekleri  
 Genişlet veya daralt **neden seçenekleri** bölümü. Aşağıdaki seçenekler seçilen veya temizlenen:  
  
 Bul sonuçları 1 penceresi  
 Bu onay kutusu seçildiğinde, geçerli arama sonuçları içeriğini değiştirin **Bul sonuçları 1** penceresi. Bu pencere, arama sonuçlarını görüntülemek için otomatik olarak açılır. El ile bu pencereyi açmak için seçmeniz **diğer Windows** gelen **görünümü** menü ve **Bul sonuçları 1**.  
  
 Sonuçları 2 pencereyi Bul  
 Bu onay kutusu seçildiğinde, geçerli arama sonuçları içeriğini değiştirin **Bul sonuçları 2** penceresi. Bu pencere, arama sonuçlarını görüntülemek için otomatik olarak açılır. El ile bu pencereyi açmak için seçmeniz **diğer Windows** gelen **görünümü** menü ve **Bul sonuçları 2**.  
  
 Sadece dosya adlarını görüntüler  
 Bu onay kutusu seçildiğinde, sonuçları Bul windows tam adlarını ve yollarını arama dizesini içeren tüm dosyaları listeler. Ancak, sonuç dize bulunduğu kod satırının dahil değildir. Bu onay kutusu yalnızca dosyalarda bulma için kullanılabilir.  
  
 Değiştirilen dosyaları açık sonra Tümünü Değiştir tut  
 Seçili olduğunda, tüm dosyaları geri alma veya değişiklikleri kaydetmek için değişiklik yapılmıştır açık kalır. Bellek kısıtlamaları değiştirme işleminden sonra açık kalabilir dosyalarının sayısını sınırlayabilir.  
  
> [!CAUTION]
>  Kullanabileceğiniz **geri** düzenleme için açık kalması dosyaları. Bu seçenek seçilmezse düzenleme kapalı, kalacak için zaten bulunmayan dosyaları açmak ve hiçbir **geri** seçeneği kullanılabilir bu dosyaları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)   
 [Dosyalarda Bul](../ide/find-in-files.md)   
 [Visual Studio Komutları](../ide/reference/visual-studio-commands.md)



