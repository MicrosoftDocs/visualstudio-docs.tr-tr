---
title: Menü öğelerine klavye kısayolları bağlama | Microsoft Docs
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
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5fd5ab9b09956c41620947ad1bcf529550db4aca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752904"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Menü Öğelerine Klavye Kısayolları Bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel menü komutu için klavye kısayolu bağlamak için yalnızca paketin .vsct dosyası için bir giriş ekleyin. Bu konu, bir özel düğme, menü öğesi ya da araç çubuğu komutuna bir klavye kısayolu eşlemeyle ilgili bilgi ve varsayılan Düzenleyicisi'nde klavye eşleme uygulamak veya özel bir düzenleyici sınırlandırmak nasıl açıklar.  
  
 Mevcut Visual Studio menü öğelerine klavye kısayolları atamak için bkz: [tanımlama ve özelleştirme klavye kısayolları](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Bir tuş bileşimi seçme  
 Çok sayıda klavye kısayolları Visual Studio'da zaten kullanıldı. Yinelenen bağlamalar algılamak daha zordur ve aynı zamanda, öngörülemeyen sonuçlara neden olabilir çünkü aynı kısayol için birden fazla komut atamalıdır değil. Bu nedenle, bunu atamadan önce bir kısayol kullanılabilirliğini doğrulamak için bir fikirdir.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Klavye kısayolu kullanılabilirliğini doğrulamak için  
  
1. İçinde **Araçlar / Seçenekler / ortam** penceresinde **klavye**.  
  
2. Emin olun **kullanım yeni kısayolu şunun içinde** ayarlanır **genel**.  
  
3. İçinde **kısayol tuşlarına basın** kutusuna, kullanmak istediğiniz klavye kısayolunu yazın.  
  
    Visual Studio'da kısayol zaten kullanılıyorsa **şu anda kullandığı kısayolunu** kısayol şu anda çağıran komut kutusu gösterir.  
  
4. Anahtarları farklı birleşimlerini eşlenmemiş bir tane bulana kadar deneyin.  
  
   > [!NOTE]
   >  ALT kullanan klavye kısayolları bir menüyü açabilirsiniz ve doğrudan bir komut yürütün. Bu nedenle, **şu anda kullandığı kısayolunu** ALT içeren bir kısayol yazarken kutusu boş olabilir. Kısayol menü kapanış açmaz doğrulayabilirsiniz **seçenekleri** iletişim kutusunu ve ardından tuşlarına basarak.  
  
   Aşağıdaki yordamda, bir menü komutu ile var olan bir VSPackage sahibi olduğunuzu varsayar. Böylece yardıma ihtiyacınız olursa, göz atın [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Bir komut için klavye kısayolu atamak için  
  
1. Paketiniz için .vsct dosyası açın.  
  
2. Boş bir oluşturma `<KeyBindings>` sonra bölüm `<Commands>` zaten mevcut değilse.  
  
   > [!WARNING]
   >  Tuş bağlamaları hakkında daha fazla bilgi için bkz: [tuş](../extensibility/keybinding-element.md).  
  
    İçinde `<KeyBindings>` bölümünde, oluşturun bir `<KeyBinding>` girişi.  
  
    Ayarlama `guid` ve `id` öznitelikler bu istediğiniz çağrılacak komutu.  
  
    Ayarlama `mod1` özniteliğini **denetimi**, **Alt**, veya **Shift**.  
  
    KeyBindings bölümü şöyle görünmelidir:  
  
   ```xml  
   <KeyBindings>  
       <KeyBinding guid="<name of command set>" id="<name of command id>"  
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
   </KeyBindings>  
  
   ```  
  
   Klavye kısayolu ikiden fazla anahtar gerektirdiği verilirse `mod2` ve `key2` öznitelikleri.  
  
   Çoğu durumda **Shift** ikinci bir değiştiricisi zaten tuşuna basarak bir büyük harf ya da bir simge türünü çoğu alfasayısal anahtarları neden olduğu için kullanılmamalıdır.  
  
   Sanal anahtar kodlarını denetlemenize olanak tanır, örneğin, işlev tuşlarını ilişkili bir karakter olmayan özel anahtarlarına erişmek ve **geri** anahtarı. Daha fazla bilgi için [sanal anahtar kodlarını](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
   Komut Visual Studio Düzenleyicisi'ni kullanabilmek için ayarlanmış `editor` özniteliğini `guidVSStd97`.  
  
   Komutu yalnızca özel bir düzenleyici içinde kullanılabilir hale getirmek için ayarlanmış `editor` öznitelik tarafından oluşturulan özel düzenleyici adına [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] paket VSPackage'ı oluşturduğunuzda şablonu, özel bir düzenleyici içerir. Ad değerini bulmak için konum `<Symbols>` bölümü bir `<GuidSymbol>` düğümü olan `name` özniteliği içinde sona erecek "`editorfactory`." Özel düzenleyici adıdır.  
  
## <a name="example"></a>Örnek  
 Bu örnek adlı bir komut için CTRL + ALT + C klavye kısayolunu bağlar `cmdidMyCommand` adlı bir paket içinde `MyPackage`.  
  
```  
<CommandTable>  
. . .  
<Commands>  
. . .  
</Commands>  
<KeyBindings>  
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"   
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />  
</KeyBindings>  
. . .  
</CommandTable>  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek adlı bir komut için klavye kısayolunu CTL + B bağlar `cmdidBold` adlı bir projedeki `TestEditor`. Komutu, yalnızca özel Düzenleyicisi'nde ve diğer düzenleyicilerde kullanılabilir.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Menüleri ve Komutlari Genişletme](../extensibility/extending-menus-and-commands.md)

