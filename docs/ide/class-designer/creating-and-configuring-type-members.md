---
title: Tür Üyeleri Oluşturma ve Yapılandırma (Sınıf Tasarımcısı)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b93fa4720a6f0de9e2d7a64eb2c820811610297
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938805"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Oluşturma ve tür üyeleri Sınıf Tasarımcısı'nda yapılandırma

Bu üyeleri bir sınıf türleri için diyagram ve bu üyelerin yapılandırma ekleyebileceğiniz **sınıf ayrıntıları** penceresi:

|**Türü**|**İçerebileceği üyeler**|
|--------------| - |
|örneği|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Enum|üye|
|Arabirim|yöntem, özellik, olay (C# ve Visual Basic için)|
|Soyut Sınıf|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Yapı (C# için Struct)|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|
|Temsilci|parametre|
|Modül (Yalnızca VB)|yöntem, özellik, alan, olay, oluşturucu, sabit|

> [!NOTE]
> Bir özelliğin get ve set erişimcileri ek mantığa gerek duymadığında, otomatik uygulanan özellikleri (yalnızca C#) kullanarak özellik bildirimini daha kısa yapın. Tam imzayı göstermek için **sınıf diyagramı** menüsünde **üyeler formatını Değiştir** > **tam imzayı görüntüle**. Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz: [Implemented Properties](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Ortak görevler

|Görev|Destekleyici içerik|
|----------| - |
|**Kullanmaya başlayın:** oluşturun ve tür üyeleri'ı yapılandırmadan önce açmalısınız **sınıf ayrıntıları** penceresi.|- [Sınıf ayrıntıları penceresini açma](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Sınıf ayrıntıları kullanım notları](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Salt okunur bilgileri görüntüleme](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Sınıf diyagramında ve sınıf Ayrıntıları penceresinde klavye ve Fare kısayolları](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Oluşturma ve tür üyelerini değiştirme:** yeni üyeler oluşturabilir, üyeleri değiştirebilir ve kullanarak bir yönteme parametre eklemek **sınıf ayrıntıları** penceresi.|- [Üyeleri oluşturma](creating-and-configuring-type-members.md#create-members)<br />- [Tür üyelerini değiştirme](creating-and-configuring-type-members.md#modify-type-members)<br />- [Yöntemlere parametreler ekleme](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Sınıf ayrıntıları penceresini açma

Varsayılan olarak, **sınıf ayrıntıları** yeni bir sınıf diyagramı açtığınızda penceresi otomatik olarak görüntülenir. Bkz: [nasıl yapılır: projelere sınıf diyagramları ekleme](how-to-add-class-diagrams-to-projects.md)). Ayrıca açabilirsiniz **sınıf ayrıntıları** penceresi aşağıdaki yollarla:

- Herhangi bir sınıf diyagramında bir bağlam menüsünü görüntülemek için sağ tıklayın ve ardından **sınıf ayrıntıları**.

- Seçin **görünümü** > **diğer Windows** > **sınıf ayrıntıları** menü çubuğundan.

## <a name="create-members"></a>Üyeleri oluşturma

Üye oluşturmak için aşağıdaki araçlardan herhangi birini kullanabilirsiniz:

- **Sınıf Tasarımcısı**

- **Sınıf ayrıntıları** penceresi araç çubuğu

- **Sınıf ayrıntıları** penceresi

> [!NOTE]
> Bu bölümdeki yordamları kullanarak oluşturucular ve yıkıcılar da oluşturabilirsiniz. Oluşturucular ve Yıkıcılar özel yöntem türleri olduğunu ve bu nedenle, içinde görünürler olduğunu aklınızda Lütfen size aittir **yöntemleri** sınıf diyagramı şekillerinde ve bölme **yöntemleri** bölümü **Sınıf ayrıntıları** pencere kılavuzunun.

> [!NOTE]
> Bir temsilciye ekleyebileceğiniz tek varlık parametredir. Başlıklı yordamı Not ' kullanarak üye oluşturmak için **sınıf ayrıntıları** penceresi araç çubuğu ' Bu eylem için geçerli değil.

### <a name="create-a-member-using-class-designer"></a>Sınıf Tasarımcısı kullanarak üye oluşturmak

1.  Bir üye eklemek istediğiniz türe sağ tıklayın **Ekle**, eklemek istediğiniz üye türünü seçin.

     Yeni bir üye imzası oluşturulur ve türe eklenir. Değiştirebileceğiniz bir varsayılan ad verilir **Sınıf Tasarımcısı**, **sınıf ayrıntıları** penceresinde veya **özellikleri** penceresi.

2.  İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Sınıf Ayrıntıları penceresi araç çubuğunu kullanarak üye oluşturmak

1.  Diyagram yüzeyinde, üye eklemek istediğiniz türü seçin.

     Tür odağa gelir ve içeriği görüntülenir **sınıf ayrıntıları** penceresi.

2.  İçinde **sınıf ayrıntıları** penceresi araç çubuğunda en üstteki simgeye tıklayın ve seçin **yeni \<üye >** açılan listeden.

     İşaretçiyi taşır **adı** alanında eklemek istediğiniz üye türü için bir satır. Örneğin tıkladıysanız **yeni özellik**, imleci yeni bir satıra taşır **özellikleri** bölümünü **sınıf ayrıntıları** penceresi.

3.  Oluşturmak istediğiniz üyenin adını yazın ve Enter'a basın (ya da başka bir şekilde, örneğin, Sekme tuşuna basarak odağı taşıyın).

     Yeni bir üye imzası oluşturulur ve türe eklenir. Üye artık kodun içinde vardır ve görüntülenen **Sınıf Tasarımcısı**, **sınıf ayrıntıları** penceresinde ve Özellikler penceresinde.

4.  İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="create-a-member-using-the-class-details-window"></a>Sınıf ayrıntıları penceresini kullanarak üye oluşturmak

1.  Diyagram yüzeyinde, üye eklemek istediğiniz türü seçin.

     Tür odağa gelir ve içeriği görüntülenir **sınıf ayrıntıları** penceresi.

2.  İçinde **sınıf ayrıntıları** eklemek istediğiniz üye türünü içeren bölümde tıklatıp  **\<Üye Ekle >**. Örneğin, bir alan eklemek istiyorsanız, tıklayın  **\<alan Ekle >**.

3.  Oluşturmak istediğiniz üyenin adını yazın ve Enter'a basın.

     Yeni bir üye imzası oluşturulur ve türe eklenir. Üye artık kodun içinde vardır ve görüntülenen **Sınıf Tasarımcısı**, **sınıf ayrıntıları** penceresinde ve Özellikler penceresinde.

4.  İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

     **Not:** üye oluşturmak için klavye kısayollarını kullanabilirsiniz. Daha fazla bilgi için [klavye ve Fare kısayolları sınıf diyagramında ve sınıf Ayrıntıları penceresinde](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Tür üyelerini değiştirme

Sınıf Tasarımcısı, diyagram görüntülenen türlerin üyelerinde değişiklik yapmanıza olanak sağlar. Sınıf diyagramında görüntülenen ve salt okunur olmayan her türün üyelerini değiştirebilirsiniz. Tür üyelerini tasarım yüzeyinde, Özellikler penceresinde yerinde düzenleme yaparak değiştirin ve **sınıf ayrıntıları** penceresi.

İçinde görüntülenen tüm üyeler **sınıf ayrıntıları** pencere sınıf diyagramındaki türlerin üyelerini temsil eder. Dört üye türü vardır: yöntemler, özellikler, alanlar ve olaylar.

Tüm üye satırları, üyeleri türe göre gruplandıran başlıkların altında görünür. Örneğin, tüm özellikleri başlığının altında görünür **özellikleri**, kılavuzdaki bir düğüm olarak daraltılabilen veya genişletilmiş.

Her üye satırı aşağıdaki öğeleri görüntüler:

- **Üye simgesi**

     Her üyü türü kendi simgesiyle gösterilir. Fare üyenin imzasını görüntülemek için üye simgesinin üzerine getirin. Satırı seçmek için, üye simgesine ya da üye simgesinin solundaki boşluğa tıklayın.

- **Üye adı**

     **Adı** bir üye satırındaki sütunu üyenin adını görüntüler. Bu ad ayrıca görüntülenen **adı** Özellikler penceresindeki özellik. Okuma/Yazma izinlerine sahip herhangi bir üyenin adını değiştirmek için bu hücreyi kullanın.

     Varsa **adı** sütundur tam adı, fare üye adının üzerine getirildiğinde adın görüntüler adın tamamını görüntüleyemeyecek kadar darsa.

- **Üye türü**

     **MemberType** hücresi geçerli projede veya başvurulan projelerde kullanılabilen tüm türlerin listesinden seçmenizi sağlar IntelliSense özelliğini kullanır.

- **Üye değiştiricisi**

     Üye görünürlük değiştiricilerinin ya da değiştirme `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected``Friend` (`protected``internal`), veya `Default`.

- **\<Üye Ekle >**

     Son satıra **sınıf ayrıntıları** penceresi metnini içeren  **\<Üye Ekle >** içinde **adı** hücre. Bu hücreye tıklarsanız yeni bir üye oluşturabilirsiniz. Daha fazla bilgi için [üyeleri oluşturma](creating-and-configuring-type-members.md#create-members).

- **Özellikler penceresindeki üye özellikleri**

     **Sınıf ayrıntıları** penceresi, Özellikler penceresinde görüntülenen üye özelliklerinin bir alt kümesi görüntüler. Özelliğin bir konumda değiştirilmesi, özelliğin değerini global olarak güncelleştirir. Değerinin diğer konumda görüntülenmesi de buna dahildir.

- **Özet**

     **Özet** hücresi üye hakkındaki bilgilerin bir özetini gösterir. Üç noktaya tıklayarak **özeti** hakkında bilgileri görüntüleyemez veya hücre **özeti**, **dönüş türü**, ve **açıklamalar** üyesi için .

- **Gizle**

     Zaman **Gizle** onay kutusu seçiliyse, üye türü görüntülenmez.

### <a name="to-modify-a-type-member"></a>Bir tür üyesini değiştirmek için

1.  Sınıf Tasarımcısı'nı kullanarak bir tür seçin.

2.  Varsa **sınıf ayrıntıları** penceresi görüntülenmiyorsa, tıklayın **sınıf ayrıntıları** Sınıf Tasarımcısı araç çubuğunda penceresi.

3.  Alanlarındaki değerleri düzenleyin **sınıf ayrıntıları** pencere kılavuzunun. Her düzenlemeden sonra ENTER'a basın ya da bir başka yolla, örneğin SEKME tuşuna basarak, odağı düzenlenen alanın dışına taşıyın. Düzenlemeleriniz anında koda yansır.

    > [!NOTE]
    > Bir üyenin yalnızca adını değiştirmek istiyorsanız, bunu yerinde düzenlemeyi kullanarak yapabilirsiniz.

## <a name="add-parameters-to-methods"></a>Yöntemlere parametreler ekleme

Kullanarak yöntemlere parametreler ekleme **sınıf ayrıntıları** penceresi. Parametreler, zorunlu veya isteğe bağlı olacak şekilde yapılandırılabilir. İçin bir değer sağlanması **isteğe bağlı varsayılan** özelliği, tasarımcıya kodu isteğe bağlı bir parametre olarak bildirir.

Parametre satırı aşağıdaki öğeleri içerir:

- **Ad**

     **Adı** sütunu bir parametre satırındaki parametrenin adını görüntüler. Bu ad ayrıca görüntülenen **adı** Özellikler penceresindeki özellik. Okuma/Yazma izinlerine sahip herhangi bir parametrenin adını değiştirmek için bu hücreyi kullanabilirsiniz.

     Parametre adını işaret eden görüntüler parametrenin adını **adı** sütunu adın tamamını görüntüleyemeyecek kadar darsa.

- **Türü**

     **Parametre türü** hücresi geçerli projede veya başvurulan projelerde kullanılabilen tüm türlerin listesinden seçim yapmanıza izin IntelliSense özelliğini kullanır.

- **Değiştiricisi**

     **Değiştiricisi** hücre bir parametre satırındaki kabul eder ve parametrenin yeni değiştiricisini görüntüler. Yeni bir parametre değiştiricisi girmek için seçmek için aşağı açılan liste kutusunu kullanmak **hiçbiri**, **ref**, **kullanıma**, veya **params** C# ve **ByVal**, **ByRef**, veya **ParamArray** vb'de

- **Özet**

     **Özeti** hücre bir parametre satırındaki parametreyi kod düzenleyicisine girerken Intellisense'te görünen kod açıklamalarının girme sağlar.

- **\<Parametre Ekle >**

     Bir üyenin son parametre satırı metni içeren **<add parameter>** içinde **adı** hücre. Bu hücreye tıklanması yeni bir parametre oluşturmanıza izin verir. Daha fazla bilgi için [bir yönteme parametre eklemek için](creating-and-configuring-type-members.md#add-parameters-to-methods).

**Özellikleri** penceresinde görüntülenen parametre özelliklerinin görüntüler **sınıf ayrıntıları** penceresi: **adı**, **türü**,  **Değiştiricisi**, **özeti**, hem de **isteğe bağlı varsayılan** özelliği. Özelliğin bir konumda değiştirilmesi, özelliğin değerini global olarak güncelleştirir (değerinin diğer konumda görüntülenmesi de buna dahildir).

> [!NOTE]
> Bir temsilciye parametre eklemek için bkz [üyeleri oluşturma](creating-and-configuring-type-members.md#create-members).

> [!NOTE]
> Yıkıcı üyesi bir yöntem olmasına karşın, parametrelere sahip olamaz.

### <a name="to-add-a-parameter-to-a-method"></a>Bir yönteme parametre eklemek için

1.  Diyagram yüzeyinde, parametre eklemek istediğiniz yöntemi içeren türe tıklayın.

     Tür odağa gelir ve içeriği görüntüleme **sınıf ayrıntıları** penceresi.

2.  İçinde **sınıf ayrıntıları** penceresinde, parametre eklemek istediğiniz yöntemin satırını genişletin.

     Yalnızca bir çift parantez ve sözcüklerini içeren girintili bir parametre satırı görünür  **\<parametre Ekle >.**

3.  Tıklayın  **\<parametre Ekle >**, adını yeni parametre ve basın, **Enter**.

     Yeni parametre yönteme ve yöntemin koduna eklenir. Bu görüntüler **sınıf ayrıntıları** penceresinde ve Özellikler penceresinde.

4.  İsteğe bağlı olarak, parametreyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Bir yönteme isteğe bağlı parametre eklemek için

1.  Diyagram yüzeyinde, isteğe bağlı parametre eklemek istediğiniz yöntemi içeren türe tıklayın.

     Tür odağa gelir ve içeriği görüntüleme **sınıf ayrıntıları** penceresi.

2.  İçinde **sınıf ayrıntıları** penceresinde isteğe bağlı parametre eklemek istediğiniz yöntemin satırını genişletin.

     Yalnızca bir çift parantez ve sözcüklerini içeren girintili bir parametre satırı görünür  **\<parametre Ekle >.**

3.  Tıklayın  **\<parametre Ekle >**, adını yeni parametre ve basın, **Enter**.

     Yeni parametre yönteme ve yöntemin koduna eklenir. Bu görüntüler **sınıf ayrıntıları** penceresinde ve Özellikler penceresinde.

4.  Özellikler penceresinde için bir değer yazın **isteğe bağlı varsayılan** özelliği. Bir parametrenin İsteğe Bağlı Varsayılan özelliği ayarlandığında bu parametre isteğe bağlı olur.

    > [!NOTE]
    > İsteğe bağlı parametreler, parametre listesindeki en son parametreler olmalıdır.

## <a name="class-details-usage-notes"></a>Sınıf ayrıntıları kullanım notları

Lütfen kullanmaya ilişkin Aşağıdaki ipuçlarına dikkat **sınıf ayrıntıları** penceresi.

### <a name="editable-and-non-editable-cells"></a>Düzenlenebilir ve düzenlenemez hücreler

Tüm hücreleri **sınıf ayrıntıları** penceresi birkaç istisna dışında düzenlenebilir:

- Türün tamamı salt okunur olduğunda, örneğin başvurulan bir derlemede yer alıyor. Sınıf Tasarımcısı'nda şekli seçtiğinizde **sınıf ayrıntıları** penceresi bir salt okunur durumda ayrıntılarını görüntüler.

- Dizin oluşturucular için, ad bilgisi salt okunur ve geri kalanı (tür, değiştirici, özet) düzenlenebilir özelliktedir.

- Tüm genel türler salt okunur parametrelere sahip **sınıf ayrıntıları** penceresi. Bir genel parametreyi değiştirmek için kaynak kodunu düzenleyin.

- Genel türde tanımlanan tür parametresinin adı salt okunurdur.

- Türün kodu bozuk (çözümlenemez) olduğunda **sınıf ayrıntıları** penceresi türün içeriğini salt okunur olarak görüntüler.

### <a name="the-class-details-window-and-source-code"></a>Sınıf Ayrıntıları penceresi ve kaynak kodu

- Kaynak kodu bir şekle sağ tıklatarak görüntüleyebileceğiniz **sınıf ayrıntıları** penceresinin (veya Sınıf Tasarımcısı) ve ardından kodu görüntüle. Kaynak kodu dosyası açılır ve seçili öğeye kadar ilerler.

- Kaynak kodunun değiştirilmesi hemen yansıtılır imza bilgilerinin Sınıf Tasarımcısı'nda görüntülenir ve **sınıf ayrıntıları** penceresi. Varsa **sınıf ayrıntıları** zaman penceresi kapatıldığında, yeni bilgileri, sonraki açışınızda görülebilir.

- Türün kodu bozuk (çözümlenemez) olduğunda **sınıf ayrıntıları** penceresi türün içeriğini salt okunur olarak görüntüler.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde Pano işlevselliği

Kopyala veya Kes alanları veya satırları **sınıf ayrıntıları** penceresi ve bunları başka bir türe yapıştırabilirsiniz. Bir satırı ancak salt okunur ise kesebilirsiniz. Satırı yapıştırdığınızda **sınıf ayrıntıları** penceresi çakışma olmasını önlemek için yeni bir ad (kopyalanan satırın adından türetilir) atar.

## <a name="display-of-read-only-information"></a>Salt okunur bilgileri görüntüleme

Sınıf Tasarımcısı ve **sınıf ayrıntıları** penceresi aşağıdaki türleri (ve türlerin üyelerini) görüntüleyebilir:

- Sınıf diyagramı içeren bir proje

- Sınıf diyagramı içeren bir projeden başvurulan proje

- Sınıf diyagramı içeren bir projeden başvurulan derleme

Sonraki iki durum için, başvurulan varlık (bir tür veya üye) temsil ettiği sınıf diyagramında salt okunurdur.

Bir projenin tamamı ya da kısımları (tek tek dosyalar gibi) salt okunur olabilir. Projenin veya dosyalarından birinin salt okunur olduğu en yaygın durumlar, bir kaynak kodu denetiminin altında olduğu (ve kullanıma alınmamış), bir dış derlemede var olduğu veya işletim sisteminin dosyaları salt okunur olarak düşündüğü durumlardır.

**Kaynak kodu denetimi**

Bir sınıf diyagramı, bir projede bir dosya olarak kaydedildiğinden, Sınıf Tasarımcısı'nda yaptığınız değişiklikleri kaydetmek için projeyi kontrol etmeniz veya **sınıf ayrıntıları** penceresi.

**Salt okunur projeler**

Proje, kaynak kodu denetimi dışındaki bir nedenle salt okunur olabilir. Proje kapatıldığında, proje dosyasının üzerine, (kaydetme) değişiklikleri atmak mı soran bir iletişim kutusu görüntüler veya kapatma işlemi iptal edin. Üzerine yazmayı tercih ederseniz proje dosyalarının üzerine yazılır ve okuma/yazma özellikli yapılırlar. Yeni sınıf diyagramı dosyası eklenir.

**Salt okunur türler**

Kaynak kodu dosyası salt okunur bir türü içeren bir projeyi kaydetmeyi denerseniz **salt okunur dosyanın kaydı** iletişim kutusu görüntülenirse, dosyayı yeni bir ad veya yeni bir konuma veya salt okunur dosyanın üzerine yazma seçenekleri sunar . Dosyanın üzerine yazarsanız yeni kopyası artık salt okunur özellikte olmaz.

Bir Kod dosyası sözdizimi hatası içeriyorsa, bu dosyadaki kodu gösteren şekiller söz dizimi hatası düzeltilinceye kadar geçici olarak salt okunur olur. Bu durumdaki şekiller, "Kaynak kodu dosyası ayrıştırma hatası içeriyor" yazılı araç ipucunu gösteren kırmızı bir metin ve kırmızı bir simge görüntüler.

Başka bir proje düğümü altında ya da başvurulan bir derleme düğümü altında bulunan bir başvurulan tür (.NET Framework türü gibi), Sınıf Tasarımcısı'nın tasarım yüzeyinde salt okunur olarak belirtilir. Açık durumda bulunan projede var olan bir yerel tür okuma/yazma özelliklidir ve Sınıf Tasarımcısı'nın tasarım yüzeyindeki şekli de böyle belirtilir.

Dizin oluşturucular okuma-yazma kod ve **sınıf ayrıntıları** penceresi, ancak dizin oluşturucunun adı salt okunur.

Kısmi yöntemleri Sınıf Tasarımcısı kullanarak düzenleyemezsiniz veya **sınıf ayrıntıları** penceresi; bunları düzenlemek için Kod Düzenleyicisi'ni kullanmanız gerekir.

Yerel C++ kodunu Sınıf Tasarımcısı kullanarak düzenleyemezsiniz veya **sınıf ayrıntıları** penceresi; yerel C++ kodunu düzenlemek için Kod Düzenleyicisi'ni kullanmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Türleri ve ilişkilendirmeleri görüntüleme](viewing-types-and-relationships.md)
- [Sınıfları ve türleri yeniden düzenleme](refactoring-classes-and-types.md)