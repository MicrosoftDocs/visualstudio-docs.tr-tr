---
title: Eski dil hizmetinde gezinti çubuğu desteği | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3ca2b29ca942287180df45629c40a4f38e7a573
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918161"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Gezinti Çubuğu için Destek
Düzenleyici görünümü, üst gezinti çubuğunda, türler ve üyeler dosyayı görüntüler. Türleri sol açılan menü gösterilir ve üyeleri sağındaki açılan gösterilir. Kullanıcı türü seçtiğinde kelimeyi ilk satırın türü yerleştirilir. Kullanıcı bir üye seçtiğinde, giriş işaretini üyenin tanımını yerleştirilir. Açılan kutu, geçerli giriş işareti konumunu gösterecek şekilde güncelleştirilir.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Görüntüleme ve gezinti çubuğunu güncelleştiriliyor  
 Gezinti çubuğu desteklemek için öğesinden bir sınıf türetin <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> sınıfı ve uygulama <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> yöntemi. Ne zaman, dil hizmeti verildiğinde bir kod penceresinde, temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı başlatır <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, içeren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> kod penceresini temsil eden nesne. <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Nesne ardından verildiğinde yeni bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesne. <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Yöntemi alır bir <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> nesne. Örneği döndürürse, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> sınıfı <xref:Microsoft.VisualStudio.Package.CodeWindowManager> çağrıları, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> iç doldurmak için yöntem listeler ve geçirir, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> nesnesini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] manager çubuğu açılır. Aşağı açılan yöneticisini, sırasıyla çağırır <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> yöntemi, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> oluşturmak için nesne <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> iki açılan çubuklarını tutan nesne.  
  
 Giriş işaretini hareket ettirdiğinde <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> yöntem çağrılarını <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> yöntemi. Temel <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> yöntem çağrılarını <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> yönteminde, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> gezinti çubuğunun durumunu güncellemek için sınıf. Bir dizi geçirdiğiniz <xref:Microsoft.VisualStudio.Package.DropDownMember> bu yönteme nesneleri. Her nesne açılan bir giriş temsil eder.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Gezinti çubuğu içeriği  
 Gezinti çubuğu genellikle türlerinin bir listesini ve üye listesini içerir. Türleri listesinde geçerli bir kaynak dosyasında mevcut tüm türleri içerir. Tür adları, tam ad alanı bilgileri içerir. İki tür ile C# koduna ilişkin bir örnek verilmiştir:  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 Tür listesi görüntüler `TestLanguagePackage.TestLanguageService` ve `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 Kullanılabilir üyeler türleri listede seçilen türündeki üye listesi görüntüler. Yukarıdaki kod örneğinde kullanılarak `TestLanguagePackage.TestLanguageService` seçildiğinde, türü özel üyeler üye listesi içerecektir `tokens` ve `serviceName`. İç yapısı `Token` görüntülenmez.  
  
 Giriş işaretini kopyalayıp içine yerleştirildiğinde, bir üyenin adını kalınlaştırmak için üye listesi uygulayabilirsiniz. Üyeleri ayrıca gri metin düzenini giriş işaretini geçerli nerede konumlandırılmış kapsamında olmadıklarını belirten görüntülenebilir.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Gezinti çubuğu desteği etkinleştirme  
 Gezinti çubuğu desteğini etkinleştirmek için ayarlamalısınız `ShowDropdownBarOption` parametresinin <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> özniteliğini `true`. Bu parametre ayarlar <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> özelliği. Gezinti çubuğu desteklemek için uygulamanız gereken <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> nesnesine <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodunda <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı.  
  
 Uygulamanızda <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> yöntemi varsa <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> özelliği `true`, geri dönebilirsiniz bir <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> nesne. Nesne döndürmezse, gezinti çubuğunda görüntülenmez.  
  
 Düzenleyici görünümü açıkken sıfırlamak bu denetim için mümkün olduğu için gezinti çubuğunu göster seçeneği kullanıcı tarafından ayarlanabilir. Kullanıcı, kapatın ve değişiklik gerçekleşmeden önce düzenleyici penceresini yeniden açın.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Gezinti çubuğu desteği sağlama  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Yöntemi iki liste (bir her bir açılan menü) ve her bir listedeki geçerli seçimi temsil eden iki değer alır. Listeler ve seçim değerleri, bu durumda güncelleştirilebilir <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> yöntemi döndürmelidir `true` listeleri değiştiğini göstermek için.  
  
 Seçimi açılan türlerinde değiştikçe üye listesi yeni türü yansıtacak şekilde güncelleştirilmesi gerekir. Üye listesinde gösterilen olabilir:  
  
- Geçerli tür üye listesi.  
  
- Tüm kullanılabilir olan üyelerin kaynak dosya, ancak geçerli türü değil, tüm üyeleri grileştirilmiş metni görüntülenir. Kullanıcı Hızlı gezinme için kullanılabilir, ancak bunlar şu anda seçili türün bir parçası olmadığını rengini belirtir. Bu nedenle grileştirilmiş üyelerini seçebilirsiniz.  
  
  Uygulanışı <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> yöntemi genellikle aşağıdaki adımları gerçekleştirir:  
  
1.  Kaynak dosyası için geçerli bildirimleri bir listesini alın.  
  
     Çeşitli yollarla listelerini doldurmak için vardır. Bir yaklaşım ise özel bir yönteme sürümünüze oluşturmak için <xref:Microsoft.VisualStudio.Package.LanguageService> çağıran sınıfı <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi bir özel ayrıştırma sebeple tüm bildirimleri listesini döndürür. Çağırmak için başka bir yaklaşım olabilir <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi doğrudan <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> özel ayrıştırma nedeni yöntemi. Bildirimler önbelleğe almak için üçüncü bir yaklaşım olabilir <xref:Microsoft.VisualStudio.Package.AuthoringScope> son tam ayrıştırma işlemi tarafından döndürülen sınıfı <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı ve buradan almak <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> yöntemi.  
  
2.  Doldurmak veya türlerinin listesi güncelleştirilemiyor.  
  
     Kaynak değiştiğinde veya geçerli giriş işareti konumuna bağlı türleri metin stilini değiştirme seçtiyseniz güncelleştirilmesini türleri listesi içeriğini olabilir. Bu konum için geçirilen Not <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> yöntemi.  
  
3.  Geçerli giriş işareti konumuna bağlı türleri listesinde seçilecek türünü belirleyin.  
  
     Geçerli giriş işareti konumunu kapsayan türü bulmak için 1. adımda edinilen bildirimleri arayın ve sonra da türüne türlerini listesine dizinini belirlemek türler listesinde arama yapın.  
  
4.  Doldurmak veya seçilen türe göre üye listesini güncelleştirin.  
  
     Üye listesi içinde görüntülenenleri yansıtır **üyeleri** açılır. Üye listesi içeriğini kaynak değiştiyse veya yalnızca seçili türün üyeleri görüntülediğiniz ve seçili türünü değiştirdi güncelleştirilmesi gerekebilir. Kaynak dosyadaki tüm üyelerini görüntülemeyi seçerseniz, listedeki her bir üyesinin metin stili oluşturma, şu anda seçili türün değiştiyse güncelleştirilmesi gerekir.  
  
5.  Geçerli giriş işareti konumuna bağlı üye listesi seçmek için üye belirleyin.  
  
     Edinilen bildirimleri geçerli giriş işareti konumunu içeren bir üye için 1. adımda arayın ve ardından üye listesinde üye listesine dizinini belirlemek bu üye için arama yapın.  
  
6.  Dönüş `true` listeleri ya da her iki listesinden seçim için herhangi bir değişiklik yapılmadıysa.