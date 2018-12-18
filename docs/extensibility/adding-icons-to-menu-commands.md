---
title: Menü komutlarına simge ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0d01e64915004eb21a92c21a67291dc4f034112d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155026"
---
# <a name="add-icons-to-menu-commands"></a>Menü komutlarına simge ekleme
Komutlar, menüler ve araç çubuklarında görünebilir. Araç çubukları bir komut normalde bir simge ve metin ile görünür (alanından tasarruf etmek için) yalnızca bir simge ile menülerde görüntülenecek bir komut yaygındır.  
  
 Simgeler 16 piksel genişliğinde ve 16 piksel yüksekliğinde ve 8-bit renk derinliği (256 renk) ya da 32 bit renk derinliği (gerçek renk) olabilir. 32 bit renk simgelerinin genişliğini tercih edilir. Birden çok bit eşlemleri izin verilmese de simgeleri genellikle tek bir bit eşlem tek bir yatay satır halinde düzenlenir. Bu bit eşlem içinde bildirildiği *.vsct* bit eşlem içinde kullanılabilir tek tek simgeler yanı sıra dosya. İşinize yarayacak [Bitmaps öğesi](../extensibility/bitmaps-element.md) daha fazla ayrıntı için.  
  
## <a name="add-an-icon-to-a-command"></a>Bir simge komut ekleme  
 Aşağıdaki yordam, mevcut VSPackage projesinde bir menü komutu ile sahibi olduğunuzu varsayar. Bunu yapmak nasıl öğrenmek için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Bir bit eşlem 32 bit renk derinliği ile oluşturun. Bir simge, her zaman 16 x 16 bit eşlem bu 16 piksel yüksekliğinde olması gerekir ve katı 16 piksel genişliğinde bulunur.  
  
     Her simge tek bir satırda yan yana bir bit eşlem yerleştirilir. Alfa kanalını saydamlık her simgesi yerleri belirtmek için kullanın.  
  
     Pembe, 8-bit renk derinliği kullanırsanız kullanın `RGB(255,0,255)`, saydam olarak. Ancak, 32 bit renk simgelerinin genişliğini tercih edilir.  
  
2.  Simge dosyasının konumuna kopyalayın *kaynakları* VSPackage projenizdeki dizin. İçinde **Çözüm Gezgini**, simge projeye ekleyin. (Seçin **kaynakları**, bağlam menüsünü tıklatın ve **Ekle**, ardından **var olan öğe**ve simge dosyanızı seçin.)  
  
3.  Açık *.vsct* düzenleyicideki dosyada.  
  
4.  Ekleme bir `GuidSymbol` öğe adıyla **testIcon**. Bir GUID oluştur (**Araçları** > **GUID Oluştur**, ardından **biçimi kayıt defteri** tıklatıp **kopyalama**) ve yapıştırın`value` özniteliği. Sonuç şu şekilde görünmelidir:  
  
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
  
6.  Oluşturma bir `<Bitmap>` içinde `<Bitmaps>` bölümünü *.vsct* simgelerini içeren bit eşlem temsil etmek için dosya.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Menüleri ve komutlari genişletme komutları](../extensibility/extending-menus-and-commands.md)   
 [VSCT XML Şeması Başvurusu](../extensibility/vsct-xml-schema-reference.md)