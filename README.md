<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>เครื่องคำนวณ BMI</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        .container {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        input, button {
            display: block;
            width: 100%;
            margin: 10px 0;
            padding: 5px;
        }
        #result {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>เครื่องคำนวณ BMI</h2>
        <input type="number" id="weight" placeholder="น้ำหนัก (กิโลกรัม)">
        <input type="number" id="height" placeholder="ส่วนสูง (เซนติเมตร)">
        <button onclick="calculateBMI()">คำนวณ BMI</button>
        <div id="result"></div>
    </div>

    <script>
        alert("ใส่น้ำหนักและส่วนสูงของคุณ")
        function calculateBMI() {
            const weight = parseFloat(document.getElementById('weight').value);
            const height = parseFloat(document.getElementById('height').value) / 100; // แปลงเป็นเมตร
           
            if (isNaN(weight) || isNaN(height) || height === 0) {
                document.getElementById('result').innerHTML = 'กรุณากรอกข้อมูลให้ถูกต้อง';
                return;
            }

            const bmi = weight / (height * height);
            let interpretation = '';

            if (bmi < 18.5) {
                interpretation = 'มีความเสี่ยงต่อโรคต่ำ';
            } else if (bmi < 22.9) { 
                interpretation = 'มีความเสี่ยงต่อโรคต่างๆน้อยที่สุด'; 
            } else if (bmi < 24.9) { 
                interpretation = 'ถือว่ายังมีความเสี่ยงมากกว่าคนปกติ'; 
            } else if (bmi < 29.9) { 
                interpretation = 'ยังมีความเสี่ยงต่อการเกิดโรค'; 
            } else if (bmi > 30.0) { 
                interpretation = 'เสี่ยงต่อการเกิดโรค'; 
            }






            document.getElementById('result').innerHTML = `ค่า BMI ของคุณคือ: ${bmi.toFixed(2)}<br>คุณอยู่ในเกณฑ์: ${interpretation}`;
        }
    </script>
</body>
</html>
