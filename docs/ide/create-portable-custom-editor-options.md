---
title: EditorConfig ayarları
ms.date: 09/02/2020
ms.topic: how-to
helpviewer_keywords:
- editorconfig [Visual Studio]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.openlocfilehash: 59e226fc0cc09b1eda5197d6accddfa9bd1a20ed
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402263"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>EditorConfig ile taşınabilir, özel düzenleyici ayarları oluşturma

Kod tabanında çalıştırılan herkes için tutarlı kodlama stillerini zorlamak üzere projenize veya kod tabanınıza bir EditorConfig dosyası ekleyebilirsiniz. EditorConfig ayarları, Global Visual Studio metin Düzenleyicisi ayarlarından önceliklidir. Bu, her kod temelini o projeye özel metin düzenleyici ayarlarını kullanmak üzere uyarlayabileceğiniz anlamına gelir. Visual Studio **seçenekleri** iletişim kutusunda kendi kişisel düzenleyici tercihlerinizi ayarlamaya devam edebilirsiniz. Bu ayarlar, *. editorconfig* dosyası olmayan bir kod tabanında her çalıştığınızda veya *. editorconfig* dosyası belirli bir ayarı geçersiz kılmazsa geçerlidir. Bu tür bir tercihe bir örnek, girinti stili &mdash; sekmeleri veya boşluklardan oluşur.

EditorConfig ayarları, Visual Studio da dahil olmak üzere çok sayıda kod Düzenleyicisi ve Ides tarafından desteklenir. Bu, kodunuzla taşınan taşınabilir bir bileşendir ve Visual Studio dışında bile kodlama stillerini uygulayabilir.

::: moniker range=">=vs-2019"

Visual Studio 'da projenize bir EditorConfig dosyası eklediğinizde, yeni kod satırları EditorConfig ayarlarına göre biçimlendirilir. Aşağıdaki komutlardan birini çalıştırmadığınız takdirde varolan kodun biçimlendirmesi değiştirilmez:

 - [Kod temizleme](../ide/code-styles-and-code-cleanup.md) (**CTRL** + **K**, **CTRL** + **E**), girinti stili gibi tüm beyaz boşluk ayarlarını ve nasıl sıralama yönergeleri gibi seçili kod stili ayarlarını uygular `using` .
 - **Düzenle** > **Gelişmiş** > **Format Document** **Ctrl** + **K** **Ctrl** + Yalnızca girinti stili gibi beyaz boşluk ayarlarını uygulayan belgeyi (veya varsayılan profilde CTRL**D** ) biçimlendirin.

 ::: moniker-end

::: moniker range="=vs-2017"

Visual Studio 'da projenize bir EditorConfig dosyası eklediğinizde, yeni kod satırları EditorConfig ayarlarına göre biçimlendirilir. Belgeyi biçimlendirmediğiniz **(**  >  **Gelişmiş**  >  **Biçim belgesi** veya **CTRL** + **K**, varsayılan profilde **CTRL** + **D** ), varolan kodun biçimlendirmesi değiştirilmez. Belgeyi biçimlendirmek, [ek kod temizleme işlemini gerçekleştirmek](../ide/code-styles-and-code-cleanup.md#apply-code-styles)üzere biçim belgesi yapılandırmadığınız sürece yalnızca girinti stili gibi beyaz boşluk ayarlarını etkiler.

 ::: moniker-end

::: moniker range="vs-2017"

[ **Biçimlendirme** seçenekleri sayfasında](reference/options-text-editor-csharp-formatting.md#format-document-settings) **Belge biçimini biçimlendirmek** istediğiniz düzenleyici yapılandırma ayarlarını tanımlayabilirsiniz.

::: moniker-end

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için, [Mac için Visual Studio Içindeki Editorconfig](/visualstudio/mac/editorconfig)bölümüne bakın.

## <a name="code-consistency"></a>Kod tutarlılığı

EditorConfig dosyalarındaki ayarlar, kullandığınız düzenleyiciden veya IDE 'den bağımsız olarak, bir kod tabanında, girinti stili, sekme genişliği, satır sonu karakterleri, kodlama ve daha fazlası gibi tutarlı kodlama stilleri ve ayarları korumanıza olanak sağlar. Örneğin, C# dilinde kodlarken, kod tabanınızın her zaman beş boşluk karakteri içermesi için bir kuralı varsa, belgeler UTF-8 kodlaması kullanır ve her satır her zaman bir CR/LF ile sona erer ve bunu yapmak için bir *. editorconfig* dosyası yapılandırabilirsiniz.

Kişisel projeleriniz üzerinde kullandığınız kodlama kuralları, takımınızın projelerinde kullanılanlardan farklı olabilir. Örneğin, kodlama yaparken, girintileme bir sekme karakteri ekliyor seçeneğini tercih edebilirsiniz. Ancak ekibiniz, girintileme 'nin bir sekme karakteri yerine dört boşluk karakteri eklemesine tercih edebilir. EditorConfig dosyaları, her senaryo için bir yapılandırmanıza izin vererek bu sorunu çözer.

Ayarlar kod temelindeki bir dosyada bulunduğundan, bu kod temeli ile birlikte seyahat ederler. Kod dosyasını bir EditorConfig uyumlu düzenleyicide açtığınız sürece, metin düzenleyici ayarları uygulanır. EditorConfig dosyaları hakkında daha fazla bilgi için bkz. [EditorConfig.org](https://editorconfig.org/) Web sitesi.

> [!NOTE]
> Bir EditorConfig dosyasında ayarlanan kurallar, derleme hataları veya uyarılar olarak bir CI/CD ardışık düzeninde zorlanamaz. Stil sapmaları yalnızca Visual Studio düzenleyicisinde ve **hata listesi**görünür.

## <a name="supported-settings"></a>Desteklenen ayarlar

Visual Studio 'daki düzenleyici, [Editorconfig özelliklerinin](https://editorconfig.org/#supported-properties)çekirdek kümesini destekler:

- indent_style
- indent_size
- tab_width
- Son \_ of_line
- karakter
- kırpma \_ trailing_whitespace
- \_final_newline Ekle
- kök

EditorConfig Düzenleyicisi ayarları, XML hariç tüm Visual Studio tarafından desteklenen dillerde desteklenir. Ayrıca, EditorConfig, C# ve Visual Basic için [dil](../ide/editorconfig-language-conventions.md), [biçimlendirme](../ide/editorconfig-formatting-conventions.md)ve [adlandırma](../ide/editorconfig-naming-conventions.md) kuralları da dahil olmak üzere [kod stili](../ide/editorconfig-code-style-settings-reference.md) kurallarını destekler.

## <a name="add-and-remove-editorconfig-files"></a>EditorConfig dosyalarını ekleme ve kaldırma

Projenize veya kod tabanınıza bir EditorConfig dosyası eklediğinizde, yazdığınız tüm yeni kod satırları EditorConfig dosyasına göre biçimlendirilir. Ancak, bir EditorConfig dosyası eklemek, belgeyi biçimlendirene veya [kod temizliği](../ide/code-styles-and-code-cleanup.md)çalıştırana kadar mevcut stilleri yeni olanlara dönüştürmez. Örneğin, dosyanızda sekmelerle biçimlendirilmiş Girintileriniz varsa ve boşluklarla girintilenen bir EditorConfig dosyası eklerseniz, girinti karakterleri otomatik olarak boşluklara dönüştürülmez. Belgeyi biçimlendirdiğinizde (**Edit**  >  **Gelişmiş**  >  **Biçim belgesini** Düzenle veya **CTRL** + **K**, **CTRL** + **D**), editorconfig dosyasındaki boşluk ayarları, varolan kod satırlarına uygulanır.

Bir EditorConfig dosyasını projenizden veya kod tabanınızdan kaldırırsanız ve yeni kod satırlarının genel düzenleyici ayarlarına göre biçimlendirilmesini istiyorsanız, açık kod dosyalarını kapatıp yeniden açmanız gerekir.

### <a name="add-an-editorconfig-file-to-a-project"></a>Bir projeye EditorConfig dosyası ekleme

1. Visual Studio 'da bir proje veya çözüm açın. *. Editorconfig* ayarlarınızın Çözümdeki tüm projelere mi yoksa yalnızca bir tane mi uygulandığına bağlı olarak, proje veya çözüm düğümünü seçin. Ayrıca, *. editorconfig* dosyasını eklemek için projenizde veya çözümünüzde bir klasör seçebilirsiniz.

1. Menü çubuğundan **Proje**  >  **Ekle yeni öğe**' yi seçin veya **CTRL** + **SHIFT** + **A**' ya basın.

   **Yeni öğe Ekle** iletişim kutusu açılır.

1. Arama kutusunda, **editorconfig**' i arayın.

   Arama sonuçlarında iki **editorconfig dosya** öğesi şablonu gösterilmektedir.

   ![Visual Studio 'da EditorConfig dosyası öğe şablonları](media/editorconfig-item-templates.png)

1. Girinti stili ve boyutu için iki Core EditorConfig seçeneği ile önceden doldurulan bir EditorConfig dosyası eklemek için **Editorconfig dosyası (varsayılan)** şablonunu seçin. Ya da varsayılan [.NET kod stili, biçimlendirme ve adlandırma kurallarıyla](../ide/editorconfig-code-style-settings-reference.md)önceden doldurulan bir editorconfig dosyası eklemek için **editorconfig dosyası (.net)** şablonunu seçin.

   Bir *. editorconfig* dosyası Çözüm Gezgini görünür ve düzenleyicide açılır.

   ![Çözüm Gezgini ve düzenleyicideki. editorconfig dosyası](media/editorconfig-dotnet.png)

1. Dosyayı istediğiniz gibi düzenleyin.

### <a name="other-ways-to-add-an-editorconfig-file"></a>EditorConfig dosyası eklemenin diğer yolları

Projenize bir EditorConfig dosyası eklemenin birkaç yolu vardır:

- Visual Studio için ıntellicode 'un [kod çıkarımı özelliği](/visualstudio/intellicode/code-style-inference) , kod stillerinizi mevcut koddan algılar. Daha sonra, kod stili tercihleriniz zaten tanımlanmış boş olmayan bir EditorConfig dosyası oluşturur.

- Visual Studio 2019 ' den başlayarak, **Araçlar** [seçeneklerinizde kod stili ayarlarınıza göre bir editorconfig dosyası](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) oluşturabilirsiniz  >  **Options**.

## <a name="file-hierarchy-and-precedence"></a>Dosya hiyerarşisi ve önceliği

Dosya hiyerarşinizdeki bir klasöre bir *. editorconfig* dosyası eklediğinizde, ayarları o düzeydeki ve alttaki tüm ilgili dosyalar için geçerlidir. Ayrıca, kod temelinin diğer parçalarından farklı kurallar kullanması gibi belirli bir proje, kod temeli veya kod temelinin bir parçası için EditorConfig ayarlarını geçersiz kılabilirsiniz. Bu, herhangi bir yerden kod eklediğinizde ve kurallarını değiştirmek istemediğinizde yararlı olabilir.

EditorConfig ayarlarının bir kısmını veya tamamını geçersiz kılmak için, bu geçersiz kılınan ayarların uygulanmasını istediğiniz dosya hiyerarşisi düzeyinde bir *. editorconfig* dosyası ekleyin. Yeni EditorConfig dosyası ayarları, dosyalar için aynı düzeyde ve tüm alt dizinlerde geçerlidir.

![EditorConfig hiyerarşisi](../ide/media/vside_editorconfig_hierarchy.png)

Ayarların tümünü geçersiz kılmak istiyorsanız, yalnızca *. editorconfig* dosyasında bu ayarları belirtin. Yalnızca alt düzey dosyada açıkça listeettiğiniz Özellikler geçersiz kılınır. Daha yüksek düzeydeki *. editorconfig* dosyalarındaki diğer ayarlar uygulanmaya devam eder. Kod temelinin bu bölümüne, daha üst düzey _bir_ *. editorconfig* dosyası uygulanmış _hiçbir_ ayar olmamasını sağlamak istiyorsanız, ```root=true``` özelliği alt düzey *. editorconfig* dosyasına ekleyin:

```ini
# top-most EditorConfig file
root = true
```

EditorConfig dosyaları üstten alta okunurdur. Aynı ada sahip birden fazla özellik varsa, bu adı taşıyan en son bulunan özellik öncelik kazanır.

## <a name="edit-editorconfig-files"></a>EditorConfig dosyalarını Düzenle

Visual Studio, IntelliSense tamamlanma listeleri sağlayarak *. editorconfig* dosyalarını düzenlemenize yardımcı olur.

![Bir. editorconfig dosyasında IntelliSense](media/editorconfig-intellisense-no-extension.png)

EditorConfig dosyanızı düzenledikten sonra, yeni ayarların etkili olması için kod dosyalarınızı yeniden yüklemeniz gerekir.

Çok sayıda *. editorconfig* dosyasını düzenlerseniz, [Editorconfig dil hizmeti uzantısını](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) yararlı bulabilirsiniz. Bu uzantının bazı özellikleri, sözdizimi vurgulama, geliştirilmiş IntelliSense, doğrulama ve kod biçimlendirme özelliklerini içerir.

![EditorConfig dil hizmeti uzantısı ile IntelliSense](media/editorconfig-intellisense.png)

## <a name="example"></a>Örnek

Aşağıdaki örnek, projeye bir *. editorconfig* dosyası eklemeden önce ve sonra bir C# kod parçacığının girintileme durumunu gösterir. Visual Studio metin Düzenleyicisi için **Seçenekler** Iletişim kutusundaki **Sekmeler** ayarı, **sekme** tuşuna bastığınızda boşluk karakterleri üretmek üzere ayarlanır.

![Metin düzenleyici sekmesi ayarı](../ide/media/vside_editorconfig_tabsetting.png)

Beklenen şekilde, sonraki satırdaki **sekme** tuşuna basmak, dört ek boşluk karakteri ekleyerek çizgiyi girintiler.

![EditorConfig kullanmadan önce kod](../ide/media/vside_editorconfig_before.png)

Projeye, aşağıdaki içerikle *. editorconfig* adlı yeni bir dosya ekleyin. `[*.cs]`Ayar, bu değişikliğin yalnızca projedeki C# kod dosyaları için geçerli olduğu anlamına gelir.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Artık **sekme** tuşuna bastığınızda boşluklar yerine sekme karakterleri alırsınız.

![Sekme tuşu sekme karakteri ekler](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>EditorConfig ayarları sorunlarını giderme

Projenizin konumunun veya üstündeki dizin yapısında herhangi bir yerde bir EditorConfig dosyası varsa, Visual Studio bu dosyadaki düzenleyici ayarlarını düzenleyicinize uygular. Bu durumda, durum çubuğunda aşağıdaki iletiyi görebilirsiniz:

   **"Bu dosya türü için Kullanıcı tercihleri bu projenin kodlama kuralları tarafından geçersiz kılınır."**

Diğer bir deyişle, **Araçlar**  >  **Seçenekler**  >  **metin düzenleyicisinde** (girinti boyutu ve stil, sekme boyutu veya kodlama kuralları gibi) herhangi bir düzenleyici ayarı, dizin yapısında proje üzerinde veya üzerinde bir editorconfig dosyasında belirtildiğinde, editorconfig dosyasındaki kurallar **seçeneklerindeki**ayarları geçersiz kılar. **Araç**seçenekleri metin düzenleyicisinde **Proje kodlama kurallarını izle** seçeneğini değiştirerek bu davranışı kontrol edebilirsiniz  >  **Options**  >  **Text Editor**. Seçeneğin işaretlenmesi, Visual Studio için EditorConfig desteğini devre dışı bırakır.

![Araç seçenekleri-proje kodlama kurallarını izleyin](media/coding_conventions_option.png)

Herhangi bir *. editorconfig* dosyasını, bir komut istemi açıp ve projenizi içeren diskin kökünden aşağıdaki komutu çalıştırarak, üst dizinlerde bulabilirsiniz:

```Shell
dir .editorconfig /s
```

```root=true```Deponuzın kökündeki *. editorconfig* dosyasında veya projenizin bulunduğu dizinde özelliğini ayarlayarak editorconfig kurallarınızın kapsamını kontrol edebilirsiniz. Visual Studio, açılan dosya dizininde ve her üst dizinde *. editorconfig* adlı bir dosya arar. Arama, kök FilePath 'e ulaştığında veya ile bir *. editorconfig* dosyası bulunursa sona erer ```root=true``` .

## <a name="see-also"></a>Ayrıca bkz.

- [.NET kodu stil kuralları](../ide/editorconfig-code-style-settings-reference.md)
- [Dil hizmeti için EditorConfig destekleme](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Kod düzenleyicisinin özellikleri](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Mac için Visual Studio)](/visualstudio/mac/editorconfig)
