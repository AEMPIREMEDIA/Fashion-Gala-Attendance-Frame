<!DOCTYPE html><html lang="en"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Care Collective Fashion Gala</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f8f8f8;
        }
        .container {
            margin-top: 20px;
        }
        .frame {
            width: 300px;
            height: 400px;
            border: 5px solid #ff69b4;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background-color: white;
            margin: auto;
            position: relative;
        }
        .frame img {
            max-width: 90%;
            max-height: 70%;
        }
        .caption {
            position: absolute;
            bottom: 10px;
            width: 100%;
            font-size: 14px;
            background-color: rgba(255, 105, 180, 0.8);
            color: white;
            padding: 5px;
        }
        #download {
            margin-top: 10px;
            padding: 10px 20px;
            background-color: #ff69b4;
            color: white;
            border: none;
            cursor: pointer;
            display: none;
        }
        @media (max-width: 400px) {
            .frame {
                width: 90%;
                height: auto;
            }
            .frame img {
                max-height: 60%;
            }
        }
    </style>
</head>
<body>
    <h1>Care Collective Live Facebook Fashion Gala Show</h1>
    <p>Join us on Sunday, April 6th!</p>
    <div class="container">
        <input type="file" id="upload" accept="image/*">
        <div class="frame" id="photo-frame">
            <p>Upload your photo here</p>
            <div class="caption">I am attending the Care Collective Fashion Gala!</div>
        </div>
        <button id="download">Download Image</button>
    </div>
    <script>
        document.getElementById('upload').addEventListener('change', function(event) {
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const img = document.createElement('img');
                    img.src = e.target.result;
                    img.alt = 'User uploaded photo for the Fashion Gala frame';
                    const frame = document.getElementById('photo-frame');
                    frame.innerHTML = '';
                    frame.appendChild(img);
                    const caption = document.createElement('div');
                    caption.className = 'caption';
                    caption.innerText = 'I am attending the Care Collective Fashion Gala!';
                    frame.appendChild(caption);
                    document.getElementById('download').style.display = 'block';
                };
                reader.readAsDataURL(file);
            }
        });document.getElementById('download').addEventListener('click', function() {
        const frame = document.getElementById('photo-frame');
        html2canvas(frame).then(canvas => {
            const link = document.createElement('a');
            link.href = canvas.toDataURL('image/png');
            link.download = 'fashion_gala_attendee.png';
            link.click();
        });
    });
</script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>

</body>
</html>
