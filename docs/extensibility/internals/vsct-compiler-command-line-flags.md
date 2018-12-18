---
title: VSCT derleyici komut satırı bayrakları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0cdf74d0c6c77a2c7c22829c8aaa3e238e65703a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744882"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT Derleyici Komut Satırı Bayrakları
Visual Studio komut tablosu (VSCT) derleyici .vsct dosyaları başarılı derlenmesini sağlamak için komut satırı anahtarları sağlar.  
  
## <a name="command-line-parameters"></a>Komut satırı parametreleri  
 Temel VSCT Yardım görüntülemek için bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **komut** penceresinde gidin *Visual Studio SDK yükleme yolunu*\VisualStudioIntegration\Tools\Bin\ klasörü ve türü:  
  
```  
vsct /?  
```  
  
 Bu döndürür:  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indicate what additional include paths to send to the preprocessor  
  -L    Specify the language to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        followed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependency checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  Karakter - (dash) ve / (eğik çizgi) komut satırı parametrelerini belirten için kabul edilen iki gösterimdir.  
  
 Kabul edilebilir bayrakları ve bunların anlamı aşağıda verilmiştir.  
  
|Anahtar|Açıklama|  
|------------|-----------------|  
|-D|Ek tanımlı simgeleri belirtin.|  
|-I|Ek dosya başvuruları çözümlenirken kullanılacak yol eklemeyi gösterir.|  
|-L|Belirtin <xref:System.Globalization.CultureInfo> kültür adı, örneğin "en-US".|  
|-E|Yayma C# tarafından izlenen nesneleri komut öğeler için belirtilen ad alanı [C&#124;H&#124;N]:*filename*nerede C = C#, H C++ üst bilgi, N = ad alanı =. Ad alanı, C# için gereklidir.|  
|-v|Ayrıntılı çıkış.|  
  
 -L anahtar dizeler için karşılık gelen ikili .cto dosyasını oluşturmak için bir grup seçmek için derleyiciye belirtilen <xref:System.Globalization.CultureInfo> kültür adı. Bir veya daha fazla dil özniteliğinde belirtilen kültür adı eşleşmelidir [Strings öğesi](../../extensibility/strings-element.md) .vsct dosyası içinde. Strings öğesi hiçbir dil özniteliği varsa, içeren uyarıdan devralınır [CommandTable öğesi](../../extensibility/commandtable-element.md).  
  
 .Vsct dosyası birden çok dize öğesi olabilir ve her farklı bir dil özniteliği olabilir. Genelleştirme, birden çok kez VSCT derleyici çalıştıran ve her bir kültür adı için -M anahtarı değiştirerek elde edilir.  
  
 Dizeleri herhangi bir öğenin dil özniteliği -L anahtar tarafından belirtilen kültür adı ile eşleşmiyorsa, derleyici dil ve bölge eşleşecek şekilde çalışacaktır. Örneğin, "en-US" bulunamazsa derleyici "en" Bunun yerine çalışacaktır. Bu başarısız olursa, işletim sisteminin geçerli kültürü çalışacaktır. Bu başarısız olursa, bulduğu ilk olan Strings öğesi derlenir.  
  
 -E anahtar, komut tablosu tarafından kullanılan simgeler içeren C stili bir başlık dosyası yayma ya da komut simgelerinin nesneleri içeren bir C# dosyası yaymak için kullanılabilir.  
  
 -D ve - anahtarlar aynı ada sahip Cl.exe C önişlemcisi bayrakları sözdizimi vardır. -D X = Y biçimi tanımları XML tabanlı genişletilmesi için kullanılan \<tanımlanan > içinde testleri `Condition` öznitelikleri. -I yol eklemeyi çözümlemek için kullanılan \<Ekle >, \<Extern > ve \<bit eşlem > dosya başvuruları. Daha fazla bilgi için [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md).  
  
 VSCT derleyici, ayrıca önceden oluşturulmuş bir ikili dosya uygulayamaz. Bunu yapmak için ikili dosya kaynağı \<infile >.   İkili dosya VSCT derleyici tarafından üretilmişse, simge zaten eklenmiş olacaktır ve sembolik adları ile çıktı oluşturur bir \<sembolleri > çıkış bölümü. İkili CTC derleyici tarafından üretilmişse, çıkış gerçek GUID'leri ve kimlikleri içerir. Ctc.exe geçerli sürümleri tarafından üretilen *.ctsym dosya ikili giriş dosyasıyla aynı klasörde ise sembolleri bu dosyasından yüklenen ve çıktısı için kullanılacak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)   
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)