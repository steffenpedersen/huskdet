# Backend Recap

* [x] MVC
* [x] [User interfaces](http://steffenp.dk/weblog/user-interfaces-with-asp-net/)
* [x] HTML Helper Methods
* [ ] Model binding
* [ ] Entity Framework
* [ ] Code First
* [ ] Data First
* [ ] Dynamic v. Strongly Typed Views
* [ ] C\# \(OOP\)
* [ ] Visual Studio
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




