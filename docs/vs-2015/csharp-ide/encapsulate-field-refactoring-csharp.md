---
title: Alanı Yalıt yeniden düzenleme (C#) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 35d7e03e30aa5301ee65f15a8591fbccd1de3fcd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223554"
---
# <a name="encapsulate-field-refactoring-c"></a>Alan Yeniden Düzenlemesini Yalıtma (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Yalıt** yeniden düzenleme işlemi sayesinde hızlı bir şekilde mevcut bir alandan bir özellik oluşturmak ve sorunsuz bir şekilde kodunuzu başvuruları yeni özelliği ile güncelleştirin.  
  
 Olduğunda bir [alan](http://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) olduğu [genel](http://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), diğer nesneler için söz konusu alanı doğrudan erişime sahip ve bu alanı sahibi nesne tarafından algılanamayan bunu değiştirebilirsiniz. Kullanarak [özellikleri](http://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) o alanı kapsüllemek için alanlar doğrudan erişimi engelleyebilirsiniz.  
  
 Yeni bir özellik oluşturmak için **Yalıt** işlemi için yalıtılacak istediğiniz alanı ait erişim değiştiricisinin değişiklikleri [özel](http://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)ve ardından oluşturur [alma](http://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71)ve [ayarlayın](http://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) Bu alan için erişimcileri. Bazı durumlarda, yalnızca bir `get` erişimci oluşturulur, zaman alan salt okunur bildirildiği gibi.  
  
 Kodunuzu düzenleme altyapısı belirtilen alanlarda yeni özellik başvurularını güncelleştirir **güncelleştirme başvuruları** bölümünü **Yalıt** iletişim kutusu.  
  
### <a name="to-create-a-property-from-a-field"></a>Alandan bir özellik oluşturmak için  
  
1.  Adlı bir konsol uygulaması oluşturun `EncapsulateFieldExample`ve ardından `Program` ile aşağıdaki kod örneği.  
  
    ```csharp  
    class Square  
    {  
        // Select the word 'width' and then use Encapsulate Field.  
        public int width, height;  
    }  
    class MainClass  
    {  
        public static void Main()  
        {  
            Square mySquare = new Square();  
            mySquare.width = 110;  
            mySquare.height = 150;  
            // Output values for width and height.  
            Console.WriteLine("width = {0}", mySquare.width);  
            Console.WriteLine("height = {0}", mySquare.height);  
        }  
    }  
    ```  
  
2.  İçinde [Kod Düzenleyicisi](../ide/writing-code-in-the-code-and-text-editor.md), imleç bildiriminde yalıtılacak istediğiniz alanın adını yerleştirin. Aşağıdaki örnekte, sözcüğüne imleci `width`:  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  Üzerinde **yeniden düzenleme** menüsünde tıklatın **Yalıt**.  
  
     **Yalıt** iletişim kutusu görüntülenir.  
  
     Ayrıca CTRL + R klavye kısayolunu görüntülenecek E yazabilirsiniz **Yalıt** iletişim kutusu.  
  
     Ayrıca, imleç sağ işaret **yeniden düzenleyin**ve ardından **Yalıt** görüntülenecek **Yalıt** iletişim kutusu.  
  
4.  Ayarları belirtin.  
  
5.  ENTER tuşuna basın veya tıklayın **Tamam** düğmesi.  
  
6.  Seçtiyseniz **başvuru değişikliklerini önizle** seçeneği, ardından **başvuru değişikliklerini önizle** penceresi açılır. Tıklayın **Uygula** düğmesi.  
  
     Aşağıdaki `get` ve `set` erişimci kodları, kaynak dosyanızdaki görüntülenir:  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     Kodda `Main` yöntemi ayrıca yeni güncelleştirilir `Width` özellik adı.  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## <a name="remarks"></a>Açıklamalar  
 **Yalıt** işlemi imleç alan bildirimi ile aynı satırda konumlandırıldığında yalnızca olduğu.  
  
 Birden çok alan bildirimleri **Yalıt** alanları arasındaki sınırı olarak virgül kullanır ve imleci en yakın olan alanın ve imleç ile aynı satırda yeniden düzenleme başlatır. Ayrıca, hangi alanın bildiriminde bu alanın adını seçerek yalıtılacak istediğiniz belirtebilirsiniz.  
  
 Bu yeniden düzenleme işlemi tarafından oluşturulan kodu yalıtma alan kod parçacıkları özelliği tarafından modellenir. Kod parçacıkları değiştirilebilir. Daha fazla bilgi için [kod parçacıkları](../ide/code-snippets.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden düzenlemesi (C#)](../csharp-ide/refactoring-csharp.md)   
 [Visual C# Kod Parçacıkları](../ide/visual-csharp-code-snippets.md)