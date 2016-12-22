# Backend Recap

* [x] MVC
* [x] [User interfaces](http://steffenp.dk/weblog/user-interfaces-with-asp-net/)
* [x] HTML Helper Methods
* [ ] Model binding
* [x] Entity Framework
* [x] Code First
* [x] Data First
* [x] Dynamic v. Strongly Typed Views
* [x] C\# \(OOP\)
* [x] Visual Studio
* [ ] Properties
* [ ] Model Validation
* [ ] Ajax \(MVC\)

---

## MVC

---

MVC står for Model, View og Controller, som bruges til at adskille opgaver fra hinanden.

**Model** er sæt af klasser, som beskriver vores datastruktur.

**View** definerer hvordan applikationens UI vises - indeholder det som klienten ser.

**Controller** reagerer på user input, forbinder til model \(hvis der er én\) og beslutter hvilket view der skal returneres.

Man kan bruge ASP.NET MVC, hvis man ønsker kontrol over generelt kode, som kan struktureres og følge DRY-princippet.

---

## User interfaces

---

| **Razor engine** | **CSHTML** |
| :--- | :--- |
| Er en markup syntax, som giver os mulighed for at skrive C\# i vores HTML vha. “@“. Det betyder, at vi i vores view kan skrive kode, som ASP.NET kan konvertere til HTML eller C\#. | CSHTML er filformatet som referer til brug af razor engine. I modsætning til HTML indeholder CSHTML også C\# kode som bliver compiled på serveren og vist i browseren som HTML. |
| **Layout files** | **Partial View** |
| Layout files definerer det overordnet shared layout. Med dette undgår vi gentaget HTML. | Partial view er et stykke kode, som kan genbruges flere steder. |
| **Areas** | **Child Actions** |
| Med areas er det muligt at separere en stor MVC application til relaterede grupper af models, views og controllers. Admin har ofte sit eget area. | ~~Ofte skal noget data vises på flere sider i ens application. Generelt ender vi op med at tilføje dette data til model, som overfører til views gennem action methods. Vi gentager det samme data i flere models og bryder hermed DRY princippet. Med child actions kan dette løses. Enhver action method kan være child af en action method, men child actions er action methods nedarvet inden fra et view.~~ |

---

## HTML Helper Methods

---

En vigtig del af at lave web applications, består i at skrive noget HTML, som kan præsentere grafik, formularer osv. Det er her hvor MVC frameworket med HTML Helper Methods er rigtig smart. De tilgås med HTML Helper class i vores View, som indeholder funktionalitet til at opbygge det mest basale HTML.

**Input HTML Helpers**

@Html.TextBox

**Strongly Typed Input HTML Helpers**

@Html.TextBoxFor

---

## Model Binding

---

-

---

## Entity Framework

---

ADO.NET er et framework til data access fra Microsoft. Entity Framework er som sagt en object-relational mapper. Den genererer objects og entities på baggrund af databasens tabeller. Entity Framework kan desuden udføre CRUD \(Create, Read, Update, Delete\) operations. Den kan nemt håndtere “1 to 1”, “1 to many”, and “many to many” relationships. Den kan også håndtere inheritance relationships mellem entities. Fordelene ved ADO.NET og Entity Framework er at det genererede data access kode er skrevet i et high-level language \(forståeligt sprog\). Vi kan derfor tilpasse det til behov. [Link](https://www.codeproject.com/articles/363040/an-introduction-to-entity-framework-for-absolute-b)

---

## Code First

---

Med code first starter vi med at definere model med tilhørende classes. Vi tjekker derefter om Entity Framework er installeret gennem NuGet. Vi opretter derefter en DAL-mappe med tilhørende context og initializer. Vi skal huske at tilføje følgende forbindelse under `<entityFramework>` i Web.config:

```
<contexts> 
    <context type="EksamenEFCF.DAL.CustomerContext, EksamenEFCF"> 
        <databaseInitializer type="EksamenEFCF.DAL.CustomerInitializer, EksamenEFCF" /> 
    </context> 
</contexts>
```

Vi kan oprette forbindelse til databasen gennem Server Explorer → Data Connections → Add Connection. I kan se den fulde beskrivelse på dette link. For at tilføje en ændring i models skal vi muliggøre migrations. Dette gør vi gennem Package Manager Console ved at skrive Enable-Migrations. Når vi har lavet en ændring skal vi skrive Add-Migration Navn. For at opdatere databasen skal vi skrive Update-Database. [Link](https://msdn.microsoft.com/en-us/data/jj193542), [Fordele Ulemper](http://roland.kierkels.net/c-asp-net/ef-model-vs-database-vs-code-first-approach/)

**Seed**

Du kan indsætte data i din databases tabeller under databasens initialiseringsproces. Det gøres i filen CustomerInitializer.cs. Dette vil være vigtigt, hvis du ønsker at give nogle testdata for din applikation eller til at give nogle standard stamdata for din applikation.

---

## Data First

---

Med data first opretter vi datamodellen i databasen oftest ved hjælp af SQL Management Studio eller et andet relevant redskab. Her definerer vi tabellerne med værdier og tilføjer primary keys, foreign keys eller andre constraints. Herefter henter vi databasen ind. [Fordele Ulemper](http://roland.kierkels.net/c-asp-net/ef-model-vs-database-vs-code-first-approach/)

---

## Dynamic v. Strongly Typed Views

---

Strongly typed view specificerer data typen. Det giver fordele med IntelliSense og compile time error checking.

---

## C\

---

C\# er et strongly typed \(alle variabler skal defineres med en type\) og objektorienteret programmeringssprog. Det er case sensitiv, som vil sige at det differentierer mellem små- og store bogstaver. Det er udviklet af Microsoft og gennem .NET.

**Object-oriented programming**

> **Encapsulation**: Vi laver et private field med data, som tilgås med en public property.
>
> **Data Hiding**: Hver class kender ikke til indholdet af en anden class. Data hiding er det private field beskrevet i encapsulation som indeholder data.
>
> **Specialization**: Et dyr er i mere generel form og hund er mere specialiseret form og racen er endnu mere specialiseret. Dette kan opnås gennem inheritance. Vores eksempel med User -&gt; Student.
>
> **Polymorphism**: Virtuel methods tillader os at tilføje polymorphism. Virtuel methods er at subclasses som er nedarvet fra base class kan overskrive methods \(override\).
>
> **Division of responsibility: **De har hver deres ansvar. F.eks. i et eksempel med Course og Student.

---

## Visual Studio

---

Et IDE \(integrated development environment\) fra Microsoft. Det benytter værktøjer, som gør det hele lettere for en som udvikler, som f.eks. IntelliSense der bl.a. indeholder Parameter Info, Quick Info og Complete word \(eksempel i Controller\). Det indeholder bl.a. ASP.NET, ADO.NET osv.

---

## Properties

---

-

---

## Model Validation

---

-

---

## Ajax \(MVC\)

---

-

