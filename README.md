<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Care Collective Fashion Gala Frame</title>
  <style>
    body {
      background-image: url('data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAgGBgcGBQgHBwcJCQgKDBQNDAsLDBkSEw8UHRofHh0aHBwgJC4nICIsIxwcKDcpLDAx');
      background-size: cover;
      background-position: center;
      height: 100vh;
      margin: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      font-family: Arial, sans-serif;
    }.container {
  background: rgba(255, 255, 255, 0.9);
  border-radius: 15px;
  padding: 20px;
  text-align: center;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.3);
}

canvas {
  margin-top: 20px;
  border-radius: 50%;
}

input, button {
  margin: 10px;
}

#nameInput {
  padding: 8px;
  font-size: 16px;
  width: 250px;
}

  </style>
</head>
<body>
  <div class="container">
    <h2>Care Collective Fashion Gala Frame</h2>
    <input type="file" id="imageUpload" accept="image/*" />
    <br />
    <input type="text" id="nameInput" placeholder="Enter your name" />
    <br />
    <button onclick="generateImage()">Generate Image</button>
    <a id="downloadLink" style="display: none;" download="care_collective_frame.png">Download Image</a>
    <canvas id="canvas" width="400" height="400"></canvas>
  </div>  <script>
    const logo = new Image();
    logo.src = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAKAAAACgCAYAAACLz2ctAAABBmlDQ1BJQ0MgUHJvZmlsZQAAeJxjYGCSYAACJgEGhty8kqIgdyeF'; // Truncated for brevity

    function generateImage() {
      const fileInput = document.getElementById('imageUpload');
      const name = document.getElementById('nameInput').value;
      const canvas = document.getElementById('canvas');
      const ctx = canvas.getContext('2d');

      if (!fileInput.files[0]) return alert('Please upload a picture');

      const reader = new FileReader();
      reader.onload = function(event) {
        const uploadedImage = new Image();
        uploadedImage.onload = function() {
          ctx.clearRect(0, 0, canvas.width, canvas.height);

          // Draw circular clipped user image
          ctx.save();
          ctx.beginPath();
          ctx.arc(200, 200, 180, 0, Math.PI * 2, true);
          ctx.closePath();
          ctx.clip();
          ctx.drawImage(uploadedImage, 0, 0, 400, 400);
          ctx.restore();

          // Draw the logo
          ctx.drawImage(logo, 120, 120, 160, 160);

          // Add text overlay
          ctx.fillStyle = '#00cc00';
          ctx.font = '16px Arial';
          ctx.textAlign = 'center';
          ctx.fillText('I will be Attending Care Collective', 200, 330);
          ctx.fillText('Fashion Gala Show on Sunday 6th April, 2025', 200, 350);
          ctx.fillText('by 3pm Nigerian time', 200, 370);
          ctx.fillText(name, 200, 390);

          const downloadLink = document.getElementById('downloadLink');
          downloadLink.href = canvas.toDataURL();
          downloadLink.style.display = 'inline';
        };
        uploadedImage.src = event.target.result;
      };
      reader.readAsDataURL(fileInput.files[0]);
    }
  </script></body>
</html>
