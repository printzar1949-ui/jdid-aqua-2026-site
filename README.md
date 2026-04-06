<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <title>AquaVia BMI</title>

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">

    <style>
        body {
            background: #f4f7ff;
        }
        .card {
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }
        #result {
            font-size: 22px;
            font-weight: bold;
            margin-top: 15px;
        }
    </style>

    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
</head>

<body>

<div class="container mt-5">
    <div class="row justify-content-center">

        <div class="col-md-5">
            <div class="card p-4">

                <h3 class="text-center mb-3">AquaVia BMI Calculator</h3>

                <label>الطول (سم):</label>
                <input id="txbHeight" class="form-control" placeholder="مثال: 170">

                <label class="mt-2">الوزن (كغ):</label>
                <input id="txbWeight" class="form-control" placeholder="مثال: 70">

                <button class="btn btn-primary mt-3" id="ButtonCal">
                    احسب BMI
                </button>

                <div id="result" class="text-center"></div>

            </div>
        </div>

    </div>
</div>

<script>
$(function () {

    $('#ButtonCal').click(function () {

        let height = parseFloat($('#txbHeight').val());
        let weight = parseFloat($('#txbWeight').val());

        if (!height || !weight) {
            $('#result').html("⚠️ الرجاء إدخال القيم بشكل صحيح");
            return;
        }

        height = height / 100;

        let bmi = weight / (height * height);
        let status = "";

        if (bmi < 18.5) status = "نحيف";
        else if (bmi < 25) status = "طبيعي";
        else if (bmi < 30) status = "زيادة وزن";
        else status = "سمنة";

        $('#result').html(
            "BMI: " + bmi.toFixed(2) + "<br>الحالة: " + status
        );

    });

});
</script>

</body>
</html>
