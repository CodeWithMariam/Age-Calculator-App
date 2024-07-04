# Age Calculator

This project is a simple age calculator that allows users to input their birthdate and calculates their age in years, months, and days. The calculation updates dynamically using JavaScript.

## Features
- Input for user's birthdate.
- Calculates age in years, months, and days.
- Displays the calculated age dynamically.

## How It Works
The JavaScript code listens for changes in the birthdate input field. When a date is entered, it calculates the age by comparing the birthdate with the current date and displays the result in a user-friendly format.

## Code Explanation
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Age Calculator</title>
</head>
<body>
    <h1>Age Calculator</h1>
    <input type="date" id="date">
    <button onclick="calculateAge()">Calculate Age</button>
    <p id="result"></p>

    <script>
        let userInput = document.getElementById("date");
        userInput.max = new Date().toISOString().split("T")[0];
        let result = document.getElementById("result");

        function calculateAge(){
            let birthDate = new Date(userInput.value);

            let d1 = birthDate.getDate(); // Use getDate instead of getDay
            let m1 = birthDate.getMonth() + 1;
            let y1 = birthDate.getFullYear();

            let today = new Date();

            let d2 = today.getDate(); // Use getDate instead of getDay
            let m2 = today.getMonth() + 1;
            let y2 = today.getFullYear();

            let d3, m3, y3;

            y3 = y2 - y1;

            if(m2 >= m1){
                m3 = m2 - m1;
            } else {
                y3--;
                m3 = 12 + m2 - m1;
            }
            
            if(d2 >= d1){
                d3 = d2 - d1;
            } else {
                m3--;
                d3 = getDaysInMonth(y1, m1) + d2 - d1;
            }
            if(m3 < 0){
                m3 = 11;
                y3--;
            }
            result.innerHTML = `You are <span>${y3}</span> years, <span>${m3}</span> months, and <span>${d3}</span> days old`;
        }

        function getDaysInMonth(year, month){
            return new Date(year, month, 0).getDate();
        }
    </script>
</body>
</html>
```
## Explanation
This section provides a detailed explanation of how the code works. The calculateAge function computes the difference between the birthdate and the current date in years, months, and days. The result is then displayed dynamically on the web page. The getDaysInMonth function is used to handle month and day calculations correctly.

##  Contributing
If you'd like to contribute to this project, please fork the repository and submit a pull request.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

## Additional Resources
Here are some articles that might help you understand the concepts used in this project:

- [JavaScript Date Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)
- [JavaScript Event Listeners](https://developer.mozilla.org/en-US/docs/Web/API/EventListener)
- [Calculating Age in JavaScript](https://www.javatpoint.com/calculate-age-using-javascript)
