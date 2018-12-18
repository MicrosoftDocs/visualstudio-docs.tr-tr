---
title: Biçim belirleyiciler c++ | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6634124e7dc0b50236a9fd6ff9c5c5388c3063bc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810526"
---
# <a name="format-specifiers-in-c"></a>C++ içindeki Biçim Belirticileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde bir değer görüntülenir biçimini değiştirebilirsiniz **Watch** penceresi biçim belirticilerini kullanma.  
  
 İçindeki Biçim belirticileri kullanabilirsiniz **hemen** penceresinde **komut** penceresinde ve hatta kaynak pencerelerinde. Bu pencereler içinde bir ifade üzerinde duraklarsanız, sonuç DataTip içinde görünür. DataTip görünen biçim belirticisini yansıtır.  
  
> [!NOTE]
>  Yeni bir hata ayıklama motoru değiştirildi ve Visual Studio yerel hata. Bu değişikliğin bir parçası olarak bazı yeni biçimli belirteçler eklendi eklenen ve bazı eskileri kaldırıldı. (Karışık özgün ve yönetilen) birlikte çalışabilirliği bunu yaptığınızda eski hata ayıklayıcı hala kullanılmaktadır hata ayıklamayı C + +/ CLI. Bu konudaki aşağıdaki bölümler her hata ayıklama altyapısı için biçim belirteçlerini gösterir.  
> 
> - [Biçim belirleyiciler](#BKMK_Visual_Studio_2012_format_specifiers) yeni hata ayıklama altyapısındaki biçim belirteçlerini açıklar.  
>   -   [Biçim belirleyiciler birlikte çalışma C + ile hata ayıklama için +/ CLI](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) eski hata ayıklama altyapısında biçimi Belirleyicileri açıklar.  
  
## <a name="using-format-specifiers"></a>Biçim belirticilerini kullanma  
 Aşağıdaki koda sahipseniz:  
  
```cpp  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Ekleme `my_var1` değişkenini **izleyin** penceresi (hata ayıklarken, **hata ayıklama / Windows / izleyin / izleyin 1**) ve görüntü onaltılığa ayarlayın (içinde **izleme** penceresinde değişkeni sağ tıklayıp **onaltılık gösterim**). Artık İzleme penceresinde 0x0065 değeri içerdiğini gösterir. Bir karakterin Biçim belirleyicisi bakın Ad sütununda bir tamsayı yerine bir karakter değişken adından sonra ifade bu değeri eklemek için **c**. **Değer** sütunu artık görünür ile **101 'e'**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
##  <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Biçim belirticileri  
 Aşağıdaki tablolarda, Visual Studio'da kullanabileceğiniz biçim tanımlayıcıları gösterilmektedir. Kalın yazılı tanımlayıcıları birlikte çalışma C + ile hata ayıklama için desteklenmez +/ CLI.  
  
|Belirleyici|Biçimi|Özgün izleme değeri|Görüntülenen değer|  
|---------------|------------|--------------------------|---------------------|  
|d|Ondalık tamsayı|0x00000066|102|  
|o|imzalanmamış sekizlik tamsayı|0x00000066|000000000146|  
|x<br /><br /> **h**|Onaltılık tamsayı|102|0xcccccccc|  
|X<br /><br /> **H**|Onaltılık tamsayı|102|0xCCCCCCCC|  
|c|tek karakter|0x0065, c|101 'e'|  
|s|const char * dizesini|\<konumu > "hello world"|"hello world"|  
|**sb**|const char * dizesini|\<konumu > "hello world"|Merhaba Dünya|  
|s8|const char * dizesini|\<konumu > "hello world"|"hello world"|  
|**s8b**|const char * dizesini|\<konumu > "hello world"|"hello world"|  
|Su|const wchar_t * const<br /><br /> char16_t\* dize|\<Konum > L "Merhaba Dünya"|L "Merhaba Dünya"<br /><br /> "hello world" u|  
|alt|const wchar_t * const<br /><br /> char16_t\* dize|\<Konum > L "Merhaba Dünya"|Merhaba Dünya|  
|bstr|BSTR dizesi|\<Konum > L "Merhaba Dünya"|L "Merhaba Dünya"|  
|**s32**|UTF-32 dize|\<konumu > "hello world" U|"hello world" U|  
|**s32b**|UTF-32 dize (tırnak işareti)|\<konumu > "hello world" U|Merhaba Dünya|  
|**tr**|enum|Saturday(6)|Cumartesi|  
|**hv**|İşaretçi türü - Denetlenmekte olan işaretçi değeri bir dizi yığın ayırma sonucunu örneğin olduğunu gösterir `new int[3]`.|\<Konum > {\<ilk üye >}|\<Konum > {\<ilk üye >, \<ikinci üye >,...}|  
|**na**|Bir işaretçinin bir nesne için bellek adresi bastırır.|\<Konum >, {üye = değer...}|{üye = değer...}|  
|**ND**|Türetilmiş sınıfları yok yalnızca temel sınıf bilgilerini görüntüler|`(Shape*) square` temel sınıf içerir ve türetilen sınıf bilgileri|Görüntüler, yalnızca sınıf bilgileri temel|  
|İK|HRESULT veya Win32 hata kodu. (Bu belirtici söz konusu durumlarda gerekli değil için hata ayıklayıcı artık HRESULTs otomatik olarak çözer.|S_OK|S_OK|  
|WC|Pencere sınıfı bayrağı|0x0010|WC_DEFAULTCHAR|  
|WM|Windows ileti numaraları|16|WM_CLOSE KOMUTU|  
|!|herhangi bir veri türü görünümü özelleştirmelerini yok sayan, ham biçim|\<gösterim özelleştirilmiş >|4|  
  
> [!NOTE]
>  Zaman **hv** Biçim belirleyicisi varsa, hata ayıklayıcı arabellek uzunluğunu belirlemek ve uygun öğelerin sayısını görüntülemek çalışır. Her zaman bir dizinin tam arabellek boyutunu bulmak hata ayıklayıcının mümkün olmadığı için belirleyici Boyutlandır kullanması gereken `(pBuffer,[bufferSize])` mümkün olduğunda. **Hv** biçim belirticisi, arabellek boyutu kullanılabilir olduğu senaryoları için tasarlanmıştır  
  
###  <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Diziler olarak işaretçiler için tanımlayıcılar boyutlandırın  
 Bir dizi olarak görüntülemek istediğiniz bir nesne işaretçiniz varsa, dizi öğelerinin sayısını belirtmek için bir tamsayı ya da bir ifade kullanabilirsiniz:  
  
|Belirleyici|Biçimi|Özgün Watch Valuen|Görüntülenen değer|  
|---------------|------------|---------------------------|---------------------|  
|n|Ondalık veya **onaltılık** tamsayı|pBuffer, [32]<br /><br /> pBuffer,**[0x20]**|Görüntüler `pBuffer` 32 öğe dizisi olarak.|  
|**[exp]**|Bir tamsayı olarak değerlendirir. geçerli bir C++ ifadesi.|pBuffer, [bufferSize]|Bir dizisi olarak pBuffer görüntüler `bufferSize` öğeleri.|  
|**expand(n)**|Geçerli bir tamsayı olarak değerlendirir bir C++ ifadesi|pBuffer, expand(2)|Üçüncü öğesine görüntüler  `pBuffer`|  
  
##  <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Biçim belirleyiciler birlikte çalışma C + ile hata ayıklama için +/ CLI  
 Belirleyicilerde **kalın** yalnızca yerel ve C + hata ayıklama için destekleniyor +/ CLI kodu.  
  
|Belirleyici|Biçimi|Özgün izleme değeri|Görüntülenen değer|  
|---------------|------------|--------------------------|---------------------|  
|**d, ı**|imzalanmış ondalık tamsayı|0xF000F065|-268373915|  
|**u**|imzalanmamış ondalık tamsayı|0x0065|101|  
|o|imzalanmamış sekizlik tamsayı|0xF065|0170145|  
|x, X|Onaltılık tamsayı|61541|0x0000f065|  
|**m, s**|uzun veya kısa önek: d, i, u, o, x, X|00406042|0x0c22|  
|**f**|imzalanmış kayan nokta|(3./2.), f|1.500000|  
|**e**|imzalanmış bilimsel gösterim|(3.0/2.0)|1.500000e+000|  
|**g**|imzalanan kayan nokta veya imzalanmış bilimsel gösterim, hangisi daha kısaysa|(3.0/2.0)|1,5|  
|c|tek karakter|\<Konum >|101 'e'|  
|s|const char *|\<Konum >|"hello world"|  
|Su|const wchar_t*<br /><br /> const char16_t\*|\<Konum >|L "Merhaba Dünya"|  
|alt|const wchar_t*<br /><br /> const char16_t\*|\<Konum >|Merhaba Dünya|  
|s8|const char *|\<Konum >|"hello world"|  
|İK|HRESULT veya Win32 hata kodu. (Bu belirtici söz konusu durumlarda gerekli değil için hata ayıklayıcı artık HRESULTs otomatik olarak çözer.|S_OK|S_OK|  
|WC|Pencere sınıfı bayrağı.|0x00000040,|WC_DEFAULTCHAR|  
|WM|Windows ileti numaraları|0x0010|WM_CLOSE KOMUTU|  
|!|herhangi bir veri türü görünümü özelleştirmelerini yok sayan, ham biçim|\<gösterim özelleştirilmiş >|4|  
  
###  <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Biçim belirleyiciler bellek konumları'birlikte çalışma'C + ile hata ayıklama +/ CLI  
 Aşağıdaki tablo, bellek konumları için kullanılan biçimlendirme simgeleri bulunmaktadır. Herhangi bir değer veya konumu değerlendiren bir ifade ile bellek konumu belirleyici kullanabilirsiniz.  
  
|Sembol|Biçimi|Özgün izleme değeri|Görüntülenen değer|  
|------------|------------|--------------------------|---------------------|  
|**ma**|64 ASCII karakteri|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|  
|**m**|ardından 16 ASCII karakter, onaltılık biçimde 16 bayt|0x0012ffac|0X0012FFAC B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00.... 4... 0 ". 0W &...|  
|**mb**|ardından 16 ASCII karakter, onaltılık biçimde 16 bayt|0x0012ffac|0X0012FFAC B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00.... 4... 0 ". 0W &...|  
|**mw**|8 sözcükler|0x0012ffac|0X0012FFAC 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**MD**|4 doublewords|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**mq**|2 quadwords|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|2-bayt karakter (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
###  <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Birlikte çalışma'C + ile hata ayıklama diziler olarak işaretçiler için belirleyici Boyutlandır +/ CLIt  
 Bir dizi olarak görüntülemek istediğiniz bir nesne işaretçiniz varsa, dizi öğelerinin sayısını belirtmek için bir tamsayı kullanabilirsiniz:  
  
|Belirleyici|Biçimi|İfade|Görüntülenen değer|  
|---------------|------------|----------------|---------------------|  
|n|Ondalık tamsayı|pBuffer [32]|Görüntüler `pBuffer` 32 öğe dizisi olarak.|





