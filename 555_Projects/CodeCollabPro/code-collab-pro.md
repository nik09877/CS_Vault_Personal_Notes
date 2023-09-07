1. In `FileUploading.jsx` while downloading code we need to do this for it to work in `FireFox`
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
2. Read about yjs ydoc and y-webrtc and signalling servers
3. In node server was trying to access a env variable without requiring dotenv.config()
4. react-graph-vis Graph is not working
5. Couldn't parse Leetcode problems