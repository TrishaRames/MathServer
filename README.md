# Ex.05 Design a Website for Server Side Processing
## Date:28-11-24

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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

## PROGRAM :
'''
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lamp Filament Power Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #1b1bbd;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .calculator {
            background: #cfe34e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            width: 300px;
            text-align: center;
        }

        .calculator h1 {
            font-size: 1.5rem;
            margin-bottom: 20px;
            color: #b9ec11;
        }

        .calculator label {
            font-size: 1rem;
            color: #090c0a;
        }

        .calculator input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #26cddd;
            border-radius: 5px;
        }

        .calculator button {
            background-color: #df17b7;
            color: rgb(246, 241, 241);
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            margin-top: 10px;
        }

        .calculator button:hover {
            background-color: #186dc8;
        }

        .result {
            margin-top: 15px;
            font-size: 1.2rem;
            color: #0d0e0c;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <h1>Lamp Power Calculator</h1>
        <form id="powerForm">
            <label for="intensity">Intensity (I) in Amps:</label>
            <input type="number" id="intensity" name="intensity" placeholder="Enter intensity" required step="any">

            <label for="resistance">Resistance (R) in Ohms:</label>
            <input type="number" id="resistance" name="resistance" placeholder="Enter resistance" required step="any">

            <button type="button" onclick="calculatePower()">Calculate Power</button>
        </form>
        <div class="result" id="result"></div>
    </div>

    <script>
        function calculatePower() {
            const intensity = parseFloat(document.getElementById('intensity').value);
            const resistance = parseFloat(document.getElementById('resistance').value);

            if (!isNaN(intensity) && !isNaN(resistance)) {
                const power = Math.pow(intensity, 2) * resistance;
                document.getElementById('result').innerText = `Power (P): ${power.toFixed(2)} Watts`;
            } else {
                document.getElementById('result').innerText = "Please enter valid values for both fields.";
            }
        }
    </script>
</body>
</html>
'''

## SERVER SIDE PROCESSING:

def power_calculator(request):
    power = None  

    if request.method == 'POST':
        
        intensity = request.POST.get('intensity')
        resistance = request.POST.get('resistance')

        
        if intensity and resistance:
            try:
            
                I = float(intensity)
                R = float(resistance)
                power = I**2 * R
                print('intensity=',I)
                print('resistance=',R)
                print('power=',power)  

            except ValueError:
                power = "Invalid input. Please enter numerical values."

    
    return render(request, 'mathapp/math.html', {'power': power})
## HOMEPAGE:
![alt text](<Screenshot (56).png>)
![alt text](<Screenshot (57).png>)

## RESULT:
The program for performing server side processing is completed successfully.
