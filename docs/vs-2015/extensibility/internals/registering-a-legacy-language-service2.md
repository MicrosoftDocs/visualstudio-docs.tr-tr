---
title: Bir eski dil hizmeti kaydetme2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c9077ca36a560c51ec8f8455cc04fb2fe9ba09eb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803662"
---
# <a name="registering-a-legacy-language-service"></a>Eski dil hizmeti kaydediliyor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıdaki bölümlerde kayıt defteri girdilerinin listesi çeşitli dil için kullanılabilir hizmet seçenekleri sağlanır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Kayıt defteri girdileri aşağıdaki listedeki *VS Reg kök* hkey_local_machıne\software\microsoft\visualstudio için eşittir\\*X.Y*burada *X.Y* olduğu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sürüm numarası.  
  
## <a name="registry-entries-for-language-service-options"></a>Dil hizmeti seçenekleri için kayıt defteri girişleri  
 *VS Reg kök*\Languages\Language Hizmetleri\\*dil adı* anahtarı, aşağıdaki değerleri içerebilir.  
  
|Ad|Tür|Aralık|Açıklama|  
|----------|----------|-----------|-----------------|  
|(Varsayılan)|REG_SZ|*\<GUID &GT;*|Dil hizmeti GUİD'si.|  
|LangResID|REG_DWORD|0x0 0xffff|Dil yerelleştirilmiş metin adı için kaynak tanımlayıcısı (ResID) dize.|  
|Paket|REG_SZ|*\<GUID &GT;*|VSPackage'ı GUİD'si.|  
|ShowCompletion|REG_DWORD|0-1|Belirtir olup olmadığını **deyim tamamlama** seçeneklerini **seçenekleri** iletişim kutusu etkinleştirilir.|  
|ShowSmartIndent|REG_DWORD|0-1|Belirtir olup olmadığını belirleme seçeneği **akıllı** , girintilendirme **seçenekleri** iletişim kutusu etkin.|  
|RequestStockColors|REG_DWORD|0-1|Belirtir olup özel veya varsayılan renkler, renk anahtar sözcükler için kullanılır.|  
|ShowHotURLs|REG_DWORD|0-1|URL'leri kullanıcının tıklayabileceği olup olmadığını belirtir.|  
|Etkin olmayan URL'ler için varsayılan|REG_DWORD|0-1|İlk ayarını belirtir **etkinleştirme tek tıkla URL gezinmesini** seçeneğini **seçenekleri** iletişim kutusu.|  
|DefaultToInsertSpaces|REG_DWORD|0-1|Dil hizmeti "kendi varsayılan sekme seçeneği boşluklar Ekle" olup olmadığını belirtir.|  
|ShowDropdownBarOption|REG_DWORD|0-1|Etkinleştirir veya devre dışı bırakır **gezinti çubuğu** seçeneğini **seçenekleri** gösterir veya gizler iletişim kutusu **gezinti çubuğu**.|  
|Yalnızca tek bir kod penceresi|REG_DWORD|0-1|Etkinleştirir veya devre dışı bırakır **yeni pencere** içindeki seçim **penceresi** dil hizmeti menüsü.|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|Etkinleştirir veya devre dışı bırakan bir **seçenekleri** iletişim kutusu ayarını **Gelişmiş üyeleri Gizle**.|  
|Destek CF_HTML|REG_DWORD|0-1|Düzenleyicide HTML veri kopyalama ve yapıştırma sağlayan belirtir.|  
|EnableLineNumbersOption|REG_DWORD|0-1|Belirtir olup olmadığını **satır numaraları** seçeneklerini **seçenekleri** iletişim kutusu, bir dil hizmeti için etkinleştirildi.|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Gelişmiş üyeler gibi özel alanları tamamlama listelerine gizlenip gizlenmeyeceğini belirtir.|  
|ShowBraceCompletion|REG_DWORD|0-1|Belirtir olup olmadığını **ayraç tamamlama** seçeneğini **seçenekleri** iletişim kutusu etkin.|  
  
### <a name="example"></a>Örnek  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## <a name="registry-entries-for-debugger-languages-options"></a>Hata ayıklayıcısı dil seçenekleri için kayıt defteri girişleri  
 *VS Reg kök*\Languages\Language Hizmetleri\\*dil adı*\Debugger dilleri\\*GUID*\ anahtarı, aşağıdakileri içerebilir değerler.  
  
|Ad|Tür|Aralık|Açıklama|  
|----------|----------|-----------|-----------------|  
|(Varsayılan)|REG_SZ|metin|Varsayılan değer, dilin adını belge için kullanılabilir. Bu anahtarın adını karşılık gelen bir giriş olan, ifade değerlendiricisi GUID'dir  *\<VS Reg kök >* \AD7Metrics\Expression değerlendiricisi.|  
  
### <a name="example"></a>Örnek  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## <a name="registry-entries-for-editor-tools-options"></a>Düzenleyici araç seçenekleri için kayıt defteri girişleri  
 Özellik sayfaları ve özelliği düğümü için EditorToolsOptions anahtarı altındaki kayıt defteri anahtarlarını ekleyebilirsiniz. Özellik Sayfaları'nda bu anahtarları ve değerlerini tanımlamak **seçenekleri** iletişim kutusu (üzerinde **Araçları** menüsü) dil hizmeti yapılandırmak için kullanılır. Aşağıdaki örnekte, *sayfa adı* bir özellik sayfası adıdır ve *düğüm adı* ağaçta bir düğümün adını açıktır **seçenekleri** iletişim kutusu. Sayfa ve düğüm girdileri ayrı olarak belirtilmelidir.  
  
|Ad|Tür|Aralık|Açıklama|  
|----------|----------|-----------|-----------------|  
|(Varsayılan)|REG_SZ|resID|Bu seçenek sayfada yerelleştirilmiş görünen adı. Ad metin veya # olabilir`nnn`burada `nnn` uydu DLL'deki belirtilen VSPackage'ı, bir dize kaynak kimliği.|  
|Paket|REG_SZ|*GUID*|Bu seçenekler sayfası uygulayan VSPackage GUİD'si.|  
|Sayfa|REG_SZ|*GUID*|VSPackage'ı çağırarak istemek için GUID özellik sayfasının <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> yöntemi. Bu kayıt defteri girişi mevcut değilse, kayıt defteri anahtarı bir düğüm, bir sayfa açıklar.|  
  
### <a name="example"></a>Örnek  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## <a name="registry-entries-for-file-name-extension-options"></a>Dosya adı uzantısı seçenekleri için kayıt defteri girişleri  
 Dosya uzantısı için giriş, örneğin ".myext" başında nokta içermelidir.  
  
|Ad|Tür|Aralık|Açıklama|  
|----------|----------|-----------|-----------------|  
|(Varsayılan)|REG_SZ|*GUID*|Bu dosya adı uzantısı türü için varsayılan dil hizmeti için hizmet GUID'si.|  
  
### <a name="example"></a>Örnek  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Düzenleyici seçenekleri için kayıt defteri girişleri  
 *VS Reg kök*\Editors anahtarı, aşağıdaki değerleri içerebilir:  
  
|Ad|Tür|Aralık|Açıklama|  
|----------|----------|-----------|-----------------|  
|(Varsayılan)|REG_SZ|""|Kullanılmayan; uygulamanızın adını buraya belgeleri koyabilirsiniz.|  
|DefaultToolboxTab|REG_SZ|""|Düzenleyici etkin olduğunda varsayılan hale getirmek için araç kutusu sekmesi adı.|  
|displayName|REG_SZ|resID|Görüntülenecek ad **birlikte Aç** iletişim kutusu. Adı dize kaynak kimliği veya adı standart biçimindedir.|  
|ExcludeDefTextEditor|REG_DWORD|0-1|İçin kullanılan **birlikte Aç** menü komutu. Belirli bir dosya türü için kullanılabilir düzenleyicilerin listesini varsayılan metin düzenleyicisinde listelemek istemiyorsanız bu değeri 1 olarak ayarlayın.|  
|LinkedEditorGUID|REG_SZ|*\<GUID &GT;*|Bir dosya ile kod sayfası destek açabilirsiniz herhangi bir dil hizmeti için kullanılır. Örneğin, açtığınızda, bir .txt dosyasına kullanarak **birlikte Aç** komut seçenekleri kodlama olmadan ve Kaynak Kod Düzenleyicisi'ni kullanarak için sağlanır.<br /><br /> Alt adını belirtilen için kod düzenleyici fabrikası GUID'idir; Bu belirli kayıt defteri girdisi bağlı normal Düzenleyici fabrikası için GUID'dir. Bu giriş amacı, IDE varsayılan Düzenleyicisi'ni kullanarak bir dosya açılmazsa, IDE listesinde sonraki Düzenleyicisi'ni kullanmayı deneyin. Bu düzenleyici fabrikası temelde başarısız Düzenleyici fabrikası ile aynı olduğu için bu sonraki Düzenleyicisi Kod Düzenleyici fabrikası olmamalıdır.|  
|Paket|REG_SZ|*\<GUID &GT;*|Görünen ad ResID VSPackage GUİD'i.|  
  
### <a name="example"></a>Örnek  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## <a name="registry-entries-for-logical-view-options"></a>Mantıksal görünüm seçenekleri için kayıt defteri girişleri  
 *VS Reg kök*\Editors\\*Düzenleyicisi GUI >* \LogicalViews anahtarı, aşağıdaki değerleri içerebilir.  
  
|Ad|Tür|Aralık|Açıklama|  
|----------|----------|-----------|-----------------|  
|(Varsayılan)|REG_SZ||Kullanılmayan.|  
|*\<GUID &GT;*|REG_SZ|""|Desteklenen mantıksal görünümleri anahtarı. Gereksinim duyduğunuz kadar bu olabilir. Önemli, kayıt defteri girişini adıdır her zaman boş bir dize değil değeri.|  
  
### <a name="example"></a>Örnek  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## <a name="registry-entries-for-editor-extension-options"></a>Düzenleyici uzantısı seçenekleri için kayıt defteri girişleri  
 *VS Reg kök*\Editors\\*Düzenleyici GUİD'i*\Extensions anahtarı, aşağıdaki değerleri içerebilir. Başında nokta dosya adı uzantısı içermez.  
  
|Ad|Tür|Aralık|Açıklama|  
|----------|----------|-----------|-----------------|  
|(Varsayılan)|REG_SZ||Kullanılmayan.|  
|*\<ext >*|REG_DWORD|0 0xffffffff|Uzantıları göreli önceliğini. İki veya daha fazla dil aynı uzantı paylaşıyorsanız, daha yüksek öncelikli dil seçilir.|  
  
 Ayrıca, bir düzenleyici için geçerli kullanıcının varsayılan seçimi HKEY_Current_User\Software\Microsoft\VisualStudio içinde depolanan\\*X.Y*\Default düzenleyicileri\\*ext*. Seçilen dil hizmeti özel girişi GUID'dir. Bu, geçerli kullanıcının önceliklidir.  
  
### <a name="example"></a>Örnek  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Yönetilen paket Framework dil hizmeti seçenekleri için kayıt defteri girişleri  
 Aşağıdaki kayıt defteri girdilerini yönetilen paket framework (MPF) dil hizmeti sınıfları özgüdür. Bu kayıt defteri girdileri dil hizmeti çeşitli IntelliSense özelliklerini ve diğer gelişmiş düzenleme özellikleri için desteği belirtir.  
  
 Bu kayıt defteri girdileri erişilir <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfı.  
  
|Ad|Tür|Aralık|Açıklama|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|IntelliSense işlemlerini destekler.|  
|MatchBraces|REG_DWORD|0-1|Eşleşen küme ayraçları, parantezleri ve köşeli ayraçlar gibi dil çiftleri için destek.|  
|Quickınfo'da|REG_DWORD|0-1|Hızlı bilgi IntelliSense işlemi için destek.|  
|ShowMatchingBrace|REG_DWORD|0-1|Eşleşen dil çift durum çubuğunda görüntülemek için destek.|  
|MatchBracesAtCaret|REG_DWORD|0-1|Genellikle iki öğe vurgulama ile eşleşen dil çiftlerini görüntülemek için destek.|  
|MaxErrorMessages|REG_DWORD|0-n|Sayısı, görüntülenebilen hataları **hata listesi** penceresi.|  
|CodeSenseDelay|REG_DWORD|0-n|Ayrıştırma bir IntelliSense işlemi için herhangi bir arka plan başlatmadan önce gecikme milisaniye sayısı.|  
|EnableAsyncCompletion|REG_DWORD|0-1|Arka plan ayrıştırma desteği.|  
|EnableCommenting|REG_DWORD|0-1|Desteği seçilen metin blokları açıklama eklemek için ve ayrıca uncommenting seçili metin için destek anlamına gelir.|  
|EnableFormatSelection|REG_DWORD|0-1|Otomatik Girinti gibi metin biçimlendirme veya küme ayraçlarının konumu ayarlama desteği.|  
|AutoOutlining|REG_DWORD|0-1|(Daratılmadan bölge) ana hat oluşturma desteği.|  
|MaxRegions|REG_DWORD|0-n|Gizli bölgeler dosya başına en fazla sayısı.|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)

