---
title: 'Öğretici 2: C# konsol uygulamanızı genişletme'
description: adım adım Visual Studio bir C# konsol uygulaması geliştirmeyi öğrenin.
ms.custom: vs-acquisition, get-started
ms.date: 04/15/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f7d1ae7d0d5f045c0772243c7fc4011a9f31088e
ms.sourcegitcommit: e7629e132a4d2fad6bb5869e4d68d9dbeeae9631
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2021
ms.locfileid: "113649155"
---
# <a name="tutorial-extend-c-console-app-and-debug-in-visual-studio-part-2-of-2"></a>öğretici: Visual Studio 'de C# konsol uygulamasını ve hata ayıklamayı genişletme (bölüm 2/2)

bu öğretici serisinin 2. bölümünde, birden çok projenin yönetilmesi, hata ayıklaması ve üçüncü taraf paketlere başvurmak gibi Visual Studio ' deki derleme ve hata ayıklama özelliklerinde biraz daha ayrıntılı bilgi edineceksiniz. [bu öğreticinin 1. bölümünde (öğretici-console.md) oluşturduğunuz C# konsol uygulamasını çalıştıracaksınız ve bunu yaparken Visual Studio tümleşik geliştirme ortamının (ıde) bazı özelliklerini keşfedebilirsiniz. Bu öğretici, iki bölümden oluşan bir öğretici serisinin 2. parçasıdır.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * İlk olarak başka bir proje ekleyin.
> * Başvuru kitaplıkları ve paket Ekle.
> * Daha fazla hata ayıklayın.
> * Tüm kodunuzu inceleyin.


## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerden birini yapmanız gerekir:
+ [Bu öğretici serisinin Bölüm 1 ' den Hesaplayıcı konsol uygulamasını](tutorial-console.md) kullanın 
+ Başlamak için [bir depoyu açabileceğiniz](../tutorial-open-project-from-repo.md) [vs-öğreticisi-Samples](https://github.com/MicrosoftDocs/vs-tutorial-samples) deposunda C# Hesaplayıcı uygulamasını kullanın.

## <a name="add-another-project"></a>Başka proje ekleme

Gerçek dünyada kod, bir çözümde birlikte çalışan çok sayıda proje içerir. Şimdi, hesaplayıcı uygulamasına başka bir proje ekleyelim. Bu, bazı Hesaplayıcı işlevlerini sağlayan bir sınıf kitaplığı olacaktır.

1. Visual Studio ' de, yeni bir proje eklemek için en üst düzey menü komut **dosyasını**  >    >  **yeni Project** ekle ' yi kullanabilirsiniz, ancak aynı proje adına ("proje düğümü" olarak adlandırılır) sağ tıklayıp projenin kısayol menüsünü (veya bağlam menüsünü) açabilirsiniz. Bu kısayol menüsü, projelerinize işlevsellik eklemenin birçok yolunu içerir. bu nedenle, **Çözüm Gezgini**' de proje düğümüne sağ tıklayın ve   >  **yeni Project** ekle ' yi seçin.

1. C# proje şablonu **sınıf kitaplığını (.NET Standard)** seçin.

   ![Sınıf kitaplığı proje şablonu seçiminin ekran görüntüsü](media/vs-2019/calculator2-add-project-dark.png)

1. Proje adı **Hesaplakitaplığı**' nı yazıp **Oluştur**' u seçin. Daha sonra, sorulduğunda .NET 3,1 ' i seçin. Visual Studio yeni projeyi oluşturur ve çözüme ekler.

   ![Hesaplatorlibrary sınıf kitaplığı projesi eklenen Çözüm Gezgini ekran görüntüsü](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. *Class1. cs* yerine, **hesaplatorlibrary. cs** dosyasını yeniden adlandırın. Yeniden adlandırmak için **Çözüm Gezgini** adına tıklayabilir veya sağ tıklayıp **Yeniden Adlandır**' ı seçebilir veya **F2** tuşuna basabilirsiniz.

   Dosyadaki tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulur `Class1` . Daha sonraki bir adımda kodu değiştirdiğinizden, yanıt sizin için önemlidir.

1. Şimdi, ilk projenin yeni sınıf kitaplığı tarafından kullanıma sunulan API 'Leri kullanabilmesi için bir proje başvurusu eklememiz gerekir.  ilk projedeki **bağımlılıklar** düğümüne sağ tıklayın ve **Project başvuru ekle**' yi seçin.

   ![Project başvuru menü öğesi ekle ekran görüntüsü](media/vs-2019/calculator2-add-project-reference-dark.png)

   **Başvuru Yöneticisi** iletişim kutusu görüntülenir. Bu iletişim kutusu, diğer projelere başvurular eklemenizi sağlar, Ayrıca, projelerinize gereken derlemeleri ve COM DLL 'Leri.

   ![Başvuru Yöneticisi iletişim kutusunun ekran görüntüsü](media/vs-2019/calculator2-ref-manager-dark.png)

1. **Başvuru Yöneticisi** iletişim kutusunda, **Hesaplayıt kitaplığı** projesinin onay kutusunu seçin ve **Tamam**' ı seçin.  Proje başvurusu **Çözüm Gezgini** Içindeki bir **Projeler** düğümü altında görüntülenir.

   ![Proje başvurusuyla Çözüm Gezgini ekran görüntüsü](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. *Program. cs*' de, `Calculator` sınıfı ve tüm kodunu seçin ve **CTRL + X** tuşlarına basarak program. cs ' den kesin. Ardından, hesap \ *kitaplık. cs*' de **hesaplatorlibrary**' de kodu `CalculatorLibrary` ad alanına yapıştırın. Daha sonra, hesaplayıcı sınıfını `public` kitaplığın dışına çıkarmak için oluşturun. *Hesaplatorlibrary. cs* dosyasındaki kod artık aşağıdaki koda benzemelidir:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
        {
            public static double DoOperation(double num1, double num2, string op)
            {
                double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

                // Use a switch statement to do the math.
                switch (op)
                {
                    case "a":
                        result = num1 + num2;
                        break;
                    case "s":
                        result = num1 - num2;
                        break;
                    case "m":
                        result = num1 * num2;
                        break;
                    case "d":
                        // Ask the user to enter a non-zero divisor.
                        if (num2 != 0)
                        {
                            result = num1 / num2;
                        }
                        break;
                    // Return text for an incorrect option entry.
                    default:
                        break;
                }
                return result;
            }
        }
    }
   ```

1. İlk projenin bir başvurusu var, ancak Hesaplayıcı. DoOperation çağrısının çözümlenmediğini belirten bir hata görürsünüz. Bunun nedeni, Hesaplagönderenin farklı bir ad alanında olması, bu nedenle `CalculatorLibrary` tam nitelikli bir başvuru için ad alanı eklemektir.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Bunun yerine, dosyanın başlangıcına bir using yönergesi eklemeyi deneyin:

   ```csharp
   using CalculatorLibrary;
   ```

   Bu değişiklik, hesap kaldırma adı ' nı çağrı sitesinden kaldırmanızı sağlar, ancak artık bir belirsizlik var. , `Calculator` Hesaplayıcı 'daki sınıftır veya ad alanı Hesaplayıcısı mi?  Belirsizliği çözümlemek için ad alanını yeniden adlandırın `CalculatorProgram` .

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Başvuru .NET kitaplıkları: bir günlüğe yazma

1. Artık tüm işlemlerin bir günlüğünü eklemek ve bir metin dosyasına yazmak istediğinizi varsayalım. .NET `Trace` sınıfı bu işlevselliği sağlar. (Temel yazdırma hata ayıklama teknikleri de yararlı olur.)  Trace sınıfı System. Diagnostics ' dir ve gibi System.IO sınıfların olması gerekir `StreamWriter` . bu nedenle, *hesaplaizetlibrary. cs*' nin en üstündeki using yönergelerini ekleyerek başlayın:

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Trace sınıfının nasıl kullanıldığına bakarak, bir FILESTREAM ile ilişkili olan sınıfı için bir başvuruya sahip olmanız gerekir. Diğer bir deyişle, hesaplayıcı bir nesne olarak daha iyi çalışacaktır, bu yüzden Hesaplayıcı *. cs* Içindeki Hesaplayıcı sınıfının başına bir Oluşturucu ekleyelim.

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. Statik `DoOperation` yöntemi üye bir yöntemde değiştirmemiz gerekiyor, bu nedenle `static` anahtar sözcüğünü kaldırın.  Ayrıca günlük için her bir hesaplamaya çıktı ekleyelim, böylece DoOperation aşağıdaki koda benzer şekilde görünür:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. Şimdi *program. cs*' ye geri döndüğünüzde, statik çağrı kırmızı dalgalı bir metinle işaretlenir. Bunu onarmak için, `calculator` döngüden hemen önce aşağıdaki satırı ekleyerek bir değişken oluşturun `while (!endApp)` :

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Ve için çağrı sitesini `DoOperation` aşağıdaki gibi değiştirin, böylece bu, küçük harfli adlı nesneye başvurur, böylece `calculator` statik bir yöntem çağrısı yerine bunu bir üye çağrısı yapar:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Programı yeniden çalıştırın ve işiniz bittiğinde proje düğümüne sağ tıklayın ve **Dosya Gezgini 'nde klasörü aç**' ı seçin ve ardından Dosya Gezgini ' nde çıkış klasörüne gidin. *Bin/Debug/netcoreapp 3.1* olabilir ve *Hesaplayıcı. log* dosyasını açabilirsiniz.

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

Bu noktada, *Hesaplatorlibrary. cs* şuna benzer şekilde görünmelidir:

```csharp
using System;
using System.IO;
using System.Diagnostics;


namespace CalculatorLibrary
{
    public class Calculator
    {

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                    break;
                case "s":
                    result = num1 - num2;
                    Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                    break;
                case "m":
                    result = num1 * num2;
                    Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }
}
```

Ve *program. cs* aşağıdakine benzemelidir:

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
}
```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>NuGet paketi ekleme: JSON dosyasına yazma

1. Artık, nesne verilerini depolamak için popüler ve taşınabilir bir biçimdeki işlemleri bir JSON biçiminde çıkarmak istediğinizi varsayalım. bu işlevselliği uygulamak için Newtonsoft.JsNuGet paketine başvurması gerekecektir. NuGet paketler, .net sınıf kitaplıklarının dağıtılması için birincil araçtır. **Çözüm Gezgini**, hesap kimliği \ kitaplık projesi için **bağımlılıklar** düğümüne sağ tıklayın ve **NuGet paketlerini yönet**' i seçin.

   ![kısayol menüsündeki NuGet paketlerinin yönetme ekran görüntüsü](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   NuGet Paket Yöneticisi açılır.

   ![NuGet Paket Yöneticisi ekran görüntüsü](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Pakette Newtonsoft.Jsaraması yapın ve **yüklemeyi** seçin.

   ![newtonsoft NuGet paket bilgilerinin ekran görüntüsü](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Paket indirilir ve projenize eklenir ve **Çözüm Gezgini** başvurular düğümünde yeni bir giriş görüntülenir.

1. System.IO ve Newtonsoft.Json paketi için *Hesaplatorlibrary. cs*' nin başlangıcında bir using yönergesi ekleyin.

   ```csharp
   using Newtonsoft.Json;
   ```

1. Şimdi Hesaplayıcı için oluşturucuyu aşağıdaki kodla değiştirin ve JsonWriter üye nesnesini oluşturun:

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. `DoOperation`JSON yazıcı kodunu eklemek için yöntemi değiştirin:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. Kullanıcı işlem verilerini girmeyi tamamladıktan sonra JSON sözdizimini tamamlayacak bir yöntem eklemeniz gerekir.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. *Program. cs*' de, sonunda bitirmek için bir çağrı ekleyin.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Uygulamayı derleyin ve çalıştırın ve birkaç işlem girmeyi tamamladıktan sonra, ' n ' komutunu kullanarak uygulamayı düzgün bir şekilde kapatın.  Şimdi dosyada calculatorlog.jsaçın ve aşağıdakine benzer bir şey görmeniz gerekir:

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="debug-set-and-hit-a-breakpoint"></a>Hata Ayıkla: kesme noktası ayarlama ve isabet

Visual Studio hata ayıklayıcı, programlama sırasında hata yaptığınız kesin noktayı bulmak için kodunuzu adım adım çalıştırmanıza olanak tanıyan güçlü bir araçtır. Kodunuzda yapmanız gereken düzeltmeleri anlamış olursunuz. Visual Studio, programı çalıştırmaya devam edebilmeniz için geçici değişiklikler yapmanıza olanak sağlar.

1. *Program. cs*' de, aşağıdaki kodun solundaki kenar boşluğuna tıklayın (veya kısayol menüsünü açın ve **kesme** noktası  >  **Ekle kesme noktası**' nı seçin veya **F9** tuşuna basın):

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Görüntülenen kırmızı daire bir kesme noktasını gösterir. Kesme noktalarını kullanarak uygulamanızı duraklatabilir ve kodu inceleyebilirsiniz. Herhangi bir çalıştırılabilir kod satırında bir kesme noktası ayarlayabilirsiniz.

   ![Kesme noktası ayarlamanın ekran görüntüsü](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Uygulamayı derleyin ve çalıştırın.

1. Çalışan uygulamada, hesaplama için bazı değerler yazın:

   - İlk numara için **8** yazın ve girin.
   - İkinci numara için **0** yazın ve girin.
   - İşleci için biraz eğlenceye sahip olalım. **d** yazın ve girin.

   Uygulama, sol tarafta sarı işaretçiye ve vurgulanan koda göre belirtilen kesme noktasını oluşturduğunuz yeri askıya alır. Vurgulanan kod henüz yürütülmedi.

   ![Kesme noktasıyla ilgili ekran görüntüsü](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Şimdi, uygulama askıya alındıyla birlikte uygulama durumunu inceebilirsiniz.

## <a name="debug-view-variables"></a>Hata ayıklama: değişkenleri görüntüleme

1. Vurgulanan kodda ve gibi değişkenlerin üzerine `cleanNum1` `op` gelin. DataTips'te görünen bu değişkenlerin ( `8` ve ) geçerli değerlerini `d` görüyorsunuz.

   ![DataTip görüntüleme ekran görüntüsü](media/vs-2019/calculator-2-debug-view-datatip.png)

   Hata ayıklama sırasında, değişkenlerin tutmasını beklediğiniz değerleri tutıp tutmay olmadığını kontrol etmek genellikle sorunları düzeltmek için kritik öneme sahiptir.

2. Alt bölmede Yereller **penceresine** bakın. (Kapalı ise Hata Ayıkla'ya **seçin**  >  **Windows**  >  **Açmak için** yereller.)

   Yereller penceresinde, değeri ve türüyle birlikte şu anda kapsamda olan her bir değişkeni görebilirsiniz.

   ![Yereller penceresinin ekran görüntüsü](media/vs-2019/calculator-2-debug-locals-window.png)

3. Otomatikler **penceresine** bakın.

   Otomatikler penceresi Yerel öğeler  penceresine benzer, ancak uygulamanın duraklatılmış olduğu geçerli kod satırına hemen önce ve sonra gelen değişkenleri gösterir.

   Ardından, hata ayıklayıcısında her bir deyiminde adımlama olarak adlandırılan bir kod *yürütebilirsiniz.*

## <a name="debug-step-through-code"></a>Hata ayıklama: kodda adım adım

1. **F11 tuşuna** basın (veya **Hata Ayıkla**  >  **adımını içine alın).**

   Uygulama, Adımla komutunu kullanarak geçerli deyimi yürütür ve sonraki yürütülebilir deyime (genellikle bir sonraki kod satırı) ilerler. Sol tarafta sarı işaretçi her zaman geçerli deyimi gösterir.

   ![Komutun içine adımla ekran görüntüsü](media/vs-2019/calculator-2-debug-step-into.png)

   sınıfındaki yöntemine `DoOperation` `Calculator` girdiniz.

1. Program akışınıza hiyerarşik bir bakış elde etmek için Çağrı Yığını **penceresine** bakın. (Kapalı ise Hata Ayıkla'ya **seçin**  >  **Windows**  >  **Çağrı Yığını**.)

   ![Çağrı yığınının ekran görüntüsü](media/vs-2019/calculator-2-debug-call-stack.png)

   Bu görünüm sarı işaretçiyle gösterilen geçerli yöntemi, ikinci satır `Calculator.DoOperation` `Main` ise *Program.cs'de* yönteminden çağıran işlevi gösterir. Çağrı **Yığını** penceresi, yöntemlerin ve işlevlerin çağrıldığı sırayı gösterir. Ayrıca, kısayol menüsünden Kaynak Koduna Git gibi birçok **hata ayıklayıcısı** özelliğine erişim sağlar.

1. Uygulama deyimi duraklatana kadar **F10** 'a (veya Hata Ayıklama   >  Adımı) birkaç kez `switch` basın.

   ```csharp
   switch (op)
   {
   ```

   Üzerinden Adımla komutu, Geçerli deyim bir işlev çağırsa, hata ayıklayıcının çağıran işlevde kodu çalıştırması ve işlev dönene kadar yürütmeyi askıya almama durumu dışında, Adımla komutuna benzer. Belirli bir işlevle ilgilenmezken Kodda gezinmenin daha hızlı bir yoludur.

1. Uygulamanın aşağıdaki kod satırına duraklatmak için **F10'a** bir kez daha basın.

   ```csharp
   if (num2 != 0)
   {
   ```

   Bu kod, sıfıra bölme büyük/küçük harflerini denetler. Uygulama devam ederse, genel bir özel durum (hata) oluşturur, ancak bunu bir hata olarak değerlendirin ve konsolda döndürülen gerçek değeri görüntüleme gibi başka bir şey yapmak istediğiniz varsayın. Seçeneklerden biri, kodda değişiklik yapmak ve ardından hata ayıklamaya devam etmek için Düzenle ve devam adlı bir hata ayıklayıcı özelliği kullanmaktır. Ancak, yürütme akışını geçici olarak değiştirmeniz için size farklı bir püf noktası gösteriz.

## <a name="debug-test-a-temporary-change"></a>Hata ayıklama: Geçici bir değişikliği test etmek

1. Deyimde duraklatılmış olan sarı `if (num2 != 0)` işaretçiyi seçin ve aşağıdaki deyime sürükleyin.

   ```csharp
   result = num1 / num2;
   ```

   Bunu yaparak uygulama deyimini tamamen `if` atlar, böylece sıfıra böldükte ne olacağını görebilir.

1. Kod **satırı yürütmek için F10** tuşuna basın.

1. değişkeninin `result` üzerine gelin ve değerini depolar. `Infinity`

   C# `Infinity` içinde, sıfıra bölerek elde edilen sonuç olur.

1. **F5 tuşuna** basın (veya Hata **Ayıklama Devam**  >  **Hata Ayıklama).**

   Infinity simgesi, matematik işlemi sonucunda konsolda gösterilir.

1. 'n' komutunu kullanarak uygulamayı düzgün bir şekilde kapatın.

## <a name="code-complete"></a>Kod tamamlandı

Tüm adımlar tamamlandıktan sonra *CalculatorLibrary.cs* dosyasının tam kodu şu şekildedir:

```csharp
using System;
using System.IO;
using System.Diagnostics;
using Newtonsoft.Json;

namespace CalculatorLibrary
{
    public class Calculator
    {

        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }

        public void Finish()
        {
            writer.WriteEndArray();
            writer.WriteEndObject();
            writer.Close();
        }
    }
}
```

Program.cs için kod *şu şekildedir:* 

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            calculator.Finish();
            return;
        }
    }
}
```

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamladıktan sonra! Daha da fazla bilgi edinmek için aşağıdaki içeriğe devam etmek için:

- [Daha fazla C# öğreticisi ile devam edin](/dotnet/csharp/tutorials/)
- [Hızlı Başlangıç: web ASP.NET Core oluşturma](../../ide/quickstart-aspnet-core.md)
- [Visual Studio'de C# kodunda hata ayıklamayı Visual Studio](tutorial-debugger.md)
- Birim testleri oluşturma ve [çalıştırmayla ilgili izlenecek yol](../../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [C# programı çalıştırma](run-program.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
- [IDE'Visual Studio genel bakış ile devam](/../visual-studio-ide.md)
