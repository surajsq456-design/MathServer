# Ex.04 Design a Website for Server Side Processing
## Date:17-12-2025

## AIM:
To create a web page to calculate vehicle mileage and fuel efficiency using server-side scripts.

## FORMULA:
M = D / F
<br> M --> Mileage (in km/l)
<br> D --> Distance Travelled (in km)
<br> F --> Fuel Consumed (in l)

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM:
```
sum.htm

<html>
<head>
    <title>Mileage Calculator</title>
    <style>
        body 
        {
            background: linear-gradient(white,pink,grey,black);
        }
        .id1 
        {
            text-align: center;
            color: rgb(0, 0, 0);
        }
        .box 
        {
            text-align: center;
            width: 30%;
            background-color: palevioletred;
            border: solid 6px black;
            padding: 25px;
            margin: 60px auto;
        }
        font{
            font-weight: bold;

        }
    </style>
</head>
<body>
    <h1 class="id1"><u>The Mileage Calculator</u></h1>
    <div class="box">
        <h2><font>Suraj R (25002481)</font></h2><br>
        <form method="post">
            {% csrf_token %}
            <label>Distance Travelled (km)</label><br>
            <input type="number" name="distance"><br><br>

            <label>Liters Consumed (L)</label><br>
            <input type="number" name="liters"><br><br>

            <button type="submit">Calculate</button>
            <br><br>
            <label>Fuel consumed per km(Km/L)</label><br>
            <input type="number" name="Mileage" value="{{mileage}}">
    </div>
    </footer>
</body>
</html>

views.py

from django.shortcuts import render


def mileage(request):
    km = int(request.POST.get('distance', 0))
    l = int(request.POST.get('liters', 0))

    mileage = km / l if request.method == 'POST' and l != 0 else 0

    print("kilometer=", km)
    print("liter=", l)
    print("mileage=", mileage)

    return render(request, 'suraj/sum.htm', {'km': km, 'l': l, 'mileage': mileage})

urls.py

from django.urls import path
from suraj import views
urlpatterns = [
    path('', views.mileage, name='mileage'),
]
```

## OUTPUT - SERVER SIDE:
![alt text](<Screenshot 2025-12-17 102718.png>)

## OUTPUT - WEBPAGE:
![alt text](<Screenshot 2025-12-17 102643.png>)

## RESULT:
The a web page to calculate vehicle mileage and fuel efficiency using server-side scripts is created successfully.
