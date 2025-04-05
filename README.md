import React, { useState } from "react"; import { Button } from "@/components/ui/button"; import { Card, CardContent } from "@/components/ui/card";

export default function FashionGalaFramePage() { const [image, setImage] = useState(null); const [framedImageUrl, setFramedImageUrl] = useState(null);

const handleImageUpload = (e) => { const file = e.target.files[0]; if (file) { const reader = new FileReader(); reader.onloadend = () => { setImage(reader.result); generateFramedImage(reader.result); }; reader.readAsDataURL(file); } };

const generateFramedImage = (imgSrc) => { const canvas = document.createElement("canvas"); const ctx = canvas.getContext("2d"); const frameImage = new Image(); const userImage = new Image();

frameImage.crossOrigin = "anonymous";
frameImage.src = "/frame.png"; // Use your frame image path
userImage.src = imgSrc;

userImage.onload = () => {
  canvas.width = 600;
  canvas.height = 600;
  ctx.drawImage(userImage, 0, 0, 600, 600);
  frameImage.onload = () => {
    ctx.drawImage(frameImage, 0, 0, 600, 600);
    setFramedImageUrl(canvas.toDataURL("image/png"));
  };
};

};

const handleDownload = () => { const link = document.createElement("a"); link.href = framedImageUrl; link.download = "fashion_gala_frame.png"; link.click(); };

return ( <div className="min-h-screen bg-white p-6 flex flex-col items-center justify-start"> <header className="w-full text-center mb-8"> <h1 className="text-4xl font-extrabold text-black mb-2"> Care Collective Fashion Gala Show 2025 </h1> <p className="text-lg text-gray-700"> Happening live on Facebook, April 6th, 2025 at 3 PM </p> </header>

<Card className="w-full max-w-md p-4 mb-4">
    <CardContent className="flex flex-col items-center">
      <input
        type="file"
        accept="image/*"
        onChange={handleImageUpload}
        className="mb-4"
      />
      {framedImageUrl && (
        <>
          <img
            src={framedImageUrl}
            alt="Framed Upload"
            className="rounded-xl shadow-md mb-4"
          />
          <Button onClick={handleDownload}>Download Framed Image</Button>
        </>
      )}
    </CardContent>
  </Card>
</div>

); }

