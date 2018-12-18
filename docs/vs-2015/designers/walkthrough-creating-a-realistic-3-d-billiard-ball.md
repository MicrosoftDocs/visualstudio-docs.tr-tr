---
title: 'İzlenecek yol: gerçekçi bir 3B bilardo topu oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 29d45f4d5df6131182dfe70467e655bd23f6fcf2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829592"
---
# <a name="walkthrough-creating-a-realistic-3-d-billiard-ball"></a>İzlenecek yol: Gerçekçi bir 3B Bilardo Topu Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol gölgelendirici Tasarımcısı ve Resim Düzenleyicisi kullanılarak gerçekçi bir 3B bilardo topu oluşturma işlemini gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bilardo topunun 3B görünümü, birçok gölgelendirici teknikleri uygun doku kaynakları ile birleştirerek elde edilir.  
  
 Bu belgede şu faaliyetler gösterilmiştir:  
  
-   Şekil ve doku kullanarak bilardo topu temel görünümünü oluşturma.  
  
-   Lambert aydınlatma modeli kullanarak derinlik ekleme.  
  
-   Temel görünümünü Yansımalı vurgular kullanarak.  
  
-   Ortamı yansıtarak alan duygusu oluşturma.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Aşağıdaki bileşenler ve beceriler, bu izlenecek yolu tamamlamak için ihtiyacınız vardır:  
  
-   Haziran 2010'da bulunan DirectX doku aracı gibi bir küp eşlemi içine dokular montajı için bir araç DirectX SDK.  
  
-   İçerisinde Resim Düzenleyicisi ile aşinalık [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   İçerisinde gölgelendirici Tasarımcısı ile aşinalık [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="creating-the-basic-appearance-with-shape-and-texture"></a>Şekil ve doku ile temel görünümünü oluşturma  
 Bilgisayar grafiklerinde, en temel görünüm öğeleri şekil ve renktir var. Bir bilgisayar benzetiminde, gerçek nesnenin şeklini temsil etmek için bir 3B model kullanımı yaygındır. Renk ayrıntıları doku eşlemi kullanılarak modelin yüzeyine sonra uygulanır.  
  
 Genellikle bir sanatçıdan, kullanabileceğiniz bir 3B model oluşturmasını istemeniz gerekebilir, ancak bilardo topu yaygın bir şekil (küre) olduğundan, gölgelendirici Tasarımcısı zaten yerleşik bir uygun model vardır.  
  
 Küre gölgelendirici tasarımcısında varsayılan Önizleme şekildir; gölgelendiricinizi önizlemek için farklı bir şekli şu anda kullanıyorsanız küre geçin.  
  
#### <a name="to-preview-the-shader-by-using-a-sphere"></a>Bir küre kullanarak gölgelendiricinin önizlemesini görüntülemek için  
  
- Gölgelendirici Tasarımcısı araç çubuğunda **küre ile Önizleme.**  
  
  Sonraki adımda, bir dokuyu modele uygulayan bir gölgelendirici program oluşturacaksınız ancak öncelikle kullanabileceğiniz bir doku oluşturmanız gerekir. Bu izlenecek yol Resim Düzenleyicisi'ni kullanarak doku oluşturmayı gösterir. bir parçası olduğu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ancak siz dokuyu uygun biçimde kaydedebilen herhangi bir resim düzenleyicisi kullanabilirsiniz.  
  
  Emin olun **özellikleri** penceresi ve **araç kutusu** görüntülenir.  
  
#### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>Resim Düzenleyicisi'ni kullanarak bir bilardo topu dokusu oluşturmak için  
  
1. Çalışmak için bir doku oluşturun. Projenize doku ekleme hakkında daha fazla bilgi için bkz. Başlarken bölümünde [Resim Düzenleyicisi](../designers/image-editor.md).  
  
2. Genişliği yüksekliğinin iki katı olması görüntüyü boyutunu ayarlayın; Bu doku, bilardo topu küresel yüzeyine eşlendi biçimi nedeniyle gereklidir. Resmi yeniden boyutlandırmak için **özellikleri** penceresi için yeni değerler belirtin **genişliği** ve **yükseklik** özellikleri. Örneğin, genişliği 512 ve yüksekliği 256 ayarlayın.  
  
3. Nasıl bir doku bir küreyle göz önünde bulundurarak bilardo topu için bir doku çizin.  
  
    Doku şuna benzer görünmelidir:  
  
    ![Doku, bilardo topu için](../designers/media/gfx-shader-demo-billiard-art-ball-texture.png "gfx_shader_demo_billiard_art_ball_texture")  
  
4. İsteğe bağlı olarak, bu dokunun depolama gereksinimlerini azaltmak isteyebilirsiniz. Yüksekliğe eşleşecek şekilde doku genişliğini azaltarak bunu yapabilirsiniz. Bu, dokuyu Enine sıkıştırır, ancak bilardo topu oluşturulduğunda dokunun küreyle eşlenme olduğunu yöntemi nedeniyle genişletilir. Yeniden boyutlandırıldıktan sonra doku şuna benzer görünmelidir:  
  
    ![Bir kare sıkıştırılmış bilardo doku](../designers/media/gfx-shader-demo-billiard-art-ball-texture-square.png "gfx_shader_demo_billiard_art_ball_texture_square")  
  
   Şimdi bu dokuyu modele uygulayan bir gölgelendirici oluşturabilirsiniz.  
  
#### <a name="to-create-a-basic-texture-shader"></a>Temel doku gölgelendiricisi oluşturma  
  
1. Çalışmak için bir DGSL gölgelendirici oluşturun. Projenize DGSL gölgelendirici ekleme hakkında daha fazla bilgi için bkz. Başlarken bölümünde [gölgelendirici Tasarımcısı](../designers/shader-designer.md).  
  
    Varsayılan olarak, gölgelendirici grafiği şöyle görünür:  
  
    ![Varsayılan gölgelendirici grafiğinin](../designers/media/gfx-shader-demo-billiard-step-0.png "gfx_shader_demo_billiard_step_0")  
  
2. Varsayılan gölgelendiriciyi, geçerli piksele bir doku örneğinin değerini geçerli olacak şekilde değiştirin. Gölgelendirici grafiği şöyle görünmelidir:  
  
    ![Bir nesneye doku uygulayan bir gölgelendirici grafiği](../designers/media/gfx-shader-demo-billiard-step-1.png "gfx_shader_demo_billiard_step_1")  
  
3. Doku özelliklerini yapılandırarak önceki yordamda oluşturduğunuz dokuyu uygulayın. Değerini **doku** özelliği **doku örneğinin** düğüme **doku1**ve ardından kullanarak doku dosyasını belirtin. **Filename**özelliği **doku1** aynı özellik penceresinde özellik grubu.  
  
   Bir dokunun gölgelendiriciye uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: temel doku gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-texture-shader.md).  
  
   Bilardo topu şuna benzer görünmelidir:  
  
   ![Doku, bilardo topu sağında](../designers/media/gfx-shader-demo.png "gfx_shader_demo_")  
  
## <a name="creating-depth-with-the-lambert-lighting-model"></a>Lambert aydınlatma modeli ile derinlik oluşturma  
 Şu ana kadar bir kolayca tanınabilir bir bilardo topu oluşturdunuz. Ancak, düz ve cansız görünür — ikna edici ister bir bilardo topunun çizgi film resmini daha. Düz görünüm, bilardo topunun yüzeyindeki her piksel aynı miktarda ışık alırsa gibi davranır alıyormuş gölgelendiriciden kaynaklanır.  
  
 Gerçek dünyada, ışık doğrudan ışık kaynağına ve daha az parlak ışık kaynağına Yatık açıda olan yüzeylere üzerinde görünür yüzey üzerinde en parlak fikirlerimizi önemli görünür. Bunun nedeni, ışık ışınlarındaki enerjinin yüzey doğrudan ışık kaynağına yüzler, en küçük yüzey alanı boyunca dağıtılır. Yüzey ışık kaynağına Sırtı bırakır gibi aynı miktarda enerji giderek artan daha geniş bir yüzey alanı boyunca dağıtılır. Yüzleri bir ışık kaynağına bakmayan yüzey hiçbir şekilde ışık enerjisi tamamen karanlık bir görünüm elde edilen hiç alır. Bu surface parlaklıkta varyans bir nesnenin bir nesnenin şeklini gösteren yardımcı olan önemli bir görsel ipucudur; Bu olmadan nesne düz görünür.  
  
 Bilgisayar grafiklerinde *aydınlatma modelleri*— Basitleştirilmiş benzetimleri karmaşık, gerçek dünya ışık etkileşimlerinin — gerçek dünya ışık görünümünü çoğaltmak için kullanılır. Lambert aydınlatma modeli farklılaştırır yansıtılan ışık miktarını önceki paragrafta açıklandığı gibi bir nesnenin yüzeyinde arasında farklılık gösterir. Lambert aydınlatma modelini, bilardo topuna daha ikna edici bir 3-D görünümü vermek için gölgelendiricinize ekleyebilirsiniz.  
  
#### <a name="to-add-lambert-lighting-to-your-shader"></a>Gölgelendiricinize Lambert aydınlatma eklemek için  
  
- Gölgelendiricinizi, Lambert aydınlatma değerini doku örneğinin değerini modulate için değiştirin. Gölgelendirici grafiğiniz şu şekilde görünmelidir:  
  
   ![Gölgelendirici grafiğinin eklenen Lambert aydınlatma ile](../designers/media/gfx-shader-demo-billiard-step-2.png "gfx_shader_demo_billiard_step_2")  
  
- İsteğe bağlı olarak yapılandırarak Aydınlatmanın nasıl davranacağını ayarlayabilirsiniz **MaterialDiffuse** gölgelendirici grafiğinin özelliği. Gölgelendirici grafiğinin özelliklerine erişmek için tasarım yüzeyinde boş bir alan seçin ve ardından, erişmek istediğiniz özelliği bulun **özellikleri** penceresi.  
  
  Gölgelendiricinize Lambert aydınlatma uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: temel Lambert gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-lambert-shader.md).  
  
  Uygulanan Lambert aydınlatma ile bilardo topu şuna benzer görünmelidir:  
  
  ![Doku ve aydınlatılmış bilardo topu sağında](../designers/media/gfx-shader-demo-billiard-ball-2.png "gfx_shader_demo_billiard_ball_2")  
  
## <a name="enhancing-the-basic-appearance-with-specular-highlights"></a>Yansımalı vurgular ile temel görünümünü geliştirme  
 Şekil ve boyut duygusu Lambert aydınlatma modeli sağlar, yalnızca doku gölgelendirici. Ancak, bilardo topu yine biraz donuk vardır.  
  
 Gerçek bilardo topu genellikle üzerine düşen ışığın bir bölümünü yansıtan parlak bir yüzeye sahiptir. Bu bazı sonuçlanır bir yüzeyin yansıma özelliklerinin benzetimini Yansımalı vurgular yansıtılır. Özelliklerine bağlı olarak, vurgular yerelleştirilmiş veya geniş, yoğun ya da hafif olabilir. Bu aynasal yansımalar, bir ışık kaynağı, yüzey ve kamera konumu yönünü arasındaki ilişkiyi kullanarak modellenir — diğer bir deyişle, yüzey yönü ışık kaynağını doğrudan yansıttığında Vurgu en yoğundur Kamera ve yansıma daha az doğrudan olmadığı.  
  
 Lambert aydınlatma modeli önceki paragrafta açıklandığı gibi Yansımalı vurgular eklemek için Phong aydınlatma modelini geliştirir. Phong aydınlatma modelini, bilardo topunu daha ilgi çekici bir görünüm sonuçlanan benzetilmiş bir son vermek için gölgelendiricinize ekleyebilirsiniz.  
  
#### <a name="to-add-specular-highlights-to-your-shader"></a>Gölgelendiricinize Yansımalı vurgular eklemek için  
  
1. Gölgelendiricinizi, ek karıştırma kullanarak Yansımalı katkı içerecek şekilde değiştirin. Gölgelendirici grafiğiniz şu şekilde görünmelidir:  
  
    ![Gölgelendirici grafiğinin eklediğiniz Yansımalı aydınlatma ile](../designers/media/gfx-shader-demo-billiard-step-3.png "gfx_shader_demo_billiard_step_3")  
  
2. İsteğe bağlı olarak Yansımalı Vurgunun yapılandırarak Yansımalı Vurgunun davranış biçimini ayarlayabilirsiniz (**MaterialSpecular** ve **MaterialSpecularPower**) gölgelendirici grafiğinin. Tasarım yüzeyinde ve ardından boş bir alan için gölgelendirici grafiğinin özelliklerine erişmek, seçin **özellikleri** penceresinde erişmek istediğiniz özelliği bulun.  
  
   Yansımalı vurguların gölgelendiriciye uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: temel Phong gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-phong-shader.md).  
  
   Uygulanan Yansımalı vurgular ile bilardo topu şuna benzer görünmelidir:  
  
   ![Yansımalı ile bilardo topu sağında eklenen](../designers/media/gfx-shader-demo-billiard-ball-3.png "gfx_shader_demo_billiard_ball_3")  
  
## <a name="creating-a-sense-of-space-by-reflecting-the-environment"></a>Ortamı yansıtarak alan duygusu oluşturma  
 Uygulanan Yansımalı vurgular ile bilardo topu oldukça ikna edici görünüyor. Doğru şekle, doğru Boya işine ve doğru son bitirmeye sahiptir. Ancak, var. yine de ortamın bir parçası gibi bilardo olmanızı sağlayacak bir teknik daha  
  
 Gerçek bir bilardo topunu yakından incelerseniz, parlak yüzeyinin yalnızca belirgin vurguları göstermediğini ancak aynı zamanda zamanda hafifçe çevresindeki dünyanın bir görüntüsünü yansıtır görebilirsiniz. Bir doku olarak ortamın bir görüntü kullanarak ve her pikselin son rengini belirlemek için modelin kendi dokusu ile onu birleştirerek bu yansımanın benzetimini yapabilirsiniz. İstediğiniz bitiş türüne bağlı olarak, birleştirebilirsiniz veya daha az yansıma doku gölgelendiricinin geri kalanı ile birlikte. Örneğin, ayna gibi yüksek oranda yansıtıcı bir yüzeyi taklit eden bir gölgelendirici yalnızca yansıtma dokusunu ancak bilardo topu üzerinde bulunan bir yansıma yalnızca küçük bir kısmını birleştirebilirsiniz gibi daha hafif bir yansımayı taklit eden bir gölgelendirici kullanabilirsiniz Kalan gölgelendirici dokusunun değeri.  
  
 Elbette, yalnızca yansıyan resmi modele modelin doku haritasına uyguladığınız aynı şekilde uygulayamazsınız. Kaldırdıysanız, yansıma için yapışmış gibi dünyanın yansıması bilardo topu ile birlikte hareket edecektir. Bir yansıma herhangi bir yönde gelebileceğinden, her açı için bir yansıma eşlem değeri sağlayacak bir yol ve yansıma eşlemini dünyaya göre yönelimli tutmak için bir yol gerekir. Bu gereksinimleri karşılamak için özel bir tür bir doku eşlemi kullanabilirsiniz — adlı bir *küp eşlemi*— bir küp tarafının oluşturmak üzere düzenlenmiş altı doku sağlayan. Bu küp içinden bir doku değeri bulmak için herhangi bir yönde gösterebilir. Küpün her tarafındaki dokular ortamının görüntülerini içeriyorsa, küpün yüzeyi üzerinde doğru konumu örnekleyerek herhangi bir yansıtma benzetimi yapabilirsiniz. Küpü dünyayla hizada tutarak çevrenin yansımasını doğru ortamı elde edersiniz. Burada küpün örneğinin alınıp alınmayacağını belirlemek için yalnızca kamera vektörünün nesne yüzeyinden yansımasını hesaplar ve sonra bunu 3B doku koordinatları olarak kullanırsınız. Küp eşlemlerinin bu şekilde kullanılması olan olarak bilinen genel bir tekniktir *ortam eşleme*.  
  
 Ortam eşleme gerçek yansımaların etkin bir yaklaşığını önceki paragraflarda açıklandığı şekilde sağlar. İçine bilardo topunu görünümde daha yerine bilardo topu yapan benzetilmiş bir son üzerindeki olan bağlılığımızı temel vermek için gölgelendiricinize ortam eşlem yansımalarını gölgelendiricinize karıştırabilirsiniz.  
  
 İlk adım bir küp eşlemi dokusu oluşturmaktır. Birçok türden uygulamada, küp eşlem içeriğini, özellikle yansıma güç algılandığında veya ekranda önemli bir alan kaplamadığında etkili olabilmesi için mükemmel olması gerekmez. Örneğin, bu yansımanın doğru olmadığı anlamına gelir. ancak birçok oyun ortam eşlemesi ve yalnızca kullanım için bir yansıtıcı her nesnenin en yakın olanında önceden hesaplanmış küp eşlemeler kullanın. Hatta yaklaşık bir tahmin genellikle ikna edici bir efekt için yeterince iyi olur.  
  
#### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>Resim Düzenleyicisi'ni kullanarak bir ortam eşlemine ilişkin dokular oluşturmak için  
  
1. Çalışmak için bir doku oluşturun. Projenize doku ekleme hakkında daha fazla bilgi için bkz. Başlarken bölümünde [Resim Düzenleyicisi](../designers/image-editor.md).  
  
2. Resim boyutunu genişliği kendi boyuna eşit olduğundan ve boyut olarak ikinin kuvveti olacak şekilde ayarlayın; Bu bir küp eşlemi dizine alınacağından gereklidir. Resmi yeniden boyutlandırmak için **özellikleri** penceresi için yeni değerler belirtin **genişliği** ve **yükseklik** özellikleri. Örneğin, değerini **genişliği** ve **yükseklik** özelliklerini 256.  
  
3. Dokuyu doldurmak için düz renk kullanın. Bu doku, bilardo masasının yüzeyine karşılık gelen küp eşleminin alt kısmındaki olacaktır. Kullandığınız rengi bir sonraki doku için aklınızda bulundurun.  
  
4. İlk olarak aynı boyutta olan ikinci bir doku oluşturun. Bu doku, üzerinde yüzeyine ve bilardo masasının tarafında ve bilardo masasının etrafındaki alana karşılık gelen küp eşleminin dört tarafında yinelenecektir. Bilardo masasının yüzeyine bu dokuyu alt aynı rengi kullanarak çizdiğinizden emin olun. Doku şuna benzer görünmelidir:  
  
    ![Dokuyu küp tarafının için](../designers/media/gfx-shader-demo-billiard-art-env-texture-side.png "gfx_shader_demo_billiard_art_env_texture_side")  
  
    Bir yansıtma eşleminin etkili olması için olması gerekmez unutmayın; Örneğin, bu makalede resimler oluşturmak için kullanılan küp eşlemi, altı yerine dört cep içerir.  
  
5. Diğerleriyle aynı boyutta olan üçüncü bir doku oluşturun. Bu doku, bilardo masasının yukarısındaki tavana karşılık gelen küp eşleminin üst olacaktır. Bu yansıma parçasını daha ilgi çekici hale getirmek için önceki yordamda gölgelendiriciye eklediğiniz Yansımalı vurguları güçlendirebilirsiniz için bir tepe ışığı çizerek. Doku şuna benzer görünmelidir:  
  
    ![Küp en üstüne için doku](../designers/media/gfx-shader-demo-billiard-art-env-texture-top2.png "gfx_shader_demo_billiard_art_env_texture_top2")  
  
   Küp eşlem yüz için tek tek dokular oluşturduğunuza göre bunları tek bir .dds doku içinde depolanabilen bir küp eşlemi içine derlemek için bir araç kullanabilirsiniz. Küp eşlemi .dds doku biçimiyle kaydedebilirsiniz sürece küp eşlem oluşturmak istediğiniz herhangi bir programı kullanabilirsiniz. Bu izlenecek yol, Haziran 2010 bir parçası olan DirectX doku aracını kullanarak doku oluşturmayı gösterir DirectX SDK.  
  
#### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>DirectX doku Aracı'nı kullanarak bir küp haritasında derlemek için  
  
1. DirectX doku aracında ana menüsündeki seçin **dosya**, **yeni doku**. **Yeni doku** iletişim kutusu görüntülenir.  
  
2. İçinde **doku türü** Grup öğesini **küp dokusu**.  
  
3. İçinde **boyutları** grubunda, doğru değeri girin **genişliği** ve **yükseklik**ve ardından **Tamam**. Yeni bir doku belgesi görüntülenir. Varsayılan olarak, doku belgesinde ilk olarak gösterilen doku karşılık **pozitif X** küp yüzü.  
  
4. Küp yüzüne dokuyu küp tarafında için oluşturduğunuz dokuyu yükleyin. Ana menüsünde **dosya**, **açık üzerine bu küp yüzü**, küpün tarafı için oluşturduğunuz dokuyu seçin ve ardından **açık**.  
  
5. 4. adımı yineleyin için **negatif X**, **pozitif Z**, ve **negatif Z** küp yüzeyleri. Bunu yapmak için yüklemek istediğiniz yüzü görüntülemeniz gerekir. Ana menüde farklı bir küp eşlemi yüzünü görüntülemek için seçin **görünümü**, **küp eşlemi yüzü**ve ardından görüntülemek istediğiniz yüzü seçin.  
  
6. İçin **pozitif Y** küp yüzü için doku üstüne için oluşturduğunuz dokuyu yükleyin.  
  
7. İçin **negatif Y** küp yüzü için doku altındaki için oluşturduğunuz dokuyu yükleyin.  
  
8. Dokuyu kaydedin.  
  
   Bu küp eşlemenin yerleşimini hayal edebilirsiniz:  
  
   ![Ortam küp eşlemenin yerleşimini](../designers/media/gfx-shader-demo-billiard-art-env-texture-top.png "gfx_shader_demo_billiard_art_env_texture_top")  
  
   Üstteki görüntü pozitif Y (+ Y) küp yüzü bulunur; ortada, soldan sağa doğru – X, + Z, + yüzleri X ve – Z küp; altındaki – Y küp yüzü bulunur.  
  
   Şimdi küp harita örneği gölgelendiricinin geri kalanı ile karıştırmak için gölgelendiriciyi değiştirebilirsiniz.  
  
#### <a name="to-add-environment-mapping-to-your-shader"></a>Gölgelendiricinize ortam eşlemesi eklemek için  
  
1. Gölgelendiricinizi, ek karıştırma kullanarak ortam eşleme katkısı içerecek şekilde değiştirin. Gölgelendirici grafiğiniz şu şekilde görünmelidir:  
  
    ![Her iki tür yansıtma gölgelendirici düğümlerinin sağında](../designers/media/gfx-shader-demo-billiard-step-4b.png "gfx_shader_demo_billiard_step_4b")  
  
    Kullanabileceğiniz Not bir **Çarp-Ekle** gölgelendirici grafiğini basitleştirmek için düğümü.  
  
    Ortam eşlemesini uygulayan gölgelendirici düğümlerinin daha ayrıntılı bir görünümünü aşağıdadır:  
  
    ![Gölgelendirici grafiğinin eklenen ortamı eşleme ile](../designers/media/gfx-shader-demo-billiard-step-4a.png "gfx_shader_demo_billiard_step_4a")  
  
2. Küp eşlem doku özelliklerini yapılandırarak önceki yordamda oluşturduğunuz dokuyu uygulayın. Değerini **doku** özelliği **küp eşleme örneği** düğüme **doku2**ve ardından kullanarak doku dosyasını belirtin. **Filename**özelliği **doku2** özellik grubu.  
  
3. İsteğe bağlı olarak, yapılandırarak bilardo topu maskeleyen ayarlayabilirsiniz **çıkış** özelliği **sabit** düğümü. Düğümün erişim özelliklerine seçin ve ardından **özellikleri** penceresinde erişmek istediğiniz özelliği bulun.  
  
   Uygulanan ortamı eşleme ile bilardo topu şuna benzer görünmelidir:  
  
   ![Ortam sağında eşlenen bilardo topu](../designers/media/gfx-shader-demo-billiard-ball-4.png "gfx_shader_demo_billiard_ball_4")  
  
   Bu son görüntüde nasıl eklediğiniz efektlerin birlikte oldukça ikna edici bir bilardo topu oluşturmak için geldiğini unutmayın. Şekil, doku ve aydınlatma, 3B nesnenin temel görünümünü oluşturmak ve vurgularla yansımalar bilardo topunu daha ilgi çekici hale ve ortamın bir parçası gibi arayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)   
 [Nasıl yapılır: 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)   
 [Görüntü Düzenleyicisi](../designers/image-editor.md)   
 [Gölgelendirici Tasarımcısı Düğümleri](../designers/shader-designer-nodes.md)



