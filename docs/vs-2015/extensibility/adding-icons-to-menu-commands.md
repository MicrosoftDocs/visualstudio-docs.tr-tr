---
title: Menü komutlarına simge ekleme | Microsoft Docs
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
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d10659487d9a747e2359f8fa2e68122b0938a77d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768132"
---
# <a name="adding-icons-to-menu-commands"></a>Menü Komutlarına Simge Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Komutlar, menüler ve araç çubuklarında görünebilir. Araç çubukları bir komut normalde bir simge ve metin ile görünür (alanından tasarruf etmek için) yalnızca bir simge ile menülerde görüntülenecek bir komut yaygındır.  
  
 Simgeler 16 piksel genişliğinde ve 16 piksel yüksekliğinde ve 8-bit renk derinliği (256 renk) ya da 32 bit renk derinliği (gerçek renk) olabilir. 32 bit renk simgelerinin genişliğini tercih edilir. Birden çok bit eşlemleri izin verilmese de simgeleri genellikle tek bir bit eşlem tek bir yatay satır halinde düzenlenir. Bu bit eşlem bit eşlem içinde kullanılabilir tek tek simgeler birlikte .vsct dosyası içinde bildirilir. İşinize yarayacak [Bitmaps öğesi](../extensibility/bitmaps-element.md) daha fazla ayrıntı için.  
  
## <a name="adding-an-icon-to-a-command"></a>Komut için bir simge ekleme  
 Aşağıdaki yordam, mevcut VSPackage projesinde bir menü komutu ile sahibi olduğunuzu varsayar. Bunu yapmak nasıl öğrenmek için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Bir bit eşlem 32 bit renk derinliği ile oluşturun. Bir simge, her zaman 16 x 16 bit eşlem bu 16 piksel yüksekliğinde olması gerekir ve katı 16 piksel genişliğinde bulunur.  
  
     Her simge tek bir satırda yan yana bir bit eşlem yerleştirilir. Alfa kanalını saydamlık her simgesi yerleri belirtmek için kullanın.  
  
     Pembe, 8-bit renk derinliği kullanırsanız kullanın `RGB(255,0,255)`, saydam olarak. Ancak, 32 bit renk simgelerinin genişliğini tercih edilir.  
  
2.  Simge dosyası VSPackage projenizdeki kaynakları dizinine kopyalayın. Çözüm Gezgini'nde projeye simgesi ekleyin. (Kaynakları seçin ve bağlam menüsünde Ekle, var olan öğeyi tıklatın ve simge dosyanızı seçin.)  
  
3.  .Vsct Dosyası Düzenleyicisi'nde açın.  
  
4.  Ekleme bir `GuidSymbol` öğe adıyla **testIcon**. Bir GUID oluştur (**Araçlar / oluşturma GUID**, ardından **biçimi kayıt defteri** ve Kopyala) yapıştırın `value` özniteliği. Sonuç şu şekilde görünmelidir:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Ekleme bir `<IDSymbol>` simgesi. `name` Özniteliktir simgesinin kimliği ve `value` varsa şeridindeki konumunu gösterir. Yalnızca bir simge varsa, 1 ekleyin. Sonuç şu şekilde görünmelidir:  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Oluşturma bir `<Bitmap>` içinde `<Bitmaps>` simgelerini içeren bit eşlem temsil etmek için .vsct dosyası bölümünü.  
  
    -   Ayarlama `guid` adı değerine `<GuidSymbol>` önceki adımda oluşturduğunuz öğesi.  
  
    -   Ayarlama `href` bit eşlem dosyasının göreli yolunu değerine (Bu durumda **kaynakları\\< simge dosyası adı\>**.  
  
    -   Ayarlama `usedList` daha önce oluşturduğunuz Idsymbol değeri. Bu öznitelik içinde VSPackage kullanılacak simgeleri virgülle ayrılmış bir listesini belirtir. Listede olmayan simgeler dışlanan form derleme var.  
  
         Bit eşlem bloğu gibi görünmelidir:  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  Mevcut `<Button>` öğe, ayarladığınız `Icon` daha önce oluşturduğunuz değerlerine GUIDSymbol ve Idsymbol öğesi. Bu değerleri içeren bir Button öğesi, bir örnek aşağıda verilmiştir:  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  Simge test edin. Projeyi oluşturmak ve hata ayıklamaya başlayın. Deneysel örneğinde komutu bulun. Eklediğiniz simgesi gösterilmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Menüleri ve komutlari genişletme komutları](../extensibility/extending-menus-and-commands.md)   
 [VSCT XML Şeması Başvurusu](../extensibility/vsct-xml-schema-reference.md)

