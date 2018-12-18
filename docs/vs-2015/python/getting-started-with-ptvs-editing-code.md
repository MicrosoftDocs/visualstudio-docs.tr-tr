---
title: 'PTVS kullanmaya Başlarken: kod düzenleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: ef0a84523a2d828e696fb50f641f392ab7bbd39f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265791"
---
# <a name="getting-started-with-ptvs-editing-code"></a>PTVS Kullanmaya Başlarken: Kodları Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS Python üretken Visual Studio Düzenleyicisi deneyimi sağlar.  
  
 Bu çok kısa yönergeleri izleyebilirsiniz [youtube video](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 Temel boş Python uygulaması proje şablonu ile başlayın.  
  
 Yazmaya başlayın bir `from … import` Düzenleyicisi'nde satır.  Açılır tamamlanma listesi olan içeri aktarma için kullanılabilir modüllerin tam listesini görürsünüz.  Bu liste, Python ve hangi sürümü göre farklılık gösterir, yüklediğiniz kitaplıkları.  Matematik kitaplığı, bir örnek olarak kullanabilirsiniz.  Karakterleri dahil olmak üzere öğelerle tamamlamaları filtrelerin listesini yazarken, yazdığınız fark edeceksiniz.  İçeri aktararak deyim tamamlama `sin` tanımlayıcısı.  
  
```python  
from math import sin  
  
```  
  
 İlişkisiz ancak Kitaplıklarınızı içinde bulunabilir tanımlayıcının kullanırsanız kodlama sırasında ihtiyacınız uygun içeri aktarma deyimi eklemek için açılan bir hızlı düzeltme PTVS sunar.  Örneğin, yazdığınız `cos`, gördüklerinizle sonra **alma matematik** sunulan.  
  
 Bir kod parçacığı, kod oluşturmak için kullanabilirsiniz.  Düzen menüsünün altında IntelliSense ve kod parçacığı Ekle'ı seçin.  Artık, Python ve ardından def olarak seçin  İşlev çağrısı `make_dot_string` ve bir parametre ekleyin `x`.  Dosyaya artık test odaklı geliştirme için Onaylamalar ekleyebilirsiniz ve PTVS tamamlanma listeleri yeni işlev zaten sunabilir bakın.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 Şimdi yeni işleve geri dönün ve aşağıdaki gövdesi yazmaya başlayın:  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 PTVS PTVS bu işleve yapılan çağrı siteleri incelediği parametresi bir tamsayıdır çünkü varsayar görürsünüz.   Hızlı düzeltme içeri aktarmak için kullanmanız gerekecektir `radians`.  
  
 Ana blok yazarak oluşturmak için başka bir kod parçacığı kullanın `main` en üst düzey, akıllı etiket UI çağırma ve kullanarak sekme "def ana..." seçmek için  Çağırmak için bir temel döngüsü yazma `make_dot_string`.  PTVS dönem tuşuna basın ve önerilen tamamlamaları bkz işlevi tarafından bir dize döndürür. bilir görürsünüz.  Bu tür bilgiler, programınızın tamamı akar, değerlerinizi düştüğünden her yerde sunabilmemiz araç ipuçları ve daha iyi yardımcı olacak tamamlamaları anlamak ve kodunuzu yazabilirsiniz.  
  
 Yazdırmak için bir çağrı ekleyin ve bir ana aşağıdakine benzer olmalıdır:  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 F5 tuşuna basarsanız, cmd.exe penceresinde kodu çalıştırır ve sürekli salınım yapan bir nokta görürsünüz.  
  
 Bu çok kısa yönergeleri izleyebilirsiniz [youtube video](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Wiki belgeleri](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [PTVS kullanmaya başlama ve kapsamlı videolar alma](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

