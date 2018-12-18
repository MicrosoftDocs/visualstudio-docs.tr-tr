---
title: 'İzlenecek yol: JavaScript kullanarak SDK oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d82e40de93a8b3323dbd03d9b76e935a1d303b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781055"
---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>İzlenecek Yol: JavaScript Kullanarak SDK Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, bir basit matematik SDK'sı bir Visual Studio Uzantısı (VSIX) olarak oluşturmak için JavaScript kullanmayı öğretir.  İzlenecek yol, şu bölümlere ayrılmıştır:  
  
- [SimpleMathVSIX uzantı SDK projesi oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
- [SDK'sını kullanan örnek bir uygulama oluşturmak için](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
  JavaScript için sınıf kitaplığı proje türü yoktur. Bu kılavuzda, örnek arithmetic.js dosyasını doğrudan içinde VSIX projesi oluşturulur. Uygulamada, öncelikle yapı ve Windows Store uygulaması olarak JavaScript ve CSS dosyaları test öneririz — kullanarak örneğin, **boş uygulama** şablonu — bir VSIX projesinde almadan önce.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createSimpleMathVSIX"></a> SimpleMathVSIX uzantı SDK projesi oluşturmak için  
  
1.  Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
2.  Şablon kategoriler listesinde altında **Visual C#** seçin **genişletilebilirlik**ve ardından **VSIX projesi** şablonu.  
  
3.  İçinde **adı** metin kutusunda, belirtin `SimpleMathVSIX` ve **Tamam** düğmesi.  
  
4.  Varsa **Visual Studio Paket Sihirbazı'nı** görüntülenirse, seçin **sonraki** düğmesini **Hoş Geldiniz** sayfasında ve ardından **sayfa 1 / 7**, seçin **Son** düğmesi.  
  
     Ancak **bildirim Tasarımcısı** açar, biz tutacağız Bu izlenecek yol basit doğrudan bildirim dosyasını değiştirerek.  
  
5.  İçinde **Çözüm Gezgini**source.extension.vsixmanifest dosyası için kısayol menüsünü açın ve ardından **kodu görüntüle**. Dosyanın mevcut içeriğini değiştirmek için bu kodu kullanın.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
      <Metadata>  
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />  
        <DisplayName>Simple Math</DisplayName>  
        <Description>Does basic arithmetic calculations.</Description>  
      </Metadata>  
      <Installation Scope="Global" AllUsers="true">  
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />  
      </Installation>  
      <Dependencies>  
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />  
      </Dependencies>  
      <Assets>  
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />  
      </Assets>  
    </PackageManifest>  
    ```  
  
6.  İçinde **Çözüm Gezgini**SimpleMathVSIX proje için kısayol menüsünü açın ve ardından **Ekle**, **yeni öğe**.  
  
7.  İçinde **veri** kategorisi seçin **XML dosyası**, dosya adı `SDKManifest.xml`ve **Ekle** düğmesi.  
  
8.  İçinde **Çözüm Gezgini**SDKManifest.xml dosyası için kısayol menüsünü açın ve ardından **açın** dosyasını görüntüleyecek şekilde **XML Düzenleyicisi**.  
  
9. SDKManifest.xml dosyaya aşağıdaki kodu ekleyin.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. İçinde **Çözüm Gezgini**, SDKManifest.xml dosyası için kısayol menüsünde **özellikleri**.  
  
11. İçinde **özellikleri** penceresinde **VSIX Ekle** özelliğini **True**.  
  
12. İçinde **Çözüm Gezgini**, SimpleMathVSIX projenin kısayol menüsünde **Ekle**, **yeni klasör**ve ardından klasörünü adlandırın `Redist`.  
  
13. Bu klasör yapısını oluşturmak için Redist altındaki alt klasörleri ekleyin:  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. \Js\ klasörü için kısayol menüsünde **Ekle**, **yeni öğe**.  
  
15. Altında **Visual C# öğeleri**seçin **Web** kategori tıklayın ve ardından **JavaScript dosyası** öğesi. Dosya adı `arithmetic.js`ve ardından **Ekle** düğmesi.  
  
16. Arithmetic.js aşağıdaki kodu ekleyin:  
  
    ```  
    (function (global) {  
        "use strict";  
        global.Arithmetic = {  
            add: function (firstNumber, secondNumber) {  
                return firstNumber + secondNumber;  
            },  
  
            subtract: function (firstNumber, secondNumber) {  
                return firstNumber - secondNumber;  
            },  
  
            multiply: function (firstNumber, secondNumber) {  
                return firstNumber * secondNumber;  
            },  
  
            divide: function (firstNumber, secondNumber) {  
                return firstNumber / secondNumber;  
            }  
        };  
    })(this);  
  
    ```  
  
17. İçinde **Çözüm Gezgini**, arithmetic.js dosyası için kısayol menüsünde **özellikleri**. Bu özellik değişiklikleri yapın:  
  
    -   Ayarlama **VSIX Ekle** özelliğini **True**.  
  
    -   Ayarlama **çıkış dizinine Kopyala** özelliğini **her zaman Kopyala**.  
  
18. İçinde **Çözüm Gezgini**, SimpleMathVSIX projenin kısayol menüsünde **yapı**.  
  
19. Yapı projesi için kısayol menüsündeki başarıyla tamamlandıktan sonra seçin **klasörü dosya Gezgini'nde Aç**. Gezinmek için \bin\Debug\\, çalıştırıp `SimpleMathVSIX.vsix` yüklemek için.  
  
20. Seçin **yükleme** düğmesi ve let yükleme tamamlandı.  
  
21. Visual Studio'yu yeniden başlatın.  
  
##  <a name="createSampleApp"></a> SDK'sını kullanan örnek bir uygulama oluşturmak için  
  
1.  Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
2.  Şablon kategoriler listesinde altında **JavaScript**seçin **Windows Store**ve ardından **boş uygulama** şablonu.  
  
3.  İçinde **adı** kutusunda, belirtin `ArithmeticUI`. Seçin **Tamam** düğmesi.  
  
4.  İçinde **Çözüm Gezgini**ArithmeticUI proje için kısayol menüsünü açın ve ardından **Ekle**, **başvuru**.  
  
5.  Altında **Windows**, seçin **uzantıları**, dikkat **basit matematik** görüntülenir.  
  
6.  Seçin **basit matematik** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.  
  
7.  İçinde **Çözüm Gezgini**altında **başvuruları**, dikkat **basit matematik** başvuru görüntülenir. Genişletin ve içerir arithmetic.js \js\ klasörü olduğuna dikkat edin. Kaynak kodunuzu yüklendiğini doğrulamak için arithmetic.js açabilirsiniz.  
  
8.  Default.htm içeriğini değiştirmek için aşağıdaki kodu kullanın.  
  
    ```  
    <!DOCTYPE html>  
    <html>  
    <head>  
        <meta charset="utf-8" />  
        <title>ArithmeticUI</title>  
  
        <!-- WinJS references -->  
        <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />  
        <script src="//Microsoft.WinJS.1.0/js/base.js"></script>  
        <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>  
  
        <!-- ArithmeticUI references -->  
        <link href="/css/default.css" rel="stylesheet" />  
        <script src="/js/default.js"></script>  
        <script src="/SimpleMath/js/arithmetic.js"></script>  
    </head>  
    <body>  
        <form>  
        <div id="calculator" class="ms-grid">  
            <input name="firstNumber" id="firstNumber" type="number" step="any">  
            <div id="operators">  
                <button class="operator" type="button">+</button>  
                <button class="operator" type="button">-</button>  
                <button class="operator" type="button">*</button>  
                <button class="operator" type="button">/</button>  
            </div>  
            <input id="secondNumber" type="number">  
            <button class="calculate" type="button">=</button>  
            <input id="result" type="number" name="result" disabled="" readonly="">  
        </div>  
        </form>  
    </body>  
    </html>  
    ```  
  
9. Sonraki kod \js\default.js içeriğini değiştirmek için kullanın.  
  
    ```  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var operation = null;  
  
        function calculateResult() {  
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),  
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),  
                result = 0;  
  
            if (isNaN(firstNumber) || isNaN(secondNumber)) {  
                result = 0;  
            }  
            else {  
                switch (operation) {  
                    case "+":  
                        result = Arithmetic.add(firstNumber, secondNumber);  
                        break;  
                    case "-":  
                        result = Arithmetic.subtract(firstNumber, secondNumber);  
                        break;  
                    case "*":  
                        result = Arithmetic.multiply(firstNumber, secondNumber);  
                        break;  
                    case "/":  
                        result = Arithmetic.divide(firstNumber, secondNumber);  
                        break;  
                    default:  
                }  
            }  
            document.querySelector("#result").value = result.toString();  
        }  
  
        app.onactivated = function (args) {  
            document.querySelector("#calculator").addEventListener("click", function (event) {  
                if (event.target.tagName.toLowerCase() === "button") {  
                    switch (event.target.className) {  
                        case "operator":  
                            operation = event.target.innerText;  
                            break;  
                        case "calculate":  
                            calculateResult();  
                            break;  
                        default:  
                            break;  
                    }  
                }  
            });  
        };  
  
        app.start();  
    })();  
    ```  
  
10. \Css\default.css içerikleri şu kodla değiştirin:  
  
    ```  
    form {  
        display: -ms-grid;  
        -ms-grid-rows: 1fr auto 1fr;  
        -ms-grid-columns: 1fr auto 1fr;  
        height: 100%;  
        width: 100%;  
    }  
  
    button, input[type=number] {  
        margin-right: 5px;  
        -ms-grid-row-align: center;  
    }  
  
    #calculator {  
        -ms-grid-column: 2;  
        -ms-grid-row: 2;  
        display: -ms-grid;  
        -ms-grid-rows: 1fr;  
        -ms-grid-columns: auto min-content auto auto auto;  
    }  
  
    .ms-grid input {  
        width: 5em;  
    }  
  
    #firstNumber {  
        -ms-grid-column: 1;  
        -ms-grid-row-align: center;  
    }  
  
    #operators {  
        -ms-grid-column: 2;  
        -ms-grid-row-align: center;  
    }  
  
        #operators button.operator {  
            margin-bottom: 5px;  
            height: 40px;  
        }  
  
    #secondNumber {  
        -ms-grid-column: 3;  
    }  
  
    button.calculate {  
        -ms-grid-column: 4;  
        -ms-grid-row-align: center;  
        height: 40px;  
    }  
  
    #result {  
        -ms-grid-column: 5;  
    }  
  
    ```  
  
11. Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
12. Uygulama kullanıcı Arabirimindeki herhangi iki sayıyı girin, bir işlem seçin ve ardından **=** düğmesi. Doğru sonucu görünür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yazılık Geliştirme Seti Oluşturma](../extensibility/creating-a-software-development-kit.md)

