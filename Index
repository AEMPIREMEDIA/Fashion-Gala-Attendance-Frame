<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Photo Frame Uploader</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 20px;
    }
    .frame {
      border: 10px solid #ff66cc;
      padding: 10px;
      background: white;
      display: inline-block;
      position: relative;
    }
    .frame img {
      max-width: 100%;
      height: auto;
      display: block;
    }
    .caption {
      background: #ff66cc;
      color: white;
      padding: 10px;
      font-size: 18px;
    }
    #download {
      margin-top: 20px;
      padding: 10px 20px;
      background-color: #ff66cc;
      color: white;
      border: none;
      cursor: pointer;
      font-size: 16px;
    }
    input[type="file"] {
      margin-bottom: 20px;
    }
  </style>
</head>
<body>
  <h1>Upload Your Photo</h1>
  <input type="file" id="imageUpload" accept="image/*">
  <div id="photoArea" class="frame" style="display:none;">
    <img id="uploadedImage" src="" alt="Uploaded">
    <div class="caption">I am attending the Care Collective Fashion Gala!</div>
  </div>
  <button id="download" style="display:none;">Download Framed Image</button>  <script>
    const imageUpload = document.getElementById('imageUpload');
    const uploadedImage = document.getElementById('uploadedImage');
    const photoArea = document.getElementById('photoArea');
    const downloadButton = document.getElementById('download');

    imageUpload.addEventListener('change', function(event) {
      const file = event.target.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onload = function(e) {
          uploadedImage.src = e.target.result;
          photoArea.style.display = 'inline-block';
          downloadButton.style.display = 'inline-block';
        }
        reader.readAsDataURL(file);
      }
    });

    downloadButton.addEventListener('click', function() {
      html2canvas(photoArea).then(canvas => {
        const link = document.createElement('a');
        link.download = 'framed-photo.png';
        link.href = canvas.toDataURL();
        link.click();
      });
    });
  </script>  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script></body>
</html>
