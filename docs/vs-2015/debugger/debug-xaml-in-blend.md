---
title: Blend'de XAML hatalarını ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b01fdc6962ea5a564537a083be4e9993533f1e4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728111"
---
# <a name="debug-xaml-in-blend"></a>Blend'de XAML hatalarını ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanabileceğiniz araçları [!INCLUDE[blend_first](../includes/blend-first-md.md)] XAML uygulamanızda hata ayıklamak için. Bir proje oluşturduğunuzda, tüm hataları görüntülenebilir **sonuçları** paneli. Hatayla ilgili biçimlendirme bulmak için bir hataya çift tıklayın. Çalışmak için daha fazla yer gerekirse gizleyebilirsiniz **sonuçları** F12 tuşuna basarak paneli.  
  
## <a name="syntax-errors"></a>Sözdizimi hataları  
 XAML veya arka plan kod dosyalarını dilin biçimlendirme kurallarına uygulamazsanız sözdizimi hataları ortaya çıkar. Hatanın açıklaması, nasıl düzeltileceğini anlamanıza yardımcı olabilir. Liste dosyasının adını ve hatanın oluştuğu satırın numarasını da belirtir. XAML hataları listelenen **biçimlendirme** sekmesinde **sonuçları** paneli.  
  
> [!TIP]
>  XAML, XML-tabanlı işaretleme dilidir ve XML sözdizimi kurallarına uyar.  
  
 XAML söz dizimi hataları bazı yaygın nedenleri:  
  
- Bir anahtar sözcük yanlış yazılmıştır veya büyük harf ayrımı yanlıştır.  
  
- Öznitelikleri veya metin dizesini tırnak işareti eksik.  
  
- XAML öğesinde bir kapatma etiketi eksiktir.  
  
- XAML öğesi, izin verilmeyen bir konumda bulunmaktadır.  
  
  Genel XAML söz dizimi hakkında daha fazla bilgi için bkz. [temel XAML söz dizimi Kılavuzu](http://go.microsoft.com/fwlink/?LinkId=329942).  
  
  Ayrıca tanımlamak ve çalışma zamanı hataları, derleme hataları ve basit arka plan kod söz dizimi hatalarını gidermek [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]. Ancak, arka plan kod hataları belirlemek ve Visual Studio'da çözmek daha kolay olabilir.  
  
### <a name="debugging-sample-xaml-code"></a>Örnek XAML kodu hata ayıklama  
 Aşağıdaki örnek, hata ayıklama oturumu basit bir XAML aracılığıyla anlatılmaktadır [!INCLUDE[blend_subs](../includes/blend-subs-md.md)].  
  
##### <a name="to-create-a-project"></a>Bir proje oluşturmak için  
  
1. İçinde [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]açın **dosya** menüsüne ve ardından **yeni proje**.  
  
    İçinde **yeni proje** iletişim kutusu, proje türleri listesinden sol tarafında görünür. Bir proje türü tıkladığınızda, kendisiyle ilişkili olan proje şablonlarını sağ tarafta görüntülenir.  
  
2. Proje türleri listesinde tıklayın **XAML (Windows Store)**.  
  
3. Proje şablonları listesinde tıklayın **boş uygulama**.  
  
4. İçinde **adı** metin kutusunda, `DebuggingSample`.  
  
5. İçinde **konumu** metin kutusunda, projeyi konumunu doğrulayın.  
  
6. İçinde **dil** listesinde **Visual C#** ve ardından **Tamam** projeyi oluşturmak için.  
  
7. Tasarım yüzeyine sağ tıklayın ve ardından **kaynağı görüntüle** geçmek **bölünmüş** görünümü.  
  
8. Tıklayarak aşağıdaki kodu kopyalayın **kopyalama** kod sağ üst köşesindeki bağlantı.  
  
   ```  
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
  
   ```  
  
9. Varsayılan bulun **kılavuz**, kodu açılış ve kapanış arasına yapıştırın **kılavuz** etiketler. İşlemi tamamladığınızda, kodunuz aşağıdaki gibi görünmelidir:  
  
    ```  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
         </Grid>  
    </Grid>  
  
    ```  
  
10. Projeyi derlemek için Ctrl + Shift + B tuşlarına basın.  
  
    Proje oluşturulamıyor, sizi bir hata iletisi görüntülenir ve **sonuçları** listeleme hataları paneli uygulama alt kısmında görüntülenir.  
  
    ![Visual Studio için blend'de XAML hatalarını ayıklama](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>XAML hatalarını çözme  
 Tasarım yüzeyinde, XAML hatalar algılandığında, projenizi geçersiz biçimlendirme içeren bir uyarı görüntüler. Hataları gidermek gibi hata listesini **sonuçları** paneli güncelleştirilir. Tüm hataları çözdükten sonra Tasarım yüzeyine etkindir ve uygulamanızı tasarım yüzeyinde görüntülenir.  
  
##### <a name="to-resolve-the-xaml-errors"></a>XAML hataları gidermek için  
  
1. Listede ilk hataya çift tıklayın. Açıklama "değer ' <' özniteliği geçerli değil." Hataya çift tıklayın, işaretçi kod içinde ilgili konuma bulur. `<` Önceki `Button` geçerli olduğunu ve bir öznitelik değil hata iletisini önerildiği. Önceki kod satırında bakarsanız, kapanış tırnak işareti öznitelik için işaretler fark edeceksiniz `Top` eksik. Kapanış tırnak işareti yazın. Hata listesini bildirimi **sonuçları** paneline değişikliklerinizi yansıtacak şekilde güncelleştirmeleri.  
  
2. Açıklama çift tıklatın "'0' geçersiz bir adın başlangıcında." `Margin="0,149,0,0"` iyi biçimlendirilmiş görünüyor. Ancak, dikkat, renk kodlaması `Margin` diğer örneklerini eşleşmiyor `Margin` kod. Önceki ad/değer çiftinden kapanış tırnak işareti olmadığından (`VerticalAlignment="Top`), `Margin="` önceki öznitelik ve 0 değerini bir parçası olarak bir ad/değer çifti başına okurken okuyun. Kapanış tırnak işaretleri yazın `Top`. Hata listesinde **sonuçları** paneline değişikliklerinizi yansıtacak şekilde güncelleştirmeleri.  
  
3. "XML kapatma etiketi 'Button' eşleşmiyor." kalan hataya çift tıklayın Kapatma sırasında bulunan bir işaretçidir **kılavuz** etiketi (`</Grid>`), hata içinde bulunan önerme `Grid` nesne. Dikkat ikinci `Button` nesne kapanış etiketi eksik. Kapanış ekledikten sonra `/`, **sonuçları** paneli listesi güncelleştirilir. Bu ilk hataları çözümlendi, iki ek hataları belirlenmiştir.  
  
4. "'Content' üyesi tanınmıyor veya erişilebilir değil." çift tıklayın. `c` İçinde `content` büyük olmalıdır. Bir büyük harf "c" küçük "c" değiştirin  
  
5. Çift tıklatın "'Mame' role'u yok özelliği '<http://schemas.microsoft.com/winfx/2006/xaml>' ad alanı." "Mame", "M", "N" olmalıdır "M" bir "n" ile değiştirin XAML ayrıştırılabilir, uygulama tasarım yüzeyinde görünür.  
  
    ![Visual Studio için blend'de XAML hata ayıklama](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
    Projenizi derleyin ve kalan herhangi bir hata olduğunu onaylamak için Ctrl + Shift + B tuşlarına basın.  
  
## <a name="debugging-in-visual-studio"></a>Visual Studio'da Hata Ayıklama  
 Açabileceğiniz [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] projeleri Visual Studio'da daha kolayca uygulamanıza kodlarda hata ayıklayın. Açmak için bir [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] Visual Studio'daki proje, projeye sağ **projeleri** paneli ve ardından **Visual Studio'da Düzenle**. Visual Studio'da hata ayıklama oturumunuz tamamladıktan sonra tüm değişikliklerinizi kaydedin ve ardından geri dönmek için Ctrl + Shift + S tuşuna basın [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]. Projeyi yeniden yüklemeniz istenir. Tıklayın **Tümüne Evet** çalışmaya devam etmek için [!INCLUDE[blend_subs](../includes/blend-subs-md.md)].  
  
 Uygulamanızı hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio'da hata ayıklama Windows Store apps](http://go.microsoft.com/fwlink/?LinkId=329944).  
  
## <a name="getting-help"></a>Yardım alma  
 Hata ayıklama için daha fazla yardıma ihtiyacınız varsa, [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] uygulamayı arayabilirsiniz [Windows Store uygulama topluluğu forumlarında](http://go.microsoft.com/fwlink/?LinkId=280308) gönderileri sorununuzla ilgili veya bir soru gönderin.



