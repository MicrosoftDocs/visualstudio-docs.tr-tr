---
title: Oyunlarda veya uygulamalarda 3B varlıklar kullanma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b41416ea923e8f14aa39bf1607ad7c349e0b149c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880684"
---
# <a name="use-3d-assets-in-your-game-or-app"></a>Oyununuzda veya uygulamanızda 3B varlıklar kullanma

Bu makalede, 3B varlıkları işlemek ve bunları derlemelerinize dahil etmek için Visual Studio nasıl kullanabileceğiniz açıklanır.

3B varlıkları oluşturmak için Visual Studio Araçları kullandıktan sonra sonraki adımda bunları uygulamanızda kullanmaktır. Ancak, kullanabilmeniz için önce varlıklarınızın DirectX'in anlayabileceği bir biçime dönüştürülmesi sahip. Varlıklarınızı dönüştürme yardımcı olmak için Visual Studio her üretebileceği varlık türü için yapı özelleştirmeleri sağlar. Yapınızda varlıkları dahil etmek için tüm yapmanız gereken olduğu yapı özelleştirmelerini kullanacak, projenize varlıklar eklemek ve doğru yapı özelleştirmesini kullanacak şekilde varlıkları yapılandırmaktır projenizi yapılandırın. Bundan sonra varlıkları uygulamanıza yükleyebilir ve bunları dolduran başka bir DirectX uygulamasında yaptığınız gibi DirectX kaynakları oluşturarak kullanabilirsiniz.

## <a name="configure-your-project"></a>Projenizi yapılandırın

3B varlıkları yapınızın bir parçası olarak dağıtmadan önce Visual Studio, dağıtmak istediğiniz varlıkların türleri hakkında bilmesi gerekir. Visual Studio, birçok yaygın dosya türünü zaten bilir, ancak yalnızca belirli türdeki uygulamalar 3B varlıklar kullandığından, Visual Studio bir proje bu tür dosyaları oluşturacağını varsaymaz. Visual Studio kullanarak uygulamanızı bu tür varlıkları kullandığını söyleyebilirsiniz *yapı özelleştirmeleri*— Visual Studio, farklı türlerde dosyaları yararlı bir şekilde işlemek bildiririz dosyaları — her varlık türü için sağlanır. Bu özelleştirmeler proje bazında uygulandığından tek yapmanız gereken olan gereken uygun özelleştirmeleri projenize ekleyin.

### <a name="to-add-the-build-customizations-to-your-project"></a>Projenize yapı özelleştirmeleri eklemek için

1.  İçinde **Çözüm Gezgini**, proje için kısayol menüsünü açın ve ardından **yapı bağımlılıkları** > **yapı özelleştirmeleri**. **Visual C++ derleme özelleştirme dosyaları** iletişim kutusu görüntülenir.

2.  Altında **kullanılabilir yapı özelleştirme dosyaları**, aşağıdaki tabloda açıklandığı şekilde, projenizde kullanmak istediğiniz varlık türlerine karşılık gelen onay kutularını işaretleyin:

    |Varlık türü|Özelleştirme adı oluştur|
    |----------------| - |
    |Dokularla ve görüntülerle|**ImageContentTask (.targets, .props)**|
    |3B modeller|**MeshContentTask (.targets, .props)**|
    |Gölgelendiricileri|**ShaderGraphContentTask (.targets, .props)**|

3.  Seçin **Tamam** düğmesi.

## <a name="include-assets-in-your-build"></a>Yapınızda varlıkları içerir
 Projeniz hakkında kullanmak istediğiniz 3B varlıkların farklı türlerini bildiğine göre sonraki adım, hangi dosyaların 3B varlıklar olduğunu ve hangi türde varlıkları bunlar söylemek olacaktır.

### <a name="to-add-an-asset-to-your-build"></a>Yapınıza bir varlık eklemek için

1.  İçinde **Çözüm Gezgini**, projenizde bir varlığın kısayol menüsünü açın ve ardından **özellikleri**. Varlığın **özellik sayfası** iletişim kutusu görüntülenir.

2.  Emin olun **yapılandırma** ve **Platform** özellikleri, yaptığınız değişiklikleri uygulamak istediğiniz değerlere ayarlanır.

3.  Altında **yapılandırma özellikleri**, seçin **genel**ve sonra özellik kılavuzunda altında **genel**ayarlayın **öğesi türü** özelliği uygun içerik ardışık düzeni öğe türüne. Örneğin, bir resim veya doku dosyası için tercih **görüntü içeriği ardışık düzeni**.

    > [!IMPORTANT]
    > Varsayılan olarak, Visual Studio pek çok resim dosyalarını kullanarak kategorize olması gerektiğini varsayar **görüntü** öğesi Visual Studio'da yerleşik olarak bulunan türü. Bu nedenle, değiştirmek zorunda **öğesi türü** , görüntü içeriği ardışık düzeni tarafından işlenmesini istediğiniz her görüntünün özelliği. Diğer içerik türlerine işlem hattı, kaynak dosyaları, 3B modeller ve görsel gölgelendirici grafikler varsayılan olarak doğru **öğesi türü**.

4.  Seçin **Tamam** düğmesi.

Aşağıda, üç içeriği ardışık düzeni öğe türleri ve bunların ilişkili kaynakları ve çıktı dosya türleri.

|Öğe türü|Kaynak dosya türleri|Çıkış dosyası biçimi|
|---------------| - | - |
|**Görüntü içeriği ardışık düzeni**|Taşınabilir Ağ Grafikleri (*.png*)<br /><br /> JPEG (*.jpg*, *.jpeg*, *.jpe*, *.jfif*)<br /><br /> Doğrudan çizim yüzeyi (*.dds*)<br /><br /> Grafik Değişim Biçimi (*.gif*)<br /><br /> Bit eşlem (*.bmp*, *.dib*)<br /><br /> Etiketli Resim dosyası biçimi (*.tif*, *.tiff*)<br /><br /> Targa (*.tga*)|DirectDraw Surface (*.dds*)|
|**Ağ içeriği ardışık düzeni**|AutoDesk FBX değişim dosyası (*.fbx*)<br /><br /> Collada DAE dosyası (*.dae*)<br /><br /> Wavefront OBJ dosyası (*.obj*)|3B mesh dosyası (*.cmo*)|
|**Gölgelendirici içerik ardışık düzeni**|Görsel gölgelendirici grafiği (*.dgsl*)|Derlenmiş gölgelendirici çıktısı (*.cso*)|

## <a name="configure-asset-content-pipeline-properties"></a>Varlık içeriği ardışık düzeni özelliklerini yapılandırın

Her varlık dosyasının içerik kanalı özelliklerini ayarlayabilirsiniz, böylece belirli bir şekilde derlenir.

### <a name="to-configure-content-pipeline-properties"></a>İçerik ardışık düzeni özelliklerini yapılandırmak için

1.  İçinde **Çözüm Gezgini**bulunan projenizde varlık dosyası için kısayol menüsünü açın ve ardından **özellikleri**. Varlığın **özellik sayfası** iletişim kutusu görüntülenir.

2.  Emin olun **yapılandırma** ve **Platform** özellikleri, değişikliklerinizi uygulanmasını istediğiniz değerlere ayarlanır.

3.  Altında **yapılandırma özellikleri**, içeriği ardışık düzeni düğümünü seçin; örneğin, **görüntü içeriği ardışık düzeni** doku ve resim varlıkları için — ve sonra özellik kılavuzunda özellikleri ayarlayın uygun değerleri. Örneğin, oluşturma zamanında doku varlığı için Mipmap üretmek için ayarlanmış **Mips üret** özelliğini **Evet**.

4.  Seçin **Tamam** düğmesi.

### <a name="image-content-pipeline-configuration"></a>Görüntü içeriği ardışık düzeni yapılandırması

Bir doku varlığı oluşturmak için görüntü içeriği ardışık düzen aracını kullandığınızda, dokuyu çeşitli şekillerde sıkıştırma, MIP düzeylerinin oluşturma zamanında oluşturulup ve çıktı dosyası adını değiştirmek olup olmadığını gösterir.

|Özellik|Açıklama|
|--------------|-----------------|
|**Sıkıştırma**|Çıkış dosyası için kullanılan sıkıştırma türünü belirtir.<br /><br /> Kullanılabilir seçenekler şunlardır:<br /><br /> -   **Sıkıştırma yok**<br />-   **BC1_UNORM sıkıştırma**<br />-   **BC1_UNORM_SRGB sıkıştırma**<br />-   **BC2_UNORM sıkıştırma**<br />-   **BC2_UNORM_SRGB sıkıştırma**<br />-   **BC3_UNORM sıkıştırma**<br />-   **BC3_UNORM_SRGB sıkıştırma**<br />-   **BC4_UNORM sıkıştırma**<br />-   **BC4_SNORM sıkıştırma**<br />-   **BC5_UNORM sıkıştırma**<br />-   **BC5_SNORM sıkıştırma**<br />-   **BC6H_UF16 sıkıştırma**<br />-   **BC6H_SF16 sıkıştırma**<br />-   **BC7_UNORM sıkıştırma**<br />-   **BC7_UNORM_SRGB sıkıştırma**<br /><br /> Hakkında hangi sıkıştırma biçimlerinin DirectX'in farklı sürümlerinde desteklendiği hakkında bilgi için bkz. [DXGI için Programlama Kılavuzu](http://go.microsoft.com/fwlink/p/?LinkId=246265).|
|Ön çarpımlı alfa biçimine Dönüştür|**Evet** görüntü çıkış dosyasına; önceden çarpılan alfa biçimine dönüştürmek için Aksi takdirde, **Hayır**. Yalnızca çıktı dosyası değiştirildi, kaynak görüntü değiştirilmez.|
|**Mips üret**|**Evet** derleme zamanında tam bir MIP zincir oluşturmak ve çıkış dosyasında; eklemek için Aksi takdirde, **Hayır**. Varsa **Hayır**, kaynak dosyası zaten mipmap zinciri içeriyor ve sonra çıktı dosyası bir MIP zinciri olur; Aksi takdirde, çıkış dosyası yok MIP zinciri olmaz.|
|**İçerik çıktısı**|Çıkış dosyasının adını belirtir. **Önemli:** sahip çıkış dosyasının dosya adı uzantısını değiştirmek dosyanın formatını etkilemez.|

### <a name="mesh-content-pipeline-configuration"></a>Kafes içerik ardışık düzen yapılandırması

Kafes değer oluşturmak için Kafes içerik ardışık düzen aracını kullandığınızda, çıkış dosyasının adını değiştirebilirsiniz.

|Özellik|Açıklama|
|--------------|-----------------|
|**İçerik çıktısı**|Çıkış dosyasının adını belirtir. **Önemli:** sahip çıkış dosyasının dosya adı uzantısını değiştirmek dosyanın formatını etkilemez.|

### <a name="shader-content-pipeline-configuration"></a>Gölgelendirici içerik ardışık düzen yapılandırması

Gölgelendirici değerini oluşturmak için gölgelendirici içeriği ardışık düzen aracını kullandığınızda, çıkış dosyasının adını değiştirebilirsiniz.

|Özellik|Açıklama|
|--------------|-----------------|
|**İçerik çıktısı**|Çıkış dosyasının adını belirtir. **Önemli:** sahip çıkış dosyasının dosya adı uzantısını değiştirmek dosyanın formatını etkilemez.|

## <a name="load-and-use-3d-assets-at-run-time"></a>Yükleme ve çalışma zamanında 3B varlıklar kullanma

### <a name="use-textures-and-images"></a>Kullanım dokular ve resimler

Direct3D Doku kaynakları oluşturmak için işlevler sağlar. Direct3D 11'de, doku kaynaklarını ve kaynak görünümünü doğrudan görüntü dosyalarından oluşturmak için D3DX11 yardımcı program kitaplığı ek işlevler sağlar. Direct3D 11'de bir doku kaynağı oluşturma hakkında daha fazla bilgi için bkz. [dokular](http://go.microsoft.com/fwlink/p/?LinkID=246267). Bir doku kaynağı veya kaynak görünümü oluşturmak için D3DX11 kitaplığının kullanma hakkında daha fazla bilgi için bir resim dosyasını görmek [nasıl yapılır: bir dosyadan doku başlatmak](http://go.microsoft.com/fwlink/p/?LinkId=246268).

### <a name="use-3d-models"></a>3B modelleri kullanma

Direct3D 11, 3B modellerden kaynak oluşturmak için işlevleri sağlamaz. Bunun yerine, 3B model dosyasını okuyan ve 3B modeli ve modelin gerektirdiği herhangi bir kaynağa temsil eden dizin arabellekleri oluşturan kod yazmanız gerekir — Örneğin, dokuları ve gölgelendiricileri.

### <a name="use-shaders"></a>Gölgelendiricileri kullanma

Direct3D, gölgelendirici kaynakları oluşturmak ve bunları programlanabilir grafik ardışık düzenine bağlamak için işlevler sağlar. Direct3D gölgelendirici kaynak oluşturma ve bunu kanala bağlama hakkında daha fazla bilgi için bkz. [HLSL için Programlama Kılavuzu](http://go.microsoft.com/fwlink/p/?LinkID=261521).

Programlanabilir grafik ardışık düzen Ardışık düzenin her aşaması işlem hattının sonraki aşamasına anlayabileceği bir şekilde biçimlendirilmiş bir sonuç vermeniz gerekir. Gölgelendirici Tasarımcısı yalnızca piksel gölgelendiricileri oluşturabildiğinden, bu, bu aldığı verilerin beklediği biçimde olmasını sağlamak için uygulamanıza kalmıştır anlamına gelir. Birçok programlanabilir gölgelendirici aşamaları, piksel gölgelendiricisinden önce oluşur ve geometrik dönüştürmeler — köşe gölgelendiricisi, hull gölgelendiricisi, etki alanı gölgelendiricisi ve geometri gölgelendiricisi. Programlanabilir olmayan Mozaik döşeme aşaması piksel gölgelendiriciden önce de gerçekleşir. Bu aşamalardan hangisi doğrudan piksel gölgelendiricisinin önünde olursa olsun, sonucunu bu biçimde vermelidir:

```hlsl
struct PixelShaderInput
{
    float4 pos : SV_POSITION;
    float4 diffuse : COLOR;
    float2 uv : TEXCOORD0;
    float3 worldNorm : TEXCOORD1;
    float3 worldPos : TEXCOORD2;
    float3 toEye : TEXCOORD3;
    float4 tangent : TEXCOORD4;
    float3 normal : TEXCOORD5;
};
```

Gölgelendiricinizi kullandığınız gölgelendirici Tasarımcısı düğümlerine bağlı olarak, bu tanımlara göre biçime ek veri sağlamanız olabilir:

```hlsl
Texture2D Texture1 : register( t0 );
Texture2D Texture2 : register( t1 );
Texture2D Texture3 : register( t2 );
Texture2D Texture4 : register( t3 );
Texture2D Texture5 : register( t4 );
Texture2D Texture6 : register( t5 );
Texture2D Texture7 : register( t6 );
Texture2D Texture8 : register( t7 );

TextureCube CubeTexture1 : register( t8 );
TextureCube CubeTexture2 : register( t9 );
TextureCube CubeTexture3 : register( t10 );
TextureCube CubeTexture4 : register( t11 );
TextureCube CubeTexture5 : register( t12 );
TextureCube CubeTexture6 : register( t13 );
TextureCube CubeTexture7 : register( t14 );
TextureCube CubeTexture8 : register( t15 );

SamplerState TexSampler : register( s0 );

cbuffer MaterialVars : register (b0)
{
    float4 MaterialAmbient;
    float4 MaterialDiffuse;
    float4 MaterialSpecular;
    float4 MaterialEmissive;
    float MaterialSpecularPower;
};

cbuffer LightVars : register (b1)
{
    float4 AmbientLight;
    float4 LightColor[4];
    float4 LightAttenuation[4];
    float3 LightDirection[4];
    float LightSpecularIntensity[4];
    uint IsPointLight[4];
    uint ActiveLights;
}

cbuffer ObjectVars : register(b2)
{
    float4x4 LocalToWorld4x4;
    float4x4 LocalToProjected4x4;
    float4x4 WorldToLocal4x4;
    float4x4 WorldToView4x4;
    float4x4 UVTransform4x4;
    float3 EyePosition;
};

cbuffer MiscVars : register(b3)
{
    float ViewportWidth;
    float ViewportHeight;
    float Time;
};
```

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: Mipmap'leri içeren dokuyu dışarı aktarma](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Hesaplanmış mipmap'leri içeren dokuyu dışarı aktarmak için görüntü içeriği ardışık düzeni kullanmayı açıklar.|
|[Nasıl yapılır: Ön çarpımlı alfa kullanan dokuyu dışarı aktarma](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Ön çarpımlı alfa değerleri içeren bir dokuyu dışarı aktarmak için görüntü içeriği ardışık düzeni kullanmayı açıklar.|
|[Nasıl yapılır: Direct2D veya Javascript uygulamaları kullanmak için dokuyu dışarı aktarma](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Direct2D veya JavaScript uygulamasında kullanılabilen bir dokuyu dışarı aktarmak için görüntü içeriği ardışık düzeni kullanmayı açıklar.|
|[Oyunlar ve uygulamalar için 3B varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Visual Studio'nun oluşturmak ve dokular ve resimler, 3B modelleri ve gölgelendiricileri içeren, 3B varlıkları işlemek için sağladığı düzenleme araçlarını açıklar.|
|[Nasıl yapılır: Gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)|Gölgelendirici Tasarımcısı'ndan gölgelendiriciyi dışarı aktarma işlemini açıklamaktadır.|