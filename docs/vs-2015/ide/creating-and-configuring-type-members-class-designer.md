---
title: Tür üyeleri (Sınıf Tasarımcısı) oluşturma ve yapılandırma | Microsoft Docs
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
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93a112fac274921fe2d1075e1a1b9178c408240c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827981"
---
# <a name="creating-and-configuring-type-members-class-designer"></a>Tür Üyeleri Oluşturma ve Yapılandırma (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu üyeleri bir sınıf türleri için diyagram ve bu üyelerin yapılandırma ekleyebileceğiniz **sınıf ayrıntıları** penceresi:  
  
|**Türü**|**İçerebileceği üyeler**|  
|--------------|--------------------------------|  
|örneği|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|  
|Enum|üye|  
|Arabirim|yöntem, özellik, olay (C# ve Visual Basic için)|  
|Soyut Sınıf|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|  
|Yapı (C# için Struct)|yöntem, özellik (C# ve Visual Basic için), alan, olay (C# ve Visual Basic için), oluşturucu (yöntem), yıkıcı (yöntem), sabit|  
|Temsilci|Parametre|  
|Modül (Yalnızca VB)|yöntem, özellik, alan, olay, oluşturucu, sabit|  
  
> [!NOTE]
>  Bir özelliğin get ve set erişimcileri ek mantığa gerek duymadığında, otomatik uygulanan özellikleri (yalnızca C#) kullanarak özellik bildirimini daha kısa yapın. Tam imzayı göstermek için **sınıf diyagramı** menüsünde seçin **üyeler formatını Değiştir**, **tam imzayı görüntüle**. Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz: [Implemented Properties](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7).  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|Destekleyici İçerik|  
|----------|------------------------|  
|**Kullanmaya başlayın:** oluşturun ve tür üyeleri'ı yapılandırmadan önce sınıf ayrıntıları penceresini açmalısınız.|-   [Sınıf ayrıntıları penceresini açma](../ide/creating-and-configuring-type-members-class-designer.md#OpenClassDetails)<br />-   [Sınıf ayrıntıları kullanım notları](../ide/creating-and-configuring-type-members-class-designer.md#ClassDetailsUsageNotes)<br />-   [Salt okunur bilgileri görüntüleme](../ide/creating-and-configuring-type-members-class-designer.md#ReadOnlyInfo)<br />-   [Klavye ve Fare kısayolları sınıf diyagramında ve sınıf Ayrıntıları penceresi (Sınıf Tasarımcısı)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md)|  
|**Oluşturma ve tür üyelerini değiştirme:** yeni üyeler oluşturabilir, üyeleri değiştirebilir ve sınıf ayrıntıları penceresini kullanarak bir yönteme parametre ekleyin.|-   [Üyeleri oluşturma](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)<br />-   [Tür üyelerini değiştirme](../ide/creating-and-configuring-type-members-class-designer.md#ModifyTypeMembers)<br />-   [Yöntemlere parametreler ekleme](../ide/creating-and-configuring-type-members-class-designer.md#AddMethodParams)|  
  
##  <a name="OpenClassDetails"></a> Sınıf ayrıntıları penceresini açma  
 Varsayılan olarak, yeni bir sınıf diyagramı açtığınızda sınıf Ayrıntıları penceresi otomatik olarak görünür. (bkz [nasıl yapılır: sınıf diyagramlarına ekleme (Sınıf Tasarımcısı) projeleri](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)). Ayrıca, aşağıdaki yollarla, Sınıf Ayrıntıları penceresini doğrudan da açabilirsiniz.  
  
#### <a name="to-open-the-class-details-window"></a>Sınıf Ayrıntıları penceresini açmak için  
  
1. Herhangi bir sınıf diyagramında bir bağlam menüsünü görüntülemek için sağ tıklayın.  
  
2. Bağlam menüsünde tıklatın **sınıf Ayrıntıları penceresi**.  
  
   – veya -  
  
-   İşaret **diğer Windows** Görünüm menüsü ve ardından **sınıf ayrıntıları**.  
  
##  <a name="CreateMembers"></a> Üyeleri oluşturma  
 Üye oluşturmak için aşağıdaki araçlardan herhangi birini kullanabilirsiniz:  
  
-   Sınıf Tasarımcısı  
  
-   Sınıf Ayrıntıları penceresi araç çubuğu  
  
-   Sınıf Ayrıntıları penceresi  
  
> [!NOTE]
>  Bu bölümdeki yordamları kullanarak oluşturucular ve yıkıcılar da oluşturabilirsiniz. Oluşturucular ve Yıkıcılar özel yöntem türleri olduğunu ve bu nedenle, içinde görünürler olduğunu aklınızda Lütfen ayı **yöntemleri** sınıf diyagramı şekillerinde ve bölme **yöntemleri** sınıfının bölümüne Ayrıntıları pencere kılavuzunun.  
  
> [!NOTE]
>  Bir temsilciye ekleyebileceğiniz tek varlık parametredir. 'Sınıf Ayrıntıları Penceresi araç çubuğunu kullanarak üye oluşturmak için' başlıklı yordamın bu eylem için geçerli olmadığını unutmayın.  
  
#### <a name="to-create-a-member-using-class-designer"></a>Sınıf Tasarımcısı'nı kullanarak üye oluşturmak için  
  
1.  Bir üye eklemek istediğiniz türe sağ tıklayın **Ekle**, eklemek istediğiniz üye türünü seçin.  
  
     Yeni bir üye imzası oluşturulur ve türe eklenir. Değiştirebileceğiniz bir varsayılan ad verilir **Sınıf Tasarımcısı**, **sınıf ayrıntıları** penceresinde veya **özellikleri** penceresi.  
  
2.  İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.  
  
#### <a name="to-create-a-member-using-the-class-details-window-toolbar"></a>Sınıf Ayrıntıları Penceresi araç çubuğunu kullanarak üye oluşturmak için  
  
1.  Diyagram yüzeyinde, üye eklemek istediğiniz türü seçin.  
  
     Tür odağa gelir ve içeriği Sınıf Ayrıntıları penceresinde görüntülenir.  
  
2.  Sınıf Ayrıntıları penceresi araç çubuğunda en üstteki simgeye tıklayıp **yeni \<üye >** açılan listeden.  
  
     İşaretçiyi taşır **adı** alanında eklemek istediğiniz üye türü için bir satır. Örneğin tıkladıysanız **yeni özellik**, imleci yeni bir satıra taşır **özellikleri** sınıf Ayrıntıları penceresinde bölümünü.  
  
3.  Oluşturmak istediğiniz üyenin adını yazın ve Enter'a basın (ya da başka bir şekilde, örneğin, Sekme tuşuna basarak odağı taşıyın).  
  
     Yeni bir üye imzası oluşturulur ve türe eklenir. Üye artık kodun içinde vardır ve görüntülenen **Sınıf Tasarımcısı**, sınıf Ayrıntıları penceresinde ve Özellikler penceresinde.  
  
4.  İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.  
  
#### <a name="to-create-a-member-using-the-class-details-window"></a>Sınıf Ayrıntıları Penceresini kullanarak üye oluşturmak için  
  
1.  Diyagram yüzeyinde, üye eklemek istediğiniz türü seçin.  
  
     Tür odağa gelir ve içeriği Sınıf Ayrıntıları penceresinde görüntülenir.  
  
2.  Sınıf Ayrıntıları penceresinde, eklemek istediğiniz üye türünü içeren bölümde tıklayın  **\<Üye Ekle >**. Örneğin, bir alan eklemek istiyorsanız, tıklayın  **\<alan Ekle >**.  
  
3.  Oluşturmak istediğiniz üyenin adını yazın ve Enter'a basın.  
  
     Yeni bir üye imzası oluşturulur ve türe eklenir. Üye artık kodun içinde vardır ve görüntülenen **Sınıf Tasarımcısı**, sınıf Ayrıntıları penceresinde ve Özellikler penceresinde.  
  
4.  İsteğe bağlı olarak, üyeyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.  
  
     **Not:** üye oluşturmak için klavye kısayollarını kullanabilirsiniz. Daha fazla bilgi için [klavye ve Fare kısayolları sınıf diyagramında ve sınıf Ayrıntıları penceresi (Sınıf Tasarımcısı)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md).  
  
##  <a name="ModifyTypeMembers"></a> Tür üyelerini değiştirme  
 Sınıf Tasarımcısı, diyagram görüntülenen türlerin üyelerinde değişiklik yapmanıza olanak sağlar. Sınıf diyagramında görüntülenen ve salt okunur olmayan her türün üyelerini değiştirebilirsiniz. (Bkz [(Sınıf Tasarımcısı) salt okunur bilgileri görüntüleme](http://msdn.microsoft.com/en-us/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Tür üyelerini tasarım yüzeyinde, Özellikler penceresinde ve Sınıf Ayrıntıları penceresinde yerinde düzenleme yaparak değiştirirsiniz.  
  
 Sınıf Ayrıntıları penceresinde görüntülenen tüm üyeler sınıf diyagramındaki türlerin üyelerini temsil eder. Dört üye türü vardır: yöntemler, özellikler, alanlar ve olaylar.  
  
 Tüm üye satırları, üyeleri türe göre gruplandıran başlıkların altında görünür. Örneğin, tüm özellikleri başlığının altında görünür **özellikleri**, kılavuzdaki bir düğüm olarak daraltılabilen veya genişletilmiş.  
  
 Her üye satırı aşağıdaki öğeleri görüntüler:  
  
-   **Üye simgesi**  
  
     Her üyü türü kendi simgesiyle gösterilir. Üyenin imzasını görüntülemek için fareyi üye simgesinin üzerine getirin. Satırı seçmek için, üye simgesine ya da üye simgesinin solundaki boşluğa tıklayın.  
  
-   **Üye adı**  
  
     **Adı** bir üye satırındaki sütunu üyenin adını görüntüler. Bu ad ayrıca görüntülenen **adı** Özellikler penceresindeki özellik. Okuma/Yazma izinlerine sahip herhangi bir üyenin adını değiştirmek için bu hücreyi kullanın.  
  
     Varsa **adı** sütundur tam adı, fare üye adının üzerine getirildiğinde adın görüntüler adın tamamını görüntüleyemeyecek kadar darsa.  
  
-   **Üye türü**  
  
     **MemberType** hücresi geçerli projede veya başvurulan projelerde kullanılabilen tüm türlerin listesinden seçmenizi sağlar IntelliSense özelliğini kullanır.  
  
-   **Üye değiştiricisi**  
  
     Üye görünürlük değiştiricilerinin ya da değiştirme `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected``Friend` (`protected``internal`), veya `Default`.  
  
-   **\<Üye Ekle >**  
  
     Sınıf ayrıntıları penceresindeki son satır metni içeren  **\<Üye Ekle >** içinde **adı** hücre. Bu hücreye tıklarsanız yeni bir üye oluşturabilirsiniz. Daha fazla bilgi için [üyeleri oluşturma](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
-   **Özellikler penceresindeki üye özellikleri**  
  
     Sınıf Ayrıntıları penceresi, Özellikler penceresinde görüntülenen üye özelliklerinin bir alt kümesini görüntüler. Özelliğin bir konumda değiştirilmesi, özelliğin değerini global olarak güncelleştirir. Değerinin diğer konumda görüntülenmesi de buna dahildir.  
  
-   **Özet**  
  
     **Özet** hücresi üye hakkındaki bilgilerin bir özetini gösterir. Üç noktaya tıklayarak **özeti** hakkında bilgileri görüntüleyemez veya hücre **özeti**, **dönüş türü**, ve **açıklamalar** üyesi için .  
  
-   **Gizle**  
  
     Zaman **Gizle** onay kutusu seçiliyse, üye türü görüntülenmez.  
  
#### <a name="to-modify-a-type-member"></a>Bir tür üyesini değiştirmek için  
  
1.  Sınıf Tasarımcısı'nı kullanarak bir tür seçin.  
  
2.  Sınıf Ayrıntıları penceresi görüntülenmiyorsa, tıklayın **sınıf Ayrıntıları penceresi** Sınıf Tasarımcısı araç çubuğunda.  
  
3.  Sınıf Ayrıntıları penceresi kılavuzunun alanlarındaki değerleri düzenleyin. Her düzenlemeden sonra ENTER'a basın ya da bir başka yolla, örneğin SEKME tuşuna basarak, odağı düzenlenen alanın dışına taşıyın. Düzenlemeleriniz anında koda yansır.  
  
    > [!NOTE]
    >  Bir üyenin yalnızca adını değiştirmek istiyorsanız, bunu yerinde düzenlemeyi kullanarak yapabilirsiniz.  
  
##  <a name="AddMethodParams"></a> Yöntemlere parametreler ekleme  
 Sınıf Ayrıntıları penceresini kullanarak yöntemlere parametreler ekleyin. Parametreler, zorunlu veya isteğe bağlı olacak şekilde yapılandırılabilir. İçin bir değer sağlanması **isteğe bağlı varsayılan** özelliği, tasarımcıya kodu isteğe bağlı bir parametre olarak bildirir.  
  
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
  
   Bir üyenin son parametre satırı metni içeren **<add parameter>** içinde **adı** hücre. Bu hücreye tıklanması yeni bir parametre oluşturmanıza izin verir. Daha fazla bilgi için [bir yönteme parametre eklemek için](../ide/creating-and-configuring-type-members-class-designer.md#HowToAddParameterToMethod).  
  
  **Özellikler penceresindeki parametre özellikleri**  
  
  Özellikler penceresi sınıf Ayrıntıları penceresinde görüntülenen parametre özelliklerinin görüntüler: **adı**, **türü**, **değiştiricisi**, **özeti**, hem de **isteğe bağlı varsayılan** özelliği. Özelliğin bir konumda değiştirilmesi, özelliğin değerini global olarak güncelleştirir (değerinin diğer konumda görüntülenmesi de buna dahildir).  
  
> [!NOTE]
>  Bir temsilciye parametre eklemek için bkz [üyeleri oluşturma](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
> [!NOTE]
>  Yıkıcı üyesi bir yöntem olmasına karşın, parametrelere sahip olamaz.  
  
###  <a name="HowToAddParameterToMethod"></a> Bir yönteme parametre eklemek için  
  
1.  Diyagram yüzeyinde, parametre eklemek istediğiniz yöntemi içeren türe tıklayın.  
  
     Tür odağa gelir ve içeriği Sınıf Ayrıntıları penceresinde görüntülenir.  
  
2.  Sınıf Ayrıntıları penceresinde, parametre eklemek istediğiniz yöntemin satırını genişletin.  
  
     Yalnızca bir çift parantez ve sözcüklerini içeren girintili bir parametre satırı görünür  **\<parametre Ekle >.**  
  
3.  Tıklayın  **\<parametre Ekle >**, adını yeni parametre ve basın, **Enter**.  
  
     Yeni parametre yönteme ve yöntemin koduna eklenir. Sınıf Ayrıntıları penceresinde ve Özellikler penceresinde görünür.  
  
4.  İsteğe bağlı olarak, parametreyle ilgili diğer ayrıntıları (örneğin, türü) belirtin.  
  
### <a name="to-add-an-optional-parameter-to-a-method"></a>Bir yönteme isteğe bağlı parametre eklemek için  
  
1.  Diyagram yüzeyinde, isteğe bağlı parametre eklemek istediğiniz yöntemi içeren türe tıklayın.  
  
     Tür odağa gelir ve içeriği Sınıf Ayrıntıları penceresinde görüntülenir.  
  
2.  Sınıf Ayrıntıları penceresinde, isteğe bağlı parametre eklemek istediğiniz yöntemin satırını genişletin.  
  
     Yalnızca bir çift parantez ve sözcüklerini içeren girintili bir parametre satırı görünür  **\<parametre Ekle >.**  
  
3.  Tıklayın  **\<parametre Ekle >**, adını yeni parametre ve basın, **Enter**.  
  
     Yeni parametre yönteme ve yöntemin koduna eklenir. Sınıf Ayrıntıları penceresinde ve Özellikler penceresinde görünür.  
  
4.  Özellikler penceresinde için bir değer yazın **isteğe bağlı varsayılan** özelliği. Bir parametrenin İsteğe Bağlı Varsayılan özelliği ayarlandığında bu parametre isteğe bağlı olur.  
  
    > [!NOTE]
    >  İsteğe bağlı parametreler, parametre listesindeki en son parametreler olmalıdır.  
  
##  <a name="ClassDetailsUsageNotes"></a> Sınıf ayrıntıları kullanım notları  
 Sınıf Ayrıntıları penceresinin kullanımına ilişkin aşağıdaki ipuçlarına dikkat edin.  
  
 **Düzenlenebilir ve düzenlenemez hücreler**  
  
 Bir kaç özel durum dışında, Sınıf Ayrıntıları penceresindeki tüm hücreler düzenlenebilir:  
  
- Türün tamamı salt okunur olduğunda, örneğin başvurulan bir derlemede yer alıyor (bkz [salt okunur bilgilerini görüntüleme (Sınıf Tasarımcısı)](http://msdn.microsoft.com/en-us/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Sınıf Tasarımcısı'nda şekli seçtiğinizde, Sınıf Ayrıntıları penceresi ilgili ayrıntıları salt okunur halde görüntüler.  
  
- Dizin oluşturucular için, ad bilgisi salt okunur ve geri kalanı (tür, değiştirici, özet) düzenlenebilir özelliktedir.  
  
- Tüm genel öğeler Sınıf Ayrıntıları penceresinde salt okunur parametrelere sahiptir. Bir genel parametreyi değiştirmek için kaynak kodunu düzenleyin.  
  
- Genel türde tanımlanan tür parametresinin adı salt okunurdur.  
  
- Türün kodu bozuk (çözümlenemez) olduğunda, Sınıf Ayrıntıları penceresi türün içeriğini salt okunur olarak görüntüler.  
  
  **Sınıf Ayrıntıları penceresi ve kaynak kodu**  
  
- Kaynak kodunu, Sınıf Ayrıntıları (veya Sınıf Tasarımcısı) penceresinde bir şekle sağ tıklayıp ardından Kodu Görüntüle'ye tıklayarak görüntüleyebilirsiniz. Kaynak kodu dosyası açılır ve seçili öğeye kadar ilerler.  
  
- Kaynak kodunun değiştirilmesi, Sınıf Tasarımcısı ve Sınıf Ayrıntıları penceresinde imza bilgilerinin görüntüsüne anında yansıtılır. Sınıf Ayrıntıları penceresi bu sırada kapalıysa, pencereyi bir sonraki açışınızda yeni bilgiler görülür.  
  
- Türün kodu bozuk (çözümlenemez) olduğunda, Sınıf Ayrıntıları penceresi türün içeriğini salt okunur olarak görüntüler.  
  
  **Sınıf Ayrıntıları penceresinde Pano işlevselliği**  
  
  Sınıf Ayrıntıları penceresinden alanları veya satırları kopyalayabilir ya da kesebilir ve bunları başka bir türe yapıştırabilirsiniz. Bir satırı ancak salt okunur ise kesebilirsiniz. Satırı yapıştırdığınızda, Sınıf Ayrıntıları penceresi çakışma olmasını önlemek için yeni bir ad (kopyalanan satırın adından türetilir) atar.  
  
##  <a name="ReadOnlyInfo"></a> Salt okunur bilgileri görüntüleme  
 Sınıf Tasarımcısı ve Sınıf Ayrıntıları penceresi aşağıdaki öğeler için türleri (ve türlerin üyelerini) görüntüleyebilir:  
  
- Sınıf diyagramı içeren bir proje  
  
- Sınıf diyagramı içeren bir projeden başvurulan proje  
  
- Sınıf diyagramı içeren bir projeden başvurulan derleme  
  
  Sonraki iki durum için, başvurulan varlık (bir tür veya üye) temsil ettiği sınıf diyagramında salt okunurdur.  
  
  Bir projenin tamamı ya da kısımları (tek tek dosyalar gibi) salt okunur olabilir. Projenin veya dosyalarından birinin salt okunur olduğu en yaygın durumlar, bir kaynak kodu denetiminin altında olduğu (ve kullanıma alınmamış), bir dış derlemede var olduğu veya işletim sisteminin dosyaları salt okunur olarak düşündüğü durumlardır.  
  
  **Kaynak kodu denetimi**  
  
  Sınıf diyagramı projenin içine bir dosya olarak kaydedildiğinden, Sınıf Tasarımcısı veya Sınıf Ayrıntıları penceresinde yaptığınız değişiklikleri kaydetmek için projeyi kullanıma almanız gerekir.  
  
  **Salt okunur projeler**  
  
  Proje, kaynak kodu denetimi dışındaki bir nedenle salt okunur olabilir. Proje kapatıldığında, proje dosyasının üzerine mi yazılacağını, değişikliklerin yok mu sayılacağını(kaydetme) ya da kapatma işleminin iptal mi edileceğini soran bir iletişim kutusu görüntülenir. Üzerine yazmayı tercih ederseniz proje dosyalarının üzerine yazılır ve okuma/yazma özellikli yapılırlar. Yeni sınıf diyagramı dosyası eklenir.  
  
  **Salt okunur türler**  
  
  Kaynak kodu dosyası salt okunur bir türü içeren bir projeyi kaydetmeyi denerseniz **salt okunur dosyanın kaydı** iletişim kutusu görüntülenirse, dosyayı yeni bir ad veya yeni bir konuma veya salt okunur dosyanın üzerine yazma seçenekleri sunar . Dosyanın üzerine yazarsanız yeni kopyası artık salt okunur özellikte olmaz.  
  
  Bir Kod dosyası sözdizimi hatası içeriyorsa, bu dosyadaki kodu gösteren şekiller söz dizimi hatası düzeltilinceye kadar geçici olarak salt okunur olur. Bu durumdaki şekiller, "Kaynak kodu dosyası ayrıştırma hatası içeriyor" yazılı araç ipucunu gösteren kırmızı bir metin ve kırmızı bir simge görüntüler.  
  
  Başka bir proje düğümü altında ya da başvurulan bir derleme düğümü altında bulunan bir başvurulan tür (.NET Framework türü gibi), Sınıf Tasarımcısı'nın tasarım yüzeyinde salt okunur olarak belirtilir. Açık durumda bulunan projede var olan bir yerel tür okuma/yazma özelliklidir ve Sınıf Tasarımcısı'nın tasarım yüzeyindeki şekli de böyle belirtilir.  
  
  Dizin oluşturucular kod içinde ve Sınıf Ayrıntıları penceresinde okuma/yazma özelliklidir, ancak dizin oluşturucunun adı salt okunurdur.  
  
  Kısmi yöntemleri Sınıf Tasarımcısı veya Sınıf Ayrıntıları penceresini kullanarak düzenleyemezsiniz; bunları düzenlemek için Kod Düzenleyicisi'ni kullanmanız gerekir.  
  
  Yerel C++ kodunu Sınıf Tasarımcısı veya Sınıf Ayrıntıları penceresini kullanarak düzenleyemezsiniz; yerel C++ kodunu düzenlemek için Kod Düzenleyicisi'ni kullanmanız gerekir.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Türleri ve İlişkilendirmeleri Görüntüleme (Sınıf Tasarımcısı)](../ide/viewing-types-and-relationships-class-designer.md)|Varolan türlerinizi, üyelerinizi ve ilişkilerinizi bir sınıf diyagramında görüntüleyebilirsiniz.|  
|[Sınıfları ve Türleri Yeniden Düzenleme (Sınıf Tasarımcısı)](../ide/refactoring-classes-and-types-class-designer.md)|Yeniden düzenlemeyi kullanarak türü ve tür üyelerini kolayca yeniden adlandırabilirsiniz. Ayrıca, sınıflar arasında üye taşıyabilir, bir sınıfı kısmi sınıflara bölebilir ve arabirimler uygulayabilirsiniz.|