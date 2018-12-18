---
title: DLL projelerinde hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/06/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c00740b31e5b9d7cc5678bfc248e673a57e59ccf
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305318"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio DLL'lerde hata ayıklama (C#, C++, Visual Basic F#)

Bir DLL (dinamik bağlantı kitaplık) kodu ve birden fazla uygulama tarafından kullanılan verileri içeren bir kitaplıktır. Visual Studio kullanan oluşturabilir, oluşturmak, yapılandırmak ve DLL'lerin hata ayıklama. 

## <a name="create-a-dll"></a>Bir DLL oluşturma

Aşağıdaki Visual Studio Proje şablonları, DLL'leri oluşturabilirsiniz:

- C#, Visual Basic veya F# sınıf kitaplığı 
- C#veya Visual Basic Windows Forms Denetim (WCF) kitaplığı 
- C++ dinamik bağlantı kitaplığı (DLL)

Daha fazla bilgi için [MFC hata ayıklama tekniklerine](../debugger/mfc-debugging-techniques.md).

Bir WCF kitaplık hata ayıklama bir sınıf kitaplığı hatalarının ayıklanmasına benzer. Ayrıntılar için bkz [Windows Forms denetimleri](/dotnet/framework/winforms/controls/index).  

Genellikle başka bir projeden bir DLL çağırın. DLL yapılandırmasına bağlı olarak, arama projede hata ayıklaması yaparken adımlama ve hata ayıklama DLL kodu. 

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> DLL hata ayıklama yapılandırması

Bir uygulama oluşturmak için Visual Studio Proje şablonu kullandığınızda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hata ayıklama ve yayın derleme yapılandırmaları için gereken ayarları otomatik olarak oluşturur. Gerekirse, bu ayarları değiştirebilirsiniz. Daha fazla bilgi için aşağıdaki makalelere bakın:

- [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Proje ayarlarını C# hata ayıklama yapılandırmaları](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Nasıl yapılır: kümesi hata ayıklama ve yayın yapılandırmaları](../debugger/how-to-set-debug-and-release-configurations.md)  
  
### <a name="set-c-debuggableattribute"></a>C++ DebuggableAttribute ayarlayın

C++ DLL'ye iliştirmek hata ayıklayıcının C++ kodu yaymalıdır `DebuggableAttribute`. 

**Ayarlanacak `DebuggableAttribute`:**

1. C++ DLL projesinde seçin **Çözüm Gezgini** seçip **özellikleri** simgesini veya projeye sağ tıklayıp seçin **özellikleri**. 
   
1. İçinde **özellikleri** bölmesi altında **bağlayıcı** > **hata ayıklama**seçin **Evet (/ ASSEMBLYDEBUG)** için  **Hatası ayıklanabilir bütünleşmiş kod**. 

Daha fazla bilgi için [assemblydebug](/cpp/build/reference/assemblydebug-add-debuggableattribute).  

### <a name="vxtskdebuggingdllprojectsexternal"></a> C/C++ DLL dosyası konumlarını ayarlama 

Dış bir DLL'de hata ayıklamak için bir arama proje DLL bulmak için olmalıdır, [.pdb dosyasını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)ve diğer dosyaları DLL gerektirir. Bu dosyaları kopyalamak için bir özel yapı görev oluşturabilir,  *\<proje klasörü > \Debug* çıktı klasörü veya kopyalayabilir dosyaların el ile.

C/C++ projeleri için çıktı klasörüne kopyalamak yerine projenin özellik sayfalarındaki üstbilgi ve LIB dosya konumları ayarlayabilirsiniz. 

**C/C++ ayarlanacak üstbilgi ve LIB dosya konumları:**

1. C/C++ DLL projesinde seçin **Çözüm Gezgini** seçip **özellikleri** simgesini veya projeye sağ tıklayıp seçin **özellikleri**. 
   
1. Üst kısmındaki **özellikleri** bölmesi altında **yapılandırma**seçin **yapılandırmalarında**.
   
1. Altında **C/C++** > **genel** > **ek içerik dizinleri**, üst bilgi dosyalarını içeren klasörü belirtin.
   
1. Altında **bağlayıcı** > **genel** > **ek kitaplıklar dizinleri**, LIB dosyalarını içeren klasörü belirtin. 
   
1. Altında **bağlayıcı** > **giriş** > **ek bağımlılıklar**, LIB dosyalar için dosya adı ve tam yolunu belirtin.

1. Seçin **Tamam**.

C++ proje ayarları hakkında daha fazla bilgi için bkz. [özellik sayfaları (Visual C++)](/cpp/ide/property-pages-visual-cpp).
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Hata ayıklama sürümü oluşturma  

DLL hata ayıklama sürümünü hata ayıklamaya başlamadan önce oluşturduğunuzdan emin olun. Bir DLL'de hata ayıklamak için bir arama uygulaması bulamadı olmalıdır, [.pdb dosyasını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) ve diğer dosyaları DLL gerektirir. 

DLL dosyaları kopyalamak için bir özel yapı görev oluşturabilir,  *\<proje klasörü çağırma > \Debug* çıktı klasörü veya kopyalayabilir dosyaların el ile.

DLL, doğru konumda çağırdığınızdan emin olun. Bu belirgin görünebilir, ancak bir arama uygulaması bulur ve DLL farklı bir kopyasını yükler, hata ayıklayıcı hiç ayarladığınız kesme noktaları isabet. 

##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Bir DLL'nin hatasını ayıklayın  

Bir DLL'yi doğrudan çalıştıramazsınız. Bu genellikle bir uygulama tarafından çağrılmalıdır bir *.exe* dosya. Daha fazla bilgi için [oluşturun ve Visual C++ projeleri yönetme](/cpp/ide/creating-and-managing-visual-cpp-projects). 

Bir DLL'de hata ayıklamak için [çağıran uygulamadan hata ayıklamayı Başlat](#vxtskdebuggingdllprojectsthecallingapplication), veya [DLL projesinde hata ayıklama](how-to-debug-from-a-dll-project.md) , çağıran uygulama belirterek. Hata ayıklayıcı ayrıca kullanabileceğiniz [komut penceresi](#vxtskdebuggingdllprojectstheimmediatewindow) DLL işlevleri veya yöntemleri çağıran bir uygulama kullanmadan tasarım zamanında değerlendirilemiyor.

Daha fazla bilgi için [hata ayıklayıcısını kullanmaya başlama](getting-started-with-the-debugger.md).

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Çağıran uygulamadan gelen hata ayıklamayı Başlat

Bir DLL çağıran uygulama aşağıdakilerden biri olabilir:  
  
- Bir uygulamadan bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aynı veya farklı bir DLL çözümden bir proje.  
- Zaten dağıtılmış mevcut bir uygulama ve bir test veya üretim bilgisayarda çalışıyor.  
- Web'de bulundu ve bir URL yoluyla erişildi.  
- Bir web uygulaması bir web sayfasıyla DLL katıştırır.  
  
Çağıran bir uygulamadan bir DLL'de hata ayıklamak için şunları yapabilirsiniz:  
  
- Arama uygulaması için projeyi açmak ve seçerek hata ayıklamayı Başlat **hata ayıklama** > **hata ayıklamayı Başlat** ya basarak **F5**.  

  veya  

- Dağıtılan ve çalışan bir test veya üretim bilgisayarda zaten olan bir uygulama ekleyin. Bu yöntem, Web sitelerinde veya web apps'te DLL'leri için kullanın. Daha fazla bilgi için [nasıl yapılır: çalışan bir işleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Çağıran uygulamada hata ayıklamaya başlamadan önce DLL'de bir kesme noktası ayarlayın. Bkz: [kesme noktalarını kullanma](../debugger/using-breakpoints.md). DLL kesme noktası isabet edildiğinde, her bir satırdaki eylemi gözleme kodda adım adım. Daha fazla bilgi için [hata ayıklayıcısı koda gitmek](../debugger/navigating-through-code-with-the-debugger.md).
  
Hata ayıklama sırasında kullanabilirsiniz **modülleri** DLL'leri doğrulamak için penceresi ve *.exe* uygulama yükleri dosyaları. Açmak için **modülleri** hata ayıklarken, penceresinde **hata ayıklama** > **Windows** > **modülleri**. Daha fazla bilgi için [nasıl yapılır: modüller penceresini kullanma](../debugger/how-to-use-the-modules-window.md). 

###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Komut penceresi kullanın  

Kullanabileceğiniz **hemen** penceresi DLL işlevleri veya yöntemleri, tasarım zamanında değerlendirilemiyor. **Hemen** penceresi çağıran bir uygulama rolü oynar. 

>[!NOTE]
>Kullanabileceğiniz **hemen** penceresi ile çoğu proje türü tasarım zamanında. SQL, web projeleri veya komut dosyası için desteklenmiyor.

Örneğin, bir yöntem test etmek için adlı `Test` sınıfında `Class1`:

1. DLL projesi açık açın **hemen** penceresini seçerek **hata ayıklama** > **Windows** > **hemen**ya basarak **Ctrl**+**Alt**+**miyim**.  
   
1. Türünde bir nesne örneği `Class1` aşağıdakileri yazarak C# kod **hemen** penceresi ve tuşlarına basarak **Enter**. Bu yönetilen kod için çalışır C# ve uygun sözdizimini değişikliklerle birlikte, Visual Basic:  
   
   ```csharp
   Class1 obj = new Class1();  
   ```  
  
   İçinde C#, tüm adlar tam olarak nitelenmiş olmalıdır. İfadeyi değerlendirmek dil hizmeti çalıştığında, yöntemlerin veya değişkenlerin geçerli kapsamda ve bağlam içinde olmalıdır.  
   
1. Varsayarak `Test` alır `int` parametresi değerlendirmek `Test` kullanarak **hemen** penceresi:  
   
   ```csharp
   ?obj.Test(10);  
   ```  
   
   İçinde sonucu yazdırmaya **hemen** penceresi.  
   
1. Hata ayıklamaya devam edebilirsiniz `Test` içine bir kesme noktası yerleştirerek ve sonra işlevi yeniden değerlendirerek.  
   
   Kesme noktasına isabet edilir ve adım adım `Test`. Yürütme ayrıldıktan sonra `Test`, hata ayıklayıcı, Tasarım modunda olur.

##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Karışık mod hata ayıklama  

Yönetilen veya yerel kodda bir DLL için çağıran bir uygulama yazabilirsiniz. Yönetilen bir DLL'yi yerel uygulamanızı çağırır ve her ikisi de hata ayıklamak istediğiniz, hem yönetilen hem de yerel hata ayıklayıcıları Proje Özellikleri'nde etkinleştirebilirsiniz. Tam geçiş işlemi, DLL projesi veya arama uygulama projesinde hata ayıklamayı başlatmak istediğinize bağlıdır. Daha fazla bilgi için [nasıl yapılır: karışık modda hata ayıklama](../debugger/how-to-debug-in-mixed-mode.md). 

Ayrıca yerel bir DLL yönetilen arama projesinden ayıklayabilirsiniz. Daha fazla bilgi için [yönetilen ve yerel kodda hata ayıklamak nasıl](how-to-debug-managed-and-native-code.md). 

## <a name="see-also"></a>Ayrıca bkz.  
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Visual C++ proje türleri](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#, F#ve Visual Basic proje türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Proje ayarlarını C# hata ayıklama yapılandırmaları](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
