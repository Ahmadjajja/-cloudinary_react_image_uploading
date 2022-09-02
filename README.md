# -cloudinary_react_image_uploading



import React, { useState } from 'react'
import axios from "axios"
const App = () => {
  
  const [imageSelected, setImageSelected] = useState("") 
  const [url, setUrl] = useState("");

  const uploadImage = () => {
    const formData = new FormData();
    formData.append("file", imageSelected)
    formData.append("upload_preset", "kgbsmcv4")
    axios.post(
      "https://api.cloudinary.com/v1_1/jajja-group-of-company/image/upload",
      formData
    ).then((response) => {
      console.log("response=> ", response.data.url);
      setUrl(response.data.url)
    });
  }
  return (
    <div>
      <div>
        <input type="file" onChange={(event) => setImageSelected(event.target.files[0])}></input>
        <button onClick={uploadImage}>Upload</button>
      </div>
      <div>
        <h1>Uploaded image will be displayed here</h1>
        <img src={url} />
      </div>
    </div>
  )
}
export default App;




helpful video link: https://youtu.be/Y-VgaRwWS3o
