﻿# image-jpeg-convert

# Example
---
**NOTE**
```
import './App.css';
import { useState } from 'react';
import jpegConveter from 'jpeg-convert';

function App() {
  const [image,setImage] = useState();
  const readFileAsync = (file) => new Promise((resolve, reject) => {
    const reader = new FileReader();
    reader.onload = () => {
      resolve(reader.result);
    };
    reader.onerror = reject;
    reader.readAsDataURL(file);
  });
  const handleChange = async (name,value) => {
    console.log(value);
    const fileArray = jpegConveter(value);
    const result =  await readFileAsync(fileArray);
    const [, fileContent] = result.split(',');
    setImage(fileContent);
    console.log('data', fileArray);
  } 
  return (
    <div className="App">
     <input type="file" onChange={(e)=>{handleChange('hello',e.target.files[0])}}/>
     <img src={`data:image/jpeg;base64,${image}`} alt="hello" sizes="max-width: 710px) 120px,
            (max-width: 991px) 193px,
            278px"/>
    </div>
  );
}

export default App;
```
---
