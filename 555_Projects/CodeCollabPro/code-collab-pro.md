1. In `FileUploading.jsx` while downloading code we need to do this for it to work in FireFox
```javascript
//DOWNLOAD CODE

  const TextFile = () => {
    const element = document.createElement('a');
    const file = new Blob([code], { type: 'text/plain' });

    element.href = URL.createObjectURL(file);
    element.download = 'CollabCodePro.txt';
    // Required for this to work in FireFox
    document.body.appendChild(element); 
    element.click();
  };
```