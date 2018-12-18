---
title: Şablon dizin açıklaması (. Vsdir) dosyaları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67e2cf5dcb898614750aecd7e4fe997fbde0b5cc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938441"
---
# <a name="template-directory-description-vsdir-files"></a>Şablon Dizin Açıklaması (.Vsdir) Dosyaları
Bir şablon dizin açıklaması (.vsdir) tümleşik geliştirme ortamı (IDE) klasörleri, sihirbaz .vsz dosyasına ve iletişim kutularında projenizle ilişkili şablon dosyaları görüntülemek için etkinleştiren bir metin dosyası dosyasıdır. İçeriği, her dosya veya klasör için bir kayıt içerir. Tüm .vsdir dosyalarını başvurulan bir konumda, yalnızca bir .vsdir dosyası birden çok klasör, sihirbazlar veya şablon dosyalarını tanımlamak için genellikle bulunmakla birleştirilir.  

 Klasörleri (alt dizin) .vsdir dosya ve .vsdir dosyasında başvurulan dosyaların tümünü aynı dizinde bulunur. IDE ne zaman bir Sihirbazı çalıştıran veya bir klasörü veya dosyayı görüntüler **yeni proje** veya **Yeni Öğe Ekle** iletişim kutuları, IDE inceler .vsdir dosyanın olup olmadığını belirlemek için yürütülen dosyalarını içeren dizin mevcut. .Vsdir dosya bulunamazsa, IDE yürütülen veya görüntülenen bir klasör veya dosya için bir giriş içerip içermediğini belirlemek için okur. Bir giriş bulunması durumunda, IDE Sihirbazı yürütme veya içeriği görüntüleme bilgileri kullanır.  

 Aşağıdaki kod örneği SourceFiles.vsdir dosyasındandır içinde \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files kayıt defteri anahtarı:  

```  
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127  
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124  
```  

 Bu durumda, iki kayıt bir dosyasındadır. Her bir kayıt (satır başı karakteri) yeni bir satıra ayırır. Her satırı farklı bir dosya türü temsil eder. Bir kanal (&#124;) karakter her kayıttaki alanlar ayırır. Farklı dosya adlarına sahip birden çok .vsdir dosyalarını tek bir dizin içerebilir veya her dosya türü için bir .vsdir dosyası olabilir.  

## <a name="fields"></a>Alanlar  
 Aşağıdaki tabloda, her kayıt için belirtilen alanları listeler.  


| Alan | Açıklama |
| - | - |
| Göreli yol adını (RelPathName) | HeaderFile.h veya MyWizard.vsz gibi klasör, şablonu veya .vsz dosyasının adı. Bu alan ayrıca bir klasörü temsil etmek için kullanılan bir ad olabilir. |
| {clsidPackage} | VSPackage'nın uydu dinamik bağlantı kitaplığı (DLL) kaynakları LocalizedName, açıklama, IconResourceId ve SuggestedBaseName, gibi yerelleştirilmiş dizeler erişim sağlayan VSPackage GUİD'si. DLLPath sağlanmıyorsa IconResourceId geçerlidir. **Not:** bir veya daha önceki alanların bir kaynak tanımlayıcısı olmadığı sürece bu alan isteğe bağlıdır. Bu alan için metin yerelleştiriyor musunuz üçüncü taraf sihirbazlara karşılık gelen .vsdir dosyalarını genellikle boş bırakılır. |
| LocalizedName | Şablon dosyasında ya da Sihirbazı yerelleştirilmiş adı. Bu alan, "#ResID" formunun bir kaynak tanımlayıcısı veya bir dize olabilir. Bu ad görüntülenen **Yeni Öğe Ekle** iletişim kutusu. **Not:** LocalizedName olan bir kaynak tanımlayıcısı sonra {clsidPackage} gereklidir. |
| SortPriority | Bu şablon dosyasında ya da Sihirbazı göreli önceliğini temsil eden bir tamsayı. Bu öğe 1 değeri varsa, örneğin, ardından bu öğe 1 ve 2 veya daha büyük bir sıralama değeri olan tüm öğeleri önüne bir değere sahip diğer öğeleri yanında görüntülenir.<br /><br /> Öğeler aynı dizine göre sıralama önceliğe sahiptir. Aynı dizinde birden fazla .vsdir dosyası olabilir. Bu durumda, tüm öğeleri <em>.</em> vsdir dosyaları dizindeki birleştirilir. Aynı önceliğe sahip öğeler görüntülenen ad büyük/küçük harfe sözlük sırasına göre listelenir. `_wcsicmp` İşlevi öğeleri sıralamak için kullanılır.<br /><br /> .Vsdir dosyalarını açıklanmayan öğeler .vsdir dosyalarını içinde listelenen en yüksek öncelikli sayısından büyük bir öncelik numarası içerir. Bu öğelerin adlarına bağımsız olarak görüntülenen listeyi sonunda olduğundan sonucudur. |
| Açıklama | Şablon dosyasında ya da Sihirbazı yerelleştirilmiş açıklaması. Bu alan, "#ResID" formunun bir kaynak tanımlayıcısı veya bir dize olabilir. Bu dize görünür **yeni proje** veya **Yeni Öğe Ekle** öğesi seçildiğinde iletişim kutusu. |
| DLLPath veya {clsidPackage} | Şablon dosyasında ya da Sihirbazı için bir simge yüklemek için kullanılır. Simge IconResourceId kullanarak bir .dll veya .exe dosyasının dışına bir kaynak olarak yüklenir. Bu .dll veya .exe dosyasının tam yolu kullanarak ya da bir VSPackage GUİD'sini kullanarak belirlenebilir. VSPackage'ı DLL'SİNİN uygulama simgesini (değil uydu DLL) yüklemek için kullanılır. |
| IconResourceId | Uygulamada DLL veya VSPackage görüntülemek üzere simgeyi belirleyen DLL kaynak tanımlayıcısı. |
| Bayrakları (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>) | Devre dışı bırakmak veya etkinleştirmek için kullanılan **adı** ve **konumu** alanlarını **Yeni Öğe Ekle** iletişim kutusu. Değerini **bayrakları** gerekli bit bayrakları birleşimi ondalık denk bir alandır.<br /><br /> Bir kullanıcı seçtiğinde bir öğe üzerinde **yeni** sekmesi, proje belirler ad alanı ve konum alanı ne zaman gösterilip gösterilmeyeceğini **Yeni Öğe Ekle** iletişim kutusu ilk görüntülenir. Bir öğe .vsdir dosyası aracılığıyla, yalnızca öğe seçildiğinde alanları devre dışı etkin olup olmadığını denetleyebilirsiniz. |
| SuggestedBaseName | Dosya, sihirbaz veya şablonu varsayılan adını temsil eder. Bu, "#ResID" formunun bir kaynak tanımlayıcısı veya bir dize alanıdır. IDE, öğe için bir varsayılan ad sağlamak için bu değeri kullanır. Bu taban değer adı MyFile21.asp gibi benzersiz hale getirmek için bir tamsayı değeri olan eklenir.<br /><br /> Önceki listede açıklaması, DLLPath, IconResourceId, bayrakları ve SuggestedBaseNumber yalnızca şablon ve Sihirbazı dosyalar için geçerlidir. Bu alanlar klasörlere geçerli değildir. Bu olgu BscPrjProjectItems dosyasında kodda gösterilmiştir \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems kayıt defteri anahtarı. Bu dosya üç kayıtlarla (her klasör için bir tane) her kayıt için dört alan içerir: RelPathName, {clsidPackage} LocalizedName ve SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Sihirbaz dosyası oluşturduğunuzda, aşağıdaki sorunları dikkate almanız gereken.  

-   Kendisi için anlamlı veri bulunmayan gerekli olmayan alan yer tutucu olarak 0 (sıfır) içermelidir.  

-   Yerelleştirilmiş adı sağlanmazsa, göreli yol adı sihirbaz dosyasında kullanılır.  

-   DLLPath clsidPackage simge konumu için geçersiz kılar.  

-   Herhangi bir simge tanımlanmazsa, IDE yerine bu uzantıya sahip bir dosya için varsayılan simgeyi koyar.  

-   Önerilen taban adı verilmezse, 'Project' kullanılır.  

-   .Vsz dosyaları, klasörleri ve şablon dosyalarını silerseniz, aynı zamanda ilişkili kayıtlarını .vsdir dosyasından kaldırmanız gerekir.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Sihirbazlar](../../extensibility/internals/wizards.md)   
 [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)