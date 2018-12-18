---
title: Dosyalarda Bul komutu | Microsoft Docs
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
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5a278bb50af4488e9e627e884b20332717d6d0f8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256730"
---
# <a name="find-in-files-command"></a>Dosyalarda Bul Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Arama bulunan seçenekler kümesini kullanarak dosyaları **dosyalarda Bul** sekmesinde **Bul ve Değiştir** penceresi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Edit.FindinFiles findwhat [/case] [/ext:extensions]  
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]  
[/text2] [/wild|/regex] [/word]  
```  
  
## <a name="arguments"></a>Arguments  
 `findwhat`  
 Gerekli. Eşleştirilecek metin.  
  
## <a name="switches"></a>Anahtarlar  
 /Case veya /c  
 İsteğe bağlı. Eşleşme gerçekleşmesi yalnızca büyük ve küçük harfleri tam olarak belirtilen platformlarla eşleşen `findwhat` bağımsız değişken.  
  
 /ext: `extensions`  
 İsteğe bağlı. Aratılmak üzere dosyalar için dosya uzantılarını belirtir. Bir daha önce girildiyse belirtilmezse, önceki uzantıyı kullanılır.  
  
 /lookin: `searchpath`  
 İsteğe bağlı. Aranacak dizini. Yol boşluklar içeriyorsa, yolun tamamını tırnak içine alın.  
  
 /Names veya /n  
 İsteğe bağlı. Eşleşmeleri dosya adlarının bir listesini görüntüler.  
  
 / Options veya /t  
 İsteğe bağlı. Geçerli bulma seçeneği ayarları listesini görüntüler ve arama yapmaz.  
  
 /Regex veya /r  
 İsteğe bağlı. Önceden tanımlanmış özel karakterleri kullanan `findwhat` bağımsız değişken olarak sabit karakterleriyle yerine metin desenleri temsil eden gösterimler. Normal ifade karakterleri tam bir listesi için bkz. [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 Reset veya /e  
 İsteğe bağlı. Bulma seçenekleri varsayılan ayarlarına geri döndürür ve bir arama yapmaz.  
  
 / stop  
 İsteğe bağlı. Devam eden ise geçerli arama işlemini durdurur. Arama, diğer tüm bağımsız değişkenleri göz ardı eder, `/stop` belirtilmedi. Örneğin, geçerli aramayı durdurmak için aşağıdaki girmeniz gerekir:  
  
```  
>Edit.FindinFiles /stop  
```  
  
 / Sub seçeneklerini veya /s  
 İsteğe bağlı. Alt klasörleri içinde /lookin belirtilen dizin içinde arar:`searchpath` bağımsız değişken.  
  
 /text2 veya /2  
 İsteğe bağlı. Arama sonuçları Bul sonuçları 2 penceresinde görüntüler.  
  
 /wild veya/l  
 İsteğe bağlı. Önceden tanımlanmış özel karakterleri kullanan `findwhat` bağımsız değişken olarak bir karakter ya da dizi karakteri temsil etmek için gösterimler.  
  
 /Word veya /w  
 İsteğe bağlı. Yalnızca için tam sözcükleri arar.  
  
## <a name="example"></a>Örnek  
 Bu örnekte "My Visual Studio projeleri" klasöründe yer alan tüm .cls dosyalarında btnCancel arar ve eşleştirme Bilgisi Bul sonuçları 2 penceresinde görüntüler.  
  
```  
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dosyalarda Bul](../../ide/find-in-files.md)   
 [Komut penceresi](../../ide/reference/command-window.md)   
 [Bul/komut kutusu](../../ide/find-command-box.md)   
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)



