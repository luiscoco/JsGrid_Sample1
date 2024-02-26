# JsGrid Sample1

Absolutely! Here's the complete source code for the jsGrid application, organized into their respective files.

Project Structure

jsGridDemo (Project Root)
wwwroot
css
jsgrid.min.css
jsgrid-theme.min.css
js
jsgrid.min.js
Controllers
HomeController.cs
Models
Person.cs
Views
Home
Index.cshtml
jsGridDemo.csproj
Program.cs
Files

1. Models/Person.cs

C#
namespace jsGridDemo.Models
{
    public class Person
    {
        public int Id { get; set; }
        public string Name { get; set; }
        public int Age { get; set; }
    }
}
Usa el código con precaución.
2. Controllers/HomeController.cs

C#
namespace jsGridDemo.Controllers
{
    using Microsoft.AspNetCore.Mvc;
    using jsGridDemo.Models;
    using System.Collections.Generic;

    public class HomeController : Controller
    {
        public IActionResult Index()
        {
            return View();
        }

        public IActionResult GetGridData()
        {
            var people = new List<Person>
            {
                new Person { Id = 1, Name = "John Doe", Age = 30 },
                new Person { Id = 2, Name = "Jane Smith", Age = 25 },
                // ... more data
            };
            return Json(people);
        }
    }
}
Usa el código con precaución.
3. Views/Home/Index.cshtml

HTML
<!DOCTYPE html>
<html>
<head>
    <title>jsGrid Integration</title>
    <link rel="stylesheet" href="~/css/jsgrid.min.css" />
    <link rel="stylesheet" href="~/css/jsgrid-theme.min.css" />
</head>
<body>
    <div id="jsGrid"></div>

    <script src="~/js/jsgrid.min.js"></script>
    <script>
        $("#jsGrid").jsGrid({
            width: "100%",
            height: "400px",

            sorting: true,
            paging: true,

            data: [], 

            fields: [
                { name: "Id", type: "number", width: 50 },
                { name: "Name", type: "text" },
                { name: "Age", type: "number"  }
            ],

            controller: {
                loadData: function() {
                    return $.ajax({
                        type: "GET",
                        url: "/Home/GetGridData"
                    });
                }
            }
        });
    </script>
</body>
</html>
Usa el código con precaución.
Remember:

Download jsGrid files if you haven't already and place them in the 'wwwroot' directory.
Adjust paths if your project structure differs.



## 1.



## 2. 



## 3. 



## 4 .

