# wind-chill-calculator
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>체감온도 계산기</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; padding: 20px; }
        input { margin: 5px; padding: 10px; width: 100px; }
        button { padding: 10px 20px; cursor: pointer; }
        #result { font-size: 20px; margin-top: 10px; font-weight: bold; }
    </style>
</head>
<body>

    <h2>체감온도 계산기</h2>
    <p>온도(℃)와 풍속(km/h)을 입력하세요</p>

    <input type="number" id="temperature" placeholder="온도 (℃)">
    <input type="number" id="windSpeed" placeholder="풍속 (km/h)">
    <button onclick="calculateWindChill()">계산하기</button>

    <p id="result"></p>

    <script>
        function calculateWindChill() {
            let T = parseFloat(document.getElementById("temperature").value);
            let V = parseFloat(document.getElementById("windSpeed").value);
            
            if (isNaN(T) || isNaN(V) || V < 0) {
                document.getElementById("result").innerText = "올바른 값을 입력하세요.";
                return;
            }

            let windChill = 13.12 + 0.6215 * T - 11.37 * Math.pow(V, 0.16) + 0.3965 * T * Math.pow(V, 0.16);
            document.getElementById("result").innerText = `체감온도: ${windChill.toFixed(1)} ℃`;
        }
    </script>

</body>
</html>
